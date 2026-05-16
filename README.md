# 🪓 Building Vikings — Workout Tracker

> Webapp personale per consultare, eseguire e tracciare il programma **Building Vikings** (18 giorni · Functional Hypertrophy · RPE 8/10).

---

## Cos'è

Building Vikings Tracker è una **single-page app** HTML/CSS/JS completamente auto-contenuta — un unico file, nessuna dipendenza da installare, nessun account richiesto. Progettata per essere usata direttamente in palestra dallo smartphone o consultata da desktop.

Il programma incluso è **Building Vikings**: 18 giorni di allenamento in split A/B/C (Gambe·Spalle / Petto·Dorso / Bicipiti·Tricipiti) basato su Functional Hypertrophy — tensione muscolare, stress metabolico e danno muscolare come driver principali.

---

## Funzionalità

### Dashboard
- Statistiche live: sessioni completate, giorno corrente, % completamento, volume totale sollevato
- Barra progresso a 18 dot cliccabili — ogni dot mostra il tipo di sessione e l'ondata
- Sessione suggerita per il giorno corrente con accesso diretto
- Prossimi 3 allenamenti in anteprima

### Workout
- Lista completa di tutte le sessioni del programma divise per tipo (A / B / C)
- Ogni sessione espande i blocchi di esercizi con warm-up, note tecniche e obiettivo del blocco
- **Tracciamento per-set**: ogni set ha la sua riga con campo kg, reps e pulsante di completamento ✓
- Colonna **PREC.** che mostra automaticamente i valori dell'ultima sessione identica — così sai sempre da dove partire
- Campo **note libere** per ogni esercizio: annotazioni su sensazioni, tecnica, variazioni
- **Rest timer** integrato con preset rapidi (30s / 1m / 1:30 / 2m / 2:30 / 3m)
- Pulsante di completamento sessione che avanza automaticamente il giorno corrente

### Progressi
- Grafico volume per sessione (kg totali sollevati)
- Grafico sessioni completate per fase del programma
- Grafico progressione carichi sui principali esercizi compound (Squat, T-Bar Row, Barbell Curl)
- Tabella progressione carichi con **calcolo automatico** dell'Ondata 2 (+5%) e del Peak (+5%)

### Note
- Legenda completa di tutte le tecniche usate (TUT, SS, TRI, DS, RPE, AMRAP, 8×8)
- Spiegazione della progressione del carico per ondata
- Linee guida nutrizionali del programma
- Note importanti e avvertenze

### Impostazioni
- Caricamento di un nuovo programma in formato `.md`
- Reset progressi (mantiene il programma)
- Reset completo
- Export dati in JSON per backup

---

## Come aprirlo

### Opzione 1 — Direttamente nel browser (più semplice)

```bash
# Linux / Ubuntu
xdg-open building_vikings_tracker.html

# macOS
open building_vikings_tracker.html

# Windows
start building_vikings_tracker.html
```

I dati vengono salvati nel `localStorage` del browser — persistono tra una sessione e l'altra finché non si cancella la cache.

### Opzione 2 — Server locale con Python

```bash
# Nella cartella dove si trova il file
python3 -m http.server 8080
```

Poi apri `http://localhost:8080/building_vikings_tracker.html` nel browser.

Utile se vuoi aprirlo da più dispositivi sulla stessa rete locale:

```bash
# Trova il tuo IP locale
ip addr show | grep "inet "

# Dal telefono apri
http://192.168.x.x:8080/building_vikings_tracker.html
```

### Opzione 3 — Deploy gratuito online

**Netlify Drop** (zero account necessario):
1. Vai su [app.netlify.com/drop](https://app.netlify.com/drop)
2. Trascina il file `building_vikings_tracker.html` nella pagina
3. Ottieni un URL pubblico in 30 secondi

**GitHub Pages**:
1. Crea un repository su GitHub
2. Carica il file come `index.html`
3. Attiva Pages in `Settings → Pages → Source: main`
4. L'app sarà disponibile su `https://tuonome.github.io/nomerepo`

> ⚠️ Su servizi online il `localStorage` è legato al browser/dispositivo. Per sincronizzare i dati tra dispositivi usa la funzione **Esporta JSON** e reimporta manualmente, oppure tieni il file su una cartella condivisa (Dropbox, Google Drive) e aprilo in locale.

---

## Struttura del programma

| Giorno | Sessione | Ondata |
|--------|----------|--------|
| 1–3 | A → B → C | Prima ondata |
| 4 | REST | — |
| 5–7 | A → B → C | Prima ondata |
| 8 | REST | — |
| 9–11 | A → B → C | Seconda ondata (+5%) |
| 12 | REST | — |
| 13–15 | A → B → C | Seconda ondata (+5%) |
| 16 | REST | — |
| 17–18 | B → A | Peak (volume max) |

**Split:**
- 🦵 **A** — Gambe / Spalle · 75–85 min
- 💪 **B** — Petto / Dorso · 80–90 min
- 🔥 **C** — Bicipiti / Tricipiti · 65–75 min

---

## Come tracciare un allenamento

1. Apri la sessione del giorno dalla **Dashboard** o dalla tab **Workout**
2. Espandi i blocchi di esercizi toccando l'intestazione
3. Per ogni esercizio compila **riga per riga**: inserisci kg e reps per ogni set
4. Premi **○** per segnare il set come completato → diventa **✓** verde
5. Usa il campo note sotto la tabella per annotazioni libere (sensazioni, tecnica, variazioni)
6. Usa i pulsanti del **rest timer** tra un set e l'altro
7. A fine sessione premi **"Segna Sessione come Completata"** — il giorno corrente avanza automaticamente

La colonna **PREC.** mostra i valori dell'ultima volta che hai eseguito lo stesso esercizio nella stessa tipologia di sessione, così puoi applicare la progressione senza dover ricordare nulla a memoria.

---

## Aggiornare il programma

La webapp supporta il caricamento di un nuovo programma generato in formato Markdown:

1. Vai in **Impostazioni → Carica Programma**
2. Trascina o seleziona il file `.md`
3. Il programma viene sostituito; log e progressi rimangono intatti

---

## Backup dei dati

I dati sono salvati nel `localStorage` del browser. Per fare un backup:

**Impostazioni → Esporta JSON** — scarica un file `building_vikings_YYYY-MM-DD.json` con tutti i log, i progressi e le note.

Per ripristinare, vai in **Impostazioni → Backup & Ripristino → Importa** e seleziona il file JSON. I dati vengono caricati immediatamente e la dashboard si aggiorna.

---

## Tecnologie

| Componente | Tecnologia |
|---|---|
| UI | HTML5 / CSS3 / JavaScript vanilla |
| Grafici | [Chart.js 4.4](https://www.chartjs.org/) |
| Font | Oswald + Space Mono (Google Fonts) |
| Persistenza | `localStorage` del browser |
| Dipendenze server | Nessuna |
| Dimensione file | ~90 KB (singolo file) |

---

## Requisiti

- Browser moderno (Chrome, Firefox, Safari, Edge — versioni 2022+)
- JavaScript abilitato
- Nessuna connessione internet richiesta dopo il primo caricamento (i font Google vengono cachati)

---

*🪓 Building Vikings — Forgiato per chi non si accontenta di sopravvivere.*
