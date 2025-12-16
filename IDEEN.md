# Ideen fuer KI-Automatisierungen

**Erstellt:** 2025-12-09 | **Aktualisiert:** 2025-12-16 | **Stand:** 67 offen, 1 umgesetzt, 5 integriert

---

## Dokumentstruktur

| Datei | Inhalt |
|-------|--------|
| **IDEEN.md** (diese Datei) | Kurzuebersicht (max 3 Zeilen/Idee) |
| **[IDEEN_DETAILS.md](IDEEN_DETAILS.md)** | Technische Details, SQL, W4A-Status |
| **[IDEEN_UEBERSICHT.html](IDEEN_UEBERSICHT.html)** | Interaktive Ansicht + Architektur |

---

## Phasen-Uebersicht

| Phase | Beschreibung | Tools |
|-------|--------------|-------|
| **0** | INFRASTRUKTUR | #58, #59, #60, #64, #68 |
| **1** | BASIS-MODULE + KRITISCH | #1, #4 ✅, #13, #36 ⭐, #39/#40/#41 (Montage-Suite) |
| **2** | KERNPROZESSE | #9, #10, #11, #22, #24, #28, #32, #33, #37, #38, #53, #55, #56, #57, #65, #66, #67, #74 |
| **3** | KOMMUNIKATION | #3, #6, #12, #23, #25, #27, #30, #47, #49, #50 |
| **4** | COMMAND CENTER | #14 (integriert #44, #51, #52) |
| **5** | KI-FEATURES | #2, #5, #7, #8, #18, #20, #21, #29, #62, #63 |

> **Hinweis:** #39/#40/#41 = Montage-Suite (zusammen implementieren)

---

## Phase 0: Infrastruktur

