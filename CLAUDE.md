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
│   └── Reparaturprozess_Analyse.md
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

### Offene Prozesse (fuer Brainstorming)

| Prozess | Notizen/Fragen | Erkannt am |
|---------|----------------|------------|
| Personal/Urlaub | Urlaubsantraege, Kapazitaet, Krankmeldung | 2025-12-14 |
| Fuhrpark | Fahrzeuge, Tanken, Wartung, TUeV | 2025-12-14 |
| Buchhaltung | Eingangsrechnungen, DATEV, Konten | 2025-12-14 |
| After-Sales | Wartungsvertraege, Nachbetreuung | 2025-12-14 |

### Offene Fragen zu bestehenden Prozessen

| Prozess | Frage/Erweiterung | Notiert am |
|---------|-------------------|------------|
| - | - | - |

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
