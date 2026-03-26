# Lezione 5 – Branch e merge

**Durata:** 1 ora
**Obiettivo:** Capire cosa sono i branch, crearli, spostarsi tra di essi, e fare il merge per unire le modifiche.

---

> ## 🖥️ Apri il terminale nel tuo ambiente
>
> | Ambiente | Come aprire |
> |----------|-------------|
> | ☁️ **Codespaces** | `Ctrl + `` ` — già nella cartella del progetto |
> | 💻 **VS Code locale** | `Ctrl + `` ` — già nella cartella se hai aperto il progetto corretto |
> | 🖥️ **GitHub Desktop** | I branch si gestiscono anche graficamente dalla barra in alto → "Current Branch" |
>
> 💡 **GitHub Desktop** mostra i branch in modo visuale: clicca "Current Branch" per creare, cambiare o fare merge di branch senza usare il terminale.

---

## Parte 1 — Cos'è un branch? (10 min)

Immagina di avere una versione funzionante del tuo progetto. Vuoi aggiungere una nuova funzionalità, ma hai paura di rompere qualcosa. Cosa fai?

Con i **branch** (rami) puoi creare una copia parallela del tuo progetto, lavorarci liberamente e, quando tutto funziona, riunire le modifiche alla versione principale.

### Analogia

Pensa a un albero:
- Il **tronco** è il branch `main`: la versione stabile e ufficiale del progetto.
- I **rami** sono i branch di sviluppo: ci lavori sopra senza toccare il tronco.
- Quando un ramo è maturo, lo **innnesti** di nuovo nel tronco (merge).

```
main:         A --- B --- C --------- F
                          \          /
feature:                   D --- E --
```

In questo schema, i commit D ed E sono stati fatti sul branch `feature` senza toccare `main`. Il commit F è il **merge**: le modifiche di `feature` vengono unite a `main`.

### Perché usare i branch?

- Puoi **sperimentare** senza paura di rompere il progetto.
- Più persone possono lavorare su **funzionalità diverse** contemporaneamente.
- Tieni il branch `main` sempre **funzionante e pulito**.


## Parte 2 — Creare e usare i branch (15 min)

Apri il terminale e vai nel tuo repository:

```bash
cd ~/progetti-github/il-mio-primo-repo
```

### Passo 1 — Visualizza i branch esistenti

```bash
git branch
```

Vedrai:

```
* main
```

L'asterisco `*` indica il branch su cui ti trovi adesso.

### Passo 2 — Crea un nuovo branch

Creiamo un branch per aggiungere una pagina "i miei progetti":

```bash
git branch pagina-progetti
```

Verifica:

```bash
git branch
```

```
* main
  pagina-progetti
```

Il branch esiste, ma sei ancora su `main`.

### Passo 3 — Spostati sul nuovo branch

```bash
git checkout pagina-progetti
```

```
Switched to branch 'pagina-progetti'
```

Verifica:

```bash
git branch
```

```
  main
* pagina-progetti
```

Ora l'asterisco è su `pagina-progetti`.

### Scorciatoia: crea e spostati in un solo comando

La prossima volta puoi usare:

```bash
git checkout -b nome-del-branch
```

Questo crea il branch E ci si sposta sopra in un colpo solo.

### Passo 4 — Lavora sul branch

Crea un nuovo file:

```bash
echo "# I Miei Progetti" > progetti.md
echo "" >> progetti.md
echo "## Progetto 1: Il mio primo repo" >> progetti.md
echo "Il primo repository creato durante il corso di Git." >> progetti.md
echo "" >> progetti.md
echo "## Progetto 2: (in arrivo)" >> progetti.md
echo "Qui descrivero' il mio prossimo progetto." >> progetti.md
```

Fai il commit:

```bash
git add progetti.md
git commit -m "Aggiunta pagina con la lista dei miei progetti"
```

Ora aggiungi anche un link nel README:

```bash
echo "" >> README.md
echo "## Link utili" >> README.md
echo "- [I miei progetti](progetti.md)" >> README.md

git add README.md
git commit -m "Aggiunto link alla pagina progetti nel README"
```

### Passo 5 — Confronta i branch

Torna su `main`:

```bash
git checkout main
```

Prova a guardare i file:

```bash
ls
```

Noterai che `progetti.md` **non c'è**! Il file esiste solo sul branch `pagina-progetti`. Ogni branch ha la sua versione dei file.

Torna su `pagina-progetti`:

```bash
git checkout pagina-progetti
ls
```

Ora `progetti.md` riappare. Questa è la magia dei branch!


## Parte 3 — Il merge: unire i branch (15 min)

Hai finito il lavoro sul branch `pagina-progetti` e sei soddisfatto. È il momento di portare le modifiche su `main`.

### Passo 1 — Spostati su main

Per fare il merge devi essere sul branch che **riceve** le modifiche:

```bash
git checkout main
```

### Passo 2 — Esegui il merge

```bash
git merge pagina-progetti
```

