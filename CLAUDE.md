# JS_Prozesse - Planung & Dokumentation

> **Repo:** `https://github.com/JS-Fenster/JS-Prozesse.git`
> **Zweck:** Ideen-Sammlung, Prozess-Analysen, Projekt-Planung fuer JS Fenster & Tueren

---

## Zentrale Wissensbasis (IMMER einlesen!)

> **Basis-Anweisungen:** `../KI_Automation/CLAUDE.md`
> **DB-Wissen:** `../KI_Automation/docs/ERP_Datenbank.md`
> **KI-News:** `../KI_Automation/docs/KI_Wissen.md`

---

## Projektstruktur

```
JS_Prozesse/
├── analysen/                    # Prozess-Dokumentationen (IST-Zustand)
│   ├── Anfrageprozess_Analyse.md
│   ├── Aufmassprozess_Analyse.md
│   ├── Bestellprozess_Analyse.md
│   ├── Einkaufsprozess_Analyse.md
│   ├── Lagerprozess_Analyse.md
│   ├── Montageprozess_Analyse.md
│   ├── Rechnungsprozess_Analyse.md
│   ├── Reklamationsprozess_Analyse.md
│   ├── Reparaturprozess_Analyse.md
│   └── BAFA_Foerderantrag_Analyse.md
├── ARCHITEKTUR.md               # ERP-Strategie (W4A + eigene Tools)
├── IDEEN.md                     # 65 Tool-Ideen (verdichtet)
├── IDEEN_DETAILS.md             # Technische Details + W4A-Status
├── IDEEN_UEBERSICHT.html        # Ideen-Katalog (Karten, Filter)
├── PROZESS_VISUALISIERUNG.html  # IST vs SOLL, Tool-Matrix
└── CLAUDE.md                    # Diese Datei
```

---

## Ideen-Management

### Neue Ideen aufnehmen

**1. PFLICHT: Duplikat-Pruefung VOR Vorschlag!**
1. Quick-Reference-Tabelle in IDEEN_DETAILS.md lesen
2. Keywords gegen bestehende Titel pruefen
3. Verwandte Kategorien checken
4. Ergebnis: "Aehnlich zu #X - dort ergaenzen?" ODER "Neue Idee #Y"

**2. Bei neuer Idee - ALLE 4 Dateien pflegen:**

| Datei | Aktion |
|-------|--------|
| `IDEEN.md` | Kurzversion (max 3 Zeilen), Phase zuordnen |
| `IDEEN_DETAILS.md` | Technische Details + Quick-Reference Tabelle aktualisieren |
| `IDEEN_UEBERSICHT.html` | Neue Karte hinzufuegen |
| `PROZESS_VISUALISIERUNG.html` | Tool-Matrix + betroffene Prozesse aktualisieren |

**3. Ideen proaktiv erkennen:**
- User hat Problem/Wunsch? → Potentielle Idee!
- Workflow koennte automatisiert werden? → Idee!

**4. Automatisierungs-Philosophie (WICHTIG!):**
```
IMMER Vollautomation anstreben
        ↓
Nicht umsetzbar? → Tool in Programmierung vereinfachen
        ↓
NIE "mach es halt manuell" als Loesung!
```
- Ziel: Technische Loesung, nicht Prozess-Workaround
- Wenn KI/OCR zu komplex → einfacheres Tool (z.B. Formular + Auto-Verteiler)
- Stufen: Vollautomatisch → Halbautomatisch (User-Trigger) → Assistiert

### Verdichten-Regeln

| Datei-Typ | Regel |
|-----------|-------|
| CLAUDE.md | Strikt verdichten |
| IDEEN.md | Max 3 Zeilen pro Idee |
| IDEEN_DETAILS.md | Ausfuehrlich (technische Referenz) |
| HTML-Dateien | Struktur beibehalten, nur Daten ergaenzen |

---

## Prozess-Analysen

### Dokumentierte Prozesse

