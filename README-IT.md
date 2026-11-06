# 🎛️ DUB FX PAD — File Sampler

🇬🇧 [English](README.md) · 🇮🇹 **Italiano**

**Un sampler a pad per il browser, utilizzabile anche offline, pensato per dub, sound system e performance dal vivo — con un'unità di eco a nastro e riverbero a molla ispirata al leggendario Roland RE-201 Space Echo. Nato per smartphone e tablet, ma perfettamente usabile anche da desktop.**

![status](https://img.shields.io/badge/status-active-brightgreen)
![type](https://img.shields.io/badge/type-single--file%20web%20app-blue)
![offline](https://img.shields.io/badge/offline-ready-success)
![platform](https://img.shields.io/badge/platform-Android%20%7C%20iOS%20%7C%20Desktop-orange)
![license](https://img.shields.io/badge/license-MIT-lightgrey)

<p align="center">
  <img src="https://i.ibb.co/8v59HxL/Screenshot-20261106-050700-com-android-chrome-Chrome-Tabbed-Activity.jpg" alt="DUB FX PAD in esecuzione su Android Chrome" width="420">
</p>

---

## ✨ Panoramica

DUB FX PAD è un **singolo file HTML autosufficiente**: nessuna build, nessun server, nessuna dipendenza da installare. Lo apri in un qualsiasi browser moderno, mobile o desktop, ed è subito un sampler a pad completo:

- Carica i tuoi file audio (MP3, WAV, OGG, FLAC, AAC, M4A) e trasformali in pad da suonare
- Organizza i suoni in categorie (Sweeps, Lasers, One-Shots, Sirens, Ambient FX, più le tue categorie personalizzate)
- Fai passare tutto in un motore **tape delay + spring reverb** in stile dub, modellato sulle classiche unità a nastro
- Mixa, silenzia, aggiungi ai preferiti, rinomina, sposta, ridimensiona e riordina ogni suono
- Premi **DELAY NOW** per lanciare l'eco su un suono che sta *già suonando* — e toglilo di nuovo con un secondo tocco
- Funziona completamente offline una volta caricato: campioni e impostazioni restano sul dispositivo (IndexedDB + localStorage), niente cloud, niente account, niente tracciamento

Pensato per performance dub/sound system dal vivo, effetti da DJ, uso come soundboard o semplicemente per giocare con un caldo eco in stile analogico dentro il browser.

---

## PROVALO ONLINE!

https://definite-teal-5ka734sq.edgeone.dev

---

## 🚀 Per iniziare

### Opzione 1 — Aprilo e basta
1. Scarica il file `.html` (oppure clona questa repo).
2. Aprilo direttamente nel browser (doppio clic, o trascinalo in una scheda).
3. Tocca **▶ POWER ON** per avviare il motore audio (i browser richiedono un gesto dell'utente prima di far partire qualsiasi suono). Sui browser compatibili, lo stesso tocco porta l'app a **schermo intero** e tiene lo schermo acceso mentre suoni.
4. Tocca **⊕ LOAD** per aggiungere i tuoi file audio.

### Opzione 2 — Servilo in locale (consigliato per i test su mobile)
Alcuni browser mobile limitano l'accesso a `file://` per funzioni come IndexedDB. Se incontri problemi, servi il file con un server HTTP locale:

```bash
# Python 3
python3 -m http.server 8080

# Node (pacchetto http-server)
npx http-server -p 8080
```

Poi apri `http://localhost:8080/<nome-file>.html` sul tuo dispositivo (stessa rete Wi-Fi per telefoni e tablet).

### Opzione 3 — Termux (Android)
La schermata iniziale mostra un percorso di esempio per i campioni:

```
/data/data/com.termux/files/home/storage/downloads/DubpadFX/
```

È solo un suggerimento per chi usa Android/Termux e tiene lì la propria libreria di suoni: è un semplice testo, **non un obbligo**. Puoi caricare file da qualsiasi posizione con il normale selettore di file.

### 📲 Aggiungi alla schermata Home
Dal menu del browser scegli **Aggiungi a schermata Home**. L'app include un'icona incorporata (*Sweet Reggae Music*) e il nome **DubPad FX**, quindi non servono altri file. Se avevi già aggiunto una versione precedente, elimina il vecchio collegamento e riaggiungilo per aggiornare l'icona.

---

## 🎚️ Funzioni

### Pad sampler
- Tocca un pad per farlo suonare all'istante (un suono alla volta; passando a un altro pad il precedente sfuma in 70 ms per evitare i click)
- Tieni premuto un pad (o clic destro su desktop) per aprire il menu contestuale:
  - ★ Aggiungi / Rimuovi dai preferiti
  - ✎ Rinomina
  - ↗ Sposta in un'altra categoria
  - ✕ Rimuovi il pad
- I pad assegnano da soli un'icona emoji in base alle parole nel nome del file (ad es. "laser", "kick", "siren", "drone"), altrimenti usano 🎵

### Categorie
- Predefinite: **Sweeps · Lasers · One-Shots · Sirens · Ambient FX · Preferiti**
- Crea quante **categorie personalizzate** vuoi, con nome, icona e colore a tua scelta
- Eliminando una categoria personalizzata, i suoi suoni vengono spostati in Ambient FX (con conferma se non è vuota)
- La vista **ALL** è **ordinata automaticamente per categoria**, nello stesso ordine delle linguette (prima le predefinite, poi le tue). All'interno di ogni categoria resta l'ordine scelto con ⇅ ORDINA

### ⛶ Dimensione dei pad — 6 preset
**XXS · XS · S · M · L · XL** con il pulsante **SIZE**. Telefoni e tablet hanno scale proprie.
- **XS** riduce icona e nome per far stare più pad sullo schermo
- **XXS** mostra solo l'icona (senza nome) per la massima densità
- La scelta viene ricordata tra una sessione e l'altra

### ⇅ Riordino dei pad
- Ogni categoria (e la vista "All") si può riordinare con il pulsante **⇅ ORDINA**
- Lista con trascinamento, funziona con il mouse **e** con il dito su mobile
- I preferiti hanno un loro ordine indipendente, salvabile nella finestra ★ PREFERITI

### 🎚️ Mixer — volume, riverbero e mandata delay per ogni suono
- Mixer a schermo intero (**🎚 MIXER**) con una striscia di canale per ogni suono caricato, scorrevole in orizzontale
- Fader verticali lunghi e precisi con **±35 dB** di escursione e tacche ogni 5 dB (tacche principali ogni 10 dB, 0 dB evidenziato)
- **0 dB = il volume originale, intatto, del file caricato** — nessuna attenuazione preimpostata
- Lettura in tempo reale di dB e percentuale per ogni canale
- Manopola **REVERB** per ogni pad (0–100 %, con scala percettiva: il 50 % suona davvero circa la metà del 100 %)
- Interruttore **DELAY** per ogni pad: silenzia *solo* la mandata di quel suono verso le ripetizioni del delay a nastro. Volume secco e riverbero a molla non cambiano
- Le modifiche si sentono **subito, anche sul suono che sta già suonando**
- **RESET ALL TO 100%** riporta ogni canale a 0 dB e riattiva il delay su tutti i pad con un solo tocco
- Se la modalità Echo attuale non ha delay (DRY, SPRING) o non ha riverbero (DRY), il mixer lo segnala invece di mostrare comandi che non farebbero nulla

### 〰 DELAY NOW — un solo pulsante, tutti i pad
Un unico pulsante generale (non uno per pad) che agisce sul **suono che sta suonando in questo momento**:
- Il suono ha il delay **spento** nel mixer → il primo tocco **accende l'eco** da quel momento fino alla fine del sample
- Il suono ha il delay **acceso** nel mixer → il primo tocco **taglia l'eco**
- Tocca ancora per riprenderlo, ancora per tagliarlo, e così via — sempre solo per il suono in corso
- Al tocco successivo di un pad si torna alle impostazioni del mixer
- Il pulsante pulsa e il LED si accende mentre l'eco è forzato
- **Quando la tendina dello Space Echo è abbassata, resta visibile una versione compatta del pulsante** in basso a destra, sempre a portata di dito
- Non disponibile nelle modalità **DRY** e **SPRING** (non hanno uscita delay): l'app te lo segnala

### 🎛️ Unità Space Echo ispirata al Roland
Un pannello di controllo sempre disponibile mentre suoni. Su telefoni e tablet in verticale è una **tendina**: trascinala in basso (o tocca la maniglia) per avere più spazio per i pad, trascinala in alto per riaprirla — la scelta viene ricordata. Sui tablet larghi in orizzontale diventa una **colonna fissa** a destra.

| Controllo | Intervallo | Descrizione |
|---|---|---|
| **DELAY TIME** | 50 ms – 2,0 s | Tempo del delay a nastro |
| **FEEDBACK** | 0 – 100 % (manopola) | Numero di ripetizioni; curva non lineare tarata a orecchio (circa 1 ripetizione in basso, ~8 a metà, ~60 in cima, con limite sotto l'auto-oscillazione) |
| **DRY/WET** | 0 – 100 % | Miscela tra segnale secco ed effetto |
| **MASTER VOL** | 0 – 100 % | Livello generale di uscita |

La quantità di riverbero si imposta **per ogni pad nel Mixer**.

**5 modalità preimpostate:**
- **DRY** — nessun effetto, segnale pulito
- **ECHO** — solo delay a nastro
- **SPRING** — solo riverbero
- **ECHO + SPRING** — entrambi insieme
- **DEEP DUB** — feedback pesante + lunga coda di riverbero, quasi tutto wet, il classico "dub-out"

**Tap Tempo / BPM manuale** — tocca **TAP** per impostare il tempo del delay a sentimento, oppure scrivi o regola i BPM (40–300) con **− / +**. Il tempo di delay si sincronizza automaticamente, e girando la manopola DELAY TIME il valore BPM si aggiorna.

Una **risposta all'impulso a convoluzione** fatta a mano modella un serbatoio di riverbero a molla/piastra con pre-delay, prime riflessioni irregolari, coda diffusa a doppia banda, leggera risonanza inarmonica della molla e canali stereo decorrelati — costruita interamente con la Web Audio API, senza campioni esterni. La catena d'uscita termina con un compressore e un limiter.

### 💾 Salvataggio
- Pad, categorie, preferiti, livelli del mixer, quantità di riverbero, delay silenziati, dimensione dei pad, stato della tendina e impostazioni dell'eco vengono salvati automaticamente in `localStorage`
- I dati audio veri e propri sono in **IndexedDB**, quindi la tua libreria di suoni sopravvive ai ricaricamenti e ai riavvii dell'app — tutto offline, niente viene caricato da nessuna parte
- Al lancio successivo i suoni vengono ripristinati e ridecodificati in automatico

### ⬇ Esporta — ZIP dei tuoi campioni
Il pulsante **ZIP** impacchetta tutti i campioni caricati in un unico download `.zip`. È scritto in JavaScript puro, senza librerie, con il metodo "store" (nessuna ricompressione — i file audio sono già compressi — quindi è veloce e affidabile).

### 🗑️ Cancellazione totale
- Il pulsante **🗑 WIPE** esegue un ripristino completo: pad, categorie, preferiti, impostazioni del mixer e dati audio salvati (IndexedDB + localStorage) vengono cancellati
- Protetto da doppia conferma, perché l'azione è irreversibile

### 🖥️ Schermo e comodità
- **Schermo intero al POWER ON** (dove il browser lo permette — Android Chrome, iPad, desktop) più il pulsante **⤢ FULL / ⤡ ESCI**
- **Screen Wake Lock**: lo schermo resta acceso durante la sessione
- Layout per tablet in orizzontale con colonna Space Echo fissa, aree di tocco più grandi e finestre centrate

### 📻 Grafica
- VU meter reattivo in testata, pilotato da un analizzatore audio in tempo reale
- **Spettro d'uscita** specchiato (bassi al centro, acuti verso i lati) disegnato dopo il limiter; si mette in pausa da solo quando la tendina è abbassata per risparmiare batteria
- Bobine che girano e nastro in movimento sull'unità eco mentre un suono suona
- Schermata introduttiva animata con pentagramma ondulato e note che salgono
- Categorie con colori coordinati su pad, linguette e strisce del mixer
- Estetica retrò da terminale/hardware: scanlines, vignettatura, bagliore CRT, caratteri monospace e display

### ❔ Guida nell'app e 🌐 traduzione in inglese
- Il pulsante **❔ INFO** apre una guida nell'app (avvio, uso quotidiano, Space Echo e DELAY NOW, installazione sulla Home, com'è fatta l'app, dove stanno i tuoi file audio)
- L'interfaccia è scritta in **italiano**. Il pulsante opzionale **EN** traduce al volo tutti i testi a schermo in inglese tramite le **API di Gemini** (serve una connessione a internet e *la tua* chiave API, da impostare con il pulsante **⚙** accanto). Le traduzioni vengono salvate in cache in locale. Tutto il resto dell'app funziona offline e non ha mai bisogno di una chiave.

### 🔎 SEO e condivisione
La pagina include un set completo di meta tag (descrizione, parole chiave, robots), tag Open Graph e Twitter Card, dati strutturati schema.org `WebApplication` in JSON-LD, un `<h1>` semantico e una sezione "informazioni" richiudibile in fondo alla pagina per i motori di ricerca — in italiano e in inglese.

---

## 🗂️ Struttura del progetto

È volutamente un **singolo file HTML** che contiene:

```
DubPadFX_Tablet.html
├── <head>    → meta SEO, Open Graph / Twitter, JSON-LD, icone per la schermata Home incorporate
├── <style>   → tutto il CSS (temi, layout per telefono + tablet + orizzontale, animazioni)
├── <body>    → markup (schermata iniziale, testata, linguette, griglia, DELAY NOW, unità eco, finestre)
└── <script>  → logica dell'app:
    ├── Stato (oggetto S) + salvataggio (localStorage + IndexedDB)
    ├── Motore audio Web Audio (delay, sintesi dell'IR del riverbero, compressore, limiter, analizzatore)
    ├── Catena per ogni pad (secco · mandata delay · mandata riverbero) + interruttore DELAY NOW
    ├── Gestione pad (aggiungi / rimuovi / sposta / rinomina / riordina)
    ├── Interfaccia (linguette, griglia + taglie, mixer, finestre, menu contestuale)
    ├── Tendina dell'eco (pannello trascinabile), manopole, tap tempo, modalità echo
    ├── Esportazione ZIP, VU meter, spettro, animazione d'intro, wake lock, schermo intero
    └── Livello opzionale di traduzione EN (Gemini)
```

Nessun bundler, nessun `npm install`, nessun framework JS. L'unica risorsa esterna è il foglio di stile di Google Fonts (`Share Tech Mono` + `Orbitron`), caricato via CDN; tutto il resto è autosufficiente. La traduzione EN opzionale è l'unica funzione che comunica con un servizio di rete.

---

## 🌐 Browser supportati e requisiti

- Qualsiasi browser moderno con supporto a **Web Audio API** e **IndexedDB** (Chrome, Firefox, Safari, Edge — desktop o mobile)
- Serve un gesto dell'utente (il tocco su **POWER ON**) prima che l'audio possa partire, come previsto dalle regole di autoplay dei browser
- Lo schermo intero non è disponibile per le pagine web su iPhone; funziona su iPad, Android e desktop
- Dà il meglio su un dispositivo touch per le interazioni a tocco e pressione lunga, ma è pienamente utilizzabile con mouse + clic destro su desktop

---

## 🛠️ Personalizzazione

Dato che tutto sta in un solo file, la maggior parte delle modifiche è rapida:

- **Categorie** — modifica l'oggetto `CAT_META` nello script per cambiare etichette, icone o colori delle categorie predefinite
- **Riconoscimento delle icone** — estendi `CAT_ICON_GUESS` per associare più parole dei nomi file a emoji
- **Carattere del riverbero** — regola il generatore dell'IR a molla (tempi di decadimento, intervalli passa-banda, frequenze di risonanza) per dare forma al suono della molla/piastra
- **Modalità echo** — l'array `modes` dentro `setMode()` definisce la miscela dry/wet/feedback/riverbero delle 5 modalità
- **Sensazione del feedback** — `fbCurve()` collega la posizione della manopola al guadagno delle ripetizioni
- **Dimensioni dei pad** — le regole `.grid[data-size="…"]` nel CSS (blocco telefono e blocco tablet) definiscono larghezza e altezza di ogni preset
- **Tema** — i colori sono proprietà CSS personalizzate sotto `:root` all'inizio del foglio di stile

---

## 🔐 Nota di sicurezza (chiavi API)

Poiché l'app è un singolo file HTML pubblico, **tutto ciò che è scritto al suo interno può essere letto da chiunque apra la pagina o la repository**. Non inserire mai una chiave API privata nel file. Per la traduzione EN opzionale, inserisci la tua chiave Gemini quando serve con il pulsante **⚙**: viene salvata solo nel `localStorage` del tuo browser. Se una chiave è mai finita in una repo pubblica, revocala dalla console Google AI Studio / Cloud e creane una nuova.

---

## 🙏 Crediti e ispirazione

Ispirato all'estetica delle classiche unità a nastro in stile **Space Echo** e alla cultura dub dei sound system giamaicani e italiani.

Strumenti e marchi citati a titolo di omaggio (badge stilizzati originali, non loghi ufficiali — nessuna affiliazione con queste aziende):

- **Roland** — Space Echo RE-201
- **Behringer**
- **NUX**
- **Korg**
- **Dubmatix**

Un ringraziamento speciale a **Paolo Baldini DubFader** — ispirazione e riferimento guida per il suono dub e per la filosofia di missaggio alla base di questo progetto.

Tutti i marchi e i nomi commerciali citati appartengono ai rispettivi proprietari. Non è implicata alcuna affiliazione o approvazione ufficiale.

---

## ⚠️ Avvertenze

Questo progetto è uno strumento audio personale/creativo. I tuoi file audio, le impostazioni e i livelli del mixer restano nella memoria locale del tuo browser e non vengono mai caricati da nessuna parte. L'unica richiesta di rete che l'app può fare è la traduzione EN opzionale, che quando la attivi invia all'API di Gemini le etichette di testo dell'interfaccia (non il tuo audio).

---

## 📄 Licenza

Rilasciato con **Licenza MIT** — vedi il file [`LICENSE`](LICENSE).

Il testo legale originale resta in inglese:

```
MIT License

Copyright (c) 2026 Swan Boccella

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

© 2026 **Swan Boccella**

---

## 🤝 Contribuire

Issue e pull request sono benvenute. Trattandosi di un'app in un solo file, la maggior parte dei contributi si può fare direttamente sul file HTML — ti chiedo di mantenere intatta la filosofia "nessuna build" quando proponi modifiche.
