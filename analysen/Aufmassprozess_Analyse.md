# Aufmassprozess - IST-Analyse

**Erstellt:** 2025-12-14 | **Quelle:** Gespraech mit Andreas

---

## Prozess-Uebersicht

```
ANFRAGE (Kunde meldet sich)
│
▼
1. ANGEBOTS-AUFMASS (kurz)
├─ Wer: Vater, Andreas, Enrico, manchmal Monteure
├─ Was: Grobe Masse, weniger Details
├─ Doku: Papier (produktspezifisch)
├─ Ablage: Scan → W4A
│
▼
ANGEBOT ERSTELLEN
│
▼
KUNDE ERTEILT AUFTRAG
│
▼
2. BESTELL-AUFMASS (detailliert)
├─ Wer: Vater, Andreas, ab und zu Monteure (einfache Produkte)
├─ Was: Finale Masse, alle Details
├─ Doku: Papier (produktspezifisch)
├─ Ablage: Scan → W4A
├─ PROBLEM: Aenderungen oft nicht nachgescannt!
│
▼
3. BESTELLUNG IM KONFIGURATOR
├─ Wer: Besteller (Roland, Jaroslaw, Andreas)
├─ Wie: Scan oeffnen, Masse MANUELL in WoT eintippen
├─ PROBLEM: Fehlerquelle beim Abtippen!
│
▼
BESTELLUNG → MONTAGE
```

---

## Details pro Schritt

### 1. Angebots-Aufmass

| Aspekt | IST-Zustand |
|--------|-------------|
| **Wer** | Vater, Andreas, Enrico, manchmal Monteure |
| **Wann** | Vor Angebotserstellung |
| **Detail-Level** | Kurz, weniger detailliert |
| **Grund** | Zu viel Aufwand wenn kein Auftrag entsteht |
| **Dokumentation** | Papier (produktspezifisch) |
| **Ablage** | Scan → W4A |

### 2. Bestell-Aufmass

| Aspekt | IST-Zustand |
|--------|-------------|
| **Wer** | Vater, Andreas, ab und zu Monteure |
| **Wann** | Nach Auftragserteilung, vor Bestellung |
| **Detail-Level** | Vollstaendig, alle Details |
| **Dokumentation** | Papier (produktspezifisch) |
| **Ablage** | Scan → W4A |

**Warum zweimal messen?**
- Angebotsaufmass: Grob fuer Preiskalkulation
- Bestellaufmass: Exakt fuer Produktion
- Baufortschritt kann sich aendern
- Kunde aendert manchmal Meinung

### 3. Aufmassblaetter (produktspezifisch)

| Produkt | Varianten | Inhalt |
|---------|-----------|--------|
| Fenster | 1 | Kundendaten, Masse, Produktdetails |
| Haustueren | 1 | Kundendaten, Masse, Produktdetails |
| Innentueren - Stahlzargen | 1 | Spezifisch fuer Stahlzargen |
| Innentueren - Glastueren | 1 | Spezifisch fuer Glastueren |
| Innentueren - Standard | 2 | Zwei Varianten |
| Garagentore | 1 | Spezifisch fuer Tore |
| **Gesamt** | **mind. 7** | |

**Notizbereich:** Vorhanden aber begrenzt, muss auch fuer Produktdetails reichen.

### 4. Foto-Dokumentation

| Aspekt | IST-Zustand |
|--------|-------------|
| **Wann** | Nur bei brisanten Details |
| **Geraet** | Smartphone |
| **Workflow** | Handy → E-Mail → PDF-Converter → ggf. verkleinern → W4A |
| **Problem** | Sehr umstaendlich, viele Schritte |

**Aktueller Foto-Workflow (6 Schritte!):**
1. Foto mit Smartphone machen
2. Per E-Mail an Arbeits-PC schicken
3. Am PC: Bilder mit PDF-Converter zusammenfuegen
4. Falls zu gross: Zurueck ans Smartphone, verkleinern
5. Erneut per E-Mail schicken
6. In W4A ablegen

### 5. Masse in Konfigurator uebertragen

| Aspekt | IST-Zustand |
|--------|-------------|
| **Wie** | Scan oeffnen, Masse manuell abtippen |
| **Wohin** | WoT (Weru), andere Konfiguratoren |
| **Problem** | Tippfehler, Zahlendreher, falsche Zeile |

---

## Erkannte Schmerzpunkte

| # | Schmerzpunkt | Auswirkung | Relevante Ideen |
|---|--------------|------------|-----------------|
| 1 | **Aenderungen nicht nachgescannt** | Veraltete Daten im System, falsche Masse bei Montage | #28 Digitales Aufmass |
| 2 | **Angebots- statt Bestellaufmass** | Unvollstaendige/falsche Masse, Reklamationen | #28, #39 Montage-Mappe |
| 3 | **Foto-Workflow umstaendlich** | 6 Schritte, Zeitverlust, wird oft weggelassen | #42 Foto-Zuordnung |
| 4 | **Wenig Platz fuer Notizen** | Besonderheiten gehen unter | #28 Digitales Aufmass |
| 5 | **7+ verschiedene Papierformate** | Unuebersichtlich, falsches Blatt moeglich | #28 Digitales Aufmass |
| 6 | **Masse manuell abtippen** | Tippfehler, doppelte Arbeit | #28 Digitales Aufmass |
| 7 | **Zweimal messen** | Doppelter Aufwand, Fahrten | Evtl. reduzierbar |

---

## Verbesserungspotential (Ideen-Verknuepfung)

| Phase | Tool-Idee | Verbesserung |
|-------|-----------|--------------|
| Aufmass | #28 Digitales Aufmass | Tablet/Handy statt Papier, Daten direkt digital |
| Fotos | #42 Foto-Zuordnung | Direkt vom Handy ins System, Auto-Zuordnung |
| Montage | #39 Montage-Mappe | Automatisch richtiges Aufmass (Bestellung, nicht Angebot) |

---

## Datenfluss: IST vs SOLL

### IST (aktuell)
```
Papier vor Ort
     ↓
Scan im Buero
     ↓
W4A ablegen
     ↓
Scan oeffnen, manuell abtippen → WoT
     ↓
Fehlerquelle!
```

### SOLL (mit #28)
```
Tablet/Handy vor Ort (digitales Formular)
     ↓
Automatisch in System (W4A oder direkt)
     ↓
Daten fliessen in Konfigurator
     ↓
Keine Tippfehler, kein Medienbruch
```

---

## Offene Fragen (fuer naechstes Brainstorming)

| # | Frage |
|---|-------|
| 1 | Koennte man Angebots- und Bestellaufmass zusammenlegen? (Einmal gruendlich statt zweimal) |
| 2 | Welche Daten sind bei Angebot vs. Bestellung unterschiedlich? |
| 3 | Gibt es Produkte wo einmal messen reicht? |
| 4 | Wuerden Monteure Tablet/Handy-Aufmass akzeptieren? |
| 5 | Kann WoT/Konfigurator Daten importieren? (API, CSV?) |

---

## Prozess-Uebergaenge

### Anfrageprozess → Aufmassprozess
- Trigger: Kunde will Angebot
- Termin vereinbaren fuer Aufmass

### Aufmassprozess → Bestellprozess
- Trigger: Auftrag erteilt, Bestellaufmass fertig
- Masse werden in Konfigurator uebertragen

### Aufmassprozess → Montageprozess
- Scan wird fuer Montage-Unterlagen verwendet
- PROBLEM: Oft falscher Scan (Angebot statt Bestellung)