| Datei | Prozess | Status |
|-------|---------|--------|
| `Anfrageprozess_Analyse.md` | Eingang → Angebot → Nachverfolgung | ✅ IST dokumentiert |
| `Bestellprozess_Analyse.md` | Auftrag → Bestellung → AB → Wareneingang | ✅ IST dokumentiert |
| `Lagerprozess_Analyse.md` | Warenannahme → Einlagerung → Kommissionierung | ✅ IST dokumentiert |
| `Rechnungsprozess_Analyse.md` | Montage fertig → Rechnung → Mahnung | ✅ IST dokumentiert |
| `Reparaturprozess_Analyse.md` | Reparatur-Lifecycle + Automatisierung | ✅ IST + SOLL |
| `Montageprozess_Analyse.md` | Montage-Workflow | ✅ IST dokumentiert |
| `Reklamationsprozess_Analyse.md` | Reklamations-Handling | ✅ IST dokumentiert |
| `Aufmassprozess_Analyse.md` | Angebots-/Bestellaufmass → Konfigurator | ✅ IST dokumentiert |
| `Einkaufsprozess_Analyse.md` | Lieferanten → Preise → Konditionen → Zahlung | ✅ IST dokumentiert |
| `Inventarprozess_Analyse.md` | Erfassung → W4A → Zuordnung → Prueffristen | ✅ IST dokumentiert |
| `Buergschaftsprozess_Analyse.md` | R+V Portal → Urkunde → W4A-Tracking | ✅ IST dokumentiert |
| `BAFA_Foerderantrag_Analyse.md` | Weru Portal → BAFA → NachweisService ⭐ KRITISCH | ✅ IST dokumentiert |

### Offene Prozesse (fuer Brainstorming)

| Prozess | Notizen/Fragen | Erkannt am |
|---------|----------------|------------|
| Personal/Urlaub | Urlaubsantraege, Kapazitaet, Krankmeldung | 2025-12-14 |
| Fuhrpark | Fahrzeuge, Tanken, Wartung, TUeV | 2025-12-14 |
| Buchhaltung | Eingangsrechnungen, DATEV, Konten | 2025-12-14 |
| After-Sales | Wartungsvertraege, Nachbetreuung | 2025-12-14 |
| ~~BAFA-Foerderantrag~~ | ~~Dokumentiert als eigener Prozess, #3 erweitert (KRITISCH!)~~ | ~~2025-12-16~~ |
| ~~Inventar-Prozess~~ | ~~W4A Inventar wird genutzt → dokumentiert, #74 erstellt~~ | ~~2025-12-16~~ |
| ~~Buergschaften~~ | ~~R+V Portal, W4A-Tracking → dokumentiert~~ | ~~2025-12-16~~ |

### Offene Fragen zu bestehenden Prozessen

| Prozess | Frage/Erweiterung | Notiert am |
|---------|-------------------|------------|
| ~~Lager~~ | ~~Lieferankuendigungen spontan/fehlen, Fahrer-Tel falsch~~ | ~~2025-12-15~~ |
| ~~Lager~~ | ~~Teilmengen: Mario statt Roland? (aber mehr Arbeit)~~ | ~~2025-12-15~~ |
| ~~Aufmass~~ | ~~Formulare hochladen lassen zur Analyse~~ | ~~2025-12-15~~ |
| ~~Rechnung~~ | ~~Ruecklaufer/Montagematerial → #70 erweitert~~ | ~~2025-12-16~~ |
| ~~Anfrage~~ | ~~E-Mails: Susann verteilt in Outlook-Ordner~~ | ~~2025-12-15~~ |
| ~~Montage~~ | ~~Rueckmeldung per Zettel → dokumentiert~~ | ~~2025-12-15~~ |
| ~~Rechnung~~ | ~~Anzahlung: Sandra prueft → dokumentiert~~ | ~~2025-12-15~~ |
| ~~Reparatur~~ | ~~Keine Benachrichtigung → dokumentiert~~ | ~~2025-12-15~~ |
| ~~W4A~~ | ~~Ladezeiten, kein Rueckgaengig, etc. → dokumentiert~~ | ~~2025-12-15~~ |
| ~~W4A~~ | ~~E-Mail-Abruf, Dokumente → dokumentiert~~ | ~~2025-12-15~~ |
| ~~W4A~~ | ~~Stempeluhr → dokumentiert~~ | ~~2025-12-15~~ |
| ~~W4A~~ | ~~Zeiterfassung → dokumentiert~~ | ~~2025-12-15~~ |
| ~~W4A~~ | ~~Ungenutzte Features → dokumentiert~~ | ~~2025-12-15~~ |
| ~~Kommunikation~~ | ~~Monteure/Buero → dokumentiert, funktioniert gut~~ | ~~2025-12-15~~ |
| ~~Dokumente~~ | ~~W4A-Verlinkung auf Server-Pool → funktioniert gut~~ | ~~2025-12-15~~ |
| ~~BAFA~~ | ~~Dokumentiert! Prozess-Analyse + #3 erweitert mit Auto-Erinnerung~~ | ~~2025-12-16~~ |
| ~~Preiserhoehungen~~ | ~~Dokumentiert in Einkaufsprozess + #71 erweitert mit Preisinfo-Verteiler~~ | ~~2025-12-16~~ |

### Prozesse proaktiv erkennen

**IMMER bei Gespraechen:**
- Neuen Prozess erwaehnt? → In "Offene Prozesse" eintragen
- Erweiterung zu bestehendem Prozess? → In "Offene Fragen" eintragen
- Oder gleich nachfragen wenn relevant

