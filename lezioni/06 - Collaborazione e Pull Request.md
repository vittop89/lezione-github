# Lezione 6 — Collaborazione e Pull Request

**Durata:** 1 ora
**Obiettivo:** Imparare a collaborare con i compagni usando fork, clone e pull request su GitHub.

---

## Parte 1 — Come funziona la collaborazione su GitHub (10 min)

Finora hai lavorato da solo sul tuo progetto. Ma il vero potere di GitHub è la **collaborazione**: più persone che lavorano sullo stesso progetto.

Ci sono due modi principali per collaborare:

### Metodo 1 — Collaboratori diretti
Il proprietario del repository aggiunge i compagni come "collaboratori". Tutti possono fare push direttamente.

### Metodo 2 — Fork e Pull Request
Chiunque può fare una copia (fork) del progetto, lavorarci e proporre le modifiche tramite una "Pull Request". Il proprietario le revisiona e decide se accettarle.

In questa lezione usiamo il **Metodo 2**, perché è quello usato dalla maggior parte dei progetti open source nel mondo reale.


## Parte 2 — Fork: copiare il progetto di un compagno (10 min)

Il **fork** è una copia completa di un repository altrui nel tuo account GitHub. Puoi modificarla liberamente senza toccare l'originale.

### Esercizio: fai il fork del repo di un compagno

Per questo esercizio, lavorerai in coppia con un compagno. Uno di voi sarà il "proprietario" e l'altro il "collaboratore". Poi vi scambierete i ruoli.

### Passo 1 — Il proprietario condivide il link

Il compagno che fa da proprietario condivide il link del suo repository, ad esempio:
```
https://github.com/compagno-username/il-mio-primo-repo
```

### Passo 2 — Il collaboratore fa il fork

1. Vai al link del repository del compagno nel browser.
2. Clicca il pulsante **Fork** in alto a destra.
3. Nella schermata che appare, clicca **Create fork**.

Ora avrai una copia del repo nel TUO account:
```
https://github.com/TUO-USERNAME/il-mio-primo-repo
```

Noterai la scritta "forked from compagno-username/il-mio-primo-repo" sotto il nome del repo.

### Passo 3 — Clona il fork sul tuo computer

```bash
cd ~/progetti-github

git clone git@github.com:TUO-USERNAME/il-mio-primo-repo.git repo-compagno

cd repo-compagno
```

Il comando `git clone` scarica il repository da GitHub e crea una cartella locale con tutti i file e la storia dei commit.

Verifica:

```bash
ls
git log --oneline
```

Vedrai tutti i file e i commit del tuo compagno!


## Parte 3 — Fare modifiche e proporre una Pull Request (20 min)

Ora lavorerai sul fork per aggiungere qualcosa al progetto del compagno.

### Passo 1 — Crea un branch per le tue modifiche

Non lavorare mai direttamente su `main` quando collabori. Crea sempre un branch:

```bash
git checkout -b contributo-di-TUO-NOME
```

Ad esempio: `contributo-di-marco`.

### Passo 2 — Fai le tue modifiche

Crea un file con un messaggio per il compagno:

```bash
echo "# Messaggio da [Il tuo nome]" > messaggio-TUO-NOME.md
echo "" >> messaggio-TUO-NOME.md
echo "Ciao! Ho trovato il tuo progetto molto interessante." >> messaggio-TUO-NOME.md
echo "" >> messaggio-TUO-NOME.md
echo "Ecco il mio contributo al progetto:" >> messaggio-TUO-NOME.md
echo "- Ho aggiunto questo file come esempio di collaborazione." >> messaggio-TUO-NOME.md
echo "- Data: $(date +%d/%m/%Y)" >> messaggio-TUO-NOME.md
```

### Passo 3 — Commit e push

```bash
git add messaggio-TUO-NOME.md
git commit -m "Aggiunto messaggio di contributo da [Il tuo nome]"
git push -u origin contributo-di-TUO-NOME
```

### Passo 4 — Crea la Pull Request su GitHub

