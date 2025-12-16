# Rechnungsprozess - IST-Analyse

**Erstellt:** 2025-12-12 | **Quelle:** Gespraech mit Andreas

---

## Prozess-Uebersicht

```
MONTAGE FERTIG (aus Montageprozess)
│
▼
1. MONTAGESCHEIN ZURUECK
├─ Wer: Monteur bringt Zettel
├─ Analyse: Susann prueft + scannt ein
│
▼
2. HAENGEAKT → ROLAND
├─ Bei fertigen Baustellen
├─ Inhalt: Alle Dokumente (Auftrag, Bestellung, Aufmass, E-Mails ausgedruckt!)
│
▼
3. RECHNUNG ERSTELLEN
├─ Wer: Roland (hauptsaechlich), Andreas (selten)
├─ Tool: W4A (schnell, da Auftrag schon vorhanden)
├─ Arbeitszeit: Vom Zettel ausrechnen
├─ Anpassungen: Positionen ergaenzen/entfernen, Text anpassen
│
▼
4. RUECKFRAGEN?
├─ JA → Roland fragt Projektleiter (Andreas/Jaroslaw)
├─ Problem: Manche Infos fehlen → vergessene Positionen
│
▼
5. RECHNUNG VERSENDEN
├─ Standard: Per E-Mail oder Post
│
▼
6. ZAHLUNGSEINGANG
├─ Wer prueft: Sandra
├─ Wie: W4A Kontoauszugsabruf + automatische Zuordnung
├─ Zahlungsziel: 14 Tage netto
├─ Skonto/Rabatte: Bei groesseren Auftraegen, Stammkunden
│
▼
7. MAHNUNG (bei Nichtzahlung)
├─ Zahlungserinnerung: Nach Frist + 7 Tage Puffer
├─ Mahnung 1: 7 Tage
├─ Mahnung 2: 7 Tage
└─ Wer: Sandra
```

---

## Details pro Schritt

### 1. Beteiligte

| Person | Rolle |
|--------|-------|
| **Susann** | Montageschein analysieren + scannen |
| **Roland** | Rechnung erstellen (hauptsaechlich) |
| **Sandra** | Rechnungskorrekturen, Zahlungspruefung, Mahnungen |
| **Andreas** | Rechnung (selten), Rueckfragen beantworten |
| **Jaroslaw** | Rueckfragen beantworten |

### 2. Haengeakt

| Inhalt | Bemerkung |
|--------|-----------|
| Auftragsdokumente | Auftrag, Bestellung, etc. |
| Aufmassblaetter | Problem: Nicht immer aktuellste Version |
| Fotos | Meist am PC, AUCH ausgedruckt |
| E-Mails | Werden ausgedruckt (!?!) |
| Handschriftliche Notizen | Alle Zettel |

**Problem:** Akt wandert oft zwischen Abteilungen, bleibt lange liegen.

### 3. Arbeitszeit-Berechnung

| Aspekt | IST-Zustand |
|--------|-------------|
| **Quelle** | Handschriftlicher Zettel vom Monteur |
| **Berechnung** | Roland oder Andreas rechnet aus |
| **Darstellung** | Pro Tag (z.B. "2x Facharbeiter a 7,25 Std.") |
| **Zeiterfassung** | Wird NICHT gepflegt, nur fuer Rechnung |

### 4. Rechnungskorrektur

| Kennzahl | Wert |
|----------|------|
| **Korrekturrate** | ~4,4% (34 von 777 Dokumenten) |
| **Hauptgrund** | Zeiten (Kunde will nicht zahlen) |
| **Nebengrund** | Preise (Aenderungen nach Bestellung nicht kommuniziert) |
| **Wer bemerkt** | Meist der Kunde |
| **Wer korrigiert** | Roland, Sandra |

### 5. Teilrechnungen

| Situation | Ablauf |
|-----------|--------|
| Teilmontage abgeschlossen | Teilrechnung moeglich |
| Noch offene Bestellungen | Haengeakt zurueck zu Bestellung, KEINE Teilrechnung |
| Mehrere Auftraege gleichzeitig | Komplex - schwer nachzuvollziehen was abrechenbar |

**Problem:** Firma geht oft in Vorleistung weil Rechnung wartet.

### 6. Anzahlung

| Problem | Auswirkung |
|---------|------------|
| Wird oft vergessen | Bei Angebot/Auftrag nicht daran gedacht |
| Spaeter nicht durchsetzbar | Cashflow-Problem |

