# Ideen für KI-Automatisierungen - Technische Details

**Erstellt:** 2025-12-09 | **Aktualisiert:** 2025-12-21 | **Status:** Brainstorming-Phase | **Anzahl:** 82 Ideen (4 merged)

---

## Dokumentstruktur

| Datei | Inhalt | Verwendung |
|-------|--------|------------|
| **[IDEEN.md](IDEEN.md)** | Verdichtete Uebersicht | Schneller Ueberblick, neue Ideen eintragen |
| **IDEEN_DETAILS.md** (diese Datei) | Technische Details + W4A-Status | SQL, Logik, Abhaengigkeiten, Eigenbau-Empfehlung |
| **[IDEEN_UEBERSICHT.html](IDEEN_UEBERSICHT.html)** | Interaktive Ansicht + **Architektur** | Filtern nach Phase, Phasen-Diagramm |

> **Wichtig:** Bei Phasen-Aenderungen oder strukturellen Ideen (#58-60, #14) auch die **Architektur-Seite** in der HTML pruefen!

---

## Quick-Reference: W4A-Status

| # | Prozess | W4A-Status | Empfehlung |
|---|---------|------------|------------|
| 1 | Preislisten-Tool | Nicht vorhanden | Eigenbau |
| 2 | Bilanz/GuV | Nicht vorhanden | DATEV nutzen |
| 3 | Weru Foerderantraege | Nicht vorhanden | Eigenbau |
| 4 | KI-Wissensdatenbank | Nicht relevant | ✅ Fertig |
| 5 | Bauplan-Analyse | Nicht vorhanden | Eigenbau |
| 6 | Budget-Angebot | Teilweise | Pruefen |
| 7 | Spracherkennung | Nicht vorhanden | Eigenbau |
| 8 | Universal-Hub | Nicht vorhanden | Eigenbau |
| 9 | Reparatur-Verwaltung | ? | Pruefen |
| 10 | Auftraege/Lieferungen | Vorhanden | Pruefen |
| 11 | Terminfindung | Teilweise | Erweitern |
| 12 | E-Mail-Verarbeitung | Nicht vorhanden | Eigenbau |
| 13 | Inventar-Verwaltung | Vorhanden | Erweitern |
| 14 | Command Center ⭐ | Nicht vorhanden | Eigenbau (Phase 4) |
| 15 | Zeiterfassung | Vorhanden | Pruefen |
| 16 | Urlaubsverwaltung | Vorhanden (Schmerzpunkte!) | → #78, #79, #80 |
| 17 | Projekt-Deckungsbeitrag | Vorhanden | Pruefen |
| 18 | Kundenportal | Nicht vorhanden | Eigenbau |
| 19 | Lieferanten-Bewertung | Nicht vorhanden | Eigenbau |
| 20 | Qualitaetsmanagement | Nicht vorhanden | Eigenbau |
| 21 | Mobile Monteur-App | Nicht vorhanden | Eigenbau |
| 22 | Routenplanung | Nicht vorhanden | Eigenbau |
| 23 | Verkaufschancen | Vorhanden? | Pruefen |
| 24 | Ticket-System | Nicht vorhanden | Eigenbau |
| 25 | Telefon-CRM | Nicht vorhanden | Eigenbau |
| 26 | Projekt-Aktivitaeten | Teilweise | Erweitern |
| 27 | Dokument-Intelligenz | Nicht vorhanden | Eigenbau |
| 28 | Digitales Aufmass | Nicht vorhanden | Eigenbau |
| 29 | Montage-Checklisten | Nicht vorhanden | Eigenbau |
| 30 | After Sales | Nicht vorhanden | Eigenbau |
| 31 | Rechnungsbuch | Vorhanden | Pruefen |
| 32 | Projektverwaltung | Vorhanden | Pruefen |
| 33 | Bestellwesen | Vorhanden | Erweitern |
| 34 | Zeiterfassung GPS | Nicht vorhanden | Eigenbau |
| 35 | Urlaubsplaner erw. | Teilweise | Erweitern |
| 36 | Beschaffungs-Dashboard | Nicht vorhanden | Eigenbau ⭐ |
| 37 | WoT-XML Transformer | Nicht vorhanden | Eigenbau |
| 38 | Lagerverwaltung | Vorhanden, ungenutzt | W4A testen |
| 39 | Tages-Briefing Monteur | Nicht vorhanden | Eigenbau |
| 40 | Material-Kommissionierliste | Nicht vorhanden | Eigenbau |
| 41 | Montage-Status Live | Nicht vorhanden | Eigenbau |
| 42 | Foto-Zuordnung | Nicht vorhanden | Eigenbau |
| 43 | Nacharbeit-Tracker | Nicht vorhanden | Eigenbau |
| 44 | Kapazitaets-Cockpit | Teilweise | Erweitern |
| 45 | ~~Angebots-Reminder~~ | → merged in #23 | - |
| 46 | ~~Schnell-Erfassung Anfrage~~ | → merged in #24 | - |
| 47 | Kunden-Historie Dashboard | Teilweise | Erweitern |
| 48 | ~~Wiederkauf-Erkennung~~ | → merged in #47 | - |
| 49 | Google-Reviews Alerts | Nicht vorhanden | Eigenbau |
| 50 | Sanfte Zahlungserinnerung | Nicht vorhanden | Eigenbau |
| 51 | Cashflow-Prognose | Nicht vorhanden | Eigenbau |
| 52 | Conversion-Tracker | Nicht vorhanden | Eigenbau |
| 53 | Mindestbestand-Alert | Nicht vorhanden | Eigenbau |
| 54 | Preis-Vergleich Lieferanten | Nicht vorhanden | Eigenbau |
| 55 | Bestellvorlage Pflichtfelder | Nicht vorhanden | Eigenbau ⭐ |
| 56 | AB-Abgleich automatisch | Nicht vorhanden | Eigenbau ⭐ |
| 57 | Lieferadressen-Logik | Nicht vorhanden | Eigenbau ⭐ |
| 58 | Web-Plattform Grundgeruest | Nicht vorhanden | Eigenbau ⭐⭐ (Phase 0) |
| 59 | Datenbank-Connector | Nicht vorhanden | Eigenbau ⭐⭐ (Phase 0) |
| 60 | Auth & Berechtigungen | Nicht vorhanden | Eigenbau ⭐⭐ (Phase 0) |
| 61 | ~~Mobiles Aufmass-Formular~~ | → merged in #28 | - |
| 62 | Ersatzteil-Erkennung | Nicht vorhanden | Eigenbau 🔴 (Phase 5, KI-Vision) |
| 63 | Fassaden-Budget | Nicht vorhanden | Eigenbau 🔴 (Phase 5, KI-Vision) |
| 64 | Data Service Layer | Nicht vorhanden | Eigenbau ⭐⭐ (Phase 0) |
| 65 | Anzahlungsrechnung-Auto | Nicht vorhanden | Eigenbau ⭐ |
| 66 | Montageplanung + Wetter | Nicht vorhanden | Eigenbau ⭐ |
| 67 | XML-Konverter (Universal → W4A) | Nicht vorhanden | Eigenbau |
| 68 | Zentrales Planungs-Dashboard | Nicht vorhanden | Eigenbau ⭐⭐ (Phase 0) |
| 69 | UTA-Tankrechnungen PDF-Tool | Nicht relevant | Eigenbau (Standalone) |
| 70 | Montagematerial-Pauschalen | Nicht vorhanden | Eigenbau ⭐ (Umsatzverlust!) |
| 71 | Einkaufs-Workflow/Preismanagement | Nicht vorhanden | Eigenbau ⭐ |
| 72 | Referenz-Automatik | Nicht vorhanden | Eigenbau |
| 73 | Google-Bewertung Vorschlag | Nicht vorhanden | Eigenbau |
| 74 | Prueffristen-Automatik | Nicht vorhanden | Eigenbau ⭐ |
| 75 | Fuehrerschein-Kontrolle | Nicht vorhanden | Eigenbau ⭐ (Rechtspflicht!) |
| 76 | Inventar-Checkout Bilderkennung | Nicht vorhanden | Eigenbau (KI-Vision) |
| 77 | Schadens-ChatBot | Nicht vorhanden | Eigenbau ⭐ (Autonom) |
| 78 | Jahresuebertrag-Automatik | W4A: Manuell | Eigenbau/Script |
| 79 | Zeitnachweis-Generator | W4A: Export umstaendlich | Eigenbau |
| 80 | Eigene Zeiterfassung | W4A: Probleme | Eigenbau ⭐⭐ |
| 81 | PDF-Merger fuer DATEV | W4A: Limitiert (1 Datei) | Eigenbau |
| 82 | Buchungskonto-Assistent | W4A: Manuell | Eigenbau |
| 83 | Wartungsvertrags-Modul | Nicht vorhanden | Eigenbau ⭐⭐ |
| 84 | Kunden-Reaktivierung | Nicht vorhanden | Eigenbau ⭐ |
| 85 | Garantie-Tracker | Nicht vorhanden | Eigenbau |
| 86 | Projekt-Controlling Alerts | W4A: Manuell | Eigenbau |
| 87 | Vertrags-Dashboard | Nicht vorhanden | Eigenbau |
| 88 | Dokumenten-Volltextsuche | W4A: Limitiert | Eigenbau |
| 89 | Schulungs-Planer | Nicht vorhanden | Eigenbau |
| 90 | Werkstatt-Auftragsplanung | Nicht vorhanden | Eigenbau ⭐⭐ |

**Legende:** Eigenbau = Selbst entwickeln | Erweitern = W4A-Funktion ausbauen | Pruefen = W4A-Status klaeren | ⭐ = Prioritaet | ⭐⭐ = Infrastruktur (ZUERST) | 🔴 = KI-Komplex

---

## Automatisierungs-Stufen Uebersicht

> **Philosophie:** Autonom > Automatisch > Halbautomatisch > Manuell (nur Notfall)

| Stufe | Definition | Beispiel |
|-------|------------|----------|
| **Autonom** | System handelt komplett selbststaendig, kein Trigger noetig | Taeglicher Report um 08:00 |
| **Automatisch** | System reagiert auf Trigger/Event, fuehrt dann selbst aus | Zahlung erkannt → Auto-E-Mail |
| **Halbautomatisch** | User startet, System fuehrt aus | Button "Angebot erstellen" → fertig |
| **Manuell** | Nur Notfall-Fallback | Excel-Export zum Selbermachen |

### Ideen nach Automatisierungs-Stufe

| # | Idee | Empfohlen | Begruendung |
|---|------|-----------|-------------|
| **Phase 0: Infrastruktur** ||||
| 58 | Web-Plattform | - | Basis-Infrastruktur |
| 59 | Datenbank-Connector | - | Basis-Infrastruktur |
| 60 | Auth & Berechtigungen | - | Basis-Infrastruktur |
| 64 | Data Service Layer | - | Basis-Infrastruktur |
| 68 | Planungs-Dashboard | Halbautomatisch | User interagiert mit Dashboard |
| **Phase 1: Basis-Module** ||||
| 1 | Preislisten-Tool | Automatisch | PDF hochladen → Auto-Konvertierung |
| 4 | KI-Wissensdatenbank ✅ | **Autonom** | Wöchentliche Updates ohne Trigger |
| 13 | Inventar-Verwaltung | Halbautomatisch | CRUD-Operationen durch User |
| 36 | Beschaffungs-Dashboard | **Autonom** | Echtzeit-Ampel ohne User-Aktion |
| 39 | Tages-Briefing Monteur | **Autonom** | Taeglich 06:00 Auto-Generierung |
| 40 | Material-Kommissionierliste | Automatisch | Bei Montage-Termin Auto-Generierung |
| 41 | Montage-Status Live | Automatisch | Status-Aenderung → Auto-SMS |
| **Phase 2: Kernprozesse** ||||
| 9 | Reparatur-Verwaltung | Halbautomatisch | Kanban-Board, User-Interaktion |
| 10 | Auftraege & Lieferungen | Halbautomatisch | User verwaltet Auftraege |
| 11 | Terminfindung | Automatisch | Verfuegbarkeit auto-pruefen |
| 22 | Routenplanung | Automatisch | Tagesplan → Auto-Optimierung |
| 24 | Ticket-System | Automatisch | E-Mail → Auto-Ticket |
| 28 | Digitales Aufmass | Halbautomatisch | Erfassung durch User |
| 32 | Projektverwaltung | Halbautomatisch | User verwaltet Projekte |
| 33 | Bestellwesen | Halbautomatisch | User loest Bestellung aus |
| 37 | WoT-XML Transformer | Automatisch | XML hochladen → Auto-Konvertierung |
| 38 | Lagerverwaltung | Halbautomatisch | User bucht Ein/Aus |
| 53 | Mindestbestand-Alert | **Autonom** | Staendige Pruefung, Auto-Warnung |
| 55 | Bestellvorlage Pflichtfelder | Automatisch | Auto-Validierung bei Eingabe |
| 56 | AB-Abgleich | Automatisch | AB-Upload → Auto-Vergleich |
| 57 | Lieferadressen-Logik | Automatisch | Artikeltyp → Auto-Adresse |
| 65 | Anzahlungsrechnung-Auto | Automatisch | Auftrag → Auto-Erinnerung |
| 66 | Montageplanung + Wetter | **Autonom** | Taegliche Auto-Pruefung |
| 67 | XML-Konverter Universal | Automatisch | Upload → Auto-Konvertierung |
| 74 | Prueffristen-Automatik | **Autonom** | Taegliche Frist-Pruefung |
| 75 | Fuehrerschein-Kontrolle | Automatisch | Halbjahres-Erinnerung |
| **Phase 3: Kommunikation** ||||
| 3 | Weru Foerderantraege | Automatisch | Zahlung erkannt → Auto-Erinnerung |
| 6 | Budget-Angebots-Generator | Halbautomatisch | User gibt Daten ein |
| 12 | E-Mail-Verarbeitung | **Autonom** | Eingehende E-Mails auto-klassifizieren |
| 23 | Verkaufschancen-Pipeline | Automatisch | Auto-Reminder nach X Tagen |
| 25 | Telefon-CRM Integration | Automatisch | Anruf → Auto-Popup |
| 27 | Dokument-Intelligenz | Automatisch | Upload → Auto-Klassifizierung |
| 30 | After Sales Service | **Autonom** | Auto-Reminder fuer Wartung |
| 47 | Kunden-Historie | Halbautomatisch | User sieht Timeline |
| 49 | Google-Reviews Alerts | **Autonom** | Neue Bewertung → Auto-Alert |
| 50 | Sanfte Zahlungserinnerung | **Autonom** | Faelligkeit → Auto-E-Mail |
| 72 | Referenz-Automatik | Automatisch | Montage fertig → Auto-Erinnerung |
| 73 | Google-Bewertung Vorschlag | Automatisch | Positive Mail → Auto-Vorschlag |
| **Phase 4: Command Center** ||||
| 2 | Bilanz & GuV | **Autonom** | Taegliche Auto-Berechnung |
| 14 | Zentrales Dashboard | Halbautomatisch | User sieht/interagiert |
| 15 | Zeiterfassung | Halbautomatisch | User erfasst Zeit |
| 16 | Urlaubsverwaltung | Halbautomatisch | User beantragt |
| 17 | Projekt-Deckungsbeitrag | **Autonom** | Auto-Berechnung bei Aenderung |
| 19 | Lieferanten-Bewertung | **Autonom** | Auto-Scoring aus Lieferdaten |
| 26 | Projekt-Aktivitaeten | **Autonom** | Auto-Protokoll aller Aktionen |
| 31 | Rechnungsbuch | Halbautomatisch | User verwaltet |
| 34 | Zeiterfassung GPS | Halbautomatisch | User erfasst, GPS auto |
| 35 | Urlaubsplaner erweitert | Automatisch | Auto-Kapazitaetspruefung |
| 42 | Foto-Zuordnung | Automatisch | Foto → Auto-Erkennung Projekt |
| 44 | Kapazitaets-Cockpit | **Autonom** | Echtzeit-Auslastung |
| 51 | Cashflow-Prognose | **Autonom** | Auto-Berechnung |
| 52 | Conversion-Tracker | **Autonom** | Auto-Statistik |
| 54 | Preis-Vergleich Lieferanten | Halbautomatisch | User startet Vergleich |
| **Phase 5: KI-Features** ||||
| 5 | Bauplan-Analyse | Automatisch | Upload → KI-Analyse |
| 7 | Spracherkennung | Automatisch | Sprache → Text/Aktion |
| 8 | Universal-Eingabe-Hub | Automatisch | Multi-Input → Auto-Dispatch |
| 18 | Kundenportal | Halbautomatisch | Kunde interagiert |
| 20 | Qualitaetsmanagement | Halbautomatisch | User dokumentiert |
| 21 | Mobile Monteur-App | Halbautomatisch | Monteur nutzt App |
| 29 | Montage-Checklisten | Automatisch | Aufmass → Auto-Checkliste |
| 62 | Ersatzteil-Erkennung | Automatisch | Foto → KI-Vorschlag |
| 63 | Fassaden-Budget | Automatisch | Foto → KI-Schaetzung |
| **Standalone** ||||
| 69 | UTA-Tankrechnungen | Automatisch | PDF → Auto-Splitting |
| 70 | Montagematerial-Pauschalen | Automatisch | Artikeltyp → Auto-Pauschale |
| 71 | Einkaufs-Workflow | Halbautomatisch | User verwaltet Preise |

### Zusammenfassung

| Stufe | Anzahl | Beispiele |
|-------|--------|-----------|
| **Autonom** | ~18 | #4, #12, #36, #39, #49, #50, #53, #66, #74 |
| **Automatisch** | ~28 | #1, #3, #11, #24, #41, #56, #57, #72 |
| **Halbautomatisch** | ~20 | #6, #9, #13, #14, #15, #18, #21, #47 |
| **Infrastruktur** | ~5 | #58, #59, #60, #64 |

---

## Anleitung fuer neue Ideen (Claude)

Diese Datei ist **primär für Claude** als Kontext-Quelle gedacht, nicht für den User.

### Was hier rein gehört:
- **SQL-Kontext:** Relevante Tabellen, Felder, Beispiel-Queries
- **Logik/Regeln:** Schwellenwerte, Berechnungen
- **Abhängigkeiten:** Welche anderen Tools werden benötigt/genutzt
- **Offene Fragen:** Was muss noch geklärt werden

### Was hier NICHT rein gehört:
- ASCII-Visualisierungen/Diagramme (bei Bedarf für User generieren)
- Ausführliche Prosa-Beschreibungen
- Screenshots/Mockups

---

## 1. Preislisten-Tool (PDF → Excel)

### Kurzbeschreibung
PDF-Preislisten von Herstellern automatisch in Excel-Artikelstamm importieren.

### Dateipfade
- **Input:** `Z:\Lieferanten\[Hersteller]\Preisliste\*.pdf`
- **Output:** `Z:\Intern\Firmensoftware\Bauelemente - Haustüren - neu.xlsx`

### Logik
- PDF-Parsing (pdfplumber)
- Artikel-Matching: PDF-Artikel ↔ Excel-ArtikelNr
- Aktualisiert: Listenpreis ohne TZ, TZ, Gültig ab
- Dry-Run Modus, Backup vor Änderung

### Abhängigkeiten
- **Liefert an:** #6 Budget-Angebot (aktuelle Preise)

### Offene Fragen
- [ ] Welche Hersteller? (ROKA, Weru, KompoTherm, Trendtüren?)
- [ ] Neue Artikel hinzufügen oder nur bestehende aktualisieren?
- [ ] GUI gewünscht?

### Status
**Planung**

---

## 2. Bilanz- und GuV-Auswertung

### Kurzbeschreibung
Analyse-Tool für Finanzkennzahlen mit Trendprognosen.

### Datenquellen
- DATEV-Export oder SQL Server (zu klären)

### Logik
- Kennzahlen: Liquidität, Eigenkapitalquote, Umsatzrendite
- Zeitreihenvergleich über Jahre
- Branchenvergleich/Benchmarking

### Abhängigkeiten
- **Nutzt:** #31 Rechnungsbuch (falls implementiert)
- **Liefert an:** #14 Management-Dashboard

### Offene Fragen
- [ ] Datenquelle? (SQL Server, DATEV, Excel?)
- [ ] Welche Kennzahlen sind relevant?
- [ ] KI für Vorhersagen?

### Status
**Idee**

---

## 3. Weru Förderanträge-Automatisierung ⭐ KRITISCH

### Kurzbeschreibung
BAFA/KfW-Foerderantraege ueber Weru FoerderService Portal. **KRITISCH:** NachweisService nach Zahlung wird vergessen → Kunde verliert Foerderung!

### Systeme
- **Portal:** https://weru.foerderservice.de/ (Session-basiert)
- **Energieberater:** Externer Dienstleister (Weru)
- **W4A:** Dokumente + Aufgaben-Tracking

### IST-Prozess (komplett)

```
AUSLOESER
├─ Kunde moechte Foerderung (BAFA/KfW)
├─ Hinweis meist bei Angebotserstellung
│
▼
VOR BESTELLUNG (WICHTIG!)
├─ Kunde liefert: Hausdaten + Vollmacht
├─ Andreas: Baumassnahme im Weru Portal anlegen
├─ Energieberater (Weru): Bearbeitet Antrag
├─ Weiterleitung an BAFA durch Energieberater
│
▼
NACH BAFA-BESTAETIGUNG
├─ Jetzt darf bestellt werden!
├─ Dokumente herunterladen → W4A ablegen
│
▼
MONTAGE + RECHNUNG + ZAHLUNG
├─ Normaler Auftragsprozess
├─ Projektakte wird nach Zahlung "geschlossen"
│
▼
⚠️ KRITISCHER SCHRITT (WIRD VERGESSEN!)
├─ "Eingabe NachweisService" im Weru Portal
├─ MUSS nach vollstaendiger Zahlung erfolgen!
├─ Ohne dies: Kunde bekommt KEINE Foerderung!
└─ Verantwortlich: Andreas
```

### KRITISCHES PROBLEM

| Aspekt | Details |
|--------|---------|
| **Problem** | NachweisService nach Zahlung wird vergessen |
| **Grund** | Projektakte wird nach Zahlung geschlossen, aber Foerderantrag muss DANACH noch abgeschlossen werden |
| **Folge** | Kunde verliert Foerderung (mehrere Tausend Euro!) |
| **Haeufigkeit** | 5-10 Antraege pro Jahr |
| **Verantwortlich** | Andreas |

### Loesung: Auto-Erinnerung nach Zahlung

**Erkennungsmerkmal in W4A:**
- Im Auftragsdokument gibt es Position "Pauschale fuer Foerderantraege"
- Kann aus `dbo.AuftragPos` ausgelesen werden

**Automatisierung:**

| Stufe | Loesung | Aufwand |
|-------|---------|---------|
| **Vollautomatisch** | Zahlung erkannt + Foerder-Position vorhanden → Auto-Aufgabe an Andreas | Mittel |
| **Halbautomatisch** | Taeglich pruefen: Auftraege mit Foerder-Position + Zahlung komplett + kein Erledigungsvermerk → Liste | Gering |
| **Assistiert** | Manueller Haken "Foerderantrag vorhanden" → Erinnerung nach Zahlung | Gering |

**SQL-Logik (Konzept):**
```sql
-- Auftraege mit Foerder-Position die vollstaendig bezahlt sind
SELECT a.Nummer, k.Name, a.Betrag,
       'NachweisService pruefen!' AS Aktion
FROM dbo.Auftrag a
JOIN dbo.Kunden k ON a.KundenCode = k.Code
JOIN dbo.AuftragPos p ON a.Code = p.AuftragCode
WHERE p.Bezeichnung LIKE '%Pauschale%Förder%'
  AND a.BezahltKomplett = -1  -- oder entsprechendes Feld
  AND a.Code NOT IN (
    -- Bereits erledigte (Aufgabe oder eigenes Feld)
    SELECT AuftragCode FROM dbo.BAFA_Erledigt  -- hypothetisch
  )
```

### W4A-Erweiterung (optional)

| Feld | Typ | Zweck |
|------|-----|-------|
| BAFA_Antrag | Ja/Nein | Foerderantrag vorhanden |
| BAFA_NachweisErledigt | Datum | Wann NachweisService gemacht |
| BAFA_Notizen | Text | Antragsnummer, Besonderheiten |

→ Aktuell keine Felder vorhanden, aber W4A erweiterbar

### Prozess-Checkliste

**Vor Bestellung:**
- [ ] Kunde hat Foerderung beantragt?
- [ ] Hausdaten + Vollmacht erhalten?
- [ ] Baumassnahme im Weru Portal angelegt?
- [ ] BAFA-Bestaetigung abwarten!

**Nach Zahlung:**
- [ ] Montage komplett abgeschlossen?
- [ ] Schlussrechnung bezahlt?
- [ ] → NachweisService im Weru Portal!
- [ ] Dokumente in W4A abgelegt?

### Abhaengigkeiten
- **Trigger:** Rechnungsprozess (Zahlung erkannt)
- **Verknuepft:** #65 Anzahlungsrechnung (gleicher Trigger-Punkt)
- **Nutzt:** #31 Rechnungsbuch (Zahlungsstatus)

### Quelle
Brainstorming 2025-12-16 (Andreas)

### Status
**Idee** - Mittel | **Prioritaet:** KRITISCH (Kundenschaden!)

---

## 4. KI-Wissensdatenbank ✅ FERTIG

### Kurzbeschreibung
Selbst-aktualisierende Wissensdatei mit KI/Automation-News.

### Implementierung
- **Datei:** `docs/KI_Wissen.md`
- **Script:** `tools/KI_Wissen/ki_wissen_updater.py`
- **Scheduler:** Windows Task (Sonntags 03:00)

### Status
**Fertig** - Wöchentliche Updates aktiv

---

## 5. Bauplan-Analyse & Elementlisten-Generator

### Kurzbeschreibung
KI-Vision liest Baupläne, extrahiert Maße, generiert Elementlisten.

### Input-Formate
- PDF, DWG, DXF, Bilder (JPG, PNG)

### Logik
- CAD vorhanden → Parser (ezdxf)
- Nur PDF/Bild → Claude Vision + OCR
- Output: Fensterliste, Türenliste (Position, Breite, Höhe, Typ)

### Tech-Stack
- pdfplumber, ezdxf, OpenCV, Tesseract OCR, Claude Vision

### Abhängigkeiten
- **Liefert an:** #6 Budget-Angebot

### Offene Fragen
- [ ] Welche Formate kommen am häufigsten?
- [ ] Genauigkeit? (±1cm, ±5cm?)
- [ ] Budget für Vision-APIs?

### Status
**Idee** - Komplex

---

## 6. Budget-Angebots-Generator

### Kurzbeschreibung
Automatische Budget-Angebote aus Elementlisten oder manueller Eingabe.

### Input-Optionen
- Manuell (Formular)
- Excel/CSV Import
- Aus #5 Bauplan-Analyse

### Logik
- Elementdaten → Artikel-Matching → Preis-Kalkulation → PDF/Word

### Preisdaten
- Excel-Artikelstamm
- Aktualisiert durch #1 Preislisten-Tool

### Abhängigkeiten
- **Nutzt:** #1 Preislisten, #5 Bauplan (optional)
- **Liefert an:** #10 Aufträge

### Offene Fragen
- [ ] Angebots-Vorlagen vorhanden?
- [ ] Rabattstaffeln?
- [ ] Montagekosten mit kalkulieren?

### Status
**Idee**

---

## 7. Spracherkennung & Anweisungsdienst

### Kurzbeschreibung
Diktat, Aufmaße vor Ort, Anweisungen per Sprache.

### Tech
- **Speech-to-Text:** Whisper (lokal oder API)
- **Intent-Erkennung:** Claude/GPT

### Anwendungsfälle
- Aufmaß vor Ort diktieren
- Schnelle Anweisungen ("Erstelle Angebot für...")

### Abhängigkeiten
- **Liefert an:** #8 Universal-Hub, #6 Angebot

### Offene Fragen
- [ ] Geräte? (PC, Handy, Tablet)
- [ ] Datenschutz: Cloud oder lokal?

### Status
**Idee** - Komplex

---

## 8. Universal-Eingabe-Hub

### Kurzbeschreibung
Das "Gehirn": Multi-Input (Bilder, E-Mails, Sprache) → LLM Dispatcher → Workflows.

### Input-Kanäle
- Fotos (Bauplan, Notiz)
- E-Mail
- Formulare
- Sprache (#7)

### Logik
- Input-Typ erkennen
- LLM analysiert Intent
- Workflow triggern (#1, #5, #6, #9, etc.)

### Abhängigkeiten
- **Orchestriert:** Alle anderen Tools

### Offene Fragen
- [ ] Welche Kanäle wichtigste?
- [ ] 24/7 Server oder on-demand?
- [ ] Welches LLM? (Claude, GPT, lokal)

### Status
**Idee** - Komplex

---

## 9. Reparatur-Verwaltung

### Kurzbeschreibung
Reklamationen, Garantieprüfung, Status-Tracking, Foto-Dokumentation.

### SQL-Kontext
- **Tabelle:** `dbo.Auftrag`
- **Felder:** `ReparaturauftragCode`, `ReparaturgarantieBis`, `GarantieNachReparatur`, `Reparaturlager`

### Logik
- Erfassung → Garantieprüfung (anhand Kaufdatum) → Terminierung → Durchführung → Abschluss

### Abhängigkeiten
- **Nutzt:** #11 Terminfindung
- **Input von:** #8 Hub, #12 E-Mail

### Status
**Idee**

---

## 10. Aufträge & Lieferungen

### Kurzbeschreibung
Zentrale Auftragsverwaltung: Aufträge, Abholungen, Lieferungen ±Montage.

### SQL-Kontext
- **Tabellen:** `dbo.Auftrag`, `dbo.Lieferschein`, `dbo.Lieferungsart`
- **Felder:** `LieferterminAbgehend`, `LieferterminTatsächlich`

### Auftragstypen
- Normaler Auftrag → Bestellung
- Abholung durch Kunde → Abholtermin
- Lieferung ohne Montage → Liefertermin
- Lieferung mit Montage → Montagetermin

### Abhängigkeiten
- **Nutzt:** #11 Terminfindung
- **Input von:** #6 Angebot

### Status
**Idee**

---

## 11. Terminfindung

### Kurzbeschreibung
Intelligente Terminplanung für Aufmaße, Beratungen, Montagen.

### SQL-Kontext
- **Tabellen:** `dbo.Termine`, `dbo.TermineTeilnehmer`, `dbo.TerminHistorie`

### Terminarten
| Typ | Dauer | Ressourcen |
|-----|-------|------------|
| Aufmaß | 1-2h | 1 MA |
| Beratung | 0.5-2h | 1 MA |
| Montage klein | 2-4h | 1-2 Monteure |
| Montage groß | 1-2 Tage | 2-4 Monteure |

### Logik
- Mitarbeiter-Verfügbarkeit prüfen
- Fahrtzeit berechnen
- Termine in Nähe gruppieren (Geo-Optimierung)

### Abhängigkeiten
- **Wird genutzt von:** #9, #10, #36

### Offene Fragen
- [ ] Online-Buchung durch Kunden?
- [ ] Automatische vs. manuelle Zuweisung?

### Status
**Idee**

---

## 12. E-Mail-Verarbeitung

### Kurzbeschreibung
LLM-Klassifizierung, Kunden-Zuordnung, Workflow-Trigger.

### SQL-Kontext
- **Lesen:** `dbo.Kunden`, `dbo.Lieferanten`, `dbo.Objekte`, `dbo.Mitarbeiter`
- **Schreiben (sicher):** `dbo.Historie` (INSERT only)

### E-Mail-Kategorien
| Kategorie | Aktion |
|-----------|--------|
| Anfrage Neubau | → #5/#6 Angebot |
| Anfrage Reparatur | → #9 Reparatur |
| Rechnung eingehend | → Buchhaltung |
| Reklamation | → #9 + Eskalation |

### Sicherheitskonzept
- SELECT: immer erlaubt
- INSERT: nur in Historie/Dokumente
- UPDATE/DELETE: NIE

### Abhängigkeiten
- **Liefert an:** #8 Hub, #9 Reparatur, #6 Angebot

### Status
**Idee**

---

## 13. Inventar-Verwaltung

### Kurzbeschreibung
Erweiterung Work4all: Rechnungslink, Standort-Tracking, QR-Codes, Ausleihe.

### SQL-Kontext
- **Tabellen:** `dbo.Inventar`, `dbo.Lagerort`

### Logik
- QR-Code pro Gerät
- Standortwechsel dokumentieren
- Ausleihe-Workflow

### Offene Fragen
- [ ] Was fehlt in Work4all am meisten?
- [ ] Werden QR-Codes bereits genutzt?

### Status
**Idee**

---

## 14. Management-Dashboard

### Kurzbeschreibung
Zentrale KPI-Übersicht, aggregiert alle Tools + Work4all.

### KPIs (Fensterbau-spezifisch)
| KPI | Quelle |
|-----|--------|
| Umsatz/Mitarbeiter | Work4all |
| Auftragsquote | Work4all |
| Ø Auftragswert | Work4all |
| Reklamationsquote | #9 |
| Liefertreue | #10 |

### Abhängigkeiten
- **Aggregiert:** Alle Tools + Work4all

### Status
**Idee**

---

## 15. Zeiterfassung & Auslastung

### Kurzbeschreibung
Projektbezogene Zeit, Kapazitätsplanung.

### SQL-Kontext
- **Tabellen:** `dbo.Zeiten` (falls vorhanden)

### Abhängigkeiten
- **Erweitert durch:** #34 (GPS)
- **Liefert an:** #17 Deckungsbeitrag

### Status
**Idee**

---

## 16. Urlaubsverwaltung

### Kurzbeschreibung
Digitale Anträge, Teamkalender.

### SQL-Kontext
- **Tabellen:** `dbo.Urlaubsantrag` (falls vorhanden), `dbo.Mitarbeiter`

### Abhängigkeiten
- **Erweitert durch:** #35 (Abwesenheitsmanagement)

### Status
**Idee**

---

## 17. Projekt-Deckungsbeitrag

### Kurzbeschreibung
Soll-Ist-Vergleich, Nachkalkulation, Budgetwarnung.

### Logik
- Kalkulation (Soll) vs. tatsächliche Kosten/Zeiten (Ist)
- Warnung bei Budgetüberschreitung

### Abhängigkeiten
- **Nutzt:** #15 Zeiterfassung, #32 Projekte

### Status
**Idee**

---

## 18. Kundenportal

### Kurzbeschreibung
Self-Service: Status, Termine, Dokumente, Reklamation.

### Features
- Auftragsstatus einsehen
- Termine buchen/verschieben
- Dokumente herunterladen
- Reklamation melden

### Abhängigkeiten
- **Nutzt:** #10, #11, #9

### Status
**Idee** - Komplex

---

## 19. Lieferanten-Bewertung

### Kurzbeschreibung
Auto-Scoring: Liefertreue, Qualität, Preis, Kommunikation.

### Logik
- Score berechnen aus historischen Daten
- Liefertreue = pünktliche / alle Lieferungen

### SQL-Kontext
- **Tabellen:** `dbo.Bestellung`, `dbo.Lieferant`

### Abhängigkeiten
- **Liefert an:** #14 Dashboard, #36 Beschaffung

### Status
**Idee**

---

## 20. Qualitätsmanagement

### Kurzbeschreibung
Reklamations-Tracking, KVP, Audit-Vorbereitung.

### Logik
- Reklamationen kategorisieren
- Ursachenanalyse
- Maßnahmen tracken

### Abhängigkeiten
- **Nutzt:** #9 Reparaturen

### Status
**Idee** - Komplex

---

## 21. Mobile Monteur-App

### Kurzbeschreibung
Unified: Tagesplan, Navigation, Checklisten, Fotos, Unterschrift, Zeit.

### Features
- Tagesübersicht mit Terminen
- Navigation zum Kunden
- Checklisten pro Auftragstyp
- Foto-Dokumentation
- Digitale Unterschrift
- Zeiterfassung

### Abhängigkeiten
- **Nutzt:** #10, #11, #15, #29

### Status
**Idee** - Komplex

---

## 22. Routenplanung

### Kurzbeschreibung
Tourenoptimierung: Fahrzeit minimieren, Termine clustern.

### ROI-Schätzung
- ~292 Std/Jahr gespart
- ~11.500 km weniger

### Logik
- Termine pro Tag nach Geo-Nähe gruppieren
- Optimale Reihenfolge berechnen

### Abhängigkeiten
- **Nutzt:** #11 Termine

### Status
**Idee**

---

## 23. Verkaufschancen-Pipeline + Angebots-Reminder

### Kurzbeschreibung
Lead-Bewertung, Scoring, Follow-up-Erinnerungen inkl. automatisierter Angebots-Nachverfolgung.

### Enthaelt (ehem. #45 Angebots-Reminder)
- Automatisch nach X Tagen nachfassen
- 2-Tage-Regel: Proaktiv Mehrwert bieten (alternative Loesung, Kostenoptimierung)
- Priorisierung nach Volumen + Deckungsbeitrag
- Eskalation: Nach 7 Tagen intensiver, nach 14 Tagen Abschluss-Anfrage

### Logik
- Leads bewerten (Budget, Zeitrahmen, Entscheidungstraeger)
- Automatische Follow-up Erinnerungen
- Nicht aufdringlich - immer GRUND fuer Anruf liefern

### SQL-Kontext
- **Tabellen:** `dbo.Angebot`, `dbo.Kunden`

### Status
**Idee** - Mittel

---

## 24. Ticket-System Integration + Schnell-Erfassung

### Kurzbeschreibung
Auto-Tickets aus E-Mails, Eskalation, SLA-Tracking inkl. Telefon-Schnellerfassung.

### Enthaelt (ehem. #46 Schnell-Erfassung Anfrage)
- Telefon klingelt → 1-Klick Formular
- Minimale Felder: Name/Firma, Bedarf (Dropdown + Freitext), Rueckruf (Checkbox + Uhrzeit)
- Telefonnummer auto. aus CTI wenn vorhanden

### Features
- Auto-Vorgangsnummer bei jeder Kundenanfrage (z.B. V-2025-001234)
- Bestaetigung an Kunden: "Ihre Anfrage unter V-XXXX erfasst"
- Alle Kommunikation unter dieser Nummer auffindbar
- SLA: Antwort-Ziel innerhalb X Stunden

### Bestehende Checklisten als Grundlage (2025-12-16)

> **Quellen:** `Z:\Vorlagen\Arbeitsabläufe\`

| Checkliste | Datei | Status | Eingebunden in |
|------------|-------|--------|----------------|
| **Tel. Kundenanfragen** | `Checkliste telefonische Kundenanfragen.odt` | Vorlage, nicht konsequent | Anfrageprozess_Analyse.md |
| **Reparaturen** | `Checkliste Reparaturen.odt` | Aktiv genutzt | Reparaturprozess_Analyse.md |

### Felder aus Checklisten fuer digitale Erfassung

**Anfragen (Neubau/Sanierung):**

| Feld | Pflicht | Notizen |
|------|---------|---------|
| Kunde pruefen (Bestands/Neu) | Ja | Auto-Lookup aus W4A |
| "Wie auf uns aufmerksam?" | Neu! | Marketing-Auswertung |
| Projekttyp (Neubau/Sanierung/Reparatur) | Ja | Steuert weiteren Ablauf |
| Projektbeginn | Ja | Fuer Priorisierung |
| Produkte (Multi-Select) | Ja | Mit Mindestpreisen |
| Budget | Optional | Qualifizierung |
| Fremdangebot vorhanden? | Optional | Wenn ja → Ausstellungs-Termin |
| Entscheider/Verantwortlicher | Wichtig! | Ohne Entscheider kein Abschluss |
| Kontaktdaten | Pflicht | Name, Adresse, Tel/Mail |
| Bauvorhaben (wenn ≠ Kunde) | Bei Bedarf | "BV:" Kennzeichen |

**Reparaturen:**

| Feld | Pflicht | Notizen |
|------|---------|---------|
| Kunde pruefen | Ja | Auto-Lookup |
| "Wie auf uns aufmerksam?" | Neu! | Marketing |
| Schadensbeschreibung | Ja | Freitext |
| Etage | Ja | Doppelanfahrt vermeiden! |
| Besonderheiten (Geruest, Leiter) | Ja | Ausruestung planen |
| Kontaktdaten | Pflicht | Standard |
| Bauvorhaben (Mietobjekt) | Bei Bedarf | Vermieter ≠ Mieter |
| Prio-Einschaetzung | Auto | Bestand > Gewerbe > Dringend > Rest |

### Erkenntnisse aus Checklisten-Review

| Erkenntnis | Auswirkung auf Tool |
|------------|---------------------|
| Reparatur-Checkliste wird gelebt | Gute Vorlage, 1:1 digitalisieren |
| Anfragen-Checkliste eher Vorlage | Digitalisierung erzwingt Nutzung |
| Prio-Regeln existieren aber nicht aktiv | Tool kann auto-priorisieren |
| "Wie gefunden" fehlt ueberall | NEU hinzufuegen → Marketing-Daten |
| Entscheider-Feld wichtig | Pflichtfeld bei Anfragen |
| Mindestpreise zur Qualifizierung | In Produkt-Auswahl integrieren |

### Abhaengigkeiten
- **Input von:** #12 E-Mail
- **Nutzt:** #25 Telefon-CRM (optional)
- **Liefert an:** #23 Verkaufschancen

### Status
**Idee** - Mittel (Checklisten-Grundlage vorhanden!)

---

## 25. Telefon-CRM Integration

### Kurzbeschreibung
Anrufer-Erkennung, Kundendaten-Popup, Notizen.

### Logik
- Eingehende Nummer → SQL-Abfrage → Kundendaten anzeigen
- Notiz direkt im Popup speichern

### Status
**Idee**

---

## 26. Projekt-Aktivitäten-Tracking

### Kurzbeschreibung
Auto-Protokoll aller Aktivitäten, Timeline-Ansicht.

### SQL-Kontext
- **Tabellen:** `dbo.Historie`, `dbo.Historie2`

### Status
**Idee**

---

## 27. Dokument-Intelligenz

### Kurzbeschreibung
Auto-Klassifizierung, OCR, Metadaten, Volltextsuche.

### Logik
- Dokument hochladen → OCR → Typ erkennen → Metadaten extrahieren → Ablage

### SQL-Kontext
- **Tabellen:** `dbo.Dokumente`, `dbo.DokumenteGr`

### Status
**Idee**

---

## #28 Digitales Aufmass + Zubehoer + Mobiles Formular

### Kurzbeschreibung
Masserfassung mit auto. Zubehoer-Berechnung (Fensterbaenke, Rolllaeden) inkl. mobilem Erfassungs-Formular.

### Problem (IST-Zustand aus Aufmassprozess-Analyse)
| # | Problem | Folge |
|---|---------|-------|
| 1 | Aenderungen nicht nachgescannt | Veraltete Daten, falsche Masse bei Montage |
| 2 | Angebots- statt Bestellaufmass | Unvollstaendige Masse, Reklamationen |
| 3 | Foto-Workflow umstaendlich | 6 Schritte (Handy→Mail→PDF→Verkleinern→W4A) |
| 4 | Wenig Platz fuer Notizen | Besonderheiten gehen unter |
| 5 | 7+ verschiedene Papierformate | Unuebersichtlich, falsches Blatt |
| 6 | Masse manuell abtippen (Papier→WoT) | Tippfehler, doppelte Arbeit |

### Enthaelt (ehem. #61 Mobiles Aufmass-Formular)
- Responsive Web-Formular fuer Handy/Tablet
- Felder: Raum, Breite, Hoehe, Tiefe, Bemerkungen
- Fotos direkt aus Kamera anhaengen
- Offline-Speicherung, spaeter sync

### Logik
- Fenstermasse eingeben
- Automatisch: Fensterbank (Breite + 10cm), Rollladen berechnen
- Daten als Basis fuer Angebot/Bestellung

### Verschiedene Formulare (wie aktuell Papier)
| Produkt | Digital abbilden |
|---------|------------------|
| Fenster | Formular 1 |
| Haustueren | Formular 2 |
| Innentueren (4 Varianten) | Formular 3a-3d |
| Garagentore | Formular 4 |

### Loest
- Papierzettel verloren, muss abgetippt werden
- Kein Zugriff auf Daten vor Ort
- Foto-Workflow vereinfacht (direkt aus App)
- Daten koennen direkt in Konfigurator fliessen

### Abhaengigkeiten
- **Braucht:** #58 Web-Plattform (responsive)
- **Liefert an:** #6 Budget-Angebot, #39 Montage-Mappe
- **Verknuepft:** #42 Foto-Zuordnung

### Quelle
Aufmassprozess-Analyse 2025-12-14

### Status
**Idee** - Mittel | **Prioritaet:** Hoch (loest 6 Schmerzpunkte!)

---

## 29. Montage-Checklisten

### Kurzbeschreibung
Auto-Checklisten aus Aufmaß: Material, Werkzeug, Arbeitsschritte.

### Logik
- Aus Aufmaß-Daten → passende Checkliste generieren
- Abhaken während Montage

### Abhängigkeiten
- **Nutzt:** #28 Aufmaß

### Status
**Idee**

---

## 30. After Sales Service

### Kurzbeschreibung
Proaktive Kundenbetreuung: Wartung, Cross-Selling.

### Logik
- Nach X Jahren: Wartungserinnerung
- Cross-Selling basierend auf Kaufhistorie

### Status
**Idee**

---

## 31. Rechnungsbuch & Finanzdokumentation

### Kurzbeschreibung
Ein-/Ausgangsrechnungen, Mahnwesen, DATEV-Export.

### SQL-Kontext
- **Tabellen:** `dbo.Rechnung`, `dbo.Zahlung`

### Features
- OCR für eingehende Rechnungen
- Zahlungsabgleich
- Liquiditätsvorschau

### Abhängigkeiten
- **Nutzt:** #12 E-Mail, #32 Projekte
- **Liefert an:** #2 Bilanz

### Status
**Idee**

---

## 32. Projekt- & Unterprojektverwaltung

### Kurzbeschreibung
Hierarchisch: Hauptprojekt → Unterprojekte → ERP-Dokumente.

### SQL-Kontext
- **Tabellen:** `dbo.Objekte`, `dbo.Auftrag`, `dbo.Angebot`

### Abhängigkeiten
- **Wird genutzt von:** #31, #33, #34, #17

### Status
**Idee**

---

## #33 Bestellwesen & Lieferanten-Auftraege

### Kurzbeschreibung
Bedarfsermittlung → Bestellung → Wareneingang mit korrekten Teilmengen.

### Problem (IST-Zustand)
- **Teilmengen falsch erfasst:** Roland uebernimmt komplette BE fuer Eingangslieferschein, obwohl nur Teilmenge geliefert
- **Folge:** W4A-Daten zeigen falsche Bestaende, Folgeprozesse (Montageplanung, Lager) brechen
- **Lieferanten-LS zeigt korrekt:** Teilmenge (z.B. "3 von 5 Fenster")
- **W4A zeigt falsch:** Alles geliefert

### Loesung (SOLL-Zustand)
1. **Teilmengen-Buchung erzwingen:** Nur gelieferte Menge im Eingangslieferschein
2. **Abgleich mit LS:** Warnung wenn Buchung ≠ Lieferschein-Scan
3. **Offene Restmengen sichtbar:** Dashboard zeigt "noch 2 Fenster offen"

### SQL-Kontext
- **Tabellen:** `dbo.Bestellung`, `dbo.Wareneingang`, `dbo.EingangsLieferschein`

### Abhaengigkeiten
- **Verknuepft:** #36 Beschaffungs-Dashboard, #38 Lagerverwaltung
- **Nutzt:** #56 AB-Abgleich (Pruefung gegen Bestellung)

### Quelle
Lagerprozess-Analyse 2025-12-14

### Status
**Idee** - Mittel | **Prioritaet:** Hoch (Datenqualitaet!)

---

## 34. Erweiterte Zeiterfassung (GPS)

### Kurzbeschreibung
Projektzuordnung Pflicht, GPS-Vorschläge, QR-Code-Erfassung.

### Datenschutz
- GPS nur während Arbeitszeit
- Mitarbeiter kann deaktivieren
- Daten nach 30 Tagen löschen
- Keine Echtzeit-Überwachung

### Abhängigkeiten
- **Erweitert:** #15
- **Nutzt:** #11, #32

### Status
**Idee**

---

## 35. Urlaubsplaner & Abwesenheitsmanagement

### Kurzbeschreibung
Teamkalender, auto. Kapazitätsprüfung, Genehmigungsworkflow.

### Logik
- Urlaubsantrag → System prüft: Wer ist sonst weg? Genug Kapazität?
- Auto-Genehmigung oder Warnung

### Abhängigkeiten
- **Erweitert:** #16
- **Nutzt:** #11

### Status
**Idee**

---

## 36. Beschaffungs-Dashboard ⭐ PRIORITÄT

### Kurzbeschreibung
Echtzeit-Übersicht kritischer Bestellvorgänge. Verhindert Montage-Stillstand durch vergessene Bestellungen.

### SQL-Kontext
- **Tabelle:** `dbo.Bestellung`
- **Relevante Felder:**
  - `Bestätigt` (0=keine AB, -1=AB da)
  - `BestellDatum` (Datum)
  - `LieferterminTatsächlich` (Soll-Liefertermin)
  - `WEDatum` (NULL=noch nicht eingetroffen)
  - `Abgeschlossen` (0=offen, -1=erledigt)
  - `KarteiCode` (FK Lieferant)
  - `ProjektCode` (FK Projekt)
  - `Wert` (Bestellwert)

### Logik (Ampel-System)
| Status | Bedingung | Schwellenwert |
|--------|-----------|---------------|
| 🔴 Kritisch | Keine AB erhalten | > 5 Tage nach Bestellung |
| 🟡 Warnung | Liefertermin überschritten | WEDatum IS NULL AND Termin < heute |
| 🟠 Abholbereit | Ware liegt beim Lieferanten | Noch zu klären: Feld vorhanden? |
| 🟢 OK | AB da, Termin in Zukunft | Standard |

### SQL-Queries
```sql
-- Ohne AB (> 3 Tage)
SELECT b.Nummer, l.Firma, b.BestellDatum, b.Wert,
       DATEDIFF(day, b.BestellDatum, GETDATE()) AS TageOffen
FROM dbo.Bestellung b
LEFT JOIN dbo.Lieferant l ON b.KarteiCode = l.Code
WHERE b.Abgeschlossen = 0 AND b.Bestätigt = 0
  AND DATEDIFF(day, b.BestellDatum, GETDATE()) > 3;

-- Überfällig
SELECT b.Nummer, l.Firma, b.LieferterminTatsächlich,
       DATEDIFF(day, b.LieferterminTatsächlich, GETDATE()) AS TageUeber
FROM dbo.Bestellung b
LEFT JOIN dbo.Lieferant l ON b.KarteiCode = l.Code
WHERE b.Abgeschlossen = 0 AND b.WEDatum IS NULL
  AND b.LieferterminTatsächlich < GETDATE();
```

### Abhängigkeiten
- **Nutzt:** SQL direkt
- **Liefert an:** #11 Termine (Montage-Warnung), #14 Dashboard (KPI)

### Offene Fragen
- [ ] Wie wird "Abholbereit" heute kommuniziert? Feld vorhanden?
- [ ] Nach wie vielen Tagen ohne AB ist es kritisch? (Vorschlag: 5)
- [ ] Wer soll Alerts bekommen?
- [ ] Standalone oder in Work4all integriert?

### Status
**Idee** - ⭐ HOHE PRIORITÄT

---

## #37 WoT-XML Transformer (Weru Konfigurator)

### Kurzbeschreibung
XML-Export aus WoT (Weru WPS on Top) Konfigurator transformieren fuer sauberen Work4all Import.

### Problem
- WoT exportiert XML mit viel Redundanz (gleiche Infos in jeder Position)
- Kein Lieferant-Feld -> muss manuell im ERP nachgetragen werden
- Positionstexte unuebersichtlich lang

### Logik
1. **XML einlesen** (iso-8859-1 Encoding beachten)
2. **Redundanz-Analyse:**
   - Alle Langtext-Felder parsen
   - Haeufige Zeilen identifizieren (>50% der Positionen)
   - Diese in Kopftext verschieben
3. **Positionstexte kuerzen:**
   - Nur einmalige Infos behalten (Raum, Masse, Sonder-Optionen)
4. **Lieferant einfuegen:**
   - Je Position ein Lieferant-Feld mit "Weru" (oder konfigurierbar)
   - W4A erkennt das beim Import und ordnet automatisch zu
5. **XML ausgeben** (transformiert)

### Beispiel-Transformation
**Vorher (Positionstext):**
```
OG - Abstellraum
Anschlag: DKL Dreh-Kipp links
Uw,N: 0,78 W/(m²K) n. EN ISO 10077-1
Breite: 980 mm, Höhe: 1325 mm
Rahmenbreite: 72 mm normal
links - Verbreiterung: 20 mm
rechts - Verbreiterung: 20 mm
Abschluss unten: Futterleiste 30 mm
```

**Nachher (Positionstext):**
```
OG - Abstellraum | DKL | 980x1325
```

**Kopftext (ergaenzt):**
```
Rahmenbreite: 72 mm normal
Verbreiterung links/rechts: 20 mm
Abschluss unten: Futterleiste 30 mm (Standard)
```

### Abhaengigkeiten
- **Input:** WoT XML Export
- **Output:** Transformierte XML fuer W4A Drag&Drop Import
- **Konfigurierbar:** Lieferant-Name, Redundanz-Schwelle

### Offene Fragen
- [ ] Welches XML-Feld nutzt W4A fuer Lieferant-Zuordnung?
- [ ] Sollen Bilder (Base64) auch uebernommen werden?
- [ ] GUI oder CLI-Tool?
- [ ] Wo soll Output-XML gespeichert werden?

### Status
**Idee** - Mittel

---

## #38 Lagerverwaltung & Inventur

### Kurzbeschreibung
Bestandsfuehrung fuer Lagerartikel, Inventur-Prozess, korrekte Wareneingangsbuchung, Gestell-Tracking.

### Ist-Zustand
- **Inventur:** Eigene Excel-Liste + Papier (getrennt von W4A)
- **W4A Artikelstamm:** Nur fuer Kalkulation, KEINE Bestaende gefuehrt
- **W4A Lagerfunktion:** Vorhanden aber nicht im Einsatz
- **Problem:** Teillieferungen werden als Komplett-Lieferung gebucht
- **NEU - Lager-Organisation:**
  - Fenstergestelle: Fester Bereich, werden bei Bedarf vorgeholt
  - Anderes Material: Feste Plaetze, nach Themen sortierte Regale
  - Material nur durch Erfahrung findbar!
- **NEU - Gestell-Problem:** Kein System "Welches Element auf welchem Gestell?"

### SQL-Kontext
- **Tabellen:** `dbo.Artikel`, `dbo.Lagerbestand` (zu pruefen ob vorhanden)
- **Relevante Felder:** Bestand, Mindestmenge, Lagerort

### Logik (potentiell)
1. **W4A Lagerfunktion aktivieren** und testen
2. **Teillieferungs-Problem loesen:** Wareneingang korrekt buchen
3. **Inventur-Workflow:** Scan-basiert oder manuell mit Abgleich
4. **Bestandswarnungen:** Bei Unterschreitung Mindestmenge
5. **NEU - Gestell-Tracking:** Element → Gestell Zuordnung
6. **NEU - Lagerplatz-System:** Wo liegt was? (fuer Einarbeitung, nicht nur Erfahrung)

### Abhaengigkeiten
- **Verknuepft:** #33 Bestellwesen, #36 Beschaffungs-Dashboard
- **Nutzt:** SQL Lagertabellen (falls W4A), Excel-Import (falls Eigenbau)

### Offene Fragen
- [ ] W4A Lagerfunktion ausreichend oder Eigenbau noetig?
- [ ] Wie viele Artikel werden auf Lager gefuehrt?
- [ ] Barcode/QR-Scan gewuenscht?
- [ ] Welche Lagerorte gibt es? (Hauptlager, Fahrzeuge, etc.)
- [ ] Wie viele Gestelle gibt es? Nummerierung?
- [ ] Sollen Gestelle getrackt werden (welches Element wo)?

### Quelle
Lagerprozess-Analyse 2025-12-14

### Status
**Idee** - Mittel

---

## #39 Tages-Briefing Monteur (Montage-Mappe)

### Kurzbeschreibung
Automatisch generierte Montage-Unterlagen statt manueller Zusammenstellung durch Buero.

### Problem (Ist-Zustand)
- Susann stellt manuell Unterlagen zusammen
- Zu viele Blaetter, nicht alle noetig
- Falsche Dokumente: Aufmass-Blaetter fuer ANGEBOT statt BESTELLUNG
- Unstrukturiert, Monteure muessen suchen

### Loesung (Soll-Zustand)
Pro Auftrag 1-3 Seiten "Montage-Mappe":
1. **Uebersicht (1 Seite):** Kunde, Adresse, Telefon, Ansprechpartner, Terminzeit
2. **Relevante Masse:** Aus BESTELLUNG (nicht Angebot!) - nur was gebaut wird
3. **Material-Checkliste:** Was muss mit? (#40)
4. **Besonderheiten:** Notizen, Zugang, Parkplatz, Sonderwuensche

### Logik
- Auftrag in W4A → Script generiert PDF
- Unterscheidung Angebot vs. Bestellung: Nur Bestell-Daten verwenden
- Material aus Auftragspositionen ableiten

### SQL-Kontext
- **Tabellen:** `dbo.Auftrag`, `dbo.AuftragPos`, `dbo.Kunden`, `dbo.Bestellung`, `dbo.BestellungPos`
- **Kritisch:** Verknuepfung Auftrag → Bestellung fuer korrekte Masse

### Output-Optionen
- PDF druckbar (aktuell realistischer)
- Digital via Handy/Tablet (Zukunft - Endgeraete + Akzeptanz pruefen!)

### Abhaengigkeiten
- **Integriert:** #40 Kommissionierliste
- **Nutzt:** #11 Termine (Tages-Uebersicht)
- **Liefert an:** Monteure, ersetzt manuelle Vorbereitung

### NEU: Digitale Erfassung (Brainstorming 2025-12-11)

**Problem:** Seite 2 der Montage-Unterlagen = Handschrift-Chaos, muss im Buero entziffert werden.

**Loesung - Tablet/Handy-App statt Papier:**
- 📱 Strukturierte Eingabe auf dem Endgeraet (Dropdown + Textfeld + Foto)
- 📷 Fotos vor Ort (statt "defekt" beschreiben - zeigen!)
- 🎤 Spracheingabe mit KI-Analyse (#7): "Endleiste 921mm fehlt" → System erkennt Material + Mass
- ⚡ Sofort im System (nicht: Papier ins Lager → naechster Tag ins Buero → entziffern)

**Vorteile:**
- Kein Entzifferungs-Aufwand (Handschrift lesen)
- Sofortige Verfuegbarkeit im Buero
- Strukturierte Daten statt Freitext
- Fotos als Beweismittel/Dokumentation

**Verknuepfung:** #7 Spracherkennung fuer Diktat-Funktion

### NEU: Material-Rueckmeldung (Lagerprozess-Analyse 2025-12-14)

**Problem:**
- Ruecklaeufer (nicht benoetigtes Material) werden oft NICHT dokumentiert
- Austausch vor Ort (anderes Material verwendet) wird nicht notiert
- Folge: Position bleibt auf Rechnung → Kunde reklamiert → Rechnungskorrektur
- Montagematerial-Position wird ueber Excel berechnet, muss haendisch aktualisiert werden

**Loesung - Material-Checkliste mit Rueckmeldung:**
1. **VOR Montage:** Kommissionierliste (#40) - was geht mit?
2. **NACH Montage:** Was wurde tatsaechlich verbaut?
   - Checkbox: "Wie geplant" oder Aenderung eintragen
   - Ruecklaeufer markieren: "Nicht benoetigt"
   - Austausch: "Statt X wurde Y verbaut"
3. **Automatisch:** Rechnung basiert auf TATSAECHLICH verbautem Material

**Vorteil:** Keine Rechnungskorrekturen mehr, weniger Kundenreklamationen

### Status
**Idee** - Mittel (hoher Impact!)

---

## #40 Material-Kommissionierliste

### Kurzbeschreibung
Auto-generierte Checkliste: Was muss ins Auto? Abhaken vor Abfahrt.

### Logik
- Auftragspositionen aus BESTELLUNG analysieren (nicht Angebot!)
- Material gruppieren:
  - Fenster/Tueren (Hauptprodukte)
  - Zubehoer (Fensterbaenke, Rolllaeden)
  - Befestigung (Schrauben, Schaum, Silikon)
  - Werkzeug (falls auftrags-spezifisch)
- Checkbox zum Abhaken vor Abfahrt
- Lagerort/Standort wenn verfuegbar

### Integration
- **Teil von #39:** Wird als Seite in Montage-Mappe integriert
- Kann auch separat generiert werden

### SQL-Kontext
- **Tabellen:** `dbo.BestellungPos`, `dbo.Artikel`, `dbo.Lagerbestand`
- **Wichtig:** Nur bestellte Artikel, nicht Angebots-Positionen!

### Abhaengigkeiten
- **Nutzt:** #10 Auftraege, #38 Lagerverwaltung
- **Integriert in:** #39 Montage-Mappe

### Status
**Idee** - Mittel

---

## #41 Montage-Status Live

### Kurzbeschreibung
Monteur meldet Status (angekommen, fertig, Problem) - alle sehen Echtzeit-Uebersicht.

### Logik
- Einfache Status-Buttons in App/SMS
- Status-Aenderung triggert Update in Zentrale
- Uebersicht zeigt: Wer ist wo, welcher Status
- Bei "Problem" sofort Benachrichtigung an Disposition

### Tech
- Push-API oder SMS-Gateway
- Dashboard fuer Buero

### Abhaengigkeiten
- **Nutzt:** #11 Termine, #21 Monteur-App (optional)
- **Liefert an:** #14 Dashboard

### NEU: Auto-Benachrichtigung an Kunde (Brainstorming 2025-12-11)

**Problem:** Kunde gibt Zugang (Schluessel, Code), ist nicht zu Hause, weiss nicht ob Monteur kommt.
- Bei Restarbeit = Monteur kommt
- Bei Material-Bedarf = Monteur kommt NICHT (erst Bestellung)
- Kunde wird nicht automatisch informiert → Unsicherheit, Rueckfragen

**Loesung - Auto-SMS/E-Mail bei Statusaenderung:**
- 📲 "Montage abgeschlossen, Rechnung folgt"
- ⚠️ "Restarbeiten noetig, Material wird bestellt, wir melden uns mit neuem Termin"
- 📅 "Ihr neuer Termin: XX.XX.XXXX um XX:XX Uhr"
- ✅ "Wir sind heute um XX:XX bei Ihnen" (morgens als Erinnerung)

**Tech:**
- SMS-Gateway (z.B. Twilio, oder deutscher Anbieter)
- E-Mail als Fallback
- Template-System fuer verschiedene Nachrichten
- Opt-in beim Kunden (DSGVO-konform)

### Status
**Idee** - Anspruchsvoll

---

## #42 Foto-Zuordnung

### Kurzbeschreibung
Handy-Foto → Auto-Erkennung Projekt/Kunde → richtige Akte.

### Logik
- Foto mit Metadaten (Zeit, GPS) analysieren
- GPS mit Kundenadresse matchen
- Zeitfenster mit Terminen abgleichen
- Vorschlag: "Dieses Foto zu Projekt X bei Kunde Y?"
- Automatisch in richtige Dokumenten-Akte ablegen

### Tech
- GPS-Koordinaten-Vergleich
- Zeitfenster-Logik

### SQL-Kontext
- **Tabellen:** `dbo.Dokumente`, `dbo.Kunden`, `dbo.Termine`

### Abhaengigkeiten
- **Nutzt:** #27 Dokument-Intelligenz

### Status
**Idee** - Anspruchsvoll

---

## #43 ~~Kanban-Dashboard fuer Ticketsystem~~ → merged in #9

### Kurzbeschreibung
Grafische Kachel-Ansicht fuer W4A-Tickets - wird als UI-Komponente von #9 Reparatur-Verwaltung implementiert.

### Hintergrund
Das W4A Ticketsystem funktioniert bereits gut mit:
- Kategorien (Restarbeiten, Montage, Reparaturen, Reklamationen, etc.)
- WV-Spalte (Wiedervorlage-Datum)
- Prioritaet + Status mit farbigen Punkten
- Detail-Bereich mit Problembeschreibung, Anhaenge, Loesung

**Problem:** Die Tabellen-Ansicht ist funktional, aber nicht visuell fuer schnellen Ueberblick.

### Logik
- Daten aus W4A Ticketliste auslesen
- Kachel-Ansicht wie Outlook-Kalender darstellen
- Drag & Drop zwischen Status/Kategorien
- Filter nach Team, Prioritaet, Wartegrund
- Farbkodierung nach Kategorie/Status

### Vorbild
- Outlook-Kacheln (bekannt bei JS Fenster)
- Trello-Style Kanban-Boards

### SQL-Kontext
- **Tabellen:** W4A Ticketsystem-Tabellen (zu ermitteln)

### Abhaengigkeiten
- **Nutzt:** Bestehende W4A Ticketliste-Daten
- **Liefert an:** #14 Command Center Dashboard

### Status
**Idee** - Mittel

---

## #44 Kapazitaets-Cockpit

### Kurzbeschreibung
Wie voll ist die Woche? Wer hat noch Luft? Uebersicht Auslastung.

### Logik
- Termine pro Mitarbeiter aggregieren
- Verfuegbare Stunden vs. gebuchte Stunden
- Ampel-System: Rot (>100%), Gelb (80-100%), Gruen (<80%)
- Drill-Down: Wer hat wann Zeit fuer dringende Auftraege?

### SQL-Kontext
- **Tabellen:** `dbo.Termine`, `dbo.Mitarbeiter`, `dbo.Arbeitszeit`

### Abhaengigkeiten
- **Nutzt:** #11 Terminfindung, #15 Zeiterfassung, #35 Urlaubsplaner
- **Liefert an:** #14 Dashboard

### Status
**Idee** - Anspruchsvoll

---

## #45 ~~Angebots-Reminder~~ → merged in #23

*Integriert in #23 Verkaufschancen-Pipeline + Angebots-Reminder*

---

## #46 ~~Schnell-Erfassung Anfrage~~ → merged in #24

*Integriert in #24 Ticket-System Integration + Schnell-Erfassung*

---

## #47 Kunden-Historie Dashboard + Wiederkauf-Erkennung

### Kurzbeschreibung
Alle Kontakte, Angebote, Auftraege, Reklamationen auf einen Blick inkl. automatischer Wiederkauf-Erkennung.

### Enthaelt (ehem. #48 Wiederkauf-Erkennung)
- "Familie Mueller hat 2019 schon Fenster gekauft" erkennen
- Historische Auftraege anzeigen bei neuer Anfrage
- Was wurde damals gekauft?
- Cross-Selling-Hinweise

### Logik
- Timeline-Ansicht pro Kunde
- Alle Dokumente chronologisch
- Letzte Kommunikation (E-Mails, Anrufe, Termine)
- Offene Vorgaenge hervorheben
- Bei neuer Anfrage: Automatisch auf Bestandskunde pruefen

### SQL-Kontext
- **Tabellen:** `dbo.Kunden`, `dbo.Historie`, `dbo.Angebot`, `dbo.Auftrag`, `dbo.AuftragPos`, `dbo.Dokumente`

### Abhaengigkeiten
- **Nutzt:** #26 Projekt-Aktivitaeten-Tracking
- **Liefert an:** #30 After Sales
- **Aehnlich:** In W4A vorhanden? Pruefen

### Status
**Idee** - Mittel

---

## #48 ~~Wiederkauf-Erkennung~~ → merged in #47

*Integriert in #47 Kunden-Historie Dashboard + Wiederkauf-Erkennung*

---

## #49 Google-Reviews Alerts

### Kurzbeschreibung
Neue Bewertung? Sofort Bescheid, schnell reagieren.

### Logik
- Google My Business API oder Scraping
- Neue Bewertung erkannt → Benachrichtigung
- Bei negativer Bewertung: Eskalation
- Response-Vorschlaege generieren

### Tech
- Google My Business API (falls Zugang)
- Alternativ: Scraping-Service

### Abhaengigkeiten
- **Standalone** - externes System

### Status
**Idee** - Einfach

---

## #50 Sanfte Zahlungserinnerung

### Kurzbeschreibung
Auto-Mail "Rechnung offen" bevor formelle Mahnung.

### Logik
- Rechnung faellig + X Tage (z.B. 14)
- Freundliche E-Mail-Erinnerung
- Antwort-Link fuer Rueckfragen
- Wenn keine Reaktion → normale Mahnung (#31)

### SQL-Kontext
- **Tabellen:** `dbo.Rechnung`, `dbo.Zahlung`, `dbo.Kunden`

### Abhaengigkeiten
- **Nutzt:** #31 Rechnungsbuch

### Status
**Idee** - Mittel

---

## #51 Cashflow-Prognose

### Kurzbeschreibung
Wann kommt Geld, wann geht's raus? Liquiditaets-Ampel.

### Logik
- Offene Forderungen mit erwartetem Zahlungseingang
- Geplante Ausgaben (Bestellungen, Gehaelter)
- Prognose 4-8 Wochen voraus
- Warnung bei kritischer Liquiditaet

### SQL-Kontext
- **Tabellen:** `dbo.Rechnung`, `dbo.Bestellung`, `dbo.Zahlung`

### Abhaengigkeiten
- **Nutzt:** #31 Rechnungsbuch, #33 Bestellwesen
- **Liefert an:** #14 Dashboard, #2 Bilanz

### Status
**Idee** - Anspruchsvoll

---

## #52 Conversion-Tracker

### Kurzbeschreibung
Wie viel % der Angebote werden Auftraege? Trend ueber Zeit.

### Logik
- Angebote zählen (pro Monat/Quartal)
- Daraus resultierende Auftraege zaehlen
- Conversion Rate berechnen
- Trend-Analyse: Wird's besser oder schlechter?
- Aufschluesselung nach Produktkategorie, Verkaeufer

### SQL-Kontext
- **Tabellen:** `dbo.Angebot`, `dbo.Auftrag`

### Abhaengigkeiten
- **Liefert an:** #14 Dashboard, #23 Verkaufschancen

### Status
**Idee** - Mittel

---

## #53 Mindestbestand-Alert

### Kurzbeschreibung
Warnung bei kritischem Lagerbestand (Silikon, Dichtungen, etc.)

### Logik
- Mindestbestand pro Artikel definieren
- Taeglich/stuendlich pruefen
- Bei Unterschreitung: Alert
- Automatischer Bestellvorschlag

### SQL-Kontext
- **Tabellen:** `dbo.Artikel`, `dbo.Lagerbestand`

### Abhaengigkeiten
- **Nutzt:** #38 Lagerverwaltung
- **Liefert an:** #33 Bestellwesen, #36 Beschaffungs-Dashboard

### Status
**Idee** - Mittel

---

## #54 Preis-Vergleich Lieferanten

### Kurzbeschreibung
Gleicher Artikel, verschiedene Lieferanten → bester Preis.

### Logik
- Artikel-Nummern verschiedener Lieferanten matchen
- Preise vergleichen (inkl. Rabatte, Staffeln)
- Empfehlung: Wo kaufen?
- Historischer Preisverlauf

### SQL-Kontext
- **Tabellen:** `dbo.Artikel`, `dbo.Lieferant`, `dbo.Bestellung`

### Abhaengigkeiten
- **Nutzt:** #1 Preislisten-Tool, #19 Lieferanten-Bewertung
- **Liefert an:** #33 Bestellwesen

### Status
**Idee** - Anspruchsvoll

---

## #55 Bestellvorlage mit Pflichtfeldern ⭐ PRIO

### Kurzbeschreibung
Verhindern dass Lieferwoche/Adresse bei Bestellung vergessen wird.

### Problem (Ist-Zustand)
- Roland/Vater bestellen ohne Lieferwoche → Ware zu frueh da
- Lieferadresse wird nicht geprueft → Falschlieferungen
- Aktuell keine Pflichtfeld-Validierung

### Loesung
Bestellformular/-pruefung mit:
1. **Pflichtfeld Lieferwoche (KW):** Muss ausgefuellt sein vor Absenden
2. **Lieferadresse automatisch:** Je Artikel-Typ (gross → Lager, klein → Buero)
3. **Warnung bei fehlenden Feldern**

### Implementierungs-Optionen
- **W4A Anpassung:** Pflichtfelder in Bestellmaske (falls moeglich)
- **Python-Checker:** Script das vor Versand prueft
- **Outlook-Regel:** E-Mail-Bestellung mit Template

### Abhaengigkeiten
- **Nutzt:** #33 Bestellwesen
- **Zusammen mit:** #57 Lieferadressen-Logik

### Status
**Idee** - Mittel | **Prioritaet:** 3 von 4 im Bestellprozess

---

## #56 AB-Abgleich automatisch ⭐ PRIO

### Kurzbeschreibung
Neue AB automatisch mit urspruenglicher Bestellung vergleichen.

### Problem (Ist-Zustand)
- Lieferant schickt AB per E-Mail (PDF)
- Haendischer Vergleich mit eigener Bestellung: Mengen, Masse, Preise
- Bei Korrektur: Neue AB kommt → wieder vergleichen
- Zeitaufwaendig, Fehler moeglich → Falschlieferungen

### Loesung
1. **PDF-Parsing:** AB extrahieren (Positionen, Mengen, Masse, Preise)
2. **Vergleich mit Bestellung:** Aus W4A oder eigener Bestelldatei
3. **Abweichungen markieren:** "Zeile 3: Breite 1200 statt 1000"
4. **Report:** Per E-Mail oder Dashboard

### Tech
- PDF-Parser (pdfplumber, camelot)
- LLM fuer unstrukturierte ABs
- Vergleichslogik

### Abhaengigkeiten
- **Nutzt:** #12 E-Mail-Verarbeitung (AB erkennen)
- **Liefert an:** #36 Beschaffungs-Dashboard (AB-Status)

### Offene Fragen
- [ ] Welche Lieferanten schicken strukturierte ABs?
- [ ] Gibt es Standard-AB-Formate?
- [ ] Wo liegt die eigene Bestellung? (W4A, E-Mail, Excel?)

### Status
**Idee** - Anspruchsvoll | **Prioritaet:** 2 von 4 im Bestellprozess

---

## #57 Lieferadressen-Logik ⭐ PRIO

### Kurzbeschreibung
Richtige Lieferadresse + Versandart automatisch je Artikel-Typ auswaehlen.

### Problem (Ist-Zustand)
- Falschlieferungen ins Buero statt Lager
- Grosse Teile (Fenster, Tueren) gehoeren ins Lager
- Paketdienste sollen aber ins Buero (immer besetzt)
- Aktuell: Manuelle Eingabe, wird oft falsch gemacht
- **NEU:** Versandart (Paket vs. LKW) wird vergessen umzustellen
- **NEU:** Externe Shops (Ammon) haben Adresse hinterlegt, wird trotzdem vergessen

### Loesung
Automatische Adress-Auswahl + Versandart nach Regel:
- **Gross (Spedition/LKW):** Fenster, Tueren, Rolllaeden → Lager-Adresse + LKW
- **Klein (Paketdienst):** Kleinteile, Beschlaege → Buero-Adresse + Paket
- **Mischbestellung:** Warnung + Aufteilen?

### Logik
```
WENN Artikel in Kategorie "Fenster", "Tueren", "Rolllaeden"
  DANN Lieferadresse = Lager
  UND Versandart = LKW/Spedition
SONST
  Lieferadresse = Buero
  UND Versandart = Paket
```

### Implementierung
| Kontext | Loesung |
|---------|---------|
| W4A Bestellmaske | Automatisch vorbelegen nach Artikelkategorie |
| Externe Shops (Ammon) | Checkliste/Reminder vor Bestellung |
| Pruefung | Warnung vor Absenden wenn Kombi unlogisch |

### Abhaengigkeiten
- **Nutzt:** Artikel-Kategorien aus W4A
- **Zusammen mit:** #55 Pflichtfelder

### Quelle
Lagerprozess-Analyse 2025-12-14

### Status
**Idee** - Einfach | **Prioritaet:** 1 von 4 im Bestellprozess (WICHTIGSTE!)

---

## Komplexitaets-Uebersicht

| Stufe | Tools |
|-------|-------|
| 🟢 Einfach | #4 ✓, #29, #49, #57 |
| 🟡 Mittel | #1, #3, #6, #9, #10, #13, #15, #16, #19, #23, #24, #28, #31, #33, #36, #37, #38, #39, #40, #43, #47, #50, #53, #55, #58, #59, #60 |
| 🟠 Anspruchsvoll | #2, #11, #12, #14, #17, #18, #22, #25, #26, #27, #30, #32, #34, #35, #41, #42, #44, #51, #52, #54, #56 |
| 🔴 Komplex | #5, #7, #8, #20, #21 |
| ⚫ Merged | #45→#23, #46→#24, #48→#47, #61→#28 |

---

## Empfohlene Reihenfolge (NEU: Nach Abhaengigkeiten)

**Phase 0 (INFRASTRUKTUR - ZUERST!):** #58 Web-Plattform, #59 DB-Connector, #60 Auth
**Phase 1 (Basis-Module):** #1 Preislisten, #13 Inventar, #57 Lieferadressen, #39/#40 Montage-Mappe
**Phase 2 (Kernprozesse):** #9, #10, #11, #36, #55, #56
**Phase 3 (Kommunikation):** #6, #12
**Phase 4 (Command Center):** #14 (integriert #36, #44, #51, #52)
**Phase 5 (KI-Features):** #5, #7, #8

---

## Phase 0: Infrastruktur (Details)

### #58 Web-Plattform Grundgeruest

**Zweck:** Basis fuer alle Tools - muss ZUERST gebaut werden!

### Was brauchen wir?
| Komponente | Tech-Empfehlung | Begruendung |
|------------|-----------------|-------------|
| Backend | Python Flask oder FastAPI | Python schon vorhanden (WinPython) |
| Frontend | Bootstrap 5 | Responsive ohne Aufwand |
| Templating | Jinja2 (in Flask enthalten) | Einfach, bewaehrt |
| Hosting | Lokal + Cloudflare Tunnel | Tunnel existiert, keine Kosten |

### Grund-Struktur
```
js-fenster-tools/
├── app.py                 # Haupt-Anwendung
├── config.py              # Konfiguration
├── templates/
│   ├── base.html          # Basis-Layout (Nav, Footer)
│   ├── index.html         # Startseite/Dashboard
│   └── modules/           # Module-Templates
├── static/
│   ├── css/               # Styles
│   └── js/                # JavaScript
└── modules/               # Tool-Module als Python-Packages
```

### Features (Minimum)
- Startseite mit Navigation
- Responsive Layout (Mobile-first)
- Modul-Architektur (jedes Tool = ein Modul)
- Einheitliches Look & Feel

### Abhaengigkeiten
- **Voraussetzung fuer:** ALLE anderen Tools!
- **Baut auf:** Nichts (Grundlage)

### Status
**Idee** - Mittel | **Prioritaet:** ⭐⭐ MUSS ZUERST!

---

### #59 Datenbank-Connector

**Zweck:** Sichere, wiederverwendbare Verbindung zu W4A SQL Server

### Bereits vorhanden
- Grundlagen in `ki_wissen_updater.py` (pyodbc)
- Tunnel-Setup in CLAUDE.md dokumentiert

### Zu erweitern
| Feature | Beschreibung |
|---------|--------------|
| Connection-Pool | Mehrere parallele Verbindungen |
| Sichere Credentials | Nicht im Code, sondern .env |
| Query-Builder | Einfache SELECT/INSERT ohne SQL-Strings |
| Logging | Wer hat wann was abgefragt? |

### Beispiel-Nutzung
```python
from db_connector import get_connection, query

# Einfache Abfrage
kunden = query("SELECT * FROM dbo.Kunden WHERE Ort = ?", ["Musterstadt"])

# Mit Context-Manager
with get_connection() as conn:
    cursor = conn.cursor()
    cursor.execute("SELECT COUNT(*) FROM dbo.Auftrag")
```

### Sicherheits-Regeln
- SELECT: Immer erlaubt
- INSERT: Nur in definierte Tabellen (Whitelist)
- UPDATE/DELETE: NIE auf Stammdaten!

### Abhaengigkeiten
- **Nutzt:** #58 Web-Plattform
- **Voraussetzung fuer:** Alle Tools die DB brauchen

### Status
**Idee** - Mittel | **Prioritaet:** ⭐⭐ MUSS ZUERST!

---

### #60 Auth & Berechtigungen

**Zweck:** Wer darf was sehen? Login-System.

### Warum wichtig?
| Rolle | Sieht | Sieht NICHT |
|-------|-------|-------------|
| GF | Alles | - |
| Buero | Auftraege, Bestellungen | Finanzkennzahlen |
| Monteur | Eigene Auftraege | Andere Kunden, Finanzen |

### Implementierung (einfach)
- Username/Passwort in lokaler DB
- Session-basiert (Flask-Login)
- Rollen: admin, buero, monteur

### Spaeter moeglich
- AD-Integration (Windows-Login)
- 2FA fuer sensible Bereiche
- Audit-Log (wer hat was wann gesehen)

### Abhaengigkeiten
- **Nutzt:** #58 Web-Plattform, #59 DB-Connector
- **Voraussetzung fuer:** Sensible Module (Finanzen, KPIs)

### Status
**Idee** - Mittel | **Prioritaet:** ⭐⭐ MUSS VOR FINANZEN!

---

### #14 Command Center (erweitert)

**Zweck:** EIN zentrales Dashboard fuer alles - nicht viele einzelne!

### Struktur
```
┌─────────────────────────────────────────────────────────┐
│  🔴 3 Alerts                        JS Fenster Dashboard │
├─────────────────────────────────────────────────────────┤
│  [Heute]  [Bestellungen]  [Montage]  [Finanzen]  [KPIs] │
├─────────────────────────────────────────────────────────┤
│  Tab-Inhalt je nach Auswahl...                          │
└─────────────────────────────────────────────────────────┘
```

### Tabs & Integrierte Tools
| Tab | Zeigt | Integriert |
|-----|-------|------------|
| Heute | Tagesgeschaeft, dringende Items | Alerts aller Module |
| Bestellungen | Offene, ohne AB, ueberfaellig | #36 Beschaffungs-Dashboard |
| Montage | Termine, Status, Material | #39/#40 Montage-Mappe |
| Finanzen | Offene Rechnungen, Cashflow | #51 Cashflow |
| KPIs | Kennzahlen, Trends, Conversion | #52 Conversion |

### Vorteile
- **Eine Anlaufstelle** statt 5 verschiedene Dashboards
- **Tabs fuer Fokus** - je nach aktuellem Bedarf
- **Alerts ueberall sichtbar** - kritisches oben
- **Modular erweiterbar** - neue Tabs spaeter

### Abhaengigkeiten
- **Nutzt:** #58 Web, #59 DB, #60 Auth
- **Integriert:** #36, #44, #51, #52 als Sub-Module
- **Baut auf:** Alle Basis-Module muessen erst existieren

### Status
**Idee** - Anspruchsvoll | **Phase:** 4 (erst wenn Basis steht)

---

## #61 ~~Mobiles Aufmass-Formular~~ → merged in #28

*Integriert in #28 Digitales Aufmass + Zubehoer + Mobiles Formular*

---

## #62 Ersatzteil-Erkennung (KI-Vision)

### Kontext (User)
- Bei Reparaturauftraegen: "Was ist das fuer ein Teil?"
- Alte Beschlaege, Griffe, Dichtungen identifizieren
- Manuell: Kataloge waelzen, Lieferanten anrufen

### Technische Umsetzung
- **Input:** Foto vom defekten Teil
- **KI:** Claude Vision / GPT-4V analysiert Bild
- **Matching:** Vergleich mit Artikelstamm (Bilder + Beschreibungen)
- **Output:** "Das koennte XY sein" + Bestellvorschlag

### SQL-Kontext
- `dbo.Artikel` - Artikelstamm mit Bezeichnungen
- `dbo.ArtikelBild` - Falls Bilder hinterlegt (pruefen!)
- Evtl. Lieferanten-Kataloge als zusaetzliche Quelle

### Verknuepfungen
- **Braucht:** #58 Web-Plattform, #59 DB-Connector
- **Ergaenzt:** #9 Reparatur-Verwaltung
- **Nutzt:** KI-API (Claude Vision)

### Status
**Idee** - Komplex (KI-Vision) | **Phase:** 5

---

## #63 Fassaden-Budget (KI-Vision)

### Kontext (User)
- Kunde fragt: "Was kostet neue Fenster fuers ganze Haus?"
- Aktuell: Aufmass-Termin noetig fuer jede Schaetzung
- Wunsch: Grobe Richtung aus Foto der Fassade

### Technische Umsetzung
- **Input:** Foto von Hausfassade
- **KI-Analyse:**
  1. Fenster/Tueren zaehlen
  2. Groessen grob schaetzen (relativ zu Fassade)
  3. Typ erkennen (Dreh-Kipp, Festverglasung, etc.)
- **Kalkulation:**
  - Durchschnittspreise je Groessenklasse
  - Aufschlag fuer Extras (Rollladen, besondere Farben)
- **Output:** "ca. 12.000-18.000€" als Budgetrahmen

### Wichtig
- **Nur Richtwert!** - Kein verbindliches Angebot
- **Disclaimer:** "Genaue Preise nach Aufmass"
- **Nutzen:** Erstgespraech, Leadqualifizierung

### Verknuepfungen
- **Braucht:** #58 Web-Plattform, KI-API
- **Ergaenzt:** #6 Budget-Angebots-Generator
- **Fuehrt zu:** Aufmass-Termin wenn Kunde interessiert

### Status
**Idee** - Komplex (KI-Vision) | **Phase:** 5

---

## #64 Data Service Layer

### Kontext
- 8 Tools greifen auf `dbo.Bestellung` zu (Konfliktpotential!)
- 7 Tools greifen auf `dbo.Auftrag` zu
- Ohne zentrale Schicht: Chaos bei parallelen Zugriffen

### Technische Umsetzung
```python
# Zentrale Services statt direkter DB-Zugriff
class BestellungService:
    cache_ttl = 300  # 5min fuer Stammdaten

    def get_offene_bestellungen(self):
        # Cache pruefen, sonst DB

    def on_change(self, bestellung_id):
        # Cache invalidieren, Events feuern
```

### Architektur
```
Tools (#14, #36, #56...) → Service Layer → Cache → DB Connector → SQL Server
```

### Caching-Strategie
| Daten-Typ | TTL | Grund |
|-----------|-----|-------|
| Stammdaten (Kunden, Artikel) | 5min | Aendern sich selten |
| Live-Daten (Bestellungen) | 30s | Muessen aktuell sein |
| Montage-Status | WebSocket | Echtzeit noetig |

### Verknuepfungen
- **Braucht:** #59 DB-Connector
- **Basis fuer:** #14 Command Center, alle Dashboards
- **Teil von:** Phase 0 Infrastruktur

### Status
**Idee** - Mittel | **Phase:** 0 (Infrastruktur)

---

## #65 Anzahlungsrechnung-Automatismus

### Kurzbeschreibung
Erinnerung/Automatismus fuer Anzahlung vor Bestellung. Verhindert Cashflow-Probleme.

### Problem (IST-Zustand)
- Anzahlung wird oft vergessen bei Auftraegen anzugeben
- Bestellung geht raus ohne dass Anzahlung gestellt/bezahlt wurde
- Cashflow-Problem: Material wird bestellt, Geld kommt erst spaeter
- Risiko bei Stornierung: Firma bleibt auf Kosten sitzen

### Loesung
1. **Pflichtfeld bei Bestellung:** Vor Bestellversand pruefen ob Anzahlung gestellt
2. **Automatische Erinnerung:** Bei Auftragserstellung Anzahlung vorschlagen
3. **Report:** Uebersicht unbezahlte Anzahlungen
4. **Schwellenwert:** Ab Auftragswert X automatisch Anzahlung erforderlich

### Logik
| Auftragswert | Anzahlung |
|--------------|-----------|
| < 500 EUR | Optional |
| 500 - 2000 EUR | Empfohlen (Hinweis) |
| > 2000 EUR | Pflicht (Warnung bei Bestellung ohne) |

### SQL-Kontext
- **Tabellen:** `dbo.Auftrag`, `dbo.Rechnung` (Anzahlungsrechnung)
- **Pruefen:** Hat Auftrag eine Anzahlungsrechnung? Ist diese bezahlt?

### Implementierung
- **Einfach:** Warnung bei Bestellung wenn keine Anzahlung
- **Mittel:** Report unbezahlter Anzahlungen
- **Erweitert:** Auto-Generierung Anzahlungsrechnung bei Auftragserstellung

### Abhaengigkeiten
- **Verknuepft:** #33 Bestellwesen, #55 Bestellvorlage
- **Nutzt:** #31 Rechnungsbuch (fuer Zahlungsstatus)

### Quelle
Bestellprozess-Analyse 2025-12-11 - Andreas: "Wird von mir und allen oft vergessen"

### Status
**Idee** - Mittel | **Phase:** 2 (Kernprozesse) | **Prioritaet:** Hoch (Cashflow!)

---

## #66 Montageplanung mit Wetterprognose

### Kurzbeschreibung
Montage-Termine automatisch mit Wetterdaten abgleichen. Warnung bei kritischem Wetter.

### Problem (IST-Zustand)
- Aussenmontagen bei Regen/Sturm = schlecht fuer Qualitaet + Mitarbeiter
- Termine werden ohne Wetter-Check vergeben
- Erst am Tag selbst merkt man: "Heute regnet es, verschieben wir"
- Kunde wartet, Planung durcheinander

### Loesung
1. **Wetter-API anbinden:** 7-Tage-Prognose fuer Montage-Orte
2. **Automatische Warnung:** Bei Terminerstellung/Tagesplan
3. **Verschiebe-Empfehlung:** Alternative Tage vorschlagen
4. **Unterscheidung:** Innen- vs. Aussenmontage (nur Aussen relevant)

### Wetter-Kriterien
| Bedingung | Warnstufe | Aktion |
|-----------|-----------|--------|
| Regen > 2mm/h | 🟡 Gelb | Hinweis: "Regen erwartet" |
| Regen > 5mm/h | 🔴 Rot | Warnung: "Stark Regen - verschieben!" |
| Wind > 50km/h | 🔴 Rot | Warnung: "Sturm - keine Aussenmontage!" |
| Temperatur < 0°C | 🟡 Gelb | Hinweis: "Frost - Silikon-Verarbeitung kritisch" |
| Schnee | 🔴 Rot | Warnung: "Schnee - verschieben!" |

### Technische Umsetzung
```python
# Wetter-Check bei Terminplanung
def check_montage_wetter(termin_datum, plz):
    wetter = openweathermap_api.forecast(plz, termin_datum)

    if wetter.regen > 5 or wetter.wind > 50:
        return {"warnung": "rot", "empfehlung": "verschieben"}
    elif wetter.regen > 2 or wetter.temp < 0:
        return {"warnung": "gelb", "empfehlung": "pruefen"}
    return {"warnung": "gruen", "empfehlung": "ok"}
```

### API-Optionen
| API | Kosten | Calls/Tag | Empfehlung |
|-----|--------|-----------|------------|
| OpenWeatherMap | Gratis | 1000 | ✅ Fuer Start |
| WeatherAPI.com | Gratis | 1000 | Alternative |
| DWD Open Data | Gratis | Unbegrenzt | Genaueste fuer DE |

### Features
- 🌧️ Alert: "Montage am Mi 15.12. - Regen erwartet, verschieben?"
- ⛈️ Automatische Empfehlung: "Alternative: Do/Fr trocken"
- 📊 Planungs-Ansicht: Kalender mit Wetter-Overlay
- 🏠 Montageart-Flag: Innen/Aussen bei Termin hinterlegen

### Abhaengigkeiten
- **Braucht:** #11 Terminfindung (Termine aus DB lesen)
- **Ergaenzt:** #22 Routenplanung (Wetter auf Route beruecksichtigen)
- **Nutzt:** #39 Montage-Mappe (Wetter-Hinweis auf Briefing)

### Implementierung
1. **Einfach:** Taeglich morgens Wetter-Check fuer kommende Woche, E-Mail bei Warnung
2. **Mittel:** Integration in Termin-Ansicht, Ampel-Anzeige
3. **Erweitert:** Auto-Verschiebe-Vorschlaege, Kunden-Benachrichtigung

### Status
**Idee** - Mittel | **Phase:** 2 (Kernprozesse) | **Prioritaet:** Normal

---

## #67 XML-Konverter (Universal → W4A)

### Kurzbeschreibung
Universeller Konverter: Bestehende XML anpassen oder aus Text-Dokumenten XML fuer W4A-Import generieren.

### Problem (IST-Zustand)
- Verschiedene Quellen liefern XML in unterschiedlichen Formaten
- W4A erwartet spezifisches XML-Schema fuer Import
- Manuelle Anpassung zeitaufwaendig und fehleranfaellig
- Textdokumente (strukturierte Daten) muessen haendisch in W4A eingegeben werden

### Loesung
1. **XML-Transformation:** Beliebige XML → W4A-kompatibles XML
2. **Text-zu-XML:** Strukturierte Textdaten → XML generieren
3. **Template-System:** Wiederverwendbare Mappings fuer verschiedene Quellen
4. **Validierung:** Pruefen ob Output W4A-konform ist

### Technische Umsetzung
```python
# Beispiel-Workflow
def convert_to_w4a(input_file, template):
    if input_file.endswith('.xml'):
        data = parse_xml(input_file)
    else:
        data = parse_text(input_file)  # CSV, TXT, etc.

    # Mapping anwenden
    w4a_data = apply_template(data, template)

    # Validieren
    validate_w4a_schema(w4a_data)

    # Output
    return generate_w4a_xml(w4a_data)
```

### Features
- **Auto-Mapping:** Feldnamen intelligent zuordnen
- **Vorschau:** Transformiertes XML vor Import anzeigen
- **Batch-Verarbeitung:** Mehrere Dateien auf einmal
- **Template-Editor:** Eigene Mappings definieren
- **Fehler-Report:** Zeigt was nicht konvertiert werden konnte

### Abhaengigkeiten
- **Verwandt:** #37 WoT-XML Transformer (speziell fuer Weru)
- **Nutzt:** #58 Web-Plattform (GUI), #59 DB-Connector (Schema-Info)

### Offene Fragen
- [ ] Welche XML-Quellen sind relevant? (Lieferanten, andere Konfiguratoren?)
- [ ] W4A-Import-Schema dokumentiert?
- [ ] Welche Textformate? (CSV, strukturierte TXT?)
- [ ] GUI oder CLI?

### Status
**Idee** - Mittel | **Phase:** 2 (Kernprozesse)

---

## #68 Zentrales Planungs-Dashboard

> **Phase:** 0 (Infrastruktur) | **Komplexitaet:** Mittel | **Status:** NEU

### Problem
Outlook-Kalender wird in 3 Prozessen als "Planungs-Dashboard" missbraucht:
- **Montage:** Kacheln fuer Auftraege, Status, Kategorien
- **Reparatur:** Status-Tracking fuer Reparatur-Vorgaenge
- **Bestellung:** Abholungen, Liefertermine

Outlook ist dafuer nicht gedacht → unuebersichtlich, fehleranfaellig, Info geht verloren.

### Loesung
EIN zentrales Planungs-Dashboard das Outlook ersetzt:
- Montage-Planung (Teams, Termine, Status)
- Reparatur-Tracking (Stefan's Tagesablauf)
- Abholungen/Lieferungen (aus Bestellprozess)
- Kalender-Ansicht + Kanban-Ansicht

### Kernfunktionen
1. **Tages-/Wochen-/Monatsansicht** wie Outlook, aber besser
2. **Drag & Drop** Termine verschieben
3. **Farbkodierung** nach Typ (Montage, Reparatur, Abholung)
4. **Filter** nach Team, Status, Kunde
5. **W4A-Integration** Daten aus/nach ERP synchronisieren

### Technische Umsetzung
- Baut auf #58 Web-Plattform auf
- Nutzt #59 DB-Connector
- Kalender-Komponente (FullCalendar.js oder aehnlich)
- Echtzeit-Updates (WebSocket oder Polling)

### Abhaengigkeiten
- **Voraussetzung:** #58 Web-Plattform, #59 DB-Connector
- **Ergaenzt:** #11 Terminfindung, #36 Beschaffungs-Dashboard
- **Nutzer:** Susann (Montage), Buero (Reparatur), Lager (Abholungen)

### Offene Fragen
- [ ] Outlook komplett ersetzen oder parallel laufen?
- [ ] Mobile Ansicht noetig?
- [ ] Benachrichtigungen (Push, E-Mail)?
- [ ] Sync mit privatem Kalender?

### Status
**NEU** - Mittel | **Phase:** 0 (Infrastruktur - frueh implementieren!)

---

## Standalone-Tools

---

## #69 UTA-Tankrechnungen PDF-Tool

### Kurzbeschreibung
UTA-Tankrechnungen (PDFs) analysieren, nach Land splitten und laenderspezifische Sammel-PDFs erstellen.

### Problem (IST-Zustand)
- UTA schickt Tankrechnungen als PDFs
- Rechnungen enthalten Tankungen aus verschiedenen Laendern (Deutschland, Oesterreich, Polen, etc.)
- Fuer Buchhaltung/Steuer muessen diese nach Land getrennt werden
- Aktuell: Manuelles Durchgehen und Sortieren

### Loesung
1. **PDF-Analyse:** Rechnungs-PDF einlesen, Positionen extrahieren
2. **Land erkennen:** Aus Tankstellen-Adresse oder Waehrung Land ableiten
3. **Splitten:** Positionen nach Land gruppieren
4. **Sammel-PDF:** Pro Land eine zusammengefasste PDF erstellen

### Technische Umsetzung
```python
# Beispiel-Workflow
def process_uta_invoice(pdf_path):
    positions = extract_positions(pdf_path)  # pdfplumber

    by_country = {}
    for pos in positions:
        country = detect_country(pos)  # DE, AT, PL, etc.
        by_country.setdefault(country, []).append(pos)

    for country, items in by_country.items():
        generate_country_pdf(country, items)
```

### Tech-Stack
- **PDF-Parsing:** pdfplumber, PyPDF2
- **PDF-Generierung:** reportlab oder fpdf
- **Optional:** OCR falls PDFs nicht text-basiert (pytesseract)

### Features
- Drag & Drop Upload
- Vorschau der erkannten Positionen
- Manuelle Korrektur falls Land falsch erkannt
- Batch-Verarbeitung mehrerer Rechnungen
- Export: Einzelne PDFs pro Land oder eine PDF mit Kapiteln

### Offene Fragen
- [ ] Wie sehen die UTA-PDFs aus? (Struktur, Text oder Bild?)
- [ ] Welche Laender kommen vor?
- [ ] Output-Format: Separate PDFs oder eine mit Trennblaettern?
- [ ] Soll Summe pro Land berechnet werden?

### Abhaengigkeiten
- **Standalone** - kein ERP-Bezug
- **Optional:** Web-UI (#58) oder CLI-Tool

### Status
**Idee** - Einfach-Mittel | **Phase:** Standalone

---

## #70 Montagematerial-Pauschalen-Automatik

> **Phase:** Standalone/Kernprozesse | **Komplexitaet:** Mittel | **Status:** NEU

### Kurzbeschreibung
Automatische Materialpauschale fuer Nicht-Fenster-Produkte (Innentuer, Markise, Raffstore, etc.). Verhindert Umsatzverlust durch vergessene Materialberechnung.

### Problem (IST-Zustand)
| Produkt | Automation | Status |
|---------|------------|--------|
| **Fenster** | WoT berechnet automatisch (aber veraltet) | ⚠️ Nicht aktuell |
| **Innentuer** | KEINE Automation | ❌ Wird vergessen |
| **Markise** | KEINE Automation | ❌ Wird vergessen |
| **Raffstore** | KEINE Automation | ❌ Wird vergessen |
| **Sonstige** | KEINE Automation | ❌ Wird vergessen |

**Folge:** Montagematerial wird verbraucht aber nicht berechnet → Umsatzverlust!

**Zusaetzliches Problem - Lager-Buchung:**
| Aspekt | Details |
|--------|---------|
| Material-Buchung | Geht aufs LAGER, nicht aufs Projekt |
| Grund | 1 Karton Kompriband reicht fuer ~30 Fenster |
| Folge | Verbrauch pro Projekt NICHT direkt trackbar |
| Loesung | Indirekte Analyse ueber Zeitraeume |

**Aktuelle Datenquelle:**
- Excel: `Montagematerial lfm.xlsx` (noch ausbaufaehig)
- Enthaelt: Laufmeter-basierte Berechnung fuer WoT

### Loesung (3 Stufen)

**Stufe 1 - Analyse (Zeitraum-basiert):**
- Zeitraum waehlen (z.B. letzte 12 Monate)
- Material-Bestellungen summieren (Kompriband, Schaum, Schrauben, etc.)
- Produkte mit Massen aus Auftraegen zaehlen (Anzahl Fenster, lfm Tuer, m² Markise)
- Durchschnitt berechnen: Material-Kosten ÷ Produkt-Menge = €/Einheit
- Formel erstellen: z.B. "Innentuer = X € pro lfm"

**WICHTIG:** Da Material aufs Lager gebucht wird, ist nur Zeitraum-Analyse moeglich (nicht pro Projekt)

**Stufe 2 - Automatik (dauerhaft):**
- Bei Angebot/Rechnung → System schlaegt Materialpauschale vor
- ALLE Produkte (inkl. Fenster!) - nicht nur WoT
- Grund: Eigene Berechnung ist AKTUELLER als WoT-Formel
- Kann nicht vergessen werden

**Stufe 3 - Preisanpassung (bei Bedarf):**
- Bei Material-Preiserhoehung → Faktoren automatisch anpassen
- Hinweis: "Kompriband +10% teurer → Pauschalen aktualisieren?"
- Quartalsweise IST vs. SOLL Vergleich
- Dashboard: Abweichungen sichtbar machen

### Datenquellen
| Quelle | Inhalt | Nutzung |
|--------|--------|---------|
| Einkaufsrechnungen | Material-Kosten (Schaum, Schrauben, etc.) | IST-Kosten ermitteln |
| W4A Auftraege | Produkttyp, Groesse, Menge | Korrelation finden |
| WoT-Formel | Fenster-Laufmeter-Berechnung | Als Referenz/Vorbild |

### Technische Umsetzung
```python
# Stufe 1: Analyse
def analyse_material_costs():
    einkauf = get_material_purchases(last_12_months)
    auftraege = get_orders(last_12_months)

    # Gruppieren nach Produkttyp
    for produkttyp in ['Innentuer', 'Markise', 'Raffstore']:
        auftraege_typ = filter_by_type(auftraege, produkttyp)
        material_anteil = calculate_material_share(einkauf, auftraege_typ)
        pauschale = material_anteil / len(auftraege_typ)
        print(f"{produkttyp}: {pauschale:.2f} EUR pro Stueck")

# Stufe 2: Automatik
def add_material_pauschale(rechnung):
    for position in rechnung.positionen:
        if position.produkttyp not in ['Fenster']:  # Fenster hat WoT
            pauschale = get_pauschale(position.produkttyp)
            rechnung.add_position("Montagematerial", pauschale)
```

### Erweiterungen (optional)
- **Groessenabhaengig:** Pauschale nach Produktgroesse staffeln
- **Ausfuehrungsabhaengig:** Unterschiedliche Pauschale je Montage-Art
- **Saisonabhaengig:** Material-Preisschwankungen beruecksichtigen

### Abhaengigkeiten
- **Nutzt:** W4A Auftragsdaten, Einkaufsrechnungen
- **Verknuepft:** #39 Montage-Mappe (Material-Rueckmeldung)
- **Liefert an:** Rechnungserstellung

### Offene Fragen
- [x] Material projektbezogen trackbar? → NEIN, geht aufs Lager (Zeitraum-Analyse noetig)
- [x] Produkte mit Massen erfasst? → JA, in Textform
- [ ] Wo liegen die Einkaufsrechnungen? (W4A, Dateisystem, Excel?)
- [ ] Wie sind Produkttypen in W4A klassifiziert? (Artikelgruppen?)
- [ ] Soll Pauschale pro Stueck, pro Laufmeter, oder pro m²?
- [ ] Welche Material-Artikel gehoeren zu "Montagematerial"? (Artikelnummern?)
- [ ] Wie wird Pauschale in Angebot/Rechnung eingefuegt? (W4A-Automatik oder Tool?)

### Quelle
- Lagerprozess-Brainstorming 2025-12-14 - Problem: Material fuer Nicht-Fenster wird vergessen
- Brainstorming 2025-12-16 - Erweiterung: Zeitraum-Analyse, Preisanpassung, alle Produkte

### Status
**Idee** - Mittel | **Phase:** Standalone/Kernprozesse | **Prioritaet:** Hoch (Umsatzverlust!)

---

## #71 Einkaufs-Workflow & Preismanagement

> **Phase:** Kernprozesse | **Komplexitaet:** Mittel | **Status:** NEU

### Kurzbeschreibung
Zentrales Tool fuer Einkaufs-Workflow: Preisanfragen tracken, Konditionen verwalten, Grossmengen-Erinnerungen. Loest das Problem der wochenlangen Wartezeiten auf Preise.

### Problem (IST-Zustand)

| Problem | Auswirkung | Haeufigkeit |
|---------|------------|-------------|
| **Preisanfragen dauern Tage/Wochen** | Angebote verzoegern sich, Kunde wartet | Oft |
| **Wuerth: Staendige AD-Anfragen** | Zeitverlust trotz existierendem Shop | Bei jeder Bestellung |
| **Grossmengen-Rabatt vergessen** | Geld verschenkt | Manchmal |
| **Konditionen verstreut** | W4A-Dokumente + Artikel + Excel | Dauerhaft |
| **Keine Uebersicht offener Anfragen** | Anfragen "versanden" | Regelmaessig |
| **Preiserhoehungen per Post** | Nicht alle informiert → falsche Preise in Angeboten | Gelegentlich |

**NEU (2025-12-16):** Preiserhoehungen kommen manchmal per Brief statt E-Mail (Bsp: Weru TZ). Dadurch wissen nicht alle relevanten Personen Bescheid → Feature "Preisinfo-Verteiler" noetig!

### Loesung (Features)

**1. Preis-Cache:**
- Letzte Preise pro Artikel/Lieferant speichern
- Bei Bedarf direkt aus Cache → keine Anfrage noetig
- Gueltigkeitsdatum (z.B. 3 Monate) → Auto-Refresh-Hinweis

**2. Preisanfrage-Tracking:**
- Status: Angefragt → Beantwortet → Ueberfaellig
- Dashboard: Offene Anfragen auf einen Blick
- Erinnerung nach X Tagen: "Nachfassen bei Lieferant Y!"
- Historie: Wann was angefragt

**3. Grossmengen-Erinnerung:**
- Regel: "Bei >X Stueck von Artikel Y → Sonderpreis anfragen!"
- Beim Bestellen: Automatischer Hinweis
- Konfigurierbar pro Artikel/Lieferant

**4. Konditionen zentral:**
- Alle Rabatte, Staffeln, Rahmenvertraege an EINEM Ort
- Ersetzt: W4A-Dokumente + W4A-Artikel + Excel
- Schnelle Suche: "Was haben wir mit Wuerth vereinbart?"

**5. Lieferanten-Quick-Info:**
- Kontaktdaten, Ansprechpartner
- Letzte Bestellungen
- Offene Anfragen
- Link zu Portal (wenn vorhanden)

**6. Preisinfo-Verteiler (NEU 2025-12-16):**

| Stufe | Loesung | Aufwand |
|-------|---------|---------|
| **Vollautomatisch** | Scan → OCR → KI erkennt "Preiserhoehung" → Auto-Verteiler | Hoch |
| **Halbautomatisch** | Scan hochladen → Typ waehlen → Auto-E-Mail an Verteiler | Mittel |
| **Assistiert** | Formular: Lieferant, Aenderung, Datum → Auto-E-Mail | Gering |

**Empfaenger-Verteiler:**
- Verkauf: Roland, Andreas, Enrico
- Projektleiter: Jaroslaw, Andreas
- Lagerist: Mario

**Features:**
- Empfaenger-Gruppen konfigurierbar
- Auto-Benachrichtigung: "Weru TZ geaendert ab [Datum]"
- Dokument wird automatisch archiviert
- Historie: Wann wurde was geaendert?

### Datenquellen

| Quelle | Inhalt | Nutzung |
|--------|--------|---------|
| W4A Artikel | Einkaufspreise, Lieferanten | Basis-Preise |
| W4A Dokumente | Rahmenvertraege | Konditionen |
| Excel (aktuell) | Zusaetzliche Konditionen | Migration |
| E-Mails | Preisanfragen/-antworten | Tracking |

### Lieferanten-Portale (bekannt)

| Lieferant | Portal | Besonderheit |
|-----------|--------|--------------|
| Weru | Ja (neu in Arbeit) | Hauptlieferant Fenster |
| Wuerth | Ja | Rabatte nicht hinterlegt! |
| Foerch | Ja | |
| Gruen Beschlaege | Ja | |
| Febes | Ja | |
| Warema | Ja | Sonnenschutz |
| Kadeco | Ja | |
| Kompotherm | Ja | |
| Trendtueren | Ja | |

### Technische Umsetzung

```python
# Preis-Cache Struktur
class PreisCache:
    artikel_id: int
    lieferant_id: int
    preis: Decimal
    gueltig_ab: date
    gueltig_bis: date  # Auto-Refresh nach Ablauf
    quelle: str  # "Preisliste", "Anfrage", "Portal"

# Preisanfrage-Tracking
class Preisanfrage:
    id: int
    lieferant_id: int
    artikel_liste: List[int]
    angefragt_am: date
    beantwortet_am: Optional[date]
    status: str  # "offen", "beantwortet", "ueberfaellig"
    erinnerung_nach_tagen: int = 7

# Grossmengen-Regel
class GrossmengenRegel:
    artikel_id: int
    lieferant_id: int
    ab_menge: int
    hinweis: str  # "Bei >100 Stueck Staffelpreis anfragen!"
```

### Abhaengigkeiten

- **Nutzt:** #59 DB-Connector, W4A Artikeldaten
- **Ergaenzt:** #19 Lieferanten-Bewertung (Qualitaet), #54 Preis-Vergleich
- **Liefert an:** #33 Bestellwesen, #36 Beschaffungs-Dashboard

### Abgrenzung zu anderen Ideen

| Idee | Fokus | Abgrenzung zu #71 |
|------|-------|-------------------|
| #19 Lieferanten-Bewertung | Retrospektive Bewertung nach Lieferung | #71 = Proaktiver Workflow |
| #54 Preis-Vergleich | Vergleich gleicher Artikel | #71 = Anfrage-Management |
| #33 Bestellwesen | Bedarfsermittlung → Bestellung | #71 = Lieferanten-Seite |

### Quick Wins (ohne Tool)

| Massnahme | Aufwand |
|-----------|---------|
| Wuerth-Rabatte einmalig komplett anfragen | Mittel |
| Excel-Konditionen nach W4A migrieren | Mittel |
| Preislisten-Import vereinfachen | Gering |

### Offene Fragen

- [ ] Koennen Wuerth-Rabatte dauerhaft hinterlegt werden?
- [ ] Welche Lieferanten-Portale haben APIs?
- [ ] Soll Preisanfrage-Tracking per E-Mail oder separates Tool?
- [ ] Wie oft aendern sich Konditionen realistisch?

### Quelle
Einkaufsprozess-Brainstorming 2025-12-14 - Schmerzpunkte: Preisanfragen, Wuerth, Grossmengen

### Status
**Idee** - Mittel | **Phase:** Kernprozesse | **Prioritaet:** Mittel

---

## #72 Referenz-Automatik

> **Phase:** Kommunikation | **Komplexitaet:** Einfach-Mittel | **Status:** NEU

### Kurzbeschreibung
Automatisierte Erinnerung nach abgeschlossener Montage: "Schoenes Projekt - Fotos fuer Website machen?" Workflow fuer Referenz-Pflege auf js-fenster.de.

### Problem (IST-Zustand)

| Problem | Auswirkung |
|---------|------------|
| **Referenzen werden vergessen** | Website veraltet, keine aktuellen Projekte |
| **Kein Trigger** | Niemand denkt dran nach Montage |
| **Schoene Projekte nicht dokumentiert** | Marketing-Potential verschenkt |
| **Keine Kunden-Erlaubnis eingeholt** | Rechtlich unsicher |

### Loesung (Features)

**1. Auto-Trigger nach Montage:**
- Montage abgeschlossen in System → Check: "Referenz-wuerdig?"
- Kriterien: Grosses Projekt, interessantes Produkt, gute Ausfuehrung
- Erinnerung an Projektleiter: "Fotos machen?"

**2. Foto-Workflow:**
- Checkliste: Welche Fotos (Aussen, Innen, Detail)?
- Hochladen direkt in Referenz-Ordner
- Auto-Zuordnung zu Projekt

**3. Kunden-Einverstaendnis:**
- Template E-Mail: "Duerfen wir Ihr Projekt als Referenz zeigen?"
- Tracking: Erlaubnis erhalten? Ja/Nein
- Ohne Erlaubnis → Keine Veroeffentlichung

**4. Website-Workflow:**
- Gesammelte Referenzen → Export fuer Website
- Kategorien: Fenster, Haustueren, Sonnenschutz, etc.
- Beschreibungstext-Vorlage

### Technische Umsetzung

```python
# Nach Montage-Abschluss
def check_referenz_potenzial(projekt):
    kriterien = {
        "wert_ueber": 5000,        # Groesseres Projekt
        "produkte": ["Haustu  er", "Fensterfront", "Terrassendach"],
        "kundenfeedback": "positiv"
    }
    if erfuellt_kriterien(projekt, kriterien):
        erstelle_referenz_aufgabe(projekt)

# Workflow-Status
class ReferenzWorkflow:
    projekt_id: int
    status: str  # "vorgeschlagen", "fotos_noetig", "erlaubnis_angefragt", "veroeffentlicht", "abgelehnt"
    fotos: List[str]
    erlaubnis_datum: Optional[date]
```

### Abhaengigkeiten

- **Nutzt:** #41 Montage-Status Live (Trigger), #42 Foto-Zuordnung
- **Liefert an:** Website, Marketing

### Offene Fragen

- [ ] Wie wird Website aktuell gepflegt? CMS?
- [ ] Soll Kunde um Fotos gebeten werden oder nur eigene?
- [ ] Wer entscheidet "referenz-wuerdig"?
- [ ] Google-Bewertung parallel anfragen? (→ #73)

### Quelle
Brainstorming 2025-12-16 - Problem: Referenzen veraltet, schoene Projekte nicht dokumentiert

### Status
**Idee** - Einfach-Mittel | **Phase:** Kommunikation | **Prioritaet:** Mittel

---

## #73 Google-Bewertung Vorschlag

> **Phase:** Kommunikation | **Komplexitaet:** Mittel | **Status:** NEU

### Kurzbeschreibung
Automatische Erkennung von positiver Kundenkommunikation → Vorschlag: "Kunden um Google-Bewertung bitten?"

### Problem (IST-Zustand)

| Problem | Auswirkung |
|---------|------------|
| **Gute Bewertungen nicht aktiv eingeholt** | Weniger Sichtbarkeit, potentielle Kunden lesen nur bestehende Reviews |
| **Positive Rueckmeldungen nicht genutzt** | Kunde freut sich, aber kein Review daraus |
| **Kein systematischer Prozess** | Abhaengig von Erinnerung einzelner Mitarbeiter |
| **Timing verpasst** | Nach 2 Wochen denkt Kunde nicht mehr dran |

### Loesung (Features)

**1. Trigger-Erkennung (manuell oder automatisch):**
- Manuell: "Kunde hat positives Feedback gegeben" → Button klicken
- Automatisch (KI): E-Mail-Analyse auf positive Keywords ("super", "danke", "empfehle weiter")
- Nach erfolgreicher Montage ohne Reklamation

**2. Bewertungs-Anfrage Template:**
- Freundliche E-Mail mit direktem Link zu Google-Bewertung
- Personalisiert: Projektbezug
- Timing: 2-3 Tage nach Montage-Abschluss

**3. Tracking:**
- Wem wurde Anfrage geschickt?
- Hat Kunde bewertet? (Manuelles Update oder Google-API Check)
- Erfolgsquote ueber Zeit

**4. Integration mit #49 Google-Reviews Alerts:**
- Neue Bewertung → Benachrichtigung
- Response-Vorschlag fuer Antwort

### E-Mail-Template (Beispiel)

```
Betreff: Wie war Ihre Erfahrung mit JS Fenster & Tueren?

Sehr geehrte/r [Kunde],

wir freuen uns, dass wir [Projekt: z.B. "Ihre neuen Fenster"] erfolgreich
abschliessen konnten.

Wenn Sie mit unserer Arbeit zufrieden waren, wuerden wir uns sehr ueber
eine kurze Bewertung auf Google freuen:

[LINK zu Google-Bewertung]

Das hilft anderen Kunden, uns zu finden - vielen Dank!

Mit freundlichen Gruessen,
Ihr Team von JS Fenster & Tueren
```

### Technische Umsetzung

```python
# Positive Kommunikation erkennen
POSITIVE_KEYWORDS = ["danke", "super", "toll", "zufrieden", "empfehle",
                      "klasse", "perfekt", "grossartig", "top"]

def check_positive_feedback(email_text):
    score = sum(1 for kw in POSITIVE_KEYWORDS if kw in email_text.lower())
    return score >= 2  # Mind. 2 positive Keywords

# Bewertungs-Anfrage
class BewertungsAnfrage:
    kunde_id: int
    projekt_id: int
    gesendet_am: date
    hat_bewertet: bool = False
    google_review_link: str
```

### Abhaengigkeiten

- **Nutzt:** #12 E-Mail-Verarbeitung (Trigger), #41 Montage-Status (Abschluss)
- **Ergaenzt:** #49 Google-Reviews Alerts
- **Liefert an:** Marketing, Reputation

### Offene Fragen

- [ ] Wie lautet der direkte Google-Bewertungs-Link?
- [ ] Soll E-Mail automatisch oder nach Bestaetigung gesendet werden?
- [ ] Nur nach Montage oder auch nach Beratung/Angebot?
- [ ] Koennen negative Erfahrungen erkannt werden? (dann NICHT fragen)

### Quelle
Brainstorming 2025-12-16 - Problem: Positive Rueckmeldungen nicht fuer Reviews genutzt

### Status
**Idee** - Mittel | **Phase:** Kommunikation | **Prioritaet:** Mittel

---

## #74 Prueffristen-Automatik

> **Phase:** Kernprozesse | **Komplexitaet:** Mittel | **Status:** NEU

### Kurzbeschreibung
Automatische Erinnerungen fuer pruefpflichtige Geraete: Leitern, Elektrowerkzeug (DGUV V3), Fahrzeuge (TUeV, UVV). X Wochen vorher an zentrale Person (Mario). Optional: Wanderinventar-Checkout-Log.

### Problem (IST-Zustand)

| Problem | Auswirkung |
|---------|------------|
| **Keine Prueffristen im System** | Pruefungen werden vergessen |
| **Kein Wartungs-Tracking** | Keine Uebersicht wann was gewartet |
| **Keine Automation** | Jaehrliche Untersuchungen manuell |
| **W4A unzureichend** | Inventar-Modul hat keine Frist-Verwaltung |
| **Wanderinventar ohne Historie** | Bei Verlust/Defekt unklar wer es zuletzt hatte |

### Pruefpflichtige Geraete

| Kategorie | Pruefung | Intervall | Rechtsgrundlage |
|-----------|----------|-----------|-----------------|
| **Leitern/Tritte** | Sichtpruefung + Doku | Jaehrlich | DGUV Info 208-016 |
| **Elektrowerkzeug** | DGUV V3 | Jaehrlich | DGUV Vorschrift 3 |
| **Fahrzeuge** | TUeV/HU | 2 Jahre (Nutzfz: 1 Jahr) | StVZO |
| **Fahrzeuge** | UVV-Pruefung | Jaehrlich | DGUV Vorschrift 70 |
| **Anhaenger** | TUeV/HU | 2 Jahre | StVZO |
| **Hebezeuge** | Sachkundigen-Pruefung | Jaehrlich | BetrSichV |
| **Verbandskästen** | Inhalt tauschen | 4-5 Jahre | StVZO, DGUV |

### Mitarbeiter-Zertifikate (NEU - aus Fuhrpark-Brainstorming)

| Zertifikat | Beschreibung | Intervall | Rechtsgrundlage |
|------------|--------------|-----------|-----------------|
| **EuP/EFK** | Elektrofachkraft fuer festgelegte Taetigkeiten | Auffrischung alle 1-3 Jahre | DGUV Vorschrift 3 |
| **Arbeitsbuehne** | Bedienung Hubarbeitsbuehne | Jaehrliche Unterweisung | DGUV Grundsatz 308-008 |
| **Staplerschein** | Flurfoerderzeuge | Jaehrliche Unterweisung | DGUV Vorschrift 68 |
| **Erste Hilfe** | Ersthelfer im Betrieb | Auffrischung alle 2 Jahre | DGUV Vorschrift 1 |
| **PSAgA** | Persoenliche Schutzausruestung gegen Absturz | Jaehrliche Unterweisung | DGUV Regel 112-198 |

**Problem:**
- Zertifikate haben Ablaufdatum oder erfordern regelmaessige Auffrischung
- Wird oft vergessen → Versicherungsschutz gefaehrdet, Bussgelder
- Keine zentrale Uebersicht wer welche Qualifikation hat

**Loesung:**
- Pro Mitarbeiter: Zertifikate mit Ablaufdatum erfassen
- Auto-Erinnerung X Wochen vor Ablauf an Verantwortlichen
- Dashboard: Wer hat welche Qualifikation? Was laeuft ab?
- Optional: Schulungsplanung (wer braucht was?)

### Verbandskästen (NEU - aus Fuhrpark-Analyse)

**Problem:**
- Jedes Fahrzeug braucht Verbandskasten (Pflicht)
- Inhalt hat Ablaufdatum (ca. 4-5 Jahre)
- Wird oft vergessen → Bussgeld bei Kontrolle, TUeV-relevant

**Loesung:**
- Pro Fahrzeug: Verbandskasten-Ablaufdatum erfassen
- Auto-Erinnerung 3 Monate vor Ablauf
- Optional: Ersatz-Verbandskästen im Lager vorhalten

### Loesung (Features)

**1. Prueffristen-Erfassung:**
- Pro Inventar: Naechste Pruefung (Datum)
- Pruefart (DGUV V3, TUeV, UVV, etc.)
- Intervall (jaehrlich, 2-jaehrlich, etc.)

**2. Auto-Erinnerungen:**
- X Wochen vor Faelligkeit: E-Mail an Mario
- Eskalation: 2 Wochen, 1 Woche, ueberfaellig
- Dashboard: Alle faelligen Pruefungen auf einen Blick

**3. Pruefprotokoll:**
- Pruefung durchgefuehrt → Datum eintragen
- Ergebnis: Bestanden / Maengel / Ausgemustert
- Dokument hochladen (Pruefprotokoll)
- Auto-Berechnung naechste Pruefung

**4. Wanderinventar-Checkout (optional):**
- Ausleihe: Wer, Wann, Welches Geraet
- Rueckgabe: Datum, Zustand
- Historie: Wer hatte es wann?
- Aufwand-Abwaegung: Nur wenn einfach genug (QR-Scan?)

### Technische Umsetzung

```python
# Prueffrist-Model
class Prueffrist:
    inventar_id: int
    pruefart: str        # "DGUV_V3", "TUEV", "UVV", "LEITER"
    letzte_pruefung: date
    intervall_monate: int
    naechste_pruefung: date  # Auto-berechnet
    erinnerung_wochen: int = 4

# Erinnerungs-Job (taeglich)
def check_faellige_pruefungen():
    heute = date.today()
    faellig = Prueffrist.objects.filter(
        naechste_pruefung__lte=heute + timedelta(weeks=4)
    )

    for p in faellig:
        tage_bis = (p.naechste_pruefung - heute).days
        if tage_bis <= 0:
            sende_email(mario, f"UEBERFAELLIG: {p.inventar}", prio="hoch")
        elif tage_bis <= 7:
            sende_email(mario, f"DRINGEND: {p.inventar} in {tage_bis} Tagen")
        elif tage_bis <= 14:
            sende_email(mario, f"Bald faellig: {p.inventar}")
        elif tage_bis <= 28:
            sende_email(mario, f"Vorwarnung: {p.inventar}")

# Wanderinventar (optional)
class InventarCheckout:
    inventar_id: int
    mitarbeiter: str
    checkout_datum: datetime
    checkin_datum: Optional[datetime]
    zustand_bei_rueckgabe: Optional[str]
```

### Wanderinventar - Aufwand-Analyse

| Option | Aufwand User | Aufwand Entwicklung | Nutzen |
|--------|--------------|---------------------|--------|
| **A: Immer "Lager"** | Keiner | Keiner | Keine Historie |
| **B: Freitext aendern** | Gering (W4A oeffnen) | Keiner | Aktuell, keine Historie |
| **C: QR-Scan App** | Minimal (Handy) | Mittel | Volle Historie |
| **D: Web-Formular** | Gering (Browser) | Gering | Volle Historie |

**Empfehlung:** Option D (Web-Formular) - einfach, Historie vorhanden, geringer Aufwand

### Abhaengigkeiten

- **Nutzt:** #13 Inventar-Verwaltung (Basis-Daten), W4A Inventar
- **Ergaenzt:** Inventarprozess
- **Optional:** #58 Web-Plattform (fuer Dashboard/Checkout)

### Offene Fragen

- [ ] Prueffristen: In W4A eintragbar oder eigene DB noetig?
- [ ] Wer fuehrt Pruefungen durch? (Intern/Extern?)
- [ ] Erinnerungs-Vorlauf: 4 Wochen OK oder mehr?
- [ ] Wanderinventar: QR-Code auf Geraeten bereits vorhanden?
- [ ] Soll Checkout per App oder Web-Formular?

### Quelle
Brainstorming 2025-12-16 - Inventar-Prozess, Luecken in W4A

### Status
**Idee** - Mittel | **Phase:** Kernprozesse | **Prioritaet:** Mittel (Rechtlich relevant!)

---

## #75 Fuehrerschein-Kontrolle

> **Phase:** Standalone | **Komplexitaet:** Gering | **Status:** NEU

### Kurzbeschreibung
Gesetzliche Pflicht! Arbeitgeber muss regelmaessig pruefen, ob Mitarbeiter gueltigen Fuehrerschein haben. Auto-Erinnerung zur Kontrolle, Nachweis-Dokumentation.

### Problem (IST-Zustand)

| Problem | Auswirkung |
|---------|------------|
| **Keine systematische Pruefung** | Arbeitgeber haftet bei Unfall ohne gueltige Fahrerlaubnis |
| **Kein Nachweis** | Bei Kontrolle/Unfall: Kein Beleg dass geprueft wurde |
| **Ablaufdatum unbekannt** | Neuere Fuehrerscheine haben Ablaufdatum (15 Jahre) |
| **Gesetzliche Pflicht** | Arbeitgeber MUSS pruefen (Verkehrssicherheitspflicht) |

### Rechtlicher Hintergrund

**Pflicht des Arbeitgebers:**
- Verkehrssicherheitspflicht nach § 823 BGB
- Bei Firmenfahrzeugen: Halterverantwortung
- Empfehlung: Mind. 2x jaehrlich pruefen
- Nachweis der Kontrolle aufbewahren

**Risiko bei Verstoß:**
- Fahren ohne Fahrerlaubnis: Straftat (§ 21 StVG)
- Arbeitgeber als Mitwisser/Anstifter haftbar
- Versicherung kann Leistung kuerzen/verweigern

### Betroffene Mitarbeiter (aus Fuhrpark-Analyse)

| Mitarbeiter | Fahrzeug | Fuehrerschein-Klasse |
|-------------|----------|----------------------|
| Mariusz | Fiat Ducato AS-JS 124 | B (>3,5t: C1?) |
| Christian | Fiat Ducato AM-JS 7 | B |
| Stefan | Fiat Ducato AM-JS 17 | B |
| Manfred | Opel Movano AM-JS 63 | B |
| Jaroslaw | Mercedes Citan AM-JS 41 | B |
| Enrico | Ford Connect AM-JS 19 | B |
| Andreas | Ford Connect AM-JS 69 | B |
| Roland | Fiat Punto AS-JS 114 | B |
| (Stapler-Fahrer) | Toyota Stapler | Staplerschein |

### Loesung (Features)

**1. Fahrer-Erfassung:**
- Wer faehrt welches Fahrzeug?
- Benoetigte Fuehrerschein-Klasse
- Fuehrerschein gueltig bis (Ablaufdatum)
- Staplerschein wenn relevant

**2. Kontroll-Intervall:**
- Empfehlung: Alle 6 Monate
- Auto-Erinnerung X Wochen vorher an Verantwortlichen
- Wer kontrolliert? (Susann? Andreas?)

**3. Nachweis-Dokumentation:**
- Kontrolle durchgefuehrt am: [Datum]
- Geprueft von: [Name]
- Ergebnis: Gueltig / Abgelaufen / Entzogen
- Optional: Foto/Scan des Fuehrerscheins

**4. Auto-Erinnerungen:**
- Halbjahres-Kontrolle faellig
- Fuehrerschein laeuft ab in X Wochen
- Kontrolle ueberfaellig!

### Automatisierungs-Stufen

| Stufe | Beschreibung | Aufwand |
|-------|--------------|---------|
| **Autonom** | Nicht moeglich (physische Pruefung noetig) | - |
| **Automatisch** | Erinnerung + Formular + Auto-Dokumentation | Gering |
| **Halbautomatisch** | Erinnerung per E-Mail, manuell dokumentieren | Minimal |
| **Manuell** | Kalender-Erinnerung, Excel-Liste | Keiner |

### Technische Umsetzung

```python
# Fuehrerschein-Model
class Fuehrerschein:
    mitarbeiter: str
    fuehrerschein_klassen: list[str]  # ["B", "BE", "C1"]
    gueltig_bis: date  # Kann None sein bei alten rosa Lappen
    staplerschein: bool = False
    letzte_kontrolle: date
    naechste_kontrolle: date  # Auto-berechnet

# Erinnerungs-Job
def check_fuehrerschein_kontrollen():
    heute = date.today()

    # Halbjahres-Kontrollen
    faellig = Fuehrerschein.objects.filter(
        naechste_kontrolle__lte=heute + timedelta(weeks=2)
    )

    for fs in faellig:
        if fs.naechste_kontrolle <= heute:
            sende_email(verantwortlicher, f"UEBERFAELLIG: FS-Kontrolle {fs.mitarbeiter}")
        else:
            sende_email(verantwortlicher, f"Faellig: FS-Kontrolle {fs.mitarbeiter}")

    # Ablauf-Warnungen
    ablaufend = Fuehrerschein.objects.filter(
        gueltig_bis__lte=heute + timedelta(weeks=12),
        gueltig_bis__isnull=False
    )

    for fs in ablaufend:
        wochen_bis = (fs.gueltig_bis - heute).days // 7
        sende_email(fs.mitarbeiter, f"Fuehrerschein laeuft ab in {wochen_bis} Wochen!")
        sende_email(verantwortlicher, f"Achtung: FS von {fs.mitarbeiter} laeuft ab!")
```

### Einfachste Loesung (MVP)

**Excel + Kalender:**
1. Excel-Liste: Mitarbeiter | FS-Klasse | Gueltig bis | Letzte Kontrolle
2. Outlook-Termin: Alle 6 Monate "Fuehrerschein-Kontrolle"
3. Bei Kontrolle: Excel aktualisieren, Foto in Personalakte

**Web-Tool (Empfohlen):**
1. Einfaches Formular: Mitarbeiter auswaehlen, "Kontrolle OK" klicken
2. Datum wird auto-gespeichert
3. Naechste Kontrolle auto-berechnet
4. E-Mail-Reminder aktiviert

### Abhaengigkeiten

- **Verknuepft mit:** Fuhrparkprozess, #74 Prueffristen
- **Optional:** #58 Web-Plattform (fuer Tool)
- **Standalone:** Kann auch ohne andere Tools funktionieren (Excel)

### Offene Fragen

- [ ] Wer ist verantwortlich fuer Kontrolle? (Susann? Andreas?)
- [ ] Wie oft pruefen? (Empfehlung: 2x/Jahr)
- [ ] Wo dokumentieren? (W4A Personalakte? Eigenes Tool? Excel?)
- [ ] Foto/Scan des Fuehrerscheins aufbewahren?
- [ ] Staplerschein: Wer hat ihn? Ablaufdatum?

### Quelle
Brainstorming 2025-12-16 - Fuhrpark-Prozess, gesetzliche Anforderung

### Status
**Idee** - Gering | **Phase:** Standalone | **Prioritaet:** Hoch (Rechtlich zwingend!)