1. Vai sul **tuo fork** su GitHub (nel browser).
2. Vedrai un banner giallo che dice "contributo-di-TUO-NOME had recent pushes". Clicca **Compare & pull request**.
3. Compila la Pull Request:
   - **Title:** "Aggiunto messaggio di contributo da [Il tuo nome]"
   - **Description:** Scrivi una breve descrizione di cosa hai fatto e perché. Ad esempio:
     ```
     Ciao! Ho aggiunto un file con un messaggio per il progetto.

     Modifiche:
     - Nuovo file messaggio-marco.md con un saluto e la data di contribuzione.
     ```
4. Verifica che il merge sia verso il repository **originale** (quello del compagno), non il tuo fork.
5. Clicca **Create pull request**.


## Parte 4 — Revisionare e accettare una Pull Request (10 min)

Ora scambiate i ruoli! Il proprietario del repository deve revisionare la Pull Request ricevuta.

### Passo 1 — Vai alla tab "Pull requests"

Il proprietario va sul proprio repository su GitHub e clicca la tab **Pull requests**. Vedrà la PR del compagno.

### Passo 2 — Revisiona le modifiche

1. Clicca sulla Pull Request per aprirla.
2. Vai alla tab **Files changed** per vedere esattamente cosa è stato modificato.
3. Puoi lasciare **commenti** su righe specifiche cliccando sul `+` a sinistra di una riga.
4. Se qualcosa non va, scrivi un commento e chiedi al compagno di correggere.

### Passo 3 — Accetta la Pull Request (merge)

Se le modifiche vanno bene:

1. Torna alla tab **Conversation**.
2. Clicca il pulsante verde **Merge pull request**.
3. Clicca **Confirm merge**.

Le modifiche del compagno sono ora nel tuo repository! Vedrai il nuovo file nella lista dei file del progetto.


## Parte 5 — Sincronizzare dopo il merge (5 min)

Dopo che il proprietario ha fatto il merge, il collaboratore deve aggiornare il suo fork e la copia locale.

### Passo 1 — Aggiungi il repository originale come "upstream"

```bash
git remote add upstream git@github.com:COMPAGNO-USERNAME/il-mio-primo-repo.git
```

### Passo 2 — Scarica gli aggiornamenti

```bash
git checkout main
git fetch upstream
git merge upstream/main
```

### Passo 3 — Aggiorna anche il tuo fork su GitHub

```bash
git push origin main
```

Ora il tuo fork, il repository originale e la tua copia locale sono tutti allineati.

### Schema del flusso completo

```
Repository originale (compagno)
        |
        | fork
        v
Il tuo fork (su GitHub)
        |
        | clone
        v
La tua copia locale
        |
        | branch + commit + push
        v
Il tuo fork (aggiornato)
        |
        | pull request
        v
Repository originale (compagno) ← merge!
```


## Parte 6 — Esercizio in coppia (5 min)

Ora scambiate i ruoli e ripetete l'intero processo:

1. Chi era "collaboratore" diventa "proprietario" e viceversa.
2. Il nuovo collaboratore fa il fork del repo del nuovo proprietario.
3. Crea un branch, aggiunge un file, fa push e apre una Pull Request.
4. Il proprietario revisiona, commenta e accetta.

### Comandi chiave della collaborazione

```bash
git clone URL                          # Scarica un repo da GitHub
git remote add upstream URL            # Aggiungi il repo originale
git fetch upstream                     # Scarica gli aggiornamenti dal repo originale
git merge upstream/main                # Unisci gli aggiornamenti
git push -u origin nome-branch         # Carica un branch sul tuo fork
```


## Riepilogo

Oggi hai imparato a:

- Fare il **fork** di un repository per creare la tua copia.
- **Clonare** un repository da GitHub al tuo computer.
- Proporre modifiche tramite **Pull Request**.
- **Revisionare** e accettare le Pull Request dei compagni.
- **Sincronizzare** il tuo fork con il repository originale.

---

**Lezione precedente:** [Lezione 5 — Branch e merge](05-branch-e-merge.md)
**Prossima lezione:** [Lezione 7 — Issues, Projects e lavoro di gruppo](07-issues-e-projects.md)
