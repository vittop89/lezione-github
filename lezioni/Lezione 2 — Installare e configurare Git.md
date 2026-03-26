# Lezione 2 — Installare e configurare Git

**Durata:** 1 ora
**Obiettivo:** Installare Git sul proprio computer, configurarlo con il proprio nome e email, e prendere confidenza con il terminale.

---

## Parte 1 — Il terminale: il tuo nuovo strumento (10 min)

Prima di installare Git, dobbiamo fare amicizia con il **terminale** (chiamato anche *riga di comando* o *shell*). È una finestra dove scrivi comandi testuali al computer invece di cliccare con il mouse.

### Come aprire il terminale

- **Windows:** cerca "Git Bash" nel menu Start (lo avrai dopo l'installazione) oppure premi `Win + R`, scrivi `cmd` e premi Invio.
- **macOS:** apri l'app "Terminale" (la trovi in Applicazioni > Utility).
- **Linux:** premi `Ctrl + Alt + T`.

### Comandi base da conoscere

Prova questi comandi nel terminale. Scrivili e premi **Invio** dopo ognuno:

```bash
# Mostra in quale cartella ti trovi adesso
pwd

# Elenca i file nella cartella corrente
ls

# Crea una nuova cartella chiamata "prova"
mkdir prova

# Entra nella cartella "prova"
cd prova

# Torna alla cartella precedente
cd ..
```

Non preoccuparti se all'inizio sembra strano: diventerà naturale con la pratica!


## Parte 2 — Installare Git (15 min)

Segui le istruzioni per il tuo sistema operativo.

### Windows

1. Vai su **https://git-scm.com/download/win**
2. Scarica l'installer (il download dovrebbe partire automaticamente).
3. Apri il file scaricato e segui l'installazione:
   - Alla schermata "Select Components", lascia tutto come predefinito.
   - Alla schermata "Choosing the default editor", seleziona **Notepad** (più semplice per iniziare).
   - Per tutte le altre schermate, clicca **Next** e infine **Install**.
4. Al termine, cerca "**Git Bash**" nel menu Start e aprilo.

### macOS

1. Apri il **Terminale**.
2. Scrivi il comando seguente e premi Invio:
   ```bash
   git --version
   ```
3. Se Git non è installato, macOS ti chiederà di installare gli "Xcode Command Line Tools". Clicca **Installa** e attendi.
4. Al termine, riprova `git --version` per verificare.

### Linux (Ubuntu/Debian)

1. Apri il **Terminale**.
2. Scrivi:
   ```bash
   sudo apt update
   sudo apt install git
   ```
3. Inserisci la tua password quando richiesto e conferma con `s` (sì).

### Verifica l'installazione

Su qualsiasi sistema, scrivi nel terminale:

```bash
git --version
```

Dovresti vedere qualcosa come:

```
git version 2.43.0
```

Il numero potrebbe essere diverso, l'importante è che non dia errore. Se vedi un messaggio simile, Git è installato correttamente!


## Parte 3 — Configurare Git (10 min)

Git ha bisogno di sapere chi sei, così ogni modifica che farai sarà "firmata" con il tuo nome. Questa configurazione si fa una volta sola.

### Passo 1 — Imposta il tuo nome

Scrivi nel terminale (sostituendo con il tuo vero nome):

```bash
git config --global user.name "Mario Rossi"
```

### Passo 2 — Imposta la tua email

Usa la **stessa email** con cui hai creato l'account GitHub nella Lezione 1:

```bash
git config --global user.email "mario.rossi@email.com"
```

### Passo 3 — Verifica la configurazione

```bash
git config --list
```

Dovresti vedere, tra le varie righe:

```
user.name=Mario Rossi
user.email=mario.rossi@email.com
```

### Passo 4 — Imposta il nome del branch predefinito

```bash
git config --global init.defaultBranch main
```

Questo fa sì che quando crei un nuovo repository, il branch principale si chiami `main` (è lo standard attuale).


## Parte 4 — Collegare Git a GitHub con SSH (15 min)

Per comunicare tra il tuo computer e GitHub in modo sicuro e senza dover inserire la password ogni volta, usiamo una **chiave SSH**. Pensala come una coppia di chiavi: una la tieni tu (privata), l'altra la dai a GitHub (pubblica).

### Passo 1 — Genera la chiave SSH

Nel terminale scrivi:

```bash
ssh-keygen -t ed25519 -C "la-tua-email@email.com"
```

Quando ti chiede dove salvare il file, premi semplicemente **Invio** (usa il percorso predefinito).

Quando ti chiede una passphrase, puoi premere **Invio** due volte per lasciarla vuota (più semplice per iniziare).

### Passo 2 — Copia la chiave pubblica

- **Windows (Git Bash):**
  ```bash
  cat ~/.ssh/id_ed25519.pub
  ```
- **macOS:**
  ```bash
  cat ~/.ssh/id_ed25519.pub | pbcopy
  ```
- **Linux:**
  ```bash
  cat ~/.ssh/id_ed25519.pub
  ```

Seleziona e copia **tutto** il testo che appare (inizia con `ssh-ed25519` e finisce con la tua email).

### Passo 3 — Aggiungi la chiave su GitHub

1. Vai su **https://github.com** e accedi al tuo account.
2. Clicca sulla tua **foto profilo** in alto a destra.
3. Vai su **Settings**.
4. Nel menu a sinistra, clicca **SSH and GPG keys**.
5. Clicca il pulsante verde **New SSH key**.
6. In "Title" scrivi un nome riconoscibile, ad esempio: `PC scuola` o `Laptop personale`.
7. In "Key" incolla la chiave che hai copiato.
8. Clicca **Add SSH key**.

### Passo 4 — Testa il collegamento

```bash
ssh -T git@github.com
```

Se ti chiede di confermare, scrivi `yes` e premi Invio.

Dovresti vedere un messaggio come:

```
Hi tuousername! You've successfully authenticated, but GitHub does not provide shell access.
```

Se vedi questo messaggio, sei collegato! Il tuo computer e GitHub ora comunicano in modo sicuro.


## Parte 5 — Esercizio di riepilogo (10 min)

Verifica di aver completato tutto correttamente. Esegui questi comandi e controlla i risultati:

```bash
# 1. Verifica che Git sia installato
git --version

# 2. Verifica il tuo nome
git config user.name

# 3. Verifica la tua email
git config user.email

# 4. Verifica il collegamento con GitHub
ssh -T git@github.com
```

### Checklist personale

Segna con una ✓ quello che hai completato:

- [ ] Git è installato sul mio computer
- [ ] Ho configurato il mio nome in Git
- [ ] Ho configurato la mia email in Git
- [ ] Ho generato una chiave SSH
- [ ] Ho aggiunto la chiave SSH al mio account GitHub
- [ ] Il comando `ssh -T git@github.com` funziona

Se qualcosa non funziona, chiedi aiuto al docente o a un compagno prima di andare avanti.


## Riepilogo

Oggi hai:

- Imparato i **comandi base del terminale** (`pwd`, `ls`, `mkdir`, `cd`).
- **Installato Git** sul tuo computer.
- **Configurato** Git con il tuo nome e la tua email.
- **Collegato** il tuo computer a GitHub tramite SSH.

Dalla prossima lezione iniziamo a usare Git per davvero!

---

**Lezione precedente:** [Lezione 1 — Cos'è Git e GitHub?](01-cos-e-git-e-github.md)
**Prossima lezione:** [Lezione 3 — Il primo repository](03-primo-repository.md)
