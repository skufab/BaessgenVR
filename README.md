# Baustellen-Scan Viewer

Zeigt Polycam-3D-Scans (.glb) direkt im Browser an — auch in VR-Brillen (Meta Quest & Co.), ganz ohne Login und ohne App-Store.

## Einrichtung (einmalig)

1. Repo auf GitHub anlegen (oder bestehendes wie bei "Vorratskammer" nutzen, z. B. neuer Ordner `vr-viewer`).
2. Diese Datei `index.html` in den Ordner hochladen.
3. Einen Unterordner `models/` anlegen und dort deine `.glb`-Dateien reinlegen.
4. In GitHub → Settings → Pages: GitHub Pages für den Branch aktivieren.
5. Die Seite ist dann erreichbar unter z. B.:
   `https://<dein-github-name>.github.io/<repo-name>/`

## Neue Baustelle/Scan hinzufügen

1. GLB-Datei aus Polycam exportieren (Export → GLTF/GLB).
2. Datei in den Ordner `models/` hochladen.
3. In `index.html` im Abschnitt `const MODELS = [...]` einen neuen Eintrag ergänzen:

```js
{
  name: "Musterstraße 12 — Fassade",
  src: "models/musterstrasse12.glb",
  hotspots: [
    { position: "0.5 1.2 -0.3", normal: "0 0 1", label: "Riss, vor Anstrich spachteln" }
  ]
}
```

4. Speichern, hochladen — die Seite aktualisiert sich automatisch (kann 1–2 Minuten dauern).

## Hotspots (Kommentare im 3D-Modell) setzen

Die `position`-Werte sind 3D-Koordinaten im Modell (X Y Z, durch Leerzeichen getrennt).
Am einfachsten: Wert grob schätzen, Seite neu laden, Punkt-Position im Modell prüfen,
Wert anpassen — nach 2–3 Versuchen sitzt er meist richtig.

Wenn's dir zu fummelig ist, sag Bescheid — man kann Punkte auch per Klick direkt im
Browser setzen lassen, das wäre ein kleiner Zusatz-Baustein für die Seite.

## Nutzung auf der Meta Quest (oder anderer VR-Brille)

1. Im Quest-Browser die GitHub-Pages-URL öffnen.
2. Baustelle im Dropdown oben rechts auswählen.
3. Auf "In VR/AR ansehen" tippen → immersiver Modus startet, mit Teleport per Controller.
4. Am Laptop parallel per **Meta-Taste → Quick Settings → Cast** mitschauen (Code am
   Laptop unter meta.com/casting eingeben).

## Hinweis

Kommentare/Hotspots aus der Polycam-App selbst werden **nicht** mit exportiert — die
Hotspots hier sind eine eigene, einfache Ersatzlösung, die direkt im Code gepflegt wird.