Vedrai un messaggio simile a:

```
Updating abc1234..def5678
Fast-forward
 README.md    | 3 +++
 progetti.md  | 7 +++++++
 2 files changed, 10 insertions(+)
 create mode 100644 progetti.md
```

"Fast-forward" significa che Git ha semplicemente spostato `main` in avanti per includere i commit di `pagina-progetti`. È il tipo di merge più semplice.

### Passo 3 — Verifica

```bash
ls
```

Ora `progetti.md` è presente anche su `main`!

```bash
git log --oneline --graph
```

Vedrai tutta la storia dei commit.

### Passo 4 — Elimina il branch (opzionale)

Se il branch ha esaurito il suo scopo:

```bash
git branch -d pagina-progetti
```

```
Deleted branch pagina-progetti (was def5678).
```

Le modifiche sono già in `main`, quindi il branch non serve più.


## Parte 4 — Gestire i conflitti (15 min)

A volte due branch modificano le **stesse righe** dello stesso file. Quando provi a fare il merge, Git non sa quale versione scegliere e ti chiede di risolvere il **conflitto** manualmente. Facciamo un esempio guidato.

### Passo 1 — Crea la situazione di conflitto

```bash
# Assicurati di essere su main
git checkout main

# Modifica la prima riga di chi-sono.txt
echo "Nome: [Il tuo nome] - Studente di liceo" > chi-sono-temp.txt
cat chi-sono.txt >> chi-sono-temp.txt
mv chi-sono-temp.txt chi-sono.txt
git add chi-sono.txt
git commit -m "Aggiornato il nome con il ruolo su main"
```

Ora crea un branch dove modifichi la stessa riga in modo diverso:

```bash
# Torna al commit precedente per creare il branch
git checkout -b modifica-nome HEAD~1

# Modifica la stessa riga in modo diverso
echo "Nome: [Il tuo nome] - Futuro programmatore" > chi-sono-temp.txt
cat chi-sono.txt >> chi-sono-temp.txt
mv chi-sono-temp.txt chi-sono.txt
git add chi-sono.txt
git commit -m "Aggiornato il nome con l'aspirazione su modifica-nome"
```

### Passo 2 — Prova il merge

```bash
git checkout main
git merge modifica-nome
```

Vedrai:

```
Auto-merging chi-sono.txt
CONFLICT (content): Merge conflict in chi-sono.txt
Automatic merge failed; fix conflicts and then commit the result.
```

### Passo 3 — Risolvi il conflitto

Apri `chi-sono.txt` con un editor di testo. Vedrai qualcosa come:

```
<<<<<<< HEAD
Nome: [Il tuo nome] - Studente di liceo
=======
Nome: [Il tuo nome] - Futuro programmatore
>>>>>>> modifica-nome
```

Questa è la sintassi dei conflitti di Git:
- Tra `<<<<<<< HEAD` e `=======` c'è la versione di `main`.
- Tra `=======` e `>>>>>>> modifica-nome` c'è la versione del branch.

**Devi scegliere** quale versione tenere (o combinare le due). Modifica il file manualmente, rimuovendo i marcatori di conflitto. Ad esempio:

```
Nome: [Il tuo nome] - Studente di liceo e futuro programmatore
```

### Passo 4 — Completa il merge

Salva il file e poi:

```bash
git add chi-sono.txt
git commit -m "Risolto conflitto: combinato ruolo e aspirazione"
```

Il conflitto è risolto! Puoi eliminare il branch:

```bash
git branch -d modifica-nome
```


## Parte 5 — Push e riepilogo (5 min)

Carica tutto su GitHub:

```bash
git push
```

### Comandi dei branch

```bash
git branch                      # Elenca i branch
git branch nome-branch          # Crea un nuovo branch
git checkout nome-branch        # Spostati su un branch
git checkout -b nome-branch     # Crea e spostati (scorciatoia)
git merge nome-branch           # Unisci un branch nel branch corrente
git branch -d nome-branch       # Elimina un branch
```

### Convenzioni per i nomi dei branch

| Prefisso | Uso |
|---------|-----|
| `feature/` | Nuova funzionalità: `feature/pagina-contatti` |
| `fix/` | Correzione di un bug: `fix/errore-calcolo` |
| `docs/` | Modifiche alla documentazione: `docs/aggiorna-readme` |


## Riepilogo

Oggi hai imparato a:

- Creare **branch** per lavorare in parallelo senza rischi.
- **Spostarti** tra branch con `git checkout`.
- **Unire** le modifiche con `git merge`.
- **Risolvere i conflitti** quando due branch modificano lo stesso file.

---

**Lezione precedente:** [Lezione 04 — Lavorare con i file e la storia](04%20-%20Lavorare%20con%20i%20file%20e%20la%20storia.md)
**Prossima lezione:** [Lezione 06 — Collaborazione e Pull Request](06%20-%20Collaborazione%20e%20Pull%20Request.md)
