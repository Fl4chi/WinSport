# DOCUMENTAZIONE TECNICA DETTAGLIATA - WinSport

Questa documentazione fornisce un'analisi tecnica completa del codice sorgente del progetto "WinSport", inclusa la nuova struttura multilingua.

---

## INDICE DEI CONTENUTI

1.  [Struttura del Progetto](#1-struttura-del-progetto)
2.  [index.html — Splash Page di Selezione Lingua](#2-indexhtml--splash-page-di-selezione-lingua)
3.  [it/ — Versione Italiana](#3-it--versione-italiana)
4.  [en/ — Versione Inglese](#4-en--versione-inglese)
5.  [Pagine del Sito (Home, Servizi, Games, Chi Siamo, Contatti)](#5-pagine-del-sito)
6.  [style.css — Design System](#6-stylecss--design-system)
7.  [Logica di Gioco JavaScript](#7-logica-di-gioco-javascript)

---

## 1. Struttura del Progetto

```
Centro Scomesse/
│
├── index.html           ← Splash page (scelta lingua)
│
├── it/                  ← 🇮🇹 Versione italiana completa
│   ├── index.html
│   ├── servizi.html
│   ├── games.html
│   ├── chisiamo.html
│   └── contatti.html
│
├── en/                  ← 🇬🇧 English version
│   ├── index.html
│   ├── services.html
│   ├── games.html
│   ├── aboutus.html
│   └── contact.html
│
├── css/
│   └── style.css        ← Foglio di stile condiviso da tutte le pagine
│
└── DOCUMENTAZIONE.md    ← Questo file
```

**Navigazione multilingua**: Ogni pagina ha nell'header un pulsante con la bandiera dell'altra lingua (🇬🇧 o 🇮🇹), visibile nell'angolo in alto a destra. Il sistema di navigazione è ora completamente confinato nelle cartelle di lingua (`it/` e `en/`), con la sola splash page nella radice per smistare l'utente.


---

## 2. `index.html` — Splash Page di Selezione Lingua

È il **punto di ingresso del sito**. Non contiene JavaScript: usa solo HTML e CSS.

### Tecnica: Effetti CSS Puri

### Tecnica: Design Semplice e Coerente

La splash page segue lo stesso stile minimalista e premium del resto del sito:
- Sfondo scuro (`#121212`) con font **Montserrat**.
- Logo dorato centrale con sottotitolo.
- Card di selezione lingua con lo stesso stile delle `service-card` (bordo oro al passaggio del mouse).

L'assenza di animazioni complesse o script pesanti garantisce un caricamento istantaneo e una perfetta coerenza visiva.

### Header e Wallet (Header Tools)
Il wallet e il pulsante lingua sono integrati direttamente nel header principale attraverso il container `.header-tools`. Questo blocco è posizionato assolutamente nell'angolo in alto a destra del nav:

```html
<div class="header-tools">
    <a href="..." class="lang-btn">🇬🇧</a>
    <div class="wallet-badge" id="wallet-display">💰 Saldo: ...</div>
</div>
```

Il CSS utilizza `display: flex` per allineare i due elementi affiancati, distanziandoli in modo elegante. Nelle pagine che non richiedono il wallet (come Chi Siamo o Contatti), il container ospita solo il pulsante lingua, mantenendo però la posizione fissa.

---

## 3. `it/` — Versione Italiana

Contiene la copia completa del sito in italiano. Ogni pagina:
- Link relativi interni puntano alle altre pagine nella stessa cartella (`href="servizi.html"`)
- Il CSS è caricato con `href="../css/style.css"` (percorso relativo alla radice)
- Il pulsante lingua nell'header punta a `../en/[equivalente].html`

---

## 4. `en/` — Versione Inglese

Struttura identica alla versione italiana, con tutti i testi tradotti in inglese. Differenze notevoli:
- `chisiamo.html` → `aboutus.html`
- `servizi.html` → `services.html`
- `contatti.html` → `contact.html`
- `games.html`: tutta la UI dei giochi è tradotta ("Hit", "Stand", "Dealer wins!", "Bust!", ecc.)
- Il pulsante lingua punta a `../[equivalente].html` (versione italiana alla radice)

---

## 5. Pagine del Sito

### Home (`index.html` in it/ o en/)

*   **Struttura**: Hero → Intro Chi Siamo → Griglia Servizi → Caratteristiche → Orari → Footer.
*   **Script Saldo**: Carica il saldo dal `localStorage` e lo mostra nell'header su `games.html`.

### Servizi (`servizi.html` / `services.html`)

*   Layout a "zig-zag" alternato (`flex-direction: row / row-reverse`) tra icona e testo.
*   Tre servizi: Scommesse Sportive, Ippica, Sala Slot & VLT.

### Games (`games.html`)

Pagina interattiva con **Roulette** e **Blackjack**. Vedi sezione 7 per la logica JS.

### Chi Siamo (`chisiamo.html` / `aboutus.html`)

*   Testo istituzionale con i tre pilastri: Sicurezza, Professionalità, Accoglienza.
*   Organigramma verticale del team: CEO → Co-CEO → CTO → Designer → AI Assistant.

### Contatti (`contatti.html` / `contact.html`)

*   Layout a due colonne: recapiti + orari a sinistra, form di contatto a destra.
*   Campi `required` per la validazione lato browser.

---

## 6. `style.css` — Design System

### Variabili Globali (`:root`)
```css
:root {
    --color-bg: #121212;      /* Nero "OLED" */
    --color-card: #1E1E1E;    /* Grigio schede */
    --color-accent: #D4AF37;  /* Oro Metallico */
    --font-main: 'Montserrat', sans-serif;
}
```
Cambiare `--color-accent` cambierebbe il colore dorato in tutto il sito istantaneamente.

### Header Tools (`.header-tools`)
```css
.header-tools {
    position: absolute;
    right: 0;
    display: flex;
    align-items: center;
    gap: 15px;
}

.lang-btn {
    display: inline-flex;
    padding: 7px 13px;
    border: 2px solid var(--color-accent);
    border-radius: 8px;
    font-size: 1.5rem;
    background: rgba(212,175,55,0.12);
}
```
*   `.header-tools` garantisce che tutti gli elementi interattivi dell'header (lingua e saldo) siano raggruppati stabilmente a destra.
*   Il pulsante lingua mostra l'emoji della bandiera dell'altra lingua, grande e leggibile.
*   Il wallet badge, quando presente, appare a destra del pulsante lingua, mantenendo uno stile premium coerente.

### Effetti e Animazioni

*   **Neon Glow** (`.wallet-badge`): `box-shadow: 0 0 15px rgba(212,175,55,0.3)`.
*   **Hover Scaling** (`.team-card`): `transform: scale(1.08)` + bordo oro.
*   **Transizioni fluide**: `transition: 0.3s` su tutti i link e bottoni.
*   **Grid Responsive**: `display: grid` con `auto-fit` per adattarsi a mobile.
*   **Media Query `@media (max-width: 768px)`**: Nav e colonne passano a layout verticale su mobile.

---

## 7. Logica di Gioco JavaScript

Presente in `games.html` (versione IT e EN). Il wallet è salvato nel `localStorage` e condiviso tra pagine.

### Wallet Condiviso
```javascript
let capitale = parseInt(localStorage.getItem('walletBalance')) || 1000;

function aggiornaWallet() {
    document.getElementById("user-balance").textContent = capitale;
    localStorage.setItem('walletBalance', capitale);
}
```
*   `localStorage` è una memoria permanente del browser: il saldo sopravvive al reload della pagina.

### Roulette
*   **Griglia dinamica**: 37 bottoni (0-36) generati via JS con colori corretti (verde, rosso, nero).
*   **Puntata numero** → paga 35:1 in caso di vittoria.
*   **Puntata colore** (Rosso/Nero) → paga 1:1. Lo zero fa perdere.

### Blackjack

**Funzione `totale(mano)`** — gestione intelligente degli Assi:
```javascript
while(assi > 0 && somma + 10 <= 21) {
    somma += 10;
    assi--;
}
```
L'Asso vale 1 di default, ma viene promosso a 11 automaticamente se non causa sballata.

**IA del Banco**:
```javascript
while(totale(manoBanco) < 17) {
    manoBanco.push(pescaCarta());
}
```
Il banco segue la regola standard: tira obbligatoriamente con 16 o meno, si ferma con 17+.

---

## 8. Conclusioni Tecniche

Il progetto WinSport è costruito seguendo gli standard del web moderno:
- **HTML5 Semantico**: Per SEO e accessibilità.
- **CSS3 Avanzato**: Glassmorphism, gradienti, animazioni pure CSS (niente librerie).
- **JavaScript Algoritmico**: Logica di gioco precisa, wallet persistente via `localStorage`.
- **Architettura Multilingua**: Due versioni complete (IT/EN) con splash page di selezione, senza framework né server — funziona aprendo i file HTML direttamente nel browser.
