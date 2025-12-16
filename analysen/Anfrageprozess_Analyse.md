# Anfrageprozess - IST-Analyse

**Erstellt:** 2025-12-11 | **Quelle:** Gespraech mit Andreas

---

## Prozess-Uebersicht

```
EINGANG
│ Telefon ──────────┐
│ E-Mail ───────────┼──► Zettel ODER W4A-Aufgabe
│ Laufkundschaft ───┤
│ Website-Formular ─┘ (→ E-Mail)
│
▼
ERFASSUNG
├─ Kunde pruefen: vorhanden?
│   └─ Nein → Kunde anlegen
│
▼
INFOS KOMPLETT?
├─ JA → Angebot erstellen
├─ NEIN:
│   ├─ Laufkundschaft: In Ausstellung klaeren, sonst Aufmass
│   ├─ Telefon: Daten aufnehmen, wenn komplex → Aufmass
│   └─ E-Mail: Nachfragen (mehrere Mails), wenn komplex → Aufmass
├─ PRODUKT NICHT RECHENBAR:
│   └─ Preisanfrage an Lieferant (Projekt MUSS existieren!)
│
▼
AUFMASS (wenn noetig)
├─ Terminvereinbarung: Telefonat, Ausstellung, oder E-Mail
├─ Wartezeit: 2-3 Wochen
├─ Dauer vor Ort: 10 Min - 3 Stunden
│
▼
ANGEBOT
├─ Erstellung in W4A + Konfiguratoren
├─ Dauer: 10 Min - 4 Stunden
├─ Nachbereitung nach Aufmass: 10 Min - 2 Stunden
│
▼
NACHVERFOLGUNG
├─ Aktuell: Kaum bis gar nicht
│
▼
KUNDE SAGT ZU
├─ SOLL: Auftrag + Projekt erstellen
└─ IST: Manchmal nur Projekt, manchmal direkt Rechnung
```

---

## Details pro Schritt

### 1. Eingangskanaele

| Kanal | Erfassung | Anteil |
|-------|-----------|--------|
| Laufkundschaft (Ausstellung) | Zettel oder W4A-Aufgabe | 40% |
| E-Mail | Bleibt E-Mail oder W4A-Aufgabe | 35% |
| Telefon | Zettel oder W4A-Aufgabe | 20% |
| Website (js-fenster.de/kontakt) | Kommt als E-Mail | 5% |

**W4A-Aufgabe:** Wird von der Person erstellt, die ans Telefon geht.

**E-Mail-Verteilung (IST):**
| Schritt | Wer | Was |
|---------|-----|-----|
| 1 | Susann | Sortiert E-Mails in Outlook-Ordner (Lieferanten, Kunden, etc.) |
| 2 | Susann | Weist zu ODER Mitarbeiter picken sich selbst E-Mails |
| 3 | - | Ordnerstruktur: z.B. "Lieferanten", "Rechnungen", "Kunden-Anfragen" |

**Problem:** Manuelle Sortierung, kein Tracking wer was bearbeitet.

**Website-Formular (js-fenster.de/kontakt):**
- Anrede (Pflicht)
- Adresse = Bauvorhaben? (Ja/Nein)
- Projekttyp: Neubau / Renovierung / Reparatur
- Produktinteresse: Fenster, Insektenschutz, Innentueren, Terrassenueberdachung, Haustueren, Sonnenschutz, Sonstiges
- Zeitplanung: Wann geplant?
- Datenschutz-Checkbox (Pflicht)

### 2. Erfassung

- **Kunde pruefen:** Existiert bereits in W4A?
- **Neu anlegen:** Falls nicht vorhanden
- **Schmerzpunkt:** Zettelwirtschaft - Infos auf Papier, nicht digital

### 3. Preisanfrage (Sonderfall)

Wenn Produkt nicht rechenbar (kein Standardpreis):
- Preisanfrage an Lieferant erstellen
- **WICHTIG:** Projekt MUSS vorher angelegt werden!
- Grund: W4A "3 Reiter" - ohne Projekt keine Zuordnung zum Kunden
- Sonst: "Sucht man sich einen Wolf"
- E-Mail-Korrespondenz mit Lieferant gehoert auch ins Projekt

