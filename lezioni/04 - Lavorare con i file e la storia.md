# Lezione 4 – Lavorare con i file e la storia

**Durata:** 1 ora
**Obiettivo:** Imparare a gestire le modifiche ai file, consultare la storia del progetto e usare `.gitignore`.

---

> ## 🖥️ Apri il terminale nel tuo ambiente
>
> | Ambiente | Come aprire il terminale |
> |----------|--------------------------|
> | ☁️ **Codespaces** | `Ctrl + `` ` — sei già nella cartella del progetto |
> | 💻 **VS Code locale** | `Ctrl + `` ` — assicurati di essere nella cartella giusta con `pwd` |
> | 🖥️ **GitHub Desktop** | Repository → Open in Git Bash |

---

## Parte 1 — Preparazione (5 min)

Apri il terminale e vai nel repository che hai creato nella Lezione 3:

```bash
cd ~/progetti-github/il-mio-primo-repo
```

Verifica di essere nel posto giusto:

```bash
git status
```

Se tutto è in ordine, vedrai `On branch main` e nessuna modifica pendente.


## Parte 2 — Vedere le differenze con `git diff` (10 min)

Quando modifichi un file, Git può mostrarti esattamente cosa è cambiato **prima** che tu faccia il commit. Questo è utilissimo per controllare il tuo lavoro.

### Esercizio pratico

Modifica il file `README.md`. Aprilo con un editor di testo (Notepad, VS Code, o qualsiasi altro) e aggiungi in fondo:

```
## Autore
Progetto creato da [Il tuo nome] per il corso di Git.
```

Salva il file. Ora nel terminale:

```bash
git diff
```

Vedrai qualcosa come:

```diff
diff --git a/README.md b/README.md
--- a/README.md
+++ b/README.md
@@ -5,3 +5,6 @@
 ## Contenuto
 - README.md: descrizione del progetto
 - chi-sono.txt: le mie informazioni
+
+## Autore
+Progetto creato da Mario Rossi per il corso di Git.
```

Le righe con `+` in verde sono quelle **aggiunte**. Le righe con `-` in rosso sarebbero quelle **rimosse**. Questo ti permette di rivedere le modifiche prima di fare il commit.

Ora salva la modifica:

```bash
git add README.md
git commit -m "Aggiunta sezione autore al README"
```


## Parte 3 — Esplorare la storia con `git log` (10 min)

La storia del progetto è uno dei superpoteri di Git. Vediamo come esplorarla.

### Versione base

```bash
git log
```

Mostra tutti i commit con i dettagli completi. Premi `q` per uscire se la lista è lunga.

### Versione compatta

```bash
git log --oneline
```

Mostra ogni commit su una riga sola: hash abbreviato + messaggio.

### Versione grafica (nel terminale)

```bash
git log --oneline --graph
```

Questo sarà più utile quando useremo i branch (Lezione 5), ma provalo già ora.

### Vedere cosa è cambiato in un commit specifico

Prendi l'hash di un commit dalla lista (es. `abc1234`) e scrivi:

```bash
git show abc1234
```

Vedrai esattamente quali file sono stati modificati e come.


## Parte 4 — Annullare le modifiche (15 min)

Capita a tutti di fare un errore. Git offre diversi modi per tornare indietro.

### Caso 1: hai modificato un file ma NON hai fatto `git add`

Aggiungi una riga sbagliata al README:

```bash
echo "Questa riga e' un errore!" >> README.md
```

Verifica:

```bash
git diff
```

Per annullare e tornare alla versione dell'ultimo commit:

```bash
git checkout -- README.md
```

Controlla: la riga sbagliata è sparita!

```bash
cat README.md
```

### Caso 2: hai fatto `git add` ma NON hai fatto il commit

```bash
echo "Un altro errore!" >> README.md
git add README.md
```

Per togliere il file dallo staging (senza perdere le modifiche nel file):

```bash
git restore --staged README.md
```

Ora il file è di nuovo "modificato ma non staged". Se vuoi annullare anche le modifiche:

```bash
git checkout -- README.md
```

### Caso 3: hai fatto il commit ma vuoi tornare indietro

Facciamo un commit "sbagliato" di proposito:

```bash
echo "Testo sbagliato" > errore.txt
git add errore.txt
git commit -m "Aggiunto file con errore (di proposito)"
```

