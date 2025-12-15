# Lagerprozess - IST-Analyse

**Erstellt:** 2025-12-14 | **Quelle:** Gespraech mit Andreas

---

## Prozess-Uebersicht

```
LIEFERUNG KOMMT AN (aus Bestellprozess)
│
▼
1. WARENANNAHME
├─ Wer: Mario (vormittags), andere (nachmittags)
├─ Grosse Ware → Lager
├─ Pakete → Buero
├─ PROBLEM: Falsche Lieferadressen!
│
▼
2. PRUEFUNG
├─ Gegen Lieferanten-LS (zeigt korrekte Teilmenge)
├─ NICHT gegen W4A-Bestellung
│
▼
3. LS ERFASSEN
├─ Roland: Scannt LS → Scanner-Ordner
├─ Roland: Legt in W4A Eingangslieferschein unter Dokumente ab
├─ KRITISCH: Uebernimmt komplette BE statt Teilmenge!
│
▼
4. EINLAGERUNG
├─ Fenstergestelle: Fester Bereich, werden bei Bedarf vorgeholt
├─ Anderes Material: Feste Plaetze, nach Themen sortiert
├─ KEINE Lagerbuchung in W4A!
│
▼
5. INFO AN PLANUNG
├─ Roland gibt Susann Bescheid
├─ Akt wird hingelegt
├─ Susann traegt in Outlook ein
│
▼
6. KOMMISSIONIERUNG (Vorabend/Morgens)
├─ Mario bekommt Info welche Montage geplant ist
├─ Liest Montagescheine → ermittelt benoetigte Waren
├─ Holt Gestell vor wenn noetig
├─ Material nur durch Erfahrung findbar!
│
▼
MONTAGE (naechster Prozess)
```

---

## Details pro Schritt

### 1. Warenannahme

| Aspekt | IST-Zustand |
|--------|-------------|
| **Wer (vormittags)** | Mario |
| **Wer (nachmittags)** | Jaroslaw, Andreas, oder Monteure |
| **Grosse Ware** | → Lager (Fenstergestelle, Paletten) |
| **Pakete** | → Buero |

**Lieferadressen-Problem:**
| Quelle | Problem |
|--------|---------|
| W4A (ERP) | Standard = Buero, wird vergessen umzustellen |
| Ammon Online Shop | Adresse hinterlegt, wird trotzdem vergessen |
| Versandart | Paket vs. LKW wird vergessen umzustellen |
| **Folge** | Grosse Ware landet im Buero statt Lager! |

### 2. Pruefung

| Aspekt | IST-Zustand |
|--------|-------------|
| **Geprueft gegen** | Lieferanten-Lieferschein |
| **Nicht geprueft gegen** | W4A-Bestellung |
| **Grund** | LS zeigt korrekte Teilmenge, BE zeigt alles |

### 3. LS erfassen in W4A

| Aspekt | IST-Zustand |
|--------|-------------|
| **Wer** | Roland |
| **Scan** | In Scanner-Ordner |
| **Ablage** | W4A Eingangslieferschein → Dokumente |

**KRITISCHES PROBLEM - Eingangslieferschein:**
| Problem | Details |
|---------|---------|
| LS vom Lieferant | Zeigt korrekt Teilmenge (z.B. 3 von 5 Fenstern) |
| Roland in W4A | Uebernimmt komplette BE → alle 5 Fenster als geliefert |
| Datenbank | Zeigt falsche Bestaende |
| **Folge** | W4A unbrauchbar fuer Folgeprozesse (Montageplanung, Lagerverwaltung) |

### 4. Einlagerung

| Bereich | Organisation |
|---------|--------------|
| **Fenstergestelle** | Fester Lagerbereich, werden verschoben je nach Bedarf |
| **Anderes Material** | Feste Lagerplaetze |
| **Regal-Struktur** | Nach Themen sortiert |
| **Lagerbuchung** | KEINE in W4A! |

**Gestell-Management:**
- Gestelle werden vorgeholt fuer naechsten Tag
- Einzelne Elemente oder ganze Gestelle werden verladen
- Kein System zur Zuordnung "Element X auf Gestell Y"

### 5. Info an Planung

| Schritt | Wer | Was |
|---------|-----|-----|
| 1 | Roland | Gibt Susann Bescheid (muendlich/Akt hinlegen) |
| 2 | Susann | Traegt alle Infos in Outlook-Auftrag ein |

**Medienbruch:** Papier-LS → muendlich → Outlook (kein durchgaengiges System)

### 6. Kommissionierung

