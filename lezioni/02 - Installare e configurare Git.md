# Lezione 2 – Installare e configurare Git

**Durata:** 1 ora
**Obiettivo:** Configurare il proprio ambiente di lavoro (Codespaces o VS Code locale) e imparare i comandi base del terminale.

---

> ## 🖥️ Prima di iniziare: apri il terminale nel tuo ambiente
>
> **Se usi ☁️ GitHub Codespaces:**
> Il terminale è già pronto. Aprilo con `Ctrl + `` ` oppure da **Terminal → New Terminal**.
> Git è già installato e configurato con il tuo account. Puoi saltare la sezione "Installare Git" e andare direttamente alla **Parte 3**.
>
> **Se usi 💻 VS Code in locale:**
> Apri il terminale con `Ctrl + `` ` oppure da **Terminal → New Terminal**.
> Devi installare Git e configurarlo — segui tutte le parti di questa lezione.
>
> **Se usi 🖥️ GitHub Desktop:**
> Apri Git Bash da **Repository → Open in Git Bash** oppure usa il terminale integrato di VS Code.

---

## Parte 1 — Il terminale: il tuo nuovo strumento (10 min)

Il **terminale** è una finestra dove scrivi comandi testuali invece di cliccare col mouse. In VS Code e Codespaces si apre direttamente nell'editor — stesso identico comportamento in entrambi gli ambienti.

### Come aprire il terminale

| Ambiente | Come aprire |
|----------|-------------|
| ☁️ Codespaces | `Ctrl + `` ` oppure Terminal → New Terminal |
| 💻 VS Code locale | `Ctrl + `` ` oppure Terminal → New Terminal |
| 🖥️ GitHub Desktop | Repository → Open in Git Bash |

### Comandi base da conoscere

```bash
# Mostra in quale cartella ti trovi
pwd

# Elenca i file nella cartella corrente
ls

# Crea una nuova cartella
mkdir prova

# Entra nella cartella
cd prova

# Torna alla cartella precedente
cd ..
```

> 💡 In Codespaces e VS Code il terminale si apre già nella cartella del tuo progetto.

---

## Parte 2 — Installare Git (solo per VS Code locale) (15 min)

> ☁️ **Codespaces:** salta questa sezione — Git è già installato e pronto.

### Windows

1. Vai su **https://git-scm.com/download/win**
2. Scarica e avvia l'installer
3. Nella schermata "Choosing the default editor" seleziona **Visual Studio Code**
4. Per tutte le altre schermate lascia i valori predefiniti → **Next → Install**
5. Al termine riapri VS Code: il terminale integrato ora ha Git disponibile

### macOS

```bash
git --version
```

Se Git non è installato, macOS ti guiderà nell'installazione degli Xcode Command Line Tools.

### Linux

```bash
sudo apt update && sudo apt install git
```

### Verifica l'installazione

```bash
git --version
# Output atteso: git version 2.43.0 (o simile)
```

---

## Parte 3 — Configurare Git (10 min)

> ☁️ **Codespaces:** Git è già associato al tuo account GitHub. Verifica con `git config --list`.

Queste impostazioni firmano ogni tuo commit. Vanno impostate **una volta sola** per computer:

```bash
git config --global user.name "Mario Rossi"
git config --global user.email "mario.rossi@email.com"
```

> Usa la **stessa email** del tuo account GitHub!

Imposta il nome del branch predefinito:

```bash
git config --global init.defaultBranch main
```

Verifica la configurazione:

```bash
git config --list
```

---

## Parte 4 — Autenticarsi con GitHub (10 min)

### ☁️ Codespaces
Sei già autenticato automaticamente. Nessuna configurazione necessaria.

### 💻 VS Code locale — autenticazione HTTPS

Quando farai `git push` per la prima volta, VS Code aprirà automaticamente una finestra browser per accedere con il tuo account GitHub. Segui le istruzioni.

### 🖥️ GitHub Desktop

1. Apri GitHub Desktop
2. Vai su **File → Options → Accounts**
3. Clicca **Sign in to GitHub.com**
4. Completa il login nel browser

Una volta autenticato, push e pull funzioneranno senza inserire credenziali ogni volta.

---

## Parte 5 — Verifica finale (10 min)

Esegui questi comandi nel terminale del tuo ambiente:

```bash
# Git è installato?
git --version

# Il nome è configurato?
git config user.name

# L'email è configurata?
git config user.email
```

### Checklist

- [ ] Il terminale si apre nel mio ambiente (Codespaces o VS Code)
- [ ] `git --version` restituisce un numero di versione
- [ ] Nome e email sono configurati correttamente
- [ ] L'email corrisponde a quella del mio account GitHub

---

## Riepilogo

Hai imparato a:

- Aprire il **terminale** in Codespaces, VS Code e GitHub Desktop
- **Installare Git** (se sei in locale)
- **Configurare** Git con nome ed email
- **Autenticarti** con GitHub nel tuo ambiente

---

**Lezione precedente:** [Lezione 01 – Cos'è Git e GitHub?](01%20-%20Cos'%C3%A8%20Git%20e%20GitHub.md)
**Prossima lezione:** [Lezione 03 – Il primo repository](03%20-%20primo%20repository%20e%20primi%20commit.md)
