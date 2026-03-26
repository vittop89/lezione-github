# Lezione 8 — GitHub Pages e progetto finale

**Durata:** 1 ora
**Obiettivo:** Pubblicare un sito web gratuito con GitHub Pages e mettere in pratica tutto quello che hai imparato nelle lezioni precedenti.

---

## Parte 1 — Cos'è GitHub Pages? (5 min)

**GitHub Pages** è un servizio gratuito di GitHub che trasforma un repository in un sito web accessibile da chiunque con un indirizzo tipo:

```
https://tuo-username.github.io/nome-repo
```

Non servono server, hosting o carte di credito. Basta un repository con dei file HTML (o Markdown) e GitHub fa tutto il resto.

Cosa puoi pubblicare con GitHub Pages:
- Il tuo portfolio personale
- La documentazione di un progetto
- Un blog
- Un sito della classe
- Qualsiasi pagina web statica


## Parte 2 — Creare un sito con GitHub Pages (20 min)

### Passo 1 — Crea un nuovo repository

1. Vai su **https://github.com** e clicca **+** > **New repository**.
2. Nome del repository: `il-mio-sito`
3. Descrizione: "Il mio primo sito web pubblicato con GitHub Pages"
4. Seleziona **Public**.
5. Seleziona **Add a README file**.
6. Clicca **Create repository**.

### Passo 2 — Clona il repository

```bash
cd ~/progetti-github
git clone https://github.com/TUO-USERNAME/il-mio-sito.git
cd il-mio-sito
```

### Passo 3 — Crea il foglio di stile condiviso

Invece di copiare il CSS in ogni pagina, creiamo **un solo file** `style.css` che tutte le pagine condivideranno. Questo è il modo corretto di organizzare un sito web.

```bash
cat > style.css << 'FINE'
body {
    font-family: 'Segoe UI', Arial, sans-serif;
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    background-color: #f5f5f5;
    color: #333;
}
header {
    background-color: #2c3e50;
    color: white;
    padding: 30px;
    border-radius: 10px;
    text-align: center;
    margin-bottom: 30px;
}
h1 { margin: 0; }
.subtitle { color: #bdc3c7; margin-top: 10px; }
.card {
    background: white;
    padding: 20px;
    border-radius: 10px;
    margin-bottom: 20px;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}
.card h2 { color: #2c3e50; }
a { color: #3498db; }
footer {
    text-align: center;
    margin-top: 40px;
    color: #7f8c8d;
}
nav {
    text-align: center;
    margin-bottom: 30px;
}
nav a {
    margin: 0 15px;
    text-decoration: none;
    font-weight: bold;
}
.tag {
    display: inline-block;
    background: #3498db;
    color: white;
    padding: 3px 10px;
    border-radius: 15px;
    font-size: 0.85em;
    margin: 2px;
}
FINE
```

### Passo 4 — Crea la homepage

```bash
cat > index.html << 'FINE'
<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Il Mio Sito</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Il Mio Sito</h1>
        <p class="subtitle">Creato con GitHub Pages</p>
    </header>

    <nav>
        <a href="index.html">Home</a>
        <a href="chi-sono.html">Chi Sono</a>
        <a href="progetti.html">Progetti</a>
    </nav>

    <div class="card">
        <h2>Benvenuto!</h2>
        <p>
            Questo e' il mio primo sito web, pubblicato gratuitamente
            con GitHub Pages. L'ho creato durante il corso di Git
            e GitHub al liceo scientifico.
        </p>
    </div>

    <div class="card">
        <h2>Cosa trovi qui</h2>
        <p>
            In questo sito puoi scoprire chi sono, vedere i miei
            progetti e seguire il mio percorso di apprendimento
            nel mondo della programmazione.
        </p>
    </div>

    <footer>
        <p>Realizzato con GitHub Pages | Corso di Git per il Liceo</p>
    </footer>
</body>
</html>
FINE
```

### Passo 5 — Crea la pagina "Chi Sono"

```bash
cat > chi-sono.html << 'FINE'
<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chi Sono</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Chi Sono</h1>
    </header>

    <nav>
        <a href="index.html">Home</a>
        <a href="chi-sono.html">Chi Sono</a>
        <a href="progetti.html">Progetti</a>
    </nav>

    <div class="card">
        <h2>Le mie informazioni</h2>
        <p><strong>Nome:</strong> [Il tuo nome]</p>
        <p><strong>Classe:</strong> [La tua classe e sezione]</p>
        <p><strong>Scuola:</strong> Liceo Scientifico [nome della scuola]</p>
    </div>

    <div class="card">
        <h2>I miei interessi</h2>
        <p>
            Scrivi qui i tuoi interessi, le materie preferite,
            gli hobby e cosa vorresti fare in futuro.
        </p>
    </div>
</body>
</html>
FINE
```

### Passo 6 — Crea la pagina "Progetti"

```bash
cat > progetti.html << 'FINE'
<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>I Miei Progetti</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>I Miei Progetti</h1>
    </header>

    <nav>
        <a href="index.html">Home</a>
        <a href="chi-sono.html">Chi Sono</a>
        <a href="progetti.html">Progetti</a>
    </nav>

    <div class="card">
        <h2>Progetto 1: Il mio primo repository</h2>
        <p>Il primo progetto creato durante il corso di Git.</p>
        <span class="tag">Git</span>
        <span class="tag">GitHub</span>
    </div>

    <div class="card">
        <h2>Progetto 2: Il mio sito web</h2>
        <p>Questo sito! Pubblicato con GitHub Pages.</p>
        <span class="tag">HTML</span>
        <span class="tag">CSS</span>
        <span class="tag">GitHub Pages</span>
    </div>

    <div class="card">
        <h2>Progetto 3: (In arrivo)</h2>
        <p>Il prossimo progetto che realizzerai...</p>
    </div>
</body>
</html>
FINE
```

