# SC Boasters Bochum — Website

Statische, einsprachig gebaute (DE/EN per JS-Umschalter) Ein-Seiten-Website für den
SC Boasters Bochum. Bereit zum Hosten über **GitLab Pages**.

## Projektstruktur

```
.
├── public/
│   └── index.html      ← die komplette Website (HTML/CSS/JS in einer Datei)
├── .gitlab-ci.yml       ← Pipeline, die public/ als GitLab Pages veröffentlicht
└── README.md
```

GitLab Pages verlangt, dass die fertige Website im Ordner `public/` liegt.
Das ist hier bereits erledigt — es ist kein Build-Schritt nötig.

## Einrichtung (einmalig)

1. **Neues, leeres Projekt auf GitLab anlegen**
   z. B. unter `https://gitlab.com/<dein-namespace>/scboasters-bochum`
   (kein README/Lizenz beim Erstellen anhaken, damit es wirklich leer ist).

2. **Dieses Projektverzeichnis pushen**

   ```bash
   cd scboasters-pages
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://gitlab.com/<dein-namespace>/scboasters-bochum.git
   git push -u origin main
   ```

3. **Pipeline abwarten**
   GitLab startet automatisch eine Pipeline (Tab **CI/CD → Pipelines**).
   Sobald sie grün ist, ist die Seite live.

4. **URL prüfen**
   Unter **Settings → Pages** in deinem GitLab-Projekt erscheint die fertige URL,
   typischerweise:

   ```
   https://<dein-namespace>.gitlab.io/scboasters-bochum/
   ```

   (Bei einem Projekt, das exakt `<dein-namespace>.gitlab.io` heißt, liegt die Seite
   direkt unter `https://<dein-namespace>.gitlab.io/`.)

## Eigene Domain (optional)

Unter **Settings → Pages → New Domain** kannst du eine eigene Domain
(z. B. `www.scboasters-bochum.de`) hinterlegen und per DNS (CNAME) auf die
GitLab-Pages-Adresse zeigen lassen. GitLab stellt dafür automatisch ein
Let's-Encrypt-Zertifikat aus.

## Änderungen vornehmen

Einfach `public/index.html` bearbeiten, committen und pushen — die Pipeline
veröffentlicht die neue Version automatisch.

## Hinweise

- Die Seite lädt Google Fonts (`Space Grotesk`, `Inter`) per CDN — dafür ist
  eine normale Internetverbindung im Browser der Besucher nötig, keine
  serverseitige Konfiguration erforderlich.
- Alle Grafiken (Court-Linien, Spieler-Illustrationen, Schläger-Icon) sind als
  Inline-SVG direkt in der HTML-Datei enthalten — keine externen Bilddateien,
  keine kaputten Links.
- Die Sprache lässt sich über den DE/EN-Button oben rechts umschalten
  (Auswahl wird im `localStorage` des Browsers gemerkt).
