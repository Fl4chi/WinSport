<div align="center">

# 🎰 WinSport

### *Il Punto di Riferimento per gli Appassionati di Sport*

[![Live Demo](https://img.shields.io/badge/🌐_Live_Demo-Visit_Site-gold?style=for-the-badge)](https://winsport-2ijt.onrender.com/)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

![WinSport Banner](https://img.shields.io/badge/Centro_Scommesse_Sportive-Premium_Experience-D4AF37?style=flat-square)

</div>

---

## 📋 Indice

- [✨ Panoramica](#-panoramica)
- [🎯 Caratteristiche Principali](#-caratteristiche-principali)
- [🎮 Giochi Interattivi](#-giochi-interattivi)
- [🛠️ Tecnologie Utilizzate](#️-tecnologie-utilizzate)
- [📁 Struttura del Progetto](#-struttura-del-progetto)
- [🚀 Come Iniziare](#-come-iniziare)
- [💻 Deployment](#-deployment)
- [👥 Team](#-team)
- [📄 Licenza](#-licenza)

---

## ✨ Panoramica

**WinSport** è un progetto web moderno che simula un centro scommesse sportive di alta gamma. Il sito combina un design elegante **dark-themed** con funzionalità interattive, offrendo un'esperienza utente coinvolgente e professionale.

### 🎨 Design Philosophy

- **🖤 Dark Mode Premium**: Palette oro (#D4AF37) su nero (#121212) per un look lussuoso
- **✨ Glassmorphism**: Effetti vetro e neon per un'estetica moderna
- **📱 Mobile-First**: Completamente responsive su tutti i dispositivi
- **⚡ Performance**: Caricamento rapido senza dipendenze esterne pesanti

---

## 🎯 Caratteristiche Principali

### 🏠 Homepage Coinvolgente
- **Hero Section** con call-to-action immediata
- **Griglia Servizi** con card interattive (Scommesse, Ippica, Slot)
- **Sistema Wallet** persistente con LocalStorage

### 📄 Pagine Dedicate

| Pagina | Descrizione |
|--------|-------------|
| 🏠 **Home** | Landing page con panoramica servizi e features |
| ⚙️ **Servizi** | Dettaglio scommesse, ippica e slot machines |
| 🎮 **Games** | Roulette e Blackjack giocabili in-browser |
| 📞 **Contatti** | Form di contatto e informazioni aziendali |
| 👥 **Chi Siamo** | Storia del team e organigramma aziendale |

### 🎲 Sistema Wallet Integrato
```javascript
// Il saldo viene salvato nel browser dell'utente
localStorage.setItem('walletBalance', balance);
// Sincronizzato tra tutte le pagine
```

---

## 🎮 Giochi Interattivi

### 🎡 Roulette Europea

**Meccaniche di Gioco:**
- 🎯 Puntata su **Numero Specifico** (35:1)
- 🔴⚫ Puntata su **Rosso/Nero** (1:1)
- 💫 Animazione fisica realistica con `cubic-bezier`
- 💰 Costo: 50 crediti per spin

**Tecnologia:**
```javascript
// Calcolo deterministico del risultato
const isWin = Math.random() < 0.5;
const targetSegment = segments[Math.floor(Math.random() * segments.length)];
const totalDegrees = 1800 + (targetSegment * 18);
```

### 🃏 Blackjack Classico

**Features:**
- ♠️ Mazzo infinito (no card counting)
- 🎴 Gestione intelligente degli **Assi** (1 o 11)
- 🤖 AI del Banco (ferma a 17+)
- 💵 Puntate personalizzabili

**Algoritmo Assi:**
```javascript
function totale(mano) {
  let somma = mano.reduce((acc, carta) => acc + Math.min(carta, 10), 0);
  let assi = mano.filter(c => c === 1).length;
  while (assi > 0 && somma + 10 <= 21) {
    somma += 10;
    assi--;
  }
  return somma;
}
```

---

## 🛠️ Tecnologie Utilizzate

### Frontend Stack

<div align="center">

| Tecnologia | Uso | Versione |
|:----------:|:---:|:--------:|
| ![HTML5](https://img.shields.io/badge/-HTML5-E34F26?style=flat-square&logo=html5&logoColor=white) | Struttura semantica | 5 |
| ![CSS3](https://img.shields.io/badge/-CSS3-1572B6?style=flat-square&logo=css3&logoColor=white) | Design System | 3 |
| ![JavaScript](https://img.shields.io/badge/-JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black) | Logica interattiva | ES6+ |

</div>

### Design Patterns

- **🎨 CSS Variables**: Sistema di temi centralizzato
- **📦 CSS Grid & Flexbox**: Layout responsive
- **✨ CSS Transitions**: Micro-interazioni fluide
- **💾 LocalStorage API**: Persistenza dati client-side

### Fonts & Icons
```css
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;700&display=swap');
/* Font primario per un look moderno e pulito */
```

---

## 📁 Struttura del Progetto

```plaintext
WinSport/
│
├── 📄 index.html              # Homepage con hero e servizi
├── 📄 servizi.html            # Pagina catalogo servizi
├── 📄 games.html              # Roulette & Blackjack
├── 📄 contatti.html           # Form contatti + info
├── 📄 chisiamo.html           # Team & storia aziendale
│
├── 📂 css/
│   └── 📄 style.css           # Design System completo
│                              # • 800+ linee di CSS
│                              # • Responsive breakpoints
│                              # • Animazioni & transizioni
│
└── 📄 DOCUMENTAZIONE.md       # Analisi tecnica completa
                               # (331 righe, 14 KB)
```

### 📊 Statistiche Codice

```
📈 Totale Linee: ~2500+
📁 File HTML: 5
🎨 File CSS: 1 (800+ linee)
⚙️ JavaScript: Inline (giochi & wallet)
```

---

## 🚀 Come Iniziare

### Opzione 1: Visita il Sito Live

🌐 **[Apri WinSport](https://winsport-2ijt.onrender.com/)** - Deployed su Render

### Opzione 2: Clone Locale

```bash
# 1. Clona il repository
git clone https://github.com/Fl4chi/WinSport.git

# 2. Entra nella cartella
cd WinSport

# 3. Apri con un server locale (es. Live Server su VSCode)
# Oppure semplicemente apri index.html nel browser
```

### 🔧 Requisiti

- **Browser Moderno**: Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- **JavaScript Abilitato**: Necessario per i giochi
- **LocalStorage Attivo**: Per salvare il saldo wallet

### ⚙️ Personalizzazione Colori

Modifica le variabili CSS in `style.css`:

```css
:root {
  --color-bg: #121212;        /* Sfondo principale */
  --color-card: #1E1E1E;      /* Card e sezioni */
  --color-accent: #D4AF37;    /* Oro (brand color) */
  --color-text: #FFFFFF;       /* Testo primario */
}
```

---

## 💻 Deployment

### 📦 Deploy su Render (Attuale)

**Configurazione:**
- **Build Command**: *Vuoto* (sito statico)
- **Publish Directory**: `.` (root)
- **Auto-Deploy**: Abilitato su push master

### 🌐 Alternative Hosting

| Provider | Difficoltà | Costo | Tempo |
|----------|:----------:|:-----:|:-----:|
| **Render** | ⭐ | Gratis | 2 min |
| **Netlify** | ⭐ | Gratis | 2 min |
| **Vercel** | ⭐⭐ | Gratis | 3 min |
| **GitHub Pages** | ⭐⭐ | Gratis | 5 min |

### 📝 Steps Generici

1. Fai il push del codice su GitHub
2. Connetti il repo al provider scelto
3. Configura come **Static Site**
4. Deploy automatico! ✨

---

## 👥 Team

<div align="center">

### 🏆 Organigramma

| Ruolo | Nome | Responsabilità |
|-------|------|----------------|
| 👑 **CEO** | Fabio Franchi | Visione strategica & direzione |
| 🤝 **Co-CEO** | Matteo B. | Co-leadership & partnership |
| 💻 **CTO** | Andrea S. | Architettura tecnica & sviluppo |
| 🎨 **Lead Designer** | Luca M. | UI/UX & brand identity |
| 🤖 **AI Assistant** | Claude | Supporto sviluppo & documentazione |

</div>

---

## 📚 Documentazione Completa

Per un'analisi tecnica **riga-per-riga** di tutto il codice, consulta:

📖 **[DOCUMENTAZIONE.md](./DOCUMENTAZIONE.md)** - 331 linee di analisi approfondita

**Contenuti:**
- 🔍 Analisi HTML di tutte le pagine
- 🎨 Deep dive nel sistema CSS
- ⚙️ Spiegazione algoritmi JavaScript
- 🎮 Logica di gioco (Roulette & Blackjack)
- 🏗️ Architettura e design patterns

---

## 📄 Licenza

Questo progetto è sviluppato per scopi **educativi e dimostrativi**.

⚠️ **Disclaimer**: WinSport è una simulazione. Non permette scommesse reali con denaro.

---

<div align="center">

### 🌟 Supporta il Progetto

Se ti piace WinSport, lascia una ⭐ su GitHub!

[![GitHub Stars](https://img.shields.io/github/stars/Fl4chi/WinSport?style=social)](https://github.com/Fl4chi/WinSport)
[![GitHub Forks](https://img.shields.io/github/forks/Fl4chi/WinSport?style=social)](https://github.com/Fl4chi/WinSport/fork)

---

**Made with 💛 by the WinSport Team**

🎲 *"Segui le partite in diretta e vivi l'emozione dello sport"* 🎲

</div>