Per annullare l'ultimo commit mantenendo i file:

```bash
git revert HEAD
```

Git creerà un **nuovo commit** che annulla le modifiche del precedente. Ti chiederà un messaggio: puoi accettare quello proposto premendo `:wq` e Invio (se si apre Vim) oppure salvando e chiudendo l'editor.

Controlla il log:

```bash
git log --oneline
```

Vedrai sia il commit sbagliato che il commit di "annullamento". La storia è preservata!

### Tabella riassuntiva

| Situazione | Comando |
|-----------|---------|
| File modificato, non aggiunto allo stage | `git checkout -- nomefile` |
| File aggiunto allo stage, non committato | `git restore --staged nomefile` |
| Commit già fatto, vuoi annullarlo | `git revert HEAD` |


## Parte 5 — Il file `.gitignore` (10 min)

Non tutti i file devono essere tracciati da Git. Ad esempio:
- File temporanei del sistema (`.DS_Store` su Mac, `Thumbs.db` su Windows)
- File con password o dati sensibili
- Cartelle generate automaticamente (come `node_modules` nei progetti web)

Il file `.gitignore` dice a Git quali file ignorare.

### Creare un `.gitignore`

```bash
# Crea il file .gitignore
echo "# File di sistema" > .gitignore
echo ".DS_Store" >> .gitignore
echo "Thumbs.db" >> .gitignore
echo "" >> .gitignore
echo "# File temporanei" >> .gitignore
echo "*.tmp" >> .gitignore
echo "*.log" >> .gitignore
echo "" >> .gitignore
echo "# Cartelle da ignorare" >> .gitignore
echo "temp/" >> .gitignore
```

### Testare il `.gitignore`

Creiamo un file che dovrebbe essere ignorato:

```bash
echo "Questo file verra' ignorato" > prova.tmp
git status
```

Noterai che `prova.tmp` **non** appare nella lista dei file non tracciati, mentre `.gitignore` sì. Git sta già ignorando i file `.tmp`!

### Committare il `.gitignore`

```bash
git add .gitignore
git commit -m "Aggiunto .gitignore per escludere file temporanei e di sistema"
```

### Sintassi di `.gitignore`

| Pattern | Cosa ignora |
|---------|------------|
| `*.log` | Tutti i file che finiscono con `.log` |
| `temp/` | L'intera cartella `temp` e il suo contenuto |
| `segreto.txt` | Uno specifico file chiamato `segreto.txt` |
| `!importante.log` | **NON** ignorare `importante.log` (eccezione) |
| `docs/*.pdf` | I file PDF solo nella cartella `docs` |


## Parte 6 — Esercizio finale e push (10 min)

Mettiamo tutto insieme.

### Esercizio

1. Crea un file `appunti.md` con un breve riassunto di quello che hai imparato oggi.
2. Modifica `chi-sono.txt` aggiungendo il nome del tuo linguaggio di programmazione preferito (o quello che vorresti imparare).
3. Usa `git diff` per vedere le modifiche a `chi-sono.txt`.
4. Aggiungi entrambi i file allo stage con un solo comando:
   ```bash
   git add appunti.md chi-sono.txt
   ```
5. Fai il commit.
6. Carica tutto su GitHub:
   ```bash
   git push
   ```
7. Vai su GitHub e verifica che le modifiche siano visibili.

### Cheat sheet aggiornata

```bash
git diff                       # Vedi le modifiche non ancora in stage
git diff --staged              # Vedi le modifiche in stage
git log --oneline              # Storia compatta dei commit
git show HASH                  # Dettagli di un commit specifico
git checkout -- nomefile       # Annulla modifiche non in stage
git restore --staged nomefile  # Rimuovi un file dallo stage
git revert HEAD                # Annulla l'ultimo commit (creandone uno nuovo)
```


## Riepilogo

Oggi hai imparato a:

- Usare `git diff` per **vedere le differenze** prima di fare commit.
- Esplorare la **storia del progetto** con `git log` e `git show`.
- **Annullare modifiche** in tre situazioni diverse.
- Usare `.gitignore` per **escludere file** dal tracciamento.

---

**Lezione precedente:** [Lezione 03 — Il primo repository](03%20-%20primo%20repository%20e%20primi%20commit.md)
**Prossima lezione:** [Lezione 05 — Branch e merge](05%20-%20Branch%20e%20merge.md)
