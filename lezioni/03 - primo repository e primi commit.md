# Lezione 3 — Il primo repository e i primi commit

**Durata:** 1 ora **Obiettivo:** Creare il tuo primo repository Git, fare i primi commit e pubblicarlo su GitHub.

---

## Parte 1 — Creare un repository locale (10 min)

Un **repository** (abbreviato "repo") è semplicemente una cartella del tuo computer a cui Git tiene traccia delle modifiche. Creiamone uno!

### Passo 1 — Crea la cartella del progetto

Apri il terminale (Git Bash su Windows) e scrivi:

```bash
# Vai nella tua cartella home
cd ~

# Crea una cartella per i tuoi progetti GitHub
mkdir progetti-github

# Entra nella cartella
cd progetti-github

# Crea la cartella del tuo primo progetto
mkdir il-mio-primo-repo

# Entra nel progetto
cd il-mio-primo-repo
```

### Passo 2 — Inizializza Git

Ora diciamo a Git di iniziare a monitorare questa cartella:

```bash
git init
```

Vedrai un messaggio simile a:

```
Initialized empty Git repository in /home/tuonome/progetti-github/il-mio-primo-repo/.git/
```

Git ha creato una cartella nascosta `.git` dentro il tuo progetto. È lì che Git salva tutta la storia delle modifiche. Non toccare mai questa cartella manualmente!

### Passo 3 — Verifica lo stato

```bash
git status
```

Questo comando ti dice "come sta" il tuo repository. Vedrai:

```
On branch main
No commits yet
nothing to commit
```

Significa: sei sul branch `main`, non hai ancora fatto nessun commit, e non ci sono file da salvare.

## Parte 2 — Il primo commit (15 min)

Un **commit** è come scattare una foto al tuo progetto in un momento preciso. Ogni commit ha:

- I file modificati
- Un messaggio che spiega cosa è cambiato
- La data e l'autore

### Il flusso di lavoro Git

Ecco come funziona il ciclo di lavoro con Git. Memorizza questi tre passaggi:

```
1. MODIFICA i file        →  Lavori normalmente sui tuoi file
2. AGGIUNGI allo stage    →  Scegli quali modifiche vuoi salvare (git add)
3. FAI IL COMMIT          →  Salvi l'istantanea con un messaggio (git commit)
```

### Passo 1 — Crea il tuo primo file

Creiamo un file README.md. Il README è il "biglietto da visita" di ogni progetto su GitHub.

```bash
echo "# Il Mio Primo Repository" > README.md
echo "" >> README.md
echo "Questo e' il mio primo progetto su GitHub!" >> README.md
echo "Creato durante il corso di Git per il liceo." >> README.md
```

Verifica che il file esista:

```bash
cat README.md
```

### Passo 2 — Controlla lo stato

```bash
git status
```

Ora vedrai:

```
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md
```

Git vede il file ma non lo sta ancora monitorando. È "untracked" (non tracciato).

### Passo 3 — Aggiungi il file all'area di staging

L'area di **staging** è come un vassoio dove metti le cose che vuoi fotografare prima di scattare la foto:

```bash
git add README.md
```

Controlla di nuovo lo stato:

```bash
git status
```

```
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
```

Il file è pronto per essere "fotografato" (committato).

### Passo 4 — Fai il commit

```bash
git commit -m "Aggiunto il file README con la descrizione del progetto"
```

Il flag `-m` serve per scrivere il messaggio del commit direttamente nel comando. Vedrai:

```
[main (root-commit) abc1234] Aggiunto il file README con la descrizione del progetto
 1 file changed, 3 insertions(+)
 create mode 100644 README.md
```

Hai fatto il tuo primo commit!

### Come scrivere un buon messaggio di commit

Il messaggio di commit deve spiegare **cosa** hai fatto e **perché**. Ecco alcune regole:

| Buoni messaggi                                    | Cattivi messaggi |
| ------------------------------------------------- | ---------------- |
| "Aggiunto file README con descrizione progetto"   | "update"         |
| "Corretta formula nell'esercizio 3"               | "fix"            |
| "Aggiunta pagina contatti al sito"                | "cose varie"     |
| "Rimosso codice duplicato nella funzione calcola" | "asdfsadf"       |

## Parte 3 — Fare altri commit (10 min)

Continuiamo a lavorare sul progetto per prendere confidenza con il ciclo add-commit.

### Esercizio: aggiungi un nuovo file

Crea un file `chi-sono.txt`:

