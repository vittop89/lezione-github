# Lezione 7 — Issues, Projects e lavoro di gruppo

**Durata:** 1 ora
**Obiettivo:** Usare le Issues per segnalare problemi e proporre miglioramenti, e i Projects per organizzare il lavoro di gruppo.

---

## Parte 1 — Le Issues: il sistema di segnalazioni (15 min)

Le **Issues** sono lo strumento di GitHub per gestire:
- Bug (errori nel codice)
- Richieste di nuove funzionalità
- Domande o discussioni sul progetto
- Attività da completare

Pensale come dei "post-it digitali" collegati al progetto.

### Esercizio: crea la tua prima Issue

Vai sul tuo repository `il-mio-primo-repo` su GitHub e segui questi passi:

### Passo 1 — Apri la tab Issues

Clicca sulla tab **Issues** nella barra in alto del repository.

### Passo 2 — Crea una nuova Issue

Clicca il pulsante verde **New issue** e compila:

- **Title:** "Aggiungere una pagina 'Chi siamo' al progetto"
- **Description:**
  ```
  ## Descrizione
  Sarebbe utile aggiungere un file chi-siamo.md con le informazioni
  su tutti i membri del gruppo che hanno contribuito al progetto.

  ## Cosa fare
  - [ ] Creare il file chi-siamo.md
  - [ ] Aggiungere nome e classe di ogni membro
  - [ ] Aggiungere il link nel README
  ```

Clicca **Submit new issue**.

### Passo 3 — Osserva la Issue

Ogni Issue ha:
- Un **numero** (es. `#1`) che la identifica.
- Una **discussione** dove si può commentare.
- Uno **stato**: Open (aperta) o Closed (chiusa/risolta).

### Passo 4 — Usa le Label

Le **Label** (etichette) categorizzano le Issues. Sulla destra della Issue, clicca **Labels** e aggiungi:
- `enhancement` (miglioramento) — per nuove funzionalità
- Oppure crea una label personalizzata come `lezione` cliccando "Edit labels"

### Le Label predefinite di GitHub

| Label | Significato |
|-------|------------|
| `bug` | Qualcosa non funziona |
| `enhancement` | Nuova funzionalità o miglioramento |
| `documentation` | Miglioramenti alla documentazione |
| `good first issue` | Adatta a chi è nuovo nel progetto |
| `help wanted` | L'autore chiede aiuto |
| `question` | Domanda o richiesta di chiarimento |


## Parte 2 — Risolvere una Issue con un commit (10 min)

Le Issues si possono **chiudere automaticamente** facendo riferimento al loro numero nel messaggio di commit.

### Esercizio

Risolviamo la Issue #1 che abbiamo appena creato.

```bash
cd ~/progetti-github/il-mio-primo-repo
```

Crea un branch dedicato:

```bash
git checkout -b feature/chi-siamo
```

Crea il file richiesto:

```bash
echo "# Chi Siamo" > chi-siamo.md
echo "" >> chi-siamo.md
echo "## Membri del progetto" >> chi-siamo.md
echo "" >> chi-siamo.md
echo "| Nome | Classe | Ruolo |" >> chi-siamo.md
echo "|------|--------|-------|" >> chi-siamo.md
echo "| [Il tuo nome] | [La tua classe] | Creatore del progetto |" >> chi-siamo.md
```

Fai il commit con un messaggio speciale:

```bash
git add chi-siamo.md
git commit -m "Aggiunto file chi-siamo.md - Closes #1"
```

La parola chiave **Closes #1** dice a GitHub di chiudere automaticamente la Issue numero 1 quando questo commit arriva su `main`.

```bash
git push -u origin feature/chi-siamo
```

Ora vai su GitHub, crea una Pull Request e fai il merge. Poi controlla: la Issue #1 dovrebbe essersi chiusa automaticamente!

### Parole chiave per chiudere le Issues

Puoi usare una qualsiasi di queste nel messaggio di commit:
- `Closes #1`
- `Fixes #1`
- `Resolves #1`


## Parte 3 — GitHub Projects: la lavagna del progetto (15 min)

I **Projects** di GitHub sono lavagne digitali (simili a Trello) per organizzare il lavoro. Ogni attività è una scheda che si sposta tra le colonne.

### Passo 1 — Crea un nuovo Project

1. Vai sul tuo repository su GitHub.
2. Clicca la tab **Projects**.
3. Clicca **New project**.
4. Scegli il template **Board** (lavagna Kanban).
5. Dai un nome al progetto: "Progetto di classe - Sito web".
6. Clicca **Create**.

### Passo 2 — Le colonne

