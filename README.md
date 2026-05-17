# kaktus-tycoon-calc
Interaktiver Produktionsrechner für Kaktus-Tycoon auf Cytooxien. Berechnet Kaktus-, Energie- und Kohleproduktion inklusive Booster, Engpässen und Laufzeiten. Die gesamte Fabrik wird als übersichtliches Flussdiagramm visualisiert und live berechnet.


Der Rechner berücksichtigt:

* Energieverbrauch & Energieproduktion
* Kohleproduktion & Kohleverbrauch
* Begrenzte Holzvorräte bei Holzöfen
* Booster mit zeitabhängiger Laufzeit
* Produktionsmengen über beliebige Zeiträume
* Engpässe wie Strom- oder Kohlemangel

Alle Berechnungen laufen vollständig lokal im Browser.



---

# Starten der Website

## Variante 1 — Direkt lokal öffnen

Einfach die Datei öffnen:

```
kaktus-tycoon-rechner.html
```

Die Website funktioniert komplett ohne Installation.

---

## Variante 2 — Mit lokalem Webserver (optional)

Falls Browser bestimmte lokale Funktionen blockieren:

### Python

```
python -m http.server 8080
```

Danach im Browser öffnen:

```
http://localhost:8080
```

---


# Aufbau der Oberfläche

Die Website ist in 4 Hauptbereiche unterteilt:

| Bereich | Funktion                                    |
| ------- | ------------------------------------------- |
| Kohle   | Kohleproduktion durch Kohlebohrer           |
| Energie | Stromproduktion durch Kraftwerke & Holzöfen |
| Kaktus  | Kaktusproduktion durch Sammler & Fabriken   |
| Output  | Gesamtergebnis & Effizienz                  |

Jedes Element wird als eigene Karte dargestellt.

# Kaktus-Sammler

Der Kaktus-Sammler produziert direkt Kakteen pro Sekunde.

## Eingabe

| Feld              | Bedeutung               |
| ----------------- | ----------------------- |
| Kakteen / Sekunde | Direkte Produktionsrate |

#  Kohlebohrer

Kohlebohrer erzeugen Kohle für Kohlekraftwerke.

## Eingaben

| Feld             | Bedeutung                              |
| ---------------- | -------------------------------------- |
| Kohle produziert | Wie viel Kohle pro Zyklus erzeugt wird |
| Intervall (Sek)  | Wie oft produziert wird                |

# Kohlekraftwerk

Kohlekraftwerke wandeln Kohle in Energie um.

## Eingaben

| Feld          | Bedeutung                     |
| ------------- | ----------------------------- |
| Energie prod. | Produzierter Strom pro Zyklus |
| Kohle verb.   | Verbrauchte Kohle pro Zyklus  |
| Intervall     | Dauer eines Produktionszyklus |

# Holzofen

Holzöfen erzeugen ebenfalls Energie.

## Eingaben

| Feld          | Bedeutung                |
| ------------- | ------------------------ |
| Energie prod. | Strom pro Zyklus         |
| Holz verb.    | Holzverbrauch pro Zyklus |
| Intervall     | Dauer eines Zyklus       |
| Holz im Lager | Startmenge an Holz       |

# Kaktus-Fabrik

Die Kaktus-Fabrik wandelt Energie in Kakteen um.

## Wichtig

Die Fabrik produziert nur dann Kakteen, wenn genug Energie vorhanden ist.

Bei Strommangel reduziert der Rechner die Produktion automatisch.

## Eingaben

| Feld          | Bedeutung                      |
| ------------- | ------------------------------ |
| Kaktus prod.  | Produzierte Kakteen pro Zyklus |
| Energie verb. | Verbrauchte Energie pro Zyklus |
| Intervall     | Dauer eines Produktionszyklus  |

# Booster-System

Jedes Element kann geboostet werden.

## Booster öffnen

Auf:
🚀 Booster
klicken.

Danach erscheinen die Booster-Einstellungen.

## Eingaben

| Feld          | Bedeutung                     |
| ------------- | ----------------------------- |
| Multiplikator | Produktions-Multiplikator     |
| Laufzeit      | Dauer des Boosters in Stunden |

## Wichtig
Falls Booster aktiv sind, werden diese in der Produktion von Cytooxien automatisch mitberechnet. Da bei der jeweiligen Fabrik/o.ä. allerdings der Basiswert angegeben werden muss, muss hier erst manuell der Wert durch den Wert des Multiplikators geteilt werden.
Beispiel:
Ist der verwendete Multiplikator 3x, so muss der Produktionswert erst durch 3 geteilt werden, um richtige Ergebnisse in der Berechnung zu liefern.

---

# Output-Bereich

Rechts wird die gesamte Produktion zusammengefasst.

## Angezeigt wird

* Kohleproduktion/s
* Energieproduktion/s
* Sammlerproduktion/s
* Fabrikproduktion/s
* Gesamtproduktion/s
* Fabrikeffizienz

---

# Warnungen & Engpässe

Der Rechner erkennt automatisch Probleme.

## Beispiele

### Strommangel
-> Kaktus-Fabrik läuft auf 62% Auslastung

### Kohlemangel
-> Kohlekraftwerk produziert keinen Strom

### Holz fast leer
->Holz reicht noch ca. 34min

---

# Produktion über Zeiträume

Unten können beliebige Zeiträume eingegeben werden.

Der Rechner berücksichtigt dabei automatisch:
* Booster-Ablauf
* Holzverbrauch
* Produktionsstopps
* Engpässe

---

# Wie die Berechnung funktioniert

Der Rechner simuliert die Produktionskette logisch:
1. Kohle wird produziert
2. Kohlekraftwerke prüfen Kohlevorrat
3. Energie wird erzeugt
4. Kaktus-Fabriken prüfen Energie
5. Kakteen werden produziert

Fehlen Ressourcen, wird die Produktion reduziert.

Dadurch entstehen realistische Ergebnisse statt einfacher Durchschnittswerte.

---

# 🛠️ Technisches
* Reines HTML/CSS/JavaScript
* Keine Frameworks
* Keine Datenübertragung
* Keine Installation notwendig
* Komplett lokal ausführbar
* WICHTIG: Disclaimer: Der gesamte Code wurde mit claude.ai generiert. Die Ergebnisse sind Grobe SChätzungen und erheben keinerlei Anspruch auf richtigkeit.