| Aspekt | IST-Zustand |
|--------|-------------|
| **Wann** | Vorabend oder morgens |
| **Wer** | Mario (wenn im Lager), sonst Andreas/Jaroslaw |
| **Info-Quelle** | Mario bekommt Info welche Montage geplant ist |
| **Waren ermitteln** | Liest Montagescheine aus |
| **Fenster/HT** | Holt Gestell vor (wenn nicht schon zugaenglich) |
| **Material finden** | Nur durch Erfahrung! |

---

## Erkannte Schmerzpunkte

| # | Schmerzpunkt | Auswirkung | Relevante Ideen |
|---|--------------|------------|-----------------|
| 1 | **Eingangslieferschein mit allen Positionen** | W4A-Daten falsch, Folgeprozesse brechen | #33 Bestellwesen |
| 2 | **Lieferadresse vergessen (ERP + Shops)** | Grosse Ware im Buero | #57 Lieferadressen-Logik |
| 3 | **Versandart (Paket/LKW) vergessen** | Falsche Lieferart | #57 erweitern |
| 4 | **Keine Lagerbuchungen** | Kein Bestandsueberblick | #38 Lagerverwaltung |
| 5 | **Material nur durch Erfahrung findbar** | Wissens-Abhaengigkeit, Einarbeitung schwer | #38 Lagerverwaltung |
| 6 | **Kein Gestell-Tracking** | "Welches Element auf welchem Gestell?" | #38 erweitern |
| 7 | **Medienbruch LS → Outlook** | Manueller Aufwand, Fehlerquelle | #36 Beschaffungs-Dashboard |
| 8 | **Pruefung nur gegen LS** | Abweichungen zur Bestellung unentdeckt | #56 AB-Abgleich |
| 9 | **Lieferankuendigungen fehlen/spontan** | Ware kommt unangekuendigt, Abladen ohne Bescheid | - |
| 10 | **Fahrer-Telefonnummern falsch** | Keine Rueckfragen moeglich | - |

---

## Verbesserungspotential (Ideen-Verknuepfung)

| Phase | Tool-Idee | Verbesserung |
|-------|-----------|--------------|
| Warenannahme | #57 Lieferadressen-Logik | Auto-Adresse + Versandart je Artikeltyp |
| LS erfassen | #33 Bestellwesen | Korrekte Teilmengen-Buchung erzwingen |
| LS erfassen | #56 AB-Abgleich | Pruefung LS gegen Bestellung |
| Einlagerung | #38 Lagerverwaltung | Echte Lagerbuchungen + Lagerplatz-System |
| Einlagerung | #38 erweitern | Gestell-Tracking (Element → Gestell) |
| Info an Planung | #36 Beschaffungs-Dashboard | Automatische Status-Updates |
| Kommissionierung | #40 Material-Kommissionierliste | Auto-Liste aus Bestellpositionen |

---

## Prozess-Uebergaenge

### Bestellprozess → Lagerprozess
- Trigger: Lieferung kommt an
- Info: Lieferanten-LS

### Lagerprozess → Montageprozess
- Trigger: Roland gibt Susann Bescheid "Ware da"
- Info: Outlook-Kachel aktualisiert
- Kommissionierung: Mario bereitet Material vor

---

## Beantwortete Fragen

| # | Frage | Antwort |
|---|-------|---------|
| 1 | Teillieferungen in Outlook? | Kachel bleibt in "nicht geliefert" Farbe |
| 2 | Wer entscheidet bei Teillieferung? | Projektmanager (Jaroslaw/Andreas) |
| 3 | Ruecklaeufer vom Monteur? | Ja, siehe unten |
| 4 | Lagerzeit bis Montage? | Ideal: naechster Tag. Real: oft Wochen |

---

## Ruecklaeufer vom Monteur

### IST-Zustand
| Aspekt | Details |
|--------|---------|
| **Haeufigkeit** | Oft |
| **Was** | Nicht benoetigtes Montagematerial |
| **Wer lagert ein** | Monteur selbst oder Mario |
| **Dokumentation** | Nur was Kunden direkt verrechnet wird |
| **Montagematerial** | Schrauben, Schaum etc. ueber Montagematerialposition abgedeckt |
| **Berechnung** | Excel-Liste, muss haendisch aktualisiert werden |

### Schmerzpunkt: Fehlende Rueckmeldung
| Problem | Folge |
|---------|-------|
| Ruecklaeufer/Austausch wird NICHT notiert | Position bleibt auf Rechnung |
| Kunde reklamiert | Rechnungskorrektur noetig |
| Aufwand | Doppelte Arbeit, schlechter Eindruck |

### Relevante Idee
→ **#39 Montage-Mappe** erweitern um Material-Rueckmeldung