Il template Board ha tre colonne predefinite:

| Colonna | Significato |
|---------|------------|
| **Todo** | Attività da fare |
| **In Progress** | Attività in corso |
| **Done** | Attività completate |

### Passo 3 — Aggiungi delle schede

Clicca il `+` nella colonna **Todo** e aggiungi queste attività:

1. "Creare la pagina principale (index.html)"
2. "Aggiungere lo stile CSS"
3. "Scrivere la pagina 'Chi siamo'"
4. "Aggiungere immagini al progetto"
5. "Pubblicare su GitHub Pages"

### Passo 4 — Collega le Issues

Puoi anche aggiungere Issues esistenti al Project:
1. Clicca `+` in una colonna.
2. Seleziona **Add item from repository**.
3. Scegli le Issues da collegare.

### Passo 5 — Assegna i compiti

Se lavori in gruppo, ogni scheda può essere assegnata a un membro:
1. Clicca su una scheda.
2. Nel pannello che si apre, cerca "Assignees".
3. Seleziona il compagno a cui assegnare l'attività.

### Passo 6 — Sposta le schede

Mentre lavori, sposta le schede trascinandole:
- Quando inizi un'attività: dalla colonna **Todo** a **In Progress**.
- Quando la completi: da **In Progress** a **Done**.


## Parte 4 — Esercizio di gruppo: pianificare un progetto (15 min)

Lavorate in gruppi di 3-4 persone. Ogni gruppo pianifica un mini-progetto usando Issues e Projects.

### Il progetto: un sito web della classe

Il proprietario del gruppo crea un nuovo repository chiamato `sito-classe-[sezione]` (es. `sito-classe-3A`).

### Passo 1 — Creare le Issues (tutti i membri)

Ogni membro del gruppo crea almeno 2 Issues. Ecco degli esempi:

- "Creare la struttura HTML della homepage" (label: `enhancement`)
- "Scrivere i contenuti della pagina Chi siamo" (label: `documentation`)
- "Scegliere i colori e il tema del sito" (label: `enhancement`)
- "Aggiungere le foto dei membri del gruppo" (label: `enhancement`)
- "Correggere l'errore nel titolo della homepage" (label: `bug`)

### Passo 2 — Organizzare il Project (il proprietario)

Il proprietario:
1. Crea un Project Board.
2. Aggiunge tutte le Issues alle colonne.
3. Assegna le Issues ai membri del gruppo.

### Passo 3 — Iniziare a lavorare

Ogni membro:
1. Prende una Issue assegnata.
2. Crea un branch dedicato (es. `feature/homepage`).
3. Lavora sulla modifica.
4. Fa push e apre una Pull Request che chiude la Issue.

Non dovete completare tutto il sito ora! L'obiettivo è praticare il flusso di lavoro.

### Passo 4 — Revisione reciproca

Prima di fare il merge:
1. Un altro membro del gruppo revisiona la Pull Request.
2. Lascia almeno un commento (positivo o con suggerimenti).
3. Approva la PR o chiede modifiche.


## Parte 5 — Buone pratiche per il lavoro di gruppo (5 min)

### Regole d'oro

1. **Un branch per ogni attività.** Non lavorare direttamente su `main`.
2. **Una Pull Request per ogni Issue.** Mantieni le modifiche piccole e focalizzate.
3. **Messaggi di commit chiari.** Chi legge deve capire cosa è cambiato.
4. **Revisionate il lavoro degli altri.** Leggere il codice altrui insegna molto.
5. **Usate le Issues per comunicare.** Scrivete commenti, chiedete chiarimenti, proponete idee.

### Assegnare i ruoli nel gruppo

| Ruolo | Responsabilità |
|-------|---------------|
| **Project Manager** | Gestisce il Project Board, assegna le attività |
| **Sviluppatore** | Scrive codice e apre Pull Request |
| **Revisore** | Controlla le Pull Request degli altri |
| **Documentatore** | Scrive README, commenti e documentazione |

Ogni membro può avere più ruoli!


## Riepilogo

Oggi hai imparato a:

- Creare e gestire **Issues** per organizzare il lavoro.
- **Chiudere Issues automaticamente** con i messaggi di commit.
- Usare **GitHub Projects** come lavagna Kanban per gestire le attività.
- Lavorare in **gruppo** seguendo un flusso di lavoro professionale.

---

**Lezione precedente:** [06 - Collaborazione e Pull Request](06%20-%20Collaborazione%20e%20Pull%20Request.md)
**Prossima lezione:** [08 - GitHub Pages e progetto finale](08%20-%20GitHub%20Pages%20e%20progetto%20finale.md)