### Passo 7 — Commit e push

```bash
git add .
git commit -m "Creato sito web con homepage, chi-sono, progetti e style.css"
git push
```

### Passo 8 — Attiva GitHub Pages

1. Vai sul repository `il-mio-sito` su GitHub.
2. Clicca **Settings** (icona ingranaggio).
3. Nel menu a sinistra, clicca **Pages**.
4. Nella sezione "Source", seleziona:
   - **Branch:** `main`
   - **Folder:** `/ (root)`
5. Clicca **Save**.

Attendi 1-2 minuti, poi visita:

```
https://TUO-USERNAME.github.io/il-mio-sito/
```

Il tuo sito e' online!


## Parte 3 — Personalizza il sito (15 min)

Ora che il sito funziona, personalizzalo. Lavora usando il flusso che hai imparato: branch, commit, push.

### Esercizio

1. Crea un branch:
   ```bash
   git checkout -b personalizzazione
   ```

2. Modifica i file HTML sostituendo i segnaposto `[Il tuo nome]`, `[La tua classe]`, ecc. con le tue informazioni reali.

3. Cambia i colori! Apri `style.css` e modifica:
   - `background-color` nell'header (prova `#e74c3c` per rosso, `#27ae60` per verde, `#8e44ad` per viola)
   - `color` dei link

   Modificando un solo file cambierai l'aspetto di tutto il sito.

4. Aggiungi contenuti alle pagine.

5. Fai commit delle modifiche:
   ```bash
   git add .
   git commit -m "Personalizzato il sito con informazioni reali e colori custom"
   ```

6. Fai merge in main e push:
   ```bash
   git checkout main
   git merge personalizzazione
   git push
   ```

7. Aspetta 1-2 minuti e ricarica il sito nel browser per vedere le modifiche.


## Parte 4 — Progetto finale di gruppo (15 min)

Mettiamo in pratica TUTTO quello che avete imparato in queste 8 lezioni. Lavorate in gruppi di 3-4 persone.

### L'obiettivo

Creare un **sito web della classe** pubblicato con GitHub Pages.

### Organizzazione

1. **Il capogruppo** crea il repository `sito-classe-[sezione]` e attiva GitHub Pages.
2. Tutti i membri fanno **fork** del repository.
3. Il capogruppo crea un **Project Board** con le attivita' da fare.
4. Create delle **Issues** per ogni pagina o funzionalita'.
5. Ogni membro sceglie un'attivita' e la realizza su un **branch dedicato**.
6. Proponete le modifiche con **Pull Request**.
7. **Revisionate** il lavoro degli altri prima di fare il merge.

### Idee per le pagine

- Homepage con presentazione della classe
- Pagina "I nostri membri" con foto e bio di ognuno
- Pagina "Le nostre materie preferite"
- Pagina "I nostri progetti" con i link ai repository di ognuno
- Pagina "Galleria" con immagini

### Suggerimenti

- Partite dal template HTML di questa lezione e modificatelo.
- Usate un solo file `style.css` condiviso per tutte le pagine — modificate quello per cambiare il look dell'intero sito in un colpo solo.
- Fate commit piccoli e frequenti con messaggi chiari.
- Comunicate tramite le Issues e i commenti delle Pull Request.


## Parte 5 — Riepilogo del corso (5 min)

Complimenti! In 8 lezioni hai imparato tutto il necessario per usare Git e GitHub come un professionista.

### Mappa completa di Git e GitHub

Tutto quello che hai imparato in queste 8 lezioni, in un unico schema:

![Mappa completa Git e GitHub](assets/08-mappa-completa.svg)

### Cosa sai fare ora

| Lezione | Competenza |
|---------|-----------|
| 00 | Hai scelto il tuo ambiente (Codespaces o VS Code) e fatto il fork del repository |
| 01 | Sai cos'e' Git e GitHub e hai un account |
| 02 | Hai installato e configurato Git |
| 03 | Sai creare repository, fare commit e push |
| 04 | Sai gestire le modifiche, la storia e il .gitignore |
| 05 | Sai usare i branch e risolvere i conflitti |
| 06 | Sai collaborare con fork e pull request |
| 07 | Sai organizzare il lavoro con Issues e Projects |
| 08 | Sai pubblicare un sito con GitHub Pages |

### Come continuare

- **Personalizza il tuo profilo GitHub.** Crea un repository con lo stesso nome del tuo username e aggiungi un README: diventerà la tua pagina profilo!
- **Contribuisci a progetti open source.** Cerca Issues con la label "good first issue" su progetti che ti interessano.
- **Usa GitHub per i tuoi progetti scolastici.** Tesine, appunti, esercizi — tutto puo' essere versionato.
- **Impara un linguaggio di programmazione.** Python, JavaScript o HTML/CSS sono ottimi punti di partenza.
- **Esplora GitHub Education.** Su https://education.github.com puoi ottenere strumenti gratuiti per studenti.

### Il tuo profilo GitHub e' il tuo portfolio

Ogni commit che fai, ogni progetto che crei, ogni contributo che dai resta visibile sul tuo profilo. E' come un curriculum che si costruisce da solo mentre impari. Quando un giorno cercherai lavoro nel mondo dell'informatica, il tuo profilo GitHub parlera' per te.

---

**Lezione precedente:** [Lezione 07 — Issues, Projects e lavoro di gruppo](07%20-%20Issues%2C%20Projects%20e%20lavoro%20di%20gruppo.md)

---

*Corso completato! Buon coding!*