### 4. Aufmass

| Aspekt | IST-Zustand |
|--------|-------------|
| **Wer faehrt raus** | Enrico, Jaroslaw, Andreas |
| **Dauer vor Ort** | 10 Min - 3 Stunden (je nach Umfang) |
| **Wartezeit** | 2-3 Wochen |
| **Kapazitaetsengpass** | Ja - zu viele Auftraege, grosse Auftraege, viele Anfragen, viel Verwaltung |

### 5. Angebotserstellung

| Aspekt | IST-Zustand |
|--------|-------------|
| **Tool** | Nur W4A |
| **Dauer** | 10 Min - 4 Stunden |
| **Nachbereitung nach Aufmass** | 10 Min - 2 Stunden |
| **Wissen** | Tiefes Fachwissen noetig fuer korrekte Angebote |

**Wer erstellt Angebote:**
| Person | Geschwindigkeit | Qualitaet |
|--------|-----------------|-----------|
| Roland | Schnell (hauptsaechlich) | Gut |
| Jaroslaw | Laenger | Sehr gut, wenig Korrekturen |
| Enrico | Lange | Unstrukturiert |
| Andreas | Kaum | Sehr gut |

**Konfiguratoren (extern):**
| Konfigurator | Schnittstelle |
|--------------|---------------|
| WoT (Weru Fenster) | XML Drag&Drop ✓ |
| my.warema | Text per Strg+C |
| Kadeco | Text per Strg+C |
| Komposoft | Text per Strg+C |
| Trendtueren | Text per Strg+C |
| Roka | Text per Strg+C |
| Weru Haustueren | Text per Strg+C |
| Sunparadise | Text per Strg+C |

### 6. Nachverfolgung

- **IST:** Sehr wenig bis kaum
- **Wenn:** Nur "Ist das Angebot noch aktuell?"
- **Kein systematisches Follow-up** (2/7/14 Tage Regel fehlt)

### 7. Nach Zusage

| SOLL | IST |
|------|-----|
| Auftrag erstellen | Manchmal nur Projekt |
| Projekt erstellen | Manchmal Angebot → unterschrieben → direkt Rechnung |
| | Auftrag fehlt → Soll-Ist-Vergleich falsch! |

**Anmerkung:** "Arbeiten dran, uns zu verbessern"

---

## Erfassungs-Checkliste Tel. Kundenanfragen (aus Vorlagen-Ordner)

> **Quelle:** `Z:\Vorlagen\Arbeitsabläufe\Checkliste telefonische Kundenanfragen.odt`
> **Status:** Eher Vorlage, nicht konsequent genutzt

### Checkliste Inhalt

| Schritt | Abfrage | Status |
|---------|---------|--------|
| **1. Kunde pruefen** | Bestandskunde? → Begruessung | Vorlage |
| | Neukunde? → "Wie auf uns aufmerksam?" | ❌ Nicht erfasst (waere gut!) |
| **2. Projekttyp** | Neubau / Sanierung / Reparatur | ✅ Wird abgefragt |
| | Projektbeginn? | ✅ Wird abgefragt |
| **3. Produkte** | Checkboxen mit Mindestpreisen | ✅ Produkte aktuell |
| | (Ueberdachung evtl. entfaellt) | ⚠️ Preise pruefen! |
| **4. Budget** | Budget-Abfrage | Gelegentlich |
| **5. Fremdangebot** | Vorhanden? → Vorab schicken lassen | Gelegentlich |
| **6. Verantwortlicher** | Entscheider identifizieren | ✅ Wichtig! |
| **7. Kontaktdaten** | Name, Vorname, Firma | ✅ Pflicht |
| | Strasse, Ort | ✅ Pflicht |
| | Tel. ODER E-Mail | ✅ Mindestens eins |
| **8. Bauvorhaben** | "BV:" wenn Auftraggeber ≠ RE | ✅ Bei Bedarf |
| **9. Terminvereinbarung** | Fremdangebot → Ausstellung | War angedacht |
| | Kein Fremdangebot → Vor-Ort | Nicht mehr aktiv |

