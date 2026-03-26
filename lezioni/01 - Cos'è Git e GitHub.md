# Lezione 1 — Cos'è Git e GitHub?

**Durata:** 1 ora
**Obiettivo:** Capire perché esistono Git e GitHub, creare il proprio account GitHub e familiarizzare con l'interfaccia.

---

## Parte 1 — Il problema (10 min)

Immagina di scrivere una tesina con un compagno. Vi scambiate il file per email:

```
tesina_v1.docx
tesina_v2_marco.docx
tesina_v2_marco_corretto.docx
tesina_FINALE.docx
tesina_FINALE_davvero.docx
```

Vi è mai successo? Questo caos nasce perché non avete un sistema per **tenere traccia delle modifiche** e **lavorare insieme** sullo stesso progetto senza sovrascrivervi a vicenda.

**Git** e **GitHub** risolvono esattamente questo problema — non solo per documenti, ma soprattutto per il codice.


## Parte 2 — Cos'è Git? (10 min)

**Git** è un programma che installi sul tuo computer. Serve a:

1. **Salvare "istantanee"** (chiamate *commit*) del tuo progetto in momenti precisi.
2. **Tornare indietro** a qualsiasi versione precedente se qualcosa va storto.
3. **Lavorare in parallelo** su funzionalità diverse senza creare conflitti.

Pensa a Git come alla funzione "Cronologia versioni" di Google Docs, ma molto più potente e pensata per il codice.

### Vocabolario essenziale

| Termine | Significato |
|---------|------------|
| **Repository (repo)** | La cartella del tuo progetto gestita da Git |
| **Commit** | Un'istantanea salvata del progetto in un momento preciso |
| **Branch** | Una "linea parallela" di sviluppo (ne parleremo nella Lezione 5) |


## Parte 3 — Cos'è GitHub? (10 min)

**GitHub** è un sito web (github.com) che ospita i tuoi repository Git online. Aggiunge:

- Un **backup nel cloud** del tuo codice.
- Strumenti per **collaborare** con altri (commenti, revisioni, segnalazioni).
- Una **vetrina pubblica** dei tuoi progetti (utile anche per il futuro!).

### Git vs GitHub — non confonderli!

| Git | GitHub |
|-----|--------|
| Programma sul tuo PC | Sito web |
| Funziona offline | Serve connessione internet |
| Gestisce le versioni | Ospita il codice e facilita la collaborazione |
| Gratuito e open source | Gratuito per uso base, a pagamento per funzioni extra |

**Analogia:** Git è come il motore di un'auto, GitHub è la strada su cui guidi. Puoi avere il motore senza la strada (Git senza GitHub), ma insieme funzionano molto meglio.


## Parte 4 — Il tuo account GitHub

> ✅ Se hai seguito la **Lezione 00**, hai già creato il tuo account GitHub. Puoi passare direttamente alla Parte 5.
>
> Se invece stai leggendo questa lezione per prima, torna alla [Lezione 00](00%20-%20Introduzione%20a%20Codespaces%20e%20VS%20Code.md) e segui il "Passo 0" per creare l'account.

Una volta dentro, completa il profilo se non l'hai già fatto:

Clicca sulla tua icona in alto a destra e vai su **Settings > Profile**:
- Aggiungi una foto (o un avatar).
- Scrivi una breve bio, ad esempio: *"Studente di liceo scientifico, appassionato di informatica"*.


## Parte 5 — Esplora GitHub (10 min)

Ora che hai un account, esploriamo un po'.

### Esercizio: trova un progetto famoso

1. Vai sulla barra di ricerca in alto su GitHub.
2. Cerca uno di questi progetti e aprilo:
   - `torvalds/linux` — il sistema operativo Linux, creato dal creatore di Git!
   - `python/cpython` — il linguaggio Python
   - `twbs/bootstrap` — uno dei framework web più usati al mondo
3. Una volta aperto il progetto, osserva:
   - Il file `README.md` che si visualizza in basso: è la "pagina di presentazione" del progetto.
   - Il numero di **Stars** (quante persone lo hanno apprezzato).
   - Il numero di **Contributors** (quante persone ci hanno lavorato).
   - La lista dei **file e cartelle** del progetto.

### Domande di riflessione

Rispondi sul tuo quaderno o in un file di testo:

1. Quante persone hanno contribuito al progetto che hai scelto?
2. Quando è stato fatto l'ultimo aggiornamento (ultimo commit)?
3. Secondo te, come fanno migliaia di persone a lavorare sullo stesso progetto senza creare caos?


## Parte 6 — Riepilogo (5 min)

Oggi hai imparato che:

- **Git** è un sistema di controllo versione che salva la storia del tuo progetto.
- **GitHub** è una piattaforma online che ospita i repository Git e facilita la collaborazione.
- Hai creato il tuo **account GitHub** e hai esplorato un progetto reale.

### Prepararsi per la prossima lezione

Nella Lezione 2 installeremo Git sul computer e lo configureremo. Se vuoi portarti avanti:

- **Windows:** scarica Git da https://git-scm.com/download/win
- **macOS:** scarica Git da https://git-scm.com/download/mac
- **Linux:** apri il terminale e scrivi `sudo apt install git`

---

**Lezione precedente:** [Lezione 00 – Scegliere l'ambiente](00%20-%20Introduzione%20a%20Codespaces%20e%20VS%20Code.md)
**Prossima lezione:** [Lezione 02 — Installare e configurare Git](02%20-%20Installare%20e%20configurare%20Git.md)
