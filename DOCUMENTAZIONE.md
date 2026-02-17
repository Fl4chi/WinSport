# DOCUMENTAZIONE TECNICA DETTAGLIATA - WinSport

Questa documentazione fornisce un'analisi tecnica completa, riga per riga e sezione per sezione, di tutto il codice sorgente del progetto "WinSport".

---

## INDICE DEI CONTENUTI

1.  [index.html (Home Page)](#1-indexhtml---home-page)
2.  [servizi.html (Pagina Servizi)](#2-servizihtml---pagina-servizi)
3.  [games.html (Nuova Pagina Giochi: Roulette & Blackjack)](#3-gameshtml---nuova-pagina-giochi)
4.  [contatti.html (Modulo & Recapiti)](#4-contattihtml---pagina-contatti)
5.  [chisiamo.html (Chi Siamo & Team)](#5-chisiamohtml---chi-siamo)
6.  [style.css (Foglio di Stile)](#6-stylecss---design-system)

---

## 1. `index.html` - Home Page

Il file `index.html` rappresenta la pagina principale e la vetrina del sito.

### Struttura e Head (Linee 1-13)
```html
<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WinSport - Centro Scommesse Sportive</title>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Montserrat..." rel="stylesheet">
    <link rel="stylesheet" href="css/style.css">
</head>
```
*   `<!DOCTYPE html>`: Dichiara che stiamo usando HTML5 moderno.
*   `<html lang="it">`: Imposta la lingua italiana, essenziale per i lettori vocali e i motori di ricerca.
*   `<meta charset="UTF-8">`: Garantisce che caratteri speciali (sì, è, à) ed emoji vengano visualizzati correttamente.
*   `<meta name="viewport"...>`: Rende il sito "responsive" (adattabile) su cellulari, dicendo al browser di usare la larghezza reale del dispositivo.
*   `<link href...fonts...>`: Scarica il font "Montserrat" da Google per dare un aspetto moderno e pulito.
*   `<link rel="stylesheet"...>`: Collega il file CSS che contiene tutti i colori e le impaginazioni.

### Header e Navigazione (Linee 17-38)
```html
<header>
    <div class="container">
        <div class="logo">...</div>
        <nav>
            <ul>
                <li><a href="index.html" class="active">Home</a></li>
                <li><a href="servizi.html">Servizi</a></li>
                <li><a href="games.html">Games</a></li>
            </ul>
            <div class="wallet-badge" id="wallet-display">...</div>
        </nav>
    </div>
</header>
```
*   Contiene il logo (`<h1>WINSPORT</h1>`) e il menu di navigazione (`<nav>`).
*   La classe `active` sul link "Home" indica visivamente all'utente su quale pagina si trova (diventa color oro).
*   `id="wallet-display"`: Questo elemento è speciale. Viene controllato via JavaScript per mostrare il saldo aggiornato dell'utente in tempo reale.

### Hero Section (Linee 41-47)
```html
<section class="hero">
    <div class="hero-content">
        <h2>WinSport – Il punto di riferimento...</h2>
        <p>Segui le partite in diretta...</p>
        <a href="games.html" class="btn">Gioca Ora</a>
    </div>
</section>
```
*   La classe `.hero` nel CSS imposta l'immagine di sfondo grande e scura.
*   Il bottone "Scopri i Games" (`class="btn"`) è una "Call to Action" (invito all'azione) per portare subito l'utente alla parte divertente del sito.

### Sezione Intro Chi Siamo (Linee 50-62)
```html
<section id="chisiamo-intro">
    ...
    <a href="chisiamo.html" class="btn btn-secondary">Scopri la nostra Storia e il Team</a>
    ...
</section>
```
*   Una breve premessa testuale.
*   Il bottone usa `btn-secondary` (bordo oro, sfondo trasparente) per distinguerlo dal bottone principale della Hero.

### Griglia Servizi (Linee 65-86)
*   Usa un `div` con classe `services-grid`. Nel CSS, questo usa `display: grid` per creare colonne automatiche che si adattano allo schermo.
*   Ogni servizio è un `service-card` che contiene un'icona (emoji), un titolo e una descrizione.

### Sezione Caratteristiche (Linee 89-119)
*   La lista `features-list` mostra i punti di forza (Wi-Fi, Schermi HD, ecc.).
*   Le icone (❄️, 📺, 📶) rendono la lettura, immediata.

### Footer (Linee 143-198)
Il piè di pagina è diviso in colonne:
1.  **Info**: Indirizzo e contatti.
2.  **Orari**: Tabella sintetica degli orari.
3.  **Menu**: Link rapidi alle pagine.
4.  **Legal**: Badge "ADM", "18+" e avvertenze legali obbligatorie per legge per i siti di scommesse.

### Script Saldo (Linee 201-214)
```javascript
document.addEventListener('DOMContentLoaded', () => {
    const balanceSpan = document.getElementById('user-balance');
    let balance = localStorage.getItem('walletBalance');
    if (!balance) {
        balance = 500; // Saldo iniziale
        localStorage.setItem('walletBalance', balance);
    }
    if (balanceSpan) balanceSpan.textContent = balance;
});
```
*   Questo codice parte appena la pagina è caricata (`DOMContentLoaded`).
*   Cerca se esiste già un "portafoglio" (`walletBalance`) salvato nel browser dell'utente (`localStorage`).
*   Se è la prima volta che entri (non c'è saldo), ti regala 500 crediti.
*   Infine, scrive il numero dentro l'elemento del menu in alto a destra.

---

## 2. `servizi.html` - Pagina Servizi
(Precedentemente games.html)

Questa pagina ora funge da catalogo dei servizi offerti (Scommesse, Ippica, Slot).
La vecchia sezione di gioco è stata rimossa per fare spazio a una presentazione più pulita.
Mantiene lo stesso stile delle card a zig-zag descritto in precedenza.

---

## 3. `games.html` - Nuova Pagina Giochi

Questa è la nuova pagina dedicata al divertimento interattivo. Include **Roulette** e **Blackjack**.

### Gestione Wallet (Portafoglio Condiviso)
Il sistema di credito è centralizzato.
```javascript
let capitale = parseInt(localStorage.getItem('walletBalance')) || 1000;
```
*   **Persistenza**: Il saldo viene salvato nel browser (`localStorage`). Se cambi pagina e torni, i tuoi soldi sono ancora lì.
*   **Condivisione**: Lo stesso saldo è visibile nell'header, ma modificabile solo giocando in questa pagina.

### Roulette
Logica adattata per WinSport:
*   Generazione dinamica della griglia (`#tavolo`) via JavaScript.
*   Puntata su Numero (35:1) o Colore (1:1).
*   Feedback visivo immediato con messaggi colorati.

### Blackjack
Implementazione completa del classico gioco di carte:
*   **Mazzo Infinito**: Simulato casualmente (`Math.random`).
*   **Logica del Banco**: Il banco tira carta finché non arriva a 17 (regola standard).
*   **Assi**: Gestiti dinamicamente (valgono 1 o 11 in base al totale).
*   **Interfaccia**: Pulsanti "Carta" e "Stai" per interagire.

(La pagina `dovisiamo.html` è stata rimossa come richiesto).

---

## 4. `contatti.html` - Pagina Contatti

Gestisce la comunicazione tra cliente e azienda.

### Layout a Due Colonne (Linee 43-87)
Usa `.contact-container`, che nel CSS è definito come:
```css
.contact-container {
    display: grid;
    grid-template-columns: 1fr 1fr; /* Due colonne uguali */
    gap: 50px;
}
```
*   **Colonna Sinistra (`contact-info-col`)**: Mostra indirizzo, telefono (con emoji) e tabella orari.
*   **Colonna Destra (`contact-form-col`)**: Contiene il modulo di contatto.

### Modulo (Form)
```html
<form class="contact-form" action="#" method="POST">
    <input type="text" ... required>
    <input type="email" ... required>
    <textarea ... required></textarea>
</form>
```
*   I campi `required` obbligano l'utente a compilare tutto prima di inviare.
*   Gli stili `.contact-form input` nel CSS rendono i campi scuri con testo chiaro, integrandosi perfettamente nel tema dark.

---

## 5. `chisiamo.html` - Chi Siamo

Pagina istituzionale rinnovata con focus sul Team.

### Testo Introduttivo (Linee 61-88)
Descrive la missione aziendale ("Sicurezza, Professionalità e Accoglienza").

### Sezione Team Aggiornata (Linee 91-137)
```html
<div class="team-section" id="team">
    <div class="team-grid">
        <!-- Membri del team... -->
    </div>
</div>
```
*   `id="team"`: Permette di linkare direttamente questa sezione (es. `chisiamo.html#team`).
*   La struttura ora usa `.team-grid` e `.team-card`, classi definite nel CSS per il nuovo layout verticale.
*   **Ordine Gerarchico**: CEO -> Co-CEO -> CTO -> Designer -> AI.
*   **Ruoli Aggiornati**: Matteo B. ora appare come Co-CEO.

---

## 6. `style.css` - Design System

File che controlla l'aspetto visivo di tutto il sito.

### Variabili Globali (`:root`)
```css
:root {
    --color-bg: #121212;      /* Nero profondo */
    --color-card: #1E1E1E;    /* Grigio scuro per le schede */
    --color-accent: #D4AF37;  /* ORO METALLICO - Colore chiave */
    --font-main: 'Montserrat', sans-serif;
}
```
Cambiare questi valori cambierebbe i colori in tutto il sito istantaneamente.

### Analisi Approfondita del Design (CSS & Grafica)

Il file `style.css` non è solo un elenco di colori, ma un sistema di design studiato per dare un'immagine "Premium" e professionale.

#### 1. Sistema di Colori e Variabili (`:root`)
```css
:root {
    --color-bg: #121212;      /* Nero "OLED" per profondità */
    --color-card: #1E1E1E;    /* Grigio per distacco visivo */
    --color-accent: #D4AF37;  /* Oro Metallico (Lusso) */
    --shadow-card: 0 4px 6px rgba(0,0,0,0.3);
}
```
*   Perché l'Oro? L'oro su nero è lo standard universale per i centri scommesse e i casinò di lusso.
*   Uso delle Variabili: In tutto il file usiamo `var(--color-accent)`. Questo significa che se volessimo cambiare il colore del sito da Oro a Rosso, basterebbe cambiare UNA riga sopra.

#### 2. Effetti Moderni: Glassmorphism e Gradienti
*   **Gradients**: Molti elementi (come i bottoni e le card) non hanno un colore piatto. Usano `linear-gradient(145deg, #1a1a1a, #252525)`. Questo crea una sottile ombra interna che dà l'idea di una superficie fisica reale.
*   **Neon Glow**: Il badge del saldo (`.wallet-badge`) usa `box-shadow: 0 0 15px rgba(212, 175, 55, 0.3)`. Questo crea un effetto "tubo al neon" che attira l'attenzione senza essere fastidioso.

#### 3. Animazioni e Interattività (Micro-interazioni)
Le animazioni sono studiate per rendere il sito "vivo":
*   **Transizioni Fluide**: Ogni volta che passi il mouse su un link o un bottone, il colore non cambia all'istante, ma in 0,3 secondi (`transition: 0.3s`). Questo rende l'esperienza utente molto più rilassante.
*   **Hover Scaling**: In `chisiamo.html`, le card dell'organigramma si ingrandiscono leggermente (`transform: scale(1.08)`) ed evidenziano il bordo in oro. È un feedback visivo che conferma all'utente "sto interagendo con questo elemento".
*   **Keyframes (Shake e Spin)**:
    - `@keyframes shake`: Usata nella roulette quando il saldo è basso per comunicare errore visivamente.
    - `transition: transform 3s cubic-bezier(...)`: Usata nella roulette per simulare l'attrito fisico che rallenta la ruota gradualmente prima di fermarsi.

#### 4. Layout Responsive (Mobile First)
*   **Flexbox & Grid**: Usiamo `display: flex` e `display: grid` ovunque. Sono gli strumenti più potenti del CSS moderno per allineare gli elementi.
*   **Media Queries**: Nelle ultime righe del file trovi `@media (max-width: 768px)`. Questo blocco di codice si attiva SOLO se lo schermo è piccolo. Cambia la navigazione e i servizi da righe a colonne per permettere una lettura facile sul telefono.

---

## 7. Approfondimento Tecnico: Logica di Gioco (JavaScript)

In questa sezione analizziamo nel dettaglio come funzionano le funzioni chiave dei giochi in `games.html`.

### ROULETTE: `spinWheel(choice)`

Questa funzione gestisce l'intera animazione e logica della roulette.

1.  **Verifica Saldo**:
    ```javascript
    if (balance < cost) { ... }
    ```
    Controlla se l'utente ha abbastanza crediti (50). Se no, fa vibrare il badge del portafoglio (`animation: shake`).

2.  **Detrazione Costo**:
    ```javascript
    balance -= cost;
    ```
    Toglie subito i soldi, come una vera macchinetta che "mangia" il gettone.

3.  **Determinismo (Il trucco)**:
    Il sito non aspetta che la ruota si fermi per sapere chi ha vinto. Decide SUBITO.
    ```javascript
    const isWin = Math.random() < 0.5; // Testa o croce (50%)
    ```
    Se `isWin` è vero, forza la ruota a fermarsi sul colore scelto dall'utente. Altrimenti, la forza sul colore opposto.

4.  **Calcolo Angolo (Matematica)**:
    La ruota è un'immagine o elemento CSS. Per farla fermare su un colore specifico, dobbiamo ruotarla di un numero preciso di gradi.
    *   La ruota ha 20 spicchi -> 18 gradi per spicchio.
    *   I segmenti pari (0, 2, 4...) sono Rossi.
    *   I segmenti dispari (1, 3, 5...) sono Neri.
    Il codice sceglie un indice a caso (es. segmento 4) che corrisponde al colore vincente e calcola i gradi totali (`targetSegment * 18`).

5.  **Animazione CSS**:
    Applica una rotazione enorme (es. `rotate(1800deg)`) tramite CSS `transform`. Grazie alla proprietà `transition`, il browser anima questo cambiamento in modo fluido per 3 secondi.

### BLACKJACK: `iniziaMano()`, `chiediCarta()`, `stai()`

Il Blackjack usa un "Vettore di Stato" per tenere traccia delle carte.

1.  **Mazzo Infinito**:
    Non usiamo un mazzo di 52 carte che si esaurisce. Ogni carta è generata al momento con `Math.random() * 13`. Questo simula un casinò che rimescola dopo ogni mano (impossibile contare le carte).

2.  **Valore Assi (Funzione `totale(mano)`)**:
    Questa è la parte più intelligente.
    ```javascript
    while(assi > 0 && somma + 10 <= 21){
        somma += 10;
        assi--;
    }
    ```
    Calcola la somma base considerando l'Asso come 1. Poi, SE hai un Asso E se aggiungendo 10 non sballi (non superi 21), trasforma quell'Asso in un 11. Questo avviene automaticamente a ogni carta pescata.

3.  **Intelligenza Artificiale del Banco (`stai()`)**:
    Quando il giocatore si ferma, il banco gioca da solo:
    ```javascript
    while(totale(manoBanco) < 17){
        manoBanco.push(pescaCarta());
    }
    ```
    È una regola fissa: il banco DEVE tirare se ha 16 o meno. DEVE stare se ha 17 o più. Non fa scelte umane, segue un algoritmo.

---

## 8. Conclusioni Tecniche


Il progetto WinSport è stato costruito seguendo i massimi standard del web moderno (W3C):
- **HTML5 Semantico**: Per una corretta lettura dei motori di ricerca.
- **CSS3 Avanzato**: Per un'estetica di alto livello senza appesantire il sito con immagini pesanti.
- **JS Algoritmico**: Per una logica di gioco precisa e "C++ style".

Tutto il codice è commentato e modulare, pronto per essere espanso con nuove funzionalità.
