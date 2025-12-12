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
├── analysen/               # Prozess-Dokumentationen
│   ├── Anfrageprozess_Analyse.md
│   ├── Bestellprozess_Analyse.md
│   ├── Montageprozess_Analyse.md
│   ├── Reklamationsprozess_Analyse.md
│   └── Reparaturprozess_Analyse.md
├── IDEEN.md                # 62+ Tool-Ideen (verdichtet)
├── IDEEN_DETAILS.md        # Technische Details + W4A-Status
├── IDEEN_UEBERSICHT.html   # Interaktive Ansicht + Architektur
└── CLAUDE.md               # Diese Datei
```

---

## Ideen-Management

### IDEEN-Dateien synchron halten!

Bei Aenderungen IMMER alle 3 Dateien pflegen:
1. `IDEEN.md` - Kurzversion (neue Ideen hier eintragen)
2. `IDEEN_DETAILS.md` - Technische Details + Quick-Reference Tabelle
3. `IDEEN_UEBERSICHT.html` - Karten, Status, Komplexitaet + Architektur-Seite

### Neue Ideen aufnehmen

**PFLICHT vor Vorschlag - Duplikat-Pruefung:**
1. Quick-Reference-Tabelle in IDEEN_DETAILS.md lesen
2. Keywords gegen bestehende Titel pruefen
3. Verwandte Kategorien checken

**Vorgehen:**
- Aehnliche Idee gefunden: "Erweiterung von #X - dort ergaenzen?"
- Keine Ueberschneidung: "Als neue Idee #Y aufnehmen?"
- Naechste freie Nummer, Phase + Komplexitaet einschaetzen

### Ideen proaktiv erkennen

Bei Gespraechen neue Tool-Ideen erkennen:
- User hat Problem/Wunsch? → Potentielle Idee!
- Workflow koennte automatisiert werden? → Idee!

---

## Prozess-Analysen

| Datei | Prozess | Status |
|-------|---------|--------|
| `Anfrageprozess_Analyse.md` | Eingang → Angebot → Nachverfolgung | ✅ IST dokumentiert |
| `Bestellprozess_Analyse.md` | Auftrag → Bestellung → AB → Wareneingang | ✅ IST dokumentiert |
| `Reparaturprozess_Analyse.md` | Reparatur-Lifecycle + Automatisierung | ✅ IST + SOLL |
| `Montageprozess_Analyse.md` | Montage-Workflow | ✅ IST dokumentiert |
| `Reklamationsprozess_Analyse.md` | Reklamations-Handling | ✅ IST dokumentiert |

### Neue Prozess-Analyse erstellen

Wenn User groessere Ablauf-Details erklaert:
1. Fragen: "Soll ich `analysen/[Prozess]_Analyse.md` anlegen?"
2. Dokumentieren: IST-Zustand, Schmerzpunkte, Automatisierungspotential
3. Diese Tabelle aktualisieren
4. Verknuepfte IDEEN mit Prozess-Verweis versehen

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