**Anzahlungs-Workflow (Detail):**

| Schritt | Wer | Was |
|---------|-----|-----|
| 1 | Sandra | Holt Kontoauszuege per HBCI in W4A ab |
| 2 | W4A | Verknuepft erkannte Zahlungen automatisch |
| 3 | Sandra | Ordnet manche haendisch zu (falsch erkannt) |
| 4 | Sandra | Korrigiert Kunde wenn falsch erkannt |
| 5 | Sandra | Korrigiert Skonto wenn noetig |
| 6 | **SOLL** | Info an Projektleiter → Bestellprozess einleiten |

**Aktueller Ablauf:**
- Bestellung nach unterschriebenem Angebot (besser: Auftragsbestaetigung)
- Trend: Wird mehr so umgesetzt
- Ausloesung Bestellungen: 1-4 Wochen Verzoegerung

**SOLL-Ablauf:**
- Anzahlung eingegangen → automatisch Info an Projektleiter
- Projektleiter leitet Bestellprozess ein

---

## Zahlungseingang (funktioniert GUT!)

| Aspekt | Details |
|--------|---------|
| **Wer** | Sandra |
| **Tool** | W4A Kontoauszugsabruf |
| **Automatisch** | Zuordnung bei Uebereinstimmung (Kundendaten + Rechnungsnummer) |
| **Zahlungsziel** | 14 Tage netto (Standard) |
| **Skonto/Rabatte** | Bei groesseren Auftraegen, Stammkunden |

---

## Mahnwesen

| Phase | Frist | Puffer |
|-------|-------|--------|
| Rechnung | 14 Tage Zahlungsziel | - |
| Zahlungserinnerung | Nach Frist | 7 Tage |
| Mahnung 1 | 7 Tage | 7 Tage |
| Mahnung 2 | 7 Tage | - |

**Wer:** Sandra

---

## Erkannte Schmerzpunkte

| # | Schmerzpunkt | Auswirkung | Relevante Ideen |
|---|--------------|------------|-----------------|
| 1 | **Roland fehlen Infos** | Vergessene Positionen (nicht verrechnet ODER faelschlich drauf) | #39 Montage-Rueckmeldung |
| 2 | **Haengeakt wandert zurueck** | Bei offenen Bestellungen keine Teilrechnung moeglich | #36 Beschaffungs-Dashboard |
| 3 | **Mehrere Auftraege komplex** | Schwer nachzuvollziehen was abrechenbar | Dashboard: Was ist montiert + nicht abgerechnet |
| 4 | **Anzahlung vergessen** | Spaeter nicht durchsetzbar, Cashflow | #65 Anzahlungsrechnung-Auto |
| 5 | **Firma in Vorleistung** | Rechnung wartet auf Rest | Teilrechnungs-Logik |
| 6 | **E-Mails ausgedruckt** | Unnoetige Papierflut | Digitaler Workflow |
| 7 | **Aufmass-Versionierung** | Aenderungen am Zettel nicht nachgescannt | Immer neu scannen ODER digital erfassen |
| 8 | **~4,4% Korrekturen** | Zeitaufwand, Kundenunzufriedenheit | Bessere Infos vorab |
| 9 | **Preisaenderungen nicht kommuniziert** | Korrektur noetig | Auto-Info bei AB-Abweichung |

---

## Was laeuft GUT

| Aspekt | Details |
|--------|---------|
| Rechnungsstellung schnell | Auftrag bereits in W4A vorhanden |
| Zahlungspruefung automatisch | W4A Kontoauszugsabruf |
| Sandra als zentrale Stelle | Mahnungen, Korrekturen |
| Struktur klar | Positionen, Arbeitszeit, Text |

---

## Verbesserungspotential (Ideen-Verknuepfung)

| Phase | Tool-Idee | Verbesserung |
|-------|-----------|--------------|
| Vor Rechnung | #39 Montage-Rueckmeldung | Vollstaendige Infos fuer Roland |
| Vor Rechnung | #36 Beschaffungs-Dashboard | Ueberblick was noch offen |
| Anzahlung | #65 Anzahlungsrechnung-Auto | Erinnerung bei Auftragsphase |
| Kommunikation | E-Mail direkt in W4A verlinken | Kein Ausdrucken mehr |
| Aufmass | Digital erfassen | Keine Versionsprobleme |

---

## Naechster Prozess

→ **Mahnwesen** (bereits hier dokumentiert)
→ **Steuerberater** (Rechnungsdokumente bereitstellen)