### #58 Web-Plattform Grundgeruest
Basis fuer alle Tools: Flask + Bootstrap, Routing, Templates.
→ [Details](IDEEN_DETAILS.md#58-web-plattform-grundgeruest)

### #59 Datenbank-Connector
Sichere W4A SQL Server Verbindung, Connection-Pool, wiederverwendbar.
→ [Details](IDEEN_DETAILS.md#59-datenbank-connector)

### #60 Auth & Berechtigungen
Login-System, Rollen (admin/buero/monteur), wer sieht was.
→ [Details](IDEEN_DETAILS.md#60-auth--berechtigungen)

### #64 Data Service Layer
Zentrale Datenzugriffs-Schicht, Cache, Events (8 Tools auf dbo.Bestellung!).
→ [Details](IDEEN_DETAILS.md#64-data-service-layer)

### #68 Zentrales Planungs-Dashboard ⭐ NEU
Ersetzt Outlook-Kalender-Missbrauch. Montage, Reparatur, Abholungen auf einen Blick.
→ [Details](IDEEN_DETAILS.md#68-zentrales-planungs-dashboard)

---

## Phase 1: Basis-Module + Kritisch

### #1 Preislisten-Tool
PDF-Preislisten (ROKA, Weru) → Excel-Artikelstamm importieren.
→ [Details](IDEEN_DETAILS.md#1-preislisten-tool-pdf--excel)

### #4 KI-Wissensdatenbank ✅
Selbst-aktualisierende Wissensdatei, Task Scheduler (So 03:00).
→ [Details](IDEEN_DETAILS.md#4-ki-wissensdatenbank--fertig)

### #13 Inventar-Verwaltung
W4A-Erweiterung: Rechnungslink, Standort-Tracking, QR-Codes, Ausleihe.
→ [Details](IDEEN_DETAILS.md#13-inventar-verwaltung)

### #36 Beschaffungs-Dashboard ⭐ KRITISCH
Echtzeit-Ampel fuer kritische Bestellungen (ohne AB, ueberfaellig, abholbereit). 4 Prozesse!
→ [Details](IDEEN_DETAILS.md#36-beschaffungs-dashboard--prioritaet)

### Montage-Suite (#39 + #40 + #41) ⭐
Zusammen implementieren - gemeinsame Datenbasis!

#### #39 Tages-Briefing Monteur
Auto-generierte Montage-Mappe (1-3 Seiten), digitale Rueckmeldung.
→ [Details](IDEEN_DETAILS.md#39-tages-briefing-monteur-montage-mappe)

#### #40 Material-Kommissionierliste
Auto-Checkliste: Was muss ins Auto? Aus BESTELLUNG, nicht Angebot.
→ [Details](IDEEN_DETAILS.md#40-material-kommissionierliste)

#### #41 Montage-Status Live
Monteur meldet Status, alle sehen Echtzeit, Auto-SMS an Kunde.
→ [Details](IDEEN_DETAILS.md#41-montage-status-live)

---

## Phase 2: Kernprozesse

### #9 Reparatur-Verwaltung (+#43 als UI)
Reklamationen, Garantiepruefung, Status-Tracking, Foto-Doku.
→ [Details](IDEEN_DETAILS.md#9-reparatur-verwaltung)

### #10 Auftraege & Lieferungen
Zentrale Auftragsverwaltung: Auftraege, Abholungen, Lieferungen ±Montage.
→ [Details](IDEEN_DETAILS.md#10-auftraege--lieferungen)

### #11 Terminfindung (Termin-Engine)
Intelligente Terminplanung, Online-Buchung, Geo-Optimierung. Wird von Anfrage, Montage, Reparatur genutzt.
→ [Details](IDEEN_DETAILS.md#11-terminfindung)

### #22 Routenplanung
Tourenoptimierung: Fahrzeit minimieren, Termine clustern (~292h/Jahr).
→ [Details](IDEEN_DETAILS.md#22-routenplanung)

### #24 Ticket-System + Schnell-Erfassung
Auto-Tickets aus E-Mails, Vorgangsnummern, SLA-Tracking, 1-Klick-Erfassung.
→ [Details](IDEEN_DETAILS.md#24-ticket-system-integration--schnell-erfassung)

### #28 Digitales Aufmass + Mobiles Formular
Masserfassung mit auto. Zubehoer-Berechnung, Offline-Sync, Fotos.
→ [Details](IDEEN_DETAILS.md#28-digitales-aufmass--zubehoer--mobiles-formular)

### #32 Projekt- & Unterprojektverwaltung
Hierarchisch: Hauptprojekt → Unterprojekte → ERP-Dokumente.
→ [Details](IDEEN_DETAILS.md#32-projekt---unterprojektverwaltung)

### #33 Bestellwesen & Lieferanten-Auftraege
Bedarfsermittlung → Bestellung → Wareneingang.
→ [Details](IDEEN_DETAILS.md#33-bestellwesen--lieferanten-auftraege)

### #37 WoT-XML Transformer
Weru WPS on Top XML aufbereiten fuer sauberen W4A-Import.
→ [Details](IDEEN_DETAILS.md#37-wot-xml-transformer-weru-konfigurator)

### #38 Lagerverwaltung & Inventur
Bestandsfuehrung, Inventur-Prozess, Teillieferungs-Problem loesen.
→ [Details](IDEEN_DETAILS.md#38-lagerverwaltung--inventur)

### #53 Mindestbestand-Alert
Warnung bei kritischem Lagerbestand, auto. Bestellvorschlag.
→ [Details](IDEEN_DETAILS.md#53-mindestbestand-alert)

### #55 Bestellvorlage Pflichtfelder ⭐
Pflichtfeld Lieferwoche, auto. Lieferadresse je Artikel-Typ.
→ [Details](IDEEN_DETAILS.md#55-bestellvorlage-mit-pflichtfeldern--prio)

### #56 AB-Abgleich automatisch ⭐
PDF-AB mit Bestellung vergleichen, Abweichungen markieren.
→ [Details](IDEEN_DETAILS.md#56-ab-abgleich-automatisch--prio)

### #57 Lieferadressen-Logik ⭐
Auto-Adresse: Gross (Fenster) → Lager, Klein (Pakete) → Buero.
→ [Details](IDEEN_DETAILS.md#57-lieferadressen-logik--prio)

### #65 Anzahlungsrechnung-Auto ⭐
Erinnerung/Pflicht fuer Anzahlung vor Bestellung (Cashflow!).
→ [Details](IDEEN_DETAILS.md#65-anzahlungsrechnung-automatismus)

### #66 Montageplanung + Wetter
Wetter-API, Warnung bei Regen/Sturm, Verschiebe-Empfehlung.
→ [Details](IDEEN_DETAILS.md#66-montageplanung-mit-wetterprognose)

### #67 XML-Konverter Universal
Beliebige XML/Text → W4A-kompatibles XML, Template-System.
→ [Details](IDEEN_DETAILS.md#67-xml-konverter-universal--w4a)

---

## Phase 3: Kommunikation

### #3 Weru Foerderantraege ⭐ KRITISCH
BAFA/KfW-Antraege + **KRITISCH:** NachweisService nach Zahlung vergessen → Kunde verliert Foerderung! Auto-Erinnerung via Foerder-Position.
→ [Details](IDEEN_DETAILS.md#3-weru-foerderantraege-automatisierung)

### #6 Budget-Angebots-Generator
Auto-Angebote aus Elementlisten, Excel-Import, Preis-Kalkulation.
→ [Details](IDEEN_DETAILS.md#6-budget-angebots-generator)

### #12 E-Mail-Verarbeitung
LLM-Klassifizierung, Kunden-Zuordnung, Auto-Ablage, Workflow-Trigger.
→ [Details](IDEEN_DETAILS.md#12-e-mail-verarbeitung)

### #23 Verkaufschancen-Pipeline
Lead-Bewertung, Scoring, Angebots-Reminder, 2-Tage-Regel.
→ [Details](IDEEN_DETAILS.md#23-verkaufschancen-pipeline--angebots-reminder)

### #25 Telefon-CRM Integration
Anrufer-Erkennung, Kundendaten-Popup, Notizen.
→ [Details](IDEEN_DETAILS.md#25-telefon-crm-integration)

### #27 Dokument-Intelligenz
Auto-Klassifizierung, OCR, Metadaten, Volltextsuche.
→ [Details](IDEEN_DETAILS.md#27-dokument-intelligenz)

### #30 After Sales Service
Proaktive Kundenbetreuung: Wartungs-Reminder, Cross-Selling.
→ [Details](IDEEN_DETAILS.md#30-after-sales-service)

### #47 Kunden-Historie + Wiederkauf
Timeline aller Kontakte/Auftraege, Stammkunden erkennen.
→ [Details](IDEEN_DETAILS.md#47-kunden-historie-dashboard--wiederkauf-erkennung)

### #49 Google-Reviews Alerts
Neue Bewertung → Sofort Bescheid, Response-Vorschlaege.
→ [Details](IDEEN_DETAILS.md#49-google-reviews-alerts)

### #50 Sanfte Zahlungserinnerung
Auto-Mail "Rechnung offen" vor formeller Mahnung.
→ [Details](IDEEN_DETAILS.md#50-sanfte-zahlungserinnerung)

---

## Phase 4: Command Center

### #14 Zentrales Dashboard ⭐
EIN Dashboard fuer alles: Heute, Bestellungen, Montage, Finanzen, KPIs.
→ [Details](IDEEN_DETAILS.md#14-management-dashboard)

### #2 Bilanz & GuV-Auswertung
Kennzahlen, Trendprognosen, Branchenvergleich.
→ [Details](IDEEN_DETAILS.md#2-bilanz--und-guv-auswertung)

### #15 Zeiterfassung & Auslastung
Projektbezogene Zeit, Kapazitaetsplanung.
→ [Details](IDEEN_DETAILS.md#15-zeiterfassung--auslastung)

### #16 Urlaubsverwaltung
Digitale Antraege, Teamkalender.
→ [Details](IDEEN_DETAILS.md#16-urlaubsverwaltung)

### #17 Projekt-Deckungsbeitrag
Soll-Ist-Vergleich, Nachkalkulation, Budgetwarnung.
→ [Details](IDEEN_DETAILS.md#17-projekt-deckungsbeitrag)

### #19 Lieferanten-Bewertung
Auto-Scoring: Liefertreue, Qualitaet, Preis, Kommunikation.
→ [Details](IDEEN_DETAILS.md#19-lieferanten-bewertung)

### #26 Projekt-Aktivitaeten-Tracking
Auto-Protokoll aller Aktivitaeten, Timeline-Ansicht.
→ [Details](IDEEN_DETAILS.md#26-projekt-aktivitaeten-tracking)

### #31 Rechnungsbuch & Finanzdoku
Ein-/Ausgangsrechnungen, Mahnwesen, DATEV-Export, Liquiditaet.
→ [Details](IDEEN_DETAILS.md#31-rechnungsbuch--finanzdokumentation)

### #34 Erweiterte Zeiterfassung (GPS)
Projektzuordnung Pflicht, GPS-Vorschlaege, QR-Code-Erfassung.
→ [Details](IDEEN_DETAILS.md#34-erweiterte-zeiterfassung-gps)

### #35 Urlaubsplaner erweitert
Teamkalender, auto. Kapazitaetspruefung, Genehmigungsworkflow.
→ [Details](IDEEN_DETAILS.md#35-urlaubsplaner--abwesenheitsmanagement)

### #42 Foto-Zuordnung
Handy-Foto → Auto-Erkennung Projekt/Kunde → richtige Akte.
→ [Details](IDEEN_DETAILS.md#42-foto-zuordnung)

### #44 Kapazitaets-Cockpit
Auslastungs-Ampel: Wer hat noch Luft? Drill-Down.
→ [Details](IDEEN_DETAILS.md#44-kapazitaets-cockpit)

### #51 Cashflow-Prognose
Liquiditaets-Ampel: Wann kommt Geld, wann geht's raus?
→ [Details](IDEEN_DETAILS.md#51-cashflow-prognose)

### #52 Conversion-Tracker
Angebots-Auftrags-Quote, Trend-Analyse, Aufschluesselung.
→ [Details](IDEEN_DETAILS.md#52-conversion-tracker)

### #54 Preis-Vergleich Lieferanten
Gleicher Artikel, verschiedene Lieferanten → bester Preis.
→ [Details](IDEEN_DETAILS.md#54-preis-vergleich-lieferanten)

---

## Phase 5: KI-Features

### #5 Bauplan-Analyse
KI-Vision liest Bauplaene, extrahiert Masse, generiert Elementlisten.
→ [Details](IDEEN_DETAILS.md#5-bauplan-analyse--elementlisten-generator)

### #7 Spracherkennung
Diktat, Aufmasse vor Ort, KI-Analyse in Echtzeit.
→ [Details](IDEEN_DETAILS.md#7-spracherkennung--anweisungsdienst)

### #8 Universal-Eingabe-Hub
Das "Gehirn": Multi-Input → LLM Dispatcher → Workflows.
→ [Details](IDEEN_DETAILS.md#8-universal-eingabe-hub)

### #18 Kundenportal
Self-Service: Status, Termine, Dokumente, Reklamation.
→ [Details](IDEEN_DETAILS.md#18-kundenportal)

### #20 Qualitaetsmanagement
Reklamations-Tracking, KVP, Audit-Vorbereitung.
→ [Details](IDEEN_DETAILS.md#20-qualitaetsmanagement)

### #21 Mobile Monteur-App
Unified: Tagesplan, Navigation, Checklisten, Fotos, Unterschrift.
→ [Details](IDEEN_DETAILS.md#21-mobile-monteur-app)

### #29 Montage-Checklisten
Auto-Checklisten aus Aufmass: Material, Werkzeug, Arbeitsschritte.
→ [Details](IDEEN_DETAILS.md#29-montage-checklisten)

### #62 Ersatzteil-Erkennung (KI-Vision)
Foto von defektem Teil → KI erkennt → Ersatzteil vorschlagen.
→ [Details](IDEEN_DETAILS.md#62-ersatzteil-erkennung-ki-vision)

### #63 Fassaden-Budget (KI-Vision)
Hausfoto → KI zaehlt Fenster → grobes Budgetangebot.
→ [Details](IDEEN_DETAILS.md#63-fassaden-budget-ki-vision)

---

## Merged Ideen

| Alt | Neu | Grund |
|-----|-----|-------|
| #45 Angebots-Reminder | → #23 | Teil von Verkaufschancen-Pipeline |
| #46 Schnell-Erfassung | → #24 | Teil von Ticket-System |
| #48 Wiederkauf-Erkennung | → #47 | Teil von Kunden-Historie |
| #61 Mobiles Aufmass | → #28 | Teil von Digitales Aufmass |
| #43 Kanban-Dashboard | → #9 | UI-Komponente von Reparatur-Verwaltung |

---

## Komplexitaet

| Stufe | Tools |
|-------|-------|
| 🟢 Einfach | #4 ✓, #29, #49, #57 |
| 🟡 Mittel | #1, #3, #6, #9, #10, #13, #15, #16, #19, #23, #24, #28, #31, #33, #36, #37, #38, #39, #40, #47, #50, #53, #55, #65, #66, #67, #70 |
| 🟠 Anspruchsvoll | #2, #11, #12, #14, #17, #18, #22, #25, #26, #27, #30, #32, #34, #35, #41, #42, #44, #51, #52, #54, #56 |
| 🔴 Komplex | #5, #7, #8, #20, #21, #62, #63 |

---

---

## Standalone-Tools

### #69 UTA-Tankrechnungen PDF-Tool
UTA-Tankrechnungen (PDFs) analysieren, nach Land splitten, laenderspezifische Sammel-PDFs erstellen.
→ [Details](IDEEN_DETAILS.md#69-uta-tankrechnungen-pdf-tool)

### #70 Montagematerial-Pauschalen-Automatik ⭐ NEU
Automatische Materialpauschale fuer Nicht-Fenster (Innentuer, Markise, etc.). Aktuell wird Material vergessen → Umsatzverlust.
→ [Details](IDEEN_DETAILS.md#70-montagematerial-pauschalen-automatik)

### #71 Einkaufs-Workflow & Preismanagement ⭐ NEU
Preis-Cache, Preisanfrage-Tracking (offen/beantwortet), Grossmengen-Erinnerung, Konditionen zentral. Schmerzpunkt: Preisanfragen dauern Tage/Wochen.
→ [Details](IDEEN_DETAILS.md#71-einkaufs-workflow--preismanagement)

### #72 Referenz-Automatik ⭐ NEU
Nach abgeschlossener Montage: Auto-Erinnerung "Fotos machen?", Workflow fuer Website-Referenzen. Problem: Wird oft vergessen, Website veraltet.
→ [Details](IDEEN_DETAILS.md#72-referenz-automatik)

### #73 Google-Bewertung Vorschlag ⭐ NEU
Nach positiver Kundenkommunikation: Automatisch erkennen + Bewertungs-Link vorschlagen. Problem: Gute Bewertungen werden nicht aktiv eingeholt.
→ [Details](IDEEN_DETAILS.md#73-google-bewertung-vorschlag)

### #74 Prueffristen-Automatik ⭐
Auto-Erinnerungen fuer Geraete (DGUV, TUeV, UVV) + Mitarbeiter-Zertifikate (EFK, Arbeitsbuehne, Staplerschein).
→ [Details](IDEEN_DETAILS.md#74-prueffristen-automatik)

### #75 Fuehrerschein-Kontrolle ⭐ NEU
Gesetzliche Pflicht! Arbeitgeber muss Fuehrerscheine pruefen. Auto-Erinnerung, Nachweis-Dokumentation.
→ [Details](IDEEN_DETAILS.md#75-fuehrerschein-kontrolle)

---

## Naechste Schritte

1. **Sofort:** #1 Preislisten-Tool
2. **Kurzfristig:** #13 Inventar, Phase 2 planen
3. **Mittelfristig:** Phase 2-3 umsetzen