```bash
echo "Nome: [Il tuo nome]" > chi-sono.txt
echo "Classe: [La tua classe]" >> chi-sono.txt
echo "Hobby: [I tuoi hobby]" >> chi-sono.txt
```

Ora fai il commit:

```bash
git add chi-sono.txt
git commit -m "Aggiunto file chi-sono con le informazioni personali"
```

### Esercizio: modifica un file esistente

Aggiungi una riga al README:

```bash
echo "" >> README.md
echo "## Contenuto" >> README.md
echo "- README.md: descrizione del progetto" >> README.md
echo "- chi-sono.txt: le mie informazioni" >> README.md
```

Fai il commit della modifica:

```bash
git add README.md
git commit -m "Aggiornato README con la lista dei file del progetto"
```

### Guarda la storia dei commit

```bash
git log
```

Vedrai tutti i tuoi commit in ordine cronologico (dal più recente al più vecchio), ognuno con:

- Un **hash** (codice univoco tipo `abc1234...`)
- L'**autore**
- La **data**
- Il **messaggio**

Per una versione più compatta:

```bash
git log --oneline
```

## Parte 4 — Pubblicare su GitHub (15 min)

Finora il repository esiste solo sul tuo computer. Ora lo pubblichiamo su GitHub così che sia accessibile online.

### Passo 1 — Crea il repository su GitHub

1. Vai su **https://github.com** e accedi.
2. Clicca il pulsante **+** in alto a destra e seleziona **New repository**.
3. Compila i campi:
   - **Repository name:** `il-mio-primo-repo`
   - **Description:** "Il mio primo progetto su GitHub — corso di Git per il liceo"
   - **Public** (lascia selezionato, così i compagni potranno vederlo)
   - **NON** selezionare "Add a README file" (l'abbiamo già creato noi!)
4. Clicca **Create repository**.

### Passo 2 — Collega il repository locale a GitHub

GitHub ti mostrerà delle istruzioni. Noi usiamo la sezione "…or push an existing repository from the command line". Nel terminale scrivi:

```bash
git remote add origin git@github.com:TUO-USERNAME/il-mio-primo-repo.git
```

Sostituisci `TUO-USERNAME` con il tuo nome utente GitHub.

Questo comando dice a Git: "Il repository remoto si chiama `origin` e si trova a questo indirizzo su GitHub".

### Passo 3 — Carica i commit su GitHub

```bash
git push -u origin main
```

Il flag `-u` collega il tuo branch locale `main` al branch remoto `main`. Dovrai usarlo solo la prima volta; le volte successive basterà scrivere `git push`.

Vedrai qualcosa come:

```
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
...
To github.com:TUO-USERNAME/il-mio-primo-repo.git
 * [new branch]      main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
```

### Passo 4 — Verifica su GitHub

Vai su `https://github.com/TUO-USERNAME/il-mio-primo-repo` nel browser. Dovresti vedere:

- I tuoi file (`README.md` e `chi-sono.txt`)
- Il contenuto del README visualizzato in basso
- La storia dei commit

Complimenti, il tuo primo progetto è online!

## Parte 5 — Esercizio finale (10 min)

Fai una modifica, committala e caricala su GitHub, tutto da solo.

1. Crea un file `interessi.md` con una lista dei tuoi interessi (scuola, sport, tecnologia...).
2. Aggiungi il file all'area di staging.
3. Fai un commit con un messaggio descrittivo.
4. Carica su GitHub con `git push`.
5. Vai su GitHub nel browser e verifica che il nuovo file sia apparso.

### Comandi da ricordare (cheat sheet)

```bash
git init                    # Inizializza un nuovo repo
git status                  # Controlla lo stato dei file
git add nomefile            # Aggiungi un file allo stage
git add .                   # Aggiungi TUTTI i file allo stage
git commit -m "messaggio"   # Salva un'istantanea (commit)
git log --oneline           # Vedi la storia dei commit
git remote add origin URL   # Collega il repo locale a GitHub
git push                    # Carica i commit su GitHub
```

## Riepilogo

Oggi hai imparato a:

- **Creare** un repository Git con `git init`.
- **Aggiungere** file all'area di staging con `git add`.
- **Salvare istantanee** del progetto con `git commit`.
- **Pubblicare** il repository su GitHub con `git push`.

---

**Lezione precedente:** [02 - Installare e configurare Git](02%20-%20Installare%20e%20configurare%20Git.md)
**Prossima lezione:** [04 - Lavorare con i file e la storia](04%20-%20Lavorare%20con%20i%20file%20e%20la%20storia.md)