### Mindestpreise (Stand: Vorlage - PRUEFEN!)

| Produkt | Mindestpreis |
|---------|--------------|
| Fenster | - |
| Insektenschutz | ab 100,- EUR |
| Haustueren | ab 2.500,- EUR |
| Hebeschiebetüren | ab 3.500,- EUR |
| Innentueren | ab 300,- EUR |
| Nebeneingangstuer | ab 1.000,- EUR |
| Wohnungseingangstuer | ab 800,- EUR |
| Vorbaurollo | ab 200,- EUR |
| Markise | ab 1.500,- EUR |
| Terrassenueberdachungen | ab 7.500,- EUR (evtl. entfaellt) |

### Priorisierung (war angedacht, nicht mehr aktiv)

| Prio | Kriterium |
|------|-----------|
| 1 | Bestandskunden (Umsatz ab 1.000 EUR) |
| 2 | Neukunden mit Komplettprojekten |
| 3 | Gewerbliche Kunden |
| 4 | Alle anderen |

### Erkenntnisse fuer Digitalisierung

| Aspekt | Erkenntnis |
|--------|------------|
| **Gut** | Strukturierte Vorlage vorhanden |
| **Gut** | Mindestpreise fuer Qualifizierung |
| **Gut** | Entscheider-Identifikation wichtig |
| **Luecke** | Vorlage wird nicht konsequent genutzt |
| **Luecke** | "Wie gefunden" nicht erfasst |
| **Luecke** | Prio-Regeln nicht mehr aktiv |
| **Potenzial** | Digitale Erfassung wuerde Nutzung erzwingen |

→ **Siehe #24 (Ticket-System)** fuer digitale Umsetzung

---

## Erkannte Schmerzpunkte

| # | Schmerzpunkt | Auswirkung | Relevante Ideen |
|---|--------------|------------|-----------------|
| 1 | **Zettelwirtschaft** | Infos gehen verloren, doppelte Erfassung | #24, #46→#24 |
| 2 | **2-3 Wochen Wartezeit Aufmass** | Kunden springen ab, Unzufriedenheit | #11, #44 |
| 3 | **Tiefes Wissen fuer Angebote** | Nur wenige koennen Angebote erstellen | #6 |
| 4 | **10min-4h Angebotsdauer** | Hoher Zeitaufwand, Kapazitaetsengpass | #6, #1 |
| 5 | **Kaum Nachverfolgung** | Verlorene Auftraege | #23 (inkl. #45) |
| 6 | **Projekt fuer Preisanfrage noetig** | Zusatzaufwand, Fehlerquelle | #32 |
| 7 | **Auftrag fehlt → Soll-Ist falsch** | Falsche Kennzahlen | #17, #32 |
| 8 | **Konfiguratoren nur Copy&Paste** | Fehleranfaellig, Zeitaufwand | #37 |
| 9 | **Kapazitaetsengpass Aufmass** | Lange Wartezeiten | #11, #44 |

---

## Verbesserungspotential (Ideen-Verknuepfung)

| Phase | Tool-Idee | Verbesserung |
|-------|-----------|--------------|
| Eingang | #24 Ticket + Schnell-Erfassung | Digitale Erfassung statt Zettel |
| Eingang | #47 Kunden-Historie | Bestandskunde sofort erkennen |
| Aufmass | #28 Digitales Aufmass + Mobil | Fotos + Masse digital, kein Zettel |
| Aufmass | #11 Terminfindung | Optimierte Terminplanung |
| Angebot | #6 Budget-Angebots-Generator | Schnellere Angebote |
| Angebot | #37 WoT-XML Transformer | Bessere Konfigurator-Integration |
| Nachverfolgung | #23 Verkaufschancen + Reminder | Systematisches Follow-up |
| Nach Zusage | #32 Projektverwaltung | Saubere Auftrag/Projekt-Erstellung |

---

## Naechster Prozess

→ **Bestellprozess** (wenn Kunde zusagt)
