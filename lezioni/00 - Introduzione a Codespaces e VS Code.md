# 📘 Lezione 00 – Scegliere il proprio ambiente di lavoro

**Durata:** 1 ora
**Obiettivo:** Creare il proprio account GitHub, capire come seguire le lezioni usando GitHub Codespaces (nel browser) oppure VS Code in locale, e fare il fork del repository per iniziare a lavorare.

---

## 🔐 Passo 0 — Crea il tuo account GitHub

Prima di fare qualsiasi altra cosa ti serve un **account GitHub**. Se ce l'hai già, salta direttamente alla sezione successiva.

1. Vai su **https://github.com** e clicca **Sign up**
2. Inserisci la tua email, scegli una password e un **username** (sarà pubblico — sceglilo bene!)
   - Buone idee: `mario-rossi`, `mrossi2010`, `marco-dev`
   - Da evitare: nomi offensivi o troppo lunghi
3. Verifica l'email cliccando il link che GitHub ti manda
4. Completa il profilo: foto e una breve bio (opzionale ma consigliato)

> 💡 La Lezione 01 approfondisce i concetti di Git e GitHub e ti guida nell'esplorazione della piattaforma. Per ora ti basta l'account creato.

---

## 🧭 Prima di tutto: fai il Fork del repository

Per seguire le lezioni hai bisogno di una **tua copia personale** del repository. Questa operazione si chiama **fork** e ti permette di lavorare liberamente senza modificare l'originale.

### Come fare il fork

1. Vai su **https://github.com/vittop89/lezione-github**
2. Clicca sul pulsante **Fork** in alto a destra
3. Seleziona il tuo account come destinazione
4. Clicca **Create fork**

> ✅ Il fork non richiede nessuna Pull Request. Lavorerai in autonomia sulla tua copia.

---

## 🖥️ Quale ambiente scegliere?

Puoi seguire le lezioni in due modi diversi. Scegli quello più adatto alla tua situazione:

| Situazione | Ambiente consigliato |
|---|---|
| Sei a scuola su un PC condiviso | ☁️ **GitHub Codespaces** (nel browser) |
| Hai un PC personale con VS Code | 💻 **VS Code in locale** |
| Vuoi lavorare offline | 💻 **VS Code in locale** |
| Non vuoi installare nulla | ☁️ **GitHub Codespaces** |

---

### Differenze tra Codespaces e locale

| Funzionalità | ☁️ Codespaces | 💻 VS Code locale |
|---|---|---|
| Installazione richiesta | ❌ No | ✅ Git + VS Code |
| Funziona da qualsiasi PC | ✅ Sì | ❌ Solo sul tuo PC |
| Funziona offline | ❌ No | ✅ Sì |
| Git già configurato | ✅ Automatico | ⚙️ Manuale (una volta) |
| Ore gratuite | 60 ore/mese | ♾️ Illimitate |
| Velocità avvio | ~30 secondi | Istantaneo |

---

## ☁️ Opzione A – GitHub Codespaces (nel browser, zero installazioni)

### Cos'è GitHub Codespaces

GitHub Codespaces è un ambiente di sviluppo completo che funziona **direttamente nel browser**. Contiene:

- 🖥️ **VS Code nel browser** — identico all'app desktop
- 🐧 **Linux** con Git già installato e configurato
- 📂 **Terminale integrato** per eseguire i comandi
- 📄 **Supporto Markdown** con anteprima formattata
- ⚡ **Zero configurazione** — è pronto in 30 secondi

È perfetto per seguire le lezioni da qualsiasi computer, anche senza permessi di installazione.

### Come aprire Codespaces sul tuo fork

1. Vai sulla pagina del **tuo fork** su GitHub (es. `https://github.com/TUO-USERNAME/lezione-github`)
2. Clicca sul pulsante verde **`<> Code`** in alto a destra
3. Seleziona la scheda **Codespaces**
4. Clicca su **"Create codespace on main"**

Dopo 20-30 secondi si aprirà VS Code nel browser, con tutti i file del repository già disponibili.

### Aprire e leggere i file Markdown in Codespaces

I file delle lezioni hanno estensione `.md`. Per leggerli:

1. Clicca sul file nella **barra laterale sinistra** (Explorer)
2. Il file si aprirà nell'editor di testo

**Per l'anteprima formattata:**

- Premi `Ctrl + Shift + V` — apre l'anteprima in una nuova scheda
- Oppure premi `Ctrl + K`, poi `V` — apre editor e anteprima **affiancati** (consigliato!)
- Oppure clicca l'icona 📖 in alto a destra nell'editor

### Usare il terminale in Codespaces

Per aprire il terminale integrato:

- Menu **Terminal → New Terminal**
- Oppure `Ctrl + `` ` (backtick, il tasto sotto Esc)

Nel terminale puoi eseguire tutti i comandi Git delle lezioni:

```bash
# Esempio di comandi che userai nelle lezioni
git status
git add .
git commit -m "Il mio primo commit"
git push
```

> 💡 In Codespaces, Git è già configurato con il tuo account GitHub. Non devi fare `git config` manualmente.

### Salvare e sincronizzare le modifiche in Codespaces

I file modificati in Codespaces vengono salvati **nel Codespace**, ma per aggiornare il tuo fork su GitHub devi fare un push:

```bash
git add .
git commit -m "Descrizione delle modifiche"
git push
```

Oppure usa la **barra laterale Source Control** (icona del grafo a sinistra) per fare commit con l'interfaccia grafica.

### Chiudere o eliminare un Codespace

**Per chiudere:**
- Chiudi semplicemente la scheda del browser. Il Codespace rimane salvato.