### Neue Prozess-Analyse erstellen

Wenn User groessere Ablauf-Details erklaert:
1. Fragen: "Soll ich `analysen/[Prozess]_Analyse.md` anlegen?"
2. **WICHTIG:** Genuegend Fragen stellen! Nicht zu frueh abbrechen.
3. Dokumentieren: IST-Zustand, Schmerzpunkte, Automatisierungspotential
4. Tabellen oben aktualisieren (aus "Offen" → "Dokumentiert")
5. Verknuepfte IDEEN mit Prozess-Verweis versehen

### Brainstorming-Regeln

**Wissen zuerst praesentieren:**
1. Alle relevanten Dokumente lesen (Analysen, IDEEN_DETAILS.md)
2. Strukturiert zeigen:
   - "Aus [Prozess X] uebernehme ich: ..." (bekannte Schritte)
   - "Luecke: Wie laeuft Schritt Y?" (nur das nachfragen)
   - "Neue Verknuepfung erkannt: ..." (bei bekannten Prozessen)
3. Nur die echten Luecken als Fragen stellen

**Querverweise:**
- Gleiche Schritte duerfen in mehreren Prozessen dokumentiert sein
- Verknuepfungen zwischen Prozessen aktiv aufzeigen

---

## W4A (Work for All) - Bekannte Probleme

> **Kontext:** Work for All ist das ERP-System. Diese Probleme sind dokumentiert aber nicht loesbar durch eigene Tools.

### Performance & UX

| Problem | Details | Auswirkung |
|---------|---------|------------|
| **Ladezeiten** | ~8 Sek/Fenster-Element bei Angebotserstellung | Zeitverlust, Frustration |
| **Kein Rueckgaengig** | Keine Undo-Funktion | Fehler muessen manuell korrigiert werden |
| **Nur 1 Aufgabe sichtbar** | Dashboard zeigt nur eine Aufgabe | Keine Uebersicht offener Tasks |
| **Fenster blockiert** | Bei laengeren Operationen "haengt" | Muss warten |

### E-Mail & Dokumente

| Problem | Details | Auswirkung |
|---------|---------|------------|
| **E-Mail-Abruf manuell** | Muss aktiv abgerufen werden | Verzoegerte Reaktion |
| **Dokumente per Hand zuordnen** | Keine Auto-Zuordnung zu Projekten | Zeitaufwand, Fehlerquelle |

### Zeiterfassung & Stempeluhr

| Problem | Details | Auswirkung |
|---------|---------|------------|
| **Stempeluhr-Missbrauch** | RFID-Karten koennen von anderen (z.B. Kindern) genutzt werden | Falsche Zeitbuchungen |
| **Anmeldefenster fehlt** | Poppt nicht automatisch auf | Vergessene Stempelungen |
| **Sollzeit nicht aenderbar** | Aenderung der Sollstunden erfordert neuen Mitarbeiter-Datensatz | Workaround-Aufwand |

### Ungenutzte Features

| Feature | Grund | Potenzial |
|---------|-------|-----------|
| **Projektplankalender** | Zu umstaendlich, Outlook stattdessen | Evtl. spaeter aktivieren |
| **Besuchsberichte** | Nicht eingefuehrt | Koennte #23 unterstuetzen |
| **Verkaufschancen** | Nicht eingefuehrt | Koennte #23 unterstuetzen |

### Dokumentation W4A-Datenbank

→ Siehe `../KI_Automation/docs/ERP_Datenbank.md` fuer SQL-Schema und Tabellen

### Dokument-Ablage (funktioniert gut!)

| Aspekt | Details |
|--------|---------|
| **Server-Pool** | `\\appserver\Work4all\B001` |
| **Prinzip** | Dokumente liegen auf Server, W4A verlinkt darauf |
| **Vorteil** | Direkter PDF-Zugriff aus W4A moeglich |
| **Nutzbar fuer Tools** | Ja - Pfad aus DB lesen → Datei oeffnen

---

## Interne Kommunikation

### Monteure

| Kanal | Wann | Details |
|-------|------|---------|
| **Fruehbesprechung** | Taeglich morgens | 15-30 Min, Jaroslaw + Andreas |
| **Telefon** | Bei Bedarf | Fuer Rueckfragen, Probleme vor Ort |

### Buero

| Kanal | Wann | Details |
|-------|------|---------|
| **Persoenlich** | Taeglich | Kurze Absprachen |
| **W4A-Aufgaben** | Bei Bedarf | Fuer laengere Tasks mit Protokoll |

→ **Fazit:** Kommunikation funktioniert gut, kein Tool-Bedarf aktuell.

---

## Verwandte Repos

