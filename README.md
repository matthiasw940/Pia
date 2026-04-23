# 🍞 Toast Atelier — Pia's Frühstücks-Studio

Eine einseitige, statische Web-App zur Konfiguration von Toast-Bestellungen im Ghibli-Stil. Beim Abgeben einer Bestellung wird automatisch eine E-Mail an dich verschickt — **ohne dass Pia's Mail-Postfach aufgehen muss**.

![GitHub Pages](https://img.shields.io/badge/deploy-GitHub%20Pages-blue) ![Web3Forms](https://img.shields.io/badge/email-Web3Forms-green)

## ✨ Features

- Mario-Kart-artiger Slot-Konfigurator für Brot, Aufstrich, Tomate, Schinken und Ei
- Per-Teller individuelle Mengen
- Mehrere Toasts pro Bestellung (nebeneinander auf eigenem Teller)
- Optionaler Kaffee mit „I ❤ Pia"-Tasse
- Sonderwunsch-Feld
- Rechnung im Receiptify-Thermopapier-Stil nach Abgabe
- Interaktive Zubereitungs-Checkliste
- **Automatischer E-Mail-Versand** per Web3Forms (kein Mail-Client nötig!)
- 100 % statisch: kein eigener Backend, keine Dependencies

## 🚀 Setup (5 Minuten)

### Schritt 1: Web3Forms Access-Key holen

1. Gehe auf **[web3forms.com](https://web3forms.com)**
2. Trage deine E-Mail-Adresse ein (die, auf der du die Bestellungen empfangen willst)
3. Klicke „Create Access Key"
4. Du bekommst sofort einen Access-Key per E-Mail zugeschickt

> 🎁 Kostenlos bis **250 Mails/Monat**, kein Account, keine Registrierung.

### Schritt 2: Key im Code eintragen

Öffne `index.html` und suche im `<script>`-Block (ganz am Anfang) nach:

```javascript
const WEB3FORMS_KEY = 'YOUR_ACCESS_KEY_HERE';  // ← hier deinen Key einfügen
```

Ersetze `YOUR_ACCESS_KEY_HERE` durch deinen Key, z. B.:

```javascript
const WEB3FORMS_KEY = 'a1b2c3d4-5678-90ab-cdef-1234567890ab';
```

### Schritt 3: Auf GitHub Pages deployen

```bash
git init
git add index.html README.md .gitignore
git commit -m "Initial commit: Toast Atelier"
git branch -M main
git remote add origin https://github.com/<dein-user>/<repo>.git
git push -u origin main
```

Danach:
- Repo → **Settings** → **Pages**
- **Source:** `Deploy from a branch`
- **Branch:** `main` / `(root)` → **Save**
- Nach ~1 Minute ist die App live unter `https://<dein-user>.github.io/<repo>/`

## 📧 So funktioniert der Mail-Versand

Wenn Pia auf „Bestellung abgeben" drückt, passiert im Hintergrund ein `fetch()` auf die Web3Forms-API. Web3Forms sendet dann direkt eine formatierte E-Mail an deine hinterlegte Adresse mit:

- **Betreff:** `Pia's Frühstücks-Bestellung — <Datum>`
- **Body:** Alle Toasts mit Mengen, Zutaten, Sonderwunsch, Gesamtpreis in 💋

Pia sieht davon nichts — sie sieht einfach die Rechnungs-Ansicht und kann mit der Zubereitung beginnen. Die Mail landet still in deinem Postfach.

## 🛠️ Lokale Entwicklung

Einfach `index.html` im Browser öffnen:

```bash
open index.html       # macOS
xdg-open index.html   # Linux
start index.html      # Windows
```

Oder mit einem lokalen Server:

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

## 🎨 Anpassungen

Alles in einer Datei:

- **Zutaten:** im `OPTS`-Objekt im `<script>`
- **Kreative Toast-Namen:** im `NAMES`-Objekt
- **Styles:** im `<style>`-Block oben
- **Mail-Adresse:** bei Web3Forms im Dashboard ändern

## 📄 Mit Liebe für Pia ♥