**Per riaprire:**
- Vai su **github.com/codespaces** e clicca sul tuo Codespace

**Per eliminarlo (e liberare spazio):**
1. Vai su **https://github.com/codespaces**
2. Trova il Codespace relativo a `lezione-github`
3. Clicca sui tre puntini `...` → **Delete**

> 📌 GitHub offre **60 ore/mese gratuite** di Codespaces per gli account gratuiti.

---

## 💻 Opzione B – VS Code in locale (sul tuo PC personale)

### Cosa ti serve

- **Git** installato sul PC ([scarica qui](https://git-scm.com))
- **VS Code** installato ([scarica qui](https://code.visualstudio.com))
- Un account **GitHub** (già creato nella Lezione 1)
- Opzionale: **GitHub Desktop** ([scarica qui](https://desktop.github.com)) — per gestire Git con interfaccia grafica

### Clonare il tuo fork in locale

Dopo aver fatto il fork, devi **clonare** il repository sul tuo computer:

**Metodo 1 – Da terminale (Git Bash / Terminal):**

```bash
git clone https://github.com/TUO-USERNAME/lezione-github.git
cd lezione-github
```

**Metodo 2 – Da GitHub Desktop:**

1. Apri **GitHub Desktop**
2. Clicca **File → Clone Repository**
3. Scegli il tuo fork dalla lista o incolla l'URL
4. Scegli la cartella dove salvarlo
5. Clicca **Clone**

**Metodo 3 – Da VS Code direttamente:**

1. Apri VS Code
2. Premi `Ctrl + Shift + P`
3. Scrivi `Git: Clone` e premi Invio
4. Incolla l'URL del tuo fork
5. Scegli la cartella e clicca **Open**

### Aprire il progetto in VS Code

Se hai clonato da terminale:

```bash
code lezione-github
```

Se hai clonato con GitHub Desktop:
- Clicca **"Open in Visual Studio Code"** nella schermata principale di GitHub Desktop

### Aprire e leggere i file Markdown in VS Code

1. Usa l'**Explorer** a sinistra (icona cartella) per navigare i file
2. Apri una lezione cliccando sul file `.md`
3. Per l'anteprima formattata: premi `Ctrl + K`, poi `V`

### Usare il terminale in VS Code locale

Apri il terminale integrato di VS Code:

- Menu **Terminal → New Terminal**
- Oppure `Ctrl + `` ` (backtick)

Il terminale si apre già nella cartella del progetto. Usa i comandi Git normalmente:

```bash
git status
git add .
git commit -m "Il mio primo commit"
git push
```

> 💡 Se hai configurato VS Code con il tuo account GitHub (tramite l'estensione GitHub), il push funzionerà senza inserire credenziali ogni volta.

### Configurare Git in locale (una volta sola)

Se è la prima volta che usi Git sul tuo PC:

```bash
git config --global user.name "Il Tuo Nome"
git config --global user.email "tua@email.com"
```

Usa la stessa email del tuo account GitHub.

## 🖱️ Usare un'interfaccia grafica invece del terminale

Se preferisci evitare i comandi, hai due alternative grafiche:

- **Source Control di VS Code / Codespaces** — l'icona dei branch (tre cerchi collegati) nella barra laterale sinistra, disponibile sia in VS Code locale che in Codespaces
- **GitHub Desktop** — app separata, solo per VS Code locale (non funziona in Codespaces)

| Operazione | Comando terminale | 🖱️ Source Control (VS Code / Codespaces) | 🖥️ GitHub Desktop |
|---|---|---|---|
| Vedere modifiche | `git status` | Pannello "Source Control" — lista file modificati | Scheda "Changes" |
| Aggiungere file | `git add .` | Clicca `+` accanto al file oppure "Stage All Changes" | Seleziona i file nella lista |
| Fare commit | `git commit -m "msg"` | Scrivi il messaggio nella casella → clicca **Commit** | Scrivi messaggio → "Commit to main" |
| Caricare | `git push` | Clicca **Sync Changes** (o l'icona ☁️ in basso) | Clicca "Push origin" |
| Scaricare | `git pull` | Clicca **Sync Changes** | Clicca "Fetch origin" |

> 💡 **Consiglio:** in Codespaces usa sempre la Source Control integrata — GitHub Desktop non è disponibile nel browser.

---

## ✅ Checklist prima di iniziare

Spunta le voci completate prima di passare alla Lezione 1:

- [ ] Ho un account GitHub su **github.com**
- [ ] Ho fatto il **fork** del repository `vittop89/lezione-github`
- [ ] Ho scelto il mio ambiente: **Codespaces** oppure **VS Code locale**
- [ ] Il progetto è aperto nell'ambiente scelto
- [ ] Riesco a vedere i file delle lezioni nella barra laterale
- [ ] Riesco ad aprire l'anteprima Markdown (`Ctrl+K`, poi `V`)
- [ ] Il terminale è aperto e funzionante

---

## 📝 Riepilogo

- **Fork** = copia personale del repo, senza modificare l'originale
- **Codespaces** = VS Code nel browser, zero installazioni, perfetto per PC scolastici
- **VS Code locale** = sul proprio PC, funziona offline, illimitato
- **GitHub Desktop** = alternativa grafica al terminale per chi preferisce evitare i comandi
- In entrambi gli ambienti il **terminale** funziona allo stesso modo per i comandi Git

---

**Prossima lezione:** [Lezione 01 – Cos'è Git e GitHub?](01%20-%20Cos'%C3%A8%20Git%20e%20GitHub.md)