| Repo | Pfad | Inhalt |
|------|------|--------|
| **KI-Automation** | `../KI-Automation/` | Shared Libs, DB-Wissen, KI-News |
| **Auftragsmanagement** | `../Auftragsmanagement/` | Web-App Implementation |

---

## Phasen-Uebersicht (aus IDEEN.md)

| Phase | Beschreibung | Beispiel-Tools |
|-------|--------------|----------------|
| **0** | INFRASTRUKTUR | #58 Web-Plattform, #59 DB-Connector, #60 Auth |
| **1** | BASIS-MODULE | #1 Preislisten, #4 KI-Wissen ✅, #13 Inventar |
| **2** | KERNPROZESSE | #36 Beschaffung, #39 Montage-Mappe, #66 Wetter |
| **3** | KOMMUNIKATION | #12 E-Mail, #23 Pipeline, #41 Status-Live |
| **4** | COMMAND CENTER | #14 Dashboard (vereint alles) |
| **5** | KI-FEATURES | #5 Bauplan-KI, #7 Sprache, #62 Ersatzteil-KI |

---

## Changelog (Struktur-Aenderungen)

> **WICHTIG:** Bei relevanten Aenderungen hier dokumentieren!

| Datum | Aenderung | Details |
|-------|-----------|---------|
| 2025-12-12 | Repo erstellt | Aus KI_Automation ausgelagert |
| 2025-12-12 | IDEEN hierher | IDEEN.md, IDEEN_DETAILS.md, IDEEN_UEBERSICHT.html |
| 2025-12-12 | Analysen hierher | 5 Prozess-Analysen in `analysen/` |
| 2025-12-12 | Idee #66 | Montageplanung + Wetterprognose hinzugefuegt |
| 2025-12-12 | Hub-Struktur | Alle Repos jetzt unter `KI_Automation_Hub/` |
| 2025-12-12 | Rechnungsprozess | Neue Analyse + Mahnwesen dokumentiert |
| 2025-12-12 | Reparaturprozess | IST-Analyse erweitert (Ersatzteile, Lieferanten) |
| 2025-12-14 | Ideen-Workflow | 4 Dateien pflegen (inkl. PROZESS_VISUALISIERUNG.html) |
| 2025-12-14 | Prozess-Tracking | Offene Prozesse + Offene Fragen Tabellen, proaktiv erkennen |
| 2025-12-14 | Lagerprozess | Neue Analyse: Warenannahme, Einlagerung, Kommissionierung |
| 2025-12-14 | Idee #70 | Montagematerial-Pauschalen-Automatik (Umsatzverlust!) |
| 2025-12-14 | Aufmassprozess | Neue Analyse: Angebots-/Bestellaufmass, Foto-Workflow |
| 2025-12-14 | Einkaufsprozess | Neue Analyse: Lieferanten, Portale, Preisanfragen-Problem |
| 2025-12-14 | Idee #71 | Einkaufs-Workflow & Preismanagement (Preis-Cache, Anfrage-Tracking) |
| 2025-12-16 | Brainstorming-Regeln | Wissen zuerst praesentieren, nur Luecken nachfragen |
| 2025-12-16 | Idee #72 | Referenz-Automatik (Fotos nach Montage → Website) |
| 2025-12-16 | Idee #73 | Google-Bewertung Vorschlag (nach positiver Kommunikation) |
| 2025-12-16 | W4A-Dokumentation | Bekannte Probleme, ungenutzte Features dokumentiert |
| 2025-12-16 | Interne Kommunikation | Fruehbesprechung + Telefon, funktioniert gut |
| 2025-12-16 | Prozess-Updates | Lager, Montage, Rechnung, Reparatur, Anfrage erweitert |
| 2025-12-16 | Checklisten eingebunden | Tel. Anfragen + Reparatur aus Vorlagen-Ordner in Analysen |
| 2025-12-16 | #24 erweitert | Checklisten als Grundlage fuer digitale Erfassung dokumentiert |
| 2025-12-16 | Inventarprozess | Neue Analyse: W4A Inventar, Migration, Prueffristen, Wanderinventar |
| 2025-12-16 | Idee #74 | Prueffristen-Automatik (DGUV, TUeV, UVV) + Wanderinventar-Checkout |
| 2025-12-16 | Buergschaftsprozess | Neue Analyse: R+V Portal, W4A-Tracking, Limit-Status |
| 2025-12-16 | #71 erweitert | Preisinfo-Verteiler (Post-Preiserhoehungen kommunizieren) |
| 2025-12-16 | BAFA-Prozess | Neue Analyse: Weru Portal, NachweisService KRITISCH |
| 2025-12-16 | #3 erweitert | KRITISCH! Auto-Erinnerung nach Zahlung, Foerder-Position als Trigger |
