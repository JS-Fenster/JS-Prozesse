# Architektur-Strategie

**Stand:** 2025-12-21 | **Entscheidung:** W4A behalten + eigene Tools + LLM-Automation

---

## Kernentscheidung

| Bereich | System | Grund |
|---------|--------|-------|
| **Stammdaten** | W4A | Kunden, Lieferanten, Artikel - alles vorhanden |
| **Dokumente** | W4A | Angebote, Auftraege, Rechnungen - gewohnt |
| **Finanzen** | W4A | Rechnungswesen, Mahnwesen - funktioniert gut |
| **Operative Prozesse** | Eigene Tools | W4A kann das nicht gut |

---

## System-Architektur

```
┌─────────────────────────────────────────────────────────────┐
│                    EIGENE WEB-TOOLS                         │
│                                                             │
│  #68 Planungs-Dashboard    #36 Beschaffungs-Dashboard       │
│  #39/40/41 Montage-Suite   #9 Reparatur-Verwaltung          │
│                                                             │
│         Flask + Bootstrap (#58) | Auth (#60)                │
└─────────────────────────┬───────────────────────────────────┘
                          │
                    SQL (pyodbc)
                    #59 DB-Connector
                          │
┌─────────────────────────▼───────────────────────────────────┐
│                    W4A (ERP)                                │
│            192.168.16.202\SQLEXPRESS                        │
│                                                             │
│  dbo.Kunde | dbo.Auftrag | dbo.Bestellung | dbo.Rechnung   │
└─────────────────────────────────────────────────────────────┘
```

---

## Datenfluss

| Richtung | Was | Beispiel |
|----------|-----|----------|
| **LESEN** | Stammdaten, Status, Historie | Kunde laden, Bestellstatus pruefen |
| **SCHREIBEN** | Status-Updates, neue Eintraege | Ticket erstellen, Termin eintragen |
| **NIEMALS** | Stammdaten aendern ohne Rueckfrage | Kunde loeschen, Preise aendern |

---

## Technologie-Stack

| Schicht | Technologie |
|---------|-------------|
| **Frontend** | HTML/CSS/JS, Bootstrap (responsive) |
| **Backend** | Python Flask |
| **Datenbank** | SQL Server (W4A) via pyodbc |
| **Auth** | Session-basiert, Rollen (GF/Buero/Monteur) |
| **Hosting** | Cloud (Details offen) |

---

## Grundsatzentscheidungen (2025-12-16)

| Frage | Entscheidung | Begruendung |
|-------|--------------|-------------|
| **Outlook ersetzen?** | Ja, komplett | Mehr Kontrollmechanismen moeglich |
| **Mobile Nutzung** | Responsive Web | Kein Native-App-Aufwand, ein System fuer alle |
| **Hosting** | Cloud | Server-Kosten + Wartung sparen |

### Konsequenzen

**Outlook ersetzen (#68):**
- Eigenes Planungs-Dashboard wird EINZIGE Quelle fuer Termine
- Kein Sync noetig, keine Doppelpflege
- Outlook bleibt NUR fuer E-Mail

**Responsive Web:**
- Ein Codebase fuer Desktop + Tablet + Handy
- PWA-Option offen (installierbar, offline-faehig)
- Kein App-Store-Aufwand

**Cloud-Hosting:**
- W4A-Datenbank bleibt on-premise (SQL Server)
- Eigene Tools in Cloud
- Verbindung: VPN oder sichere API
- Vorteil: Zugriff von ueberall, weniger lokale Wartung

### Cloud-Stack (aktuell)

| Dienst | Verwendung | Status |
|--------|------------|--------|
| **Supabase** | Datenbank (ERP-Cache), Auth, Realtime | ✅ In Nutzung (Auftragsmanagement) |
| **Cloudflare** | Hosting, CDN, DNS | ✅ In Nutzung |
| **Azure** | Erweiterung (z.B. VMs, Functions) | 💬 In Diskussion |

**Supabase-Projekt:** `https://rsmjgdujlpnydbsfuiek.supabase.co`

### Hybrid-Architektur

```
┌─────────────────────────────────────────────────────┐
│                   CLOUDFLARE                        │
│            (CDN, DNS, Edge Functions)               │
└─────────────────────┬───────────────────────────────┘
                      │
┌─────────────────────▼───────────────────────────────┐
│                   SUPABASE                          │
│                                                     │
│   - PostgreSQL (ERP-Cache, Workflow-Daten)          │
│   - Auth (Login, Rollen)                            │
│   - Realtime (Live-Updates)                         │
│   - Edge Functions (Serverless)                     │
└─────────────────────┬───────────────────────────────┘
                      │
                API / Sync-Job
                      │
┌─────────────────────▼───────────────────────────────┐
│            ON-PREMISE (Firma)                       │
│                                                     │
│   W4A SQL Server (192.168.16.202)                   │
│   - Stammdaten (Quelle der Wahrheit)                │
│   - Dokumente                                       │
└─────────────────────────────────────────────────────┘
```

### Offene Fragen Cloud

- [ ] Azure: Wofuer genau? (VMs, Functions, anderes?)
- [ ] Sync W4A → Supabase: Wie oft? Echtzeit oder scheduled?
- [ ] Cloudflare Pages oder Workers fuer Frontend?

---

## Source of Truth Prinzip (WICHTIG!)

> **Kernregel:** Jedes Datum hat genau EIN System als "Quelle der Wahrheit". Das andere System liest nur.

### Aufteilung

| System | Source of Truth fuer | Lesen erlaubt |
|--------|----------------------|---------------|
| **W4A** | Stammdaten (Kunden, Lieferanten, Artikel) | ✅ Eigenes System |
| **W4A** | Angebote, Auftraege, Rechnungen | ✅ Eigenes System |
| **W4A** | Buchhaltung, DATEV | ✅ Eigenes System |
| **W4A** | Historische Daten | ✅ Eigenes System |
| **Eigenes System** | Operative Planung (Termine, Montage) | ❌ W4A nicht |
| **Eigenes System** | Tickets, Aufgaben | ❌ W4A nicht |
| **Eigenes System** | Echtzeit-Status | ❌ W4A nicht |
| **Eigenes System** | Workflow-Daten | ❌ W4A nicht |
| **Eigenes System** | LLM-generierte Inhalte | ❌ W4A nicht |

### Warum?

Problem bei Hybrid-Systemen: Wenn W4A-Daten geloescht/geaendert werden, koennte eigenes System inkonsistent werden → Auftraege gehen unter!

**Loesung:** Klare Trennung + Konsistenz-Checks (siehe unten).

---

## LLM-Architektur (Agentic AI)

> **Ziel:** Vollautomation wo moeglich, aber mit Sicherheitsnetz.

### Ablauf

```
┌─────────────────────────────────────────────────────────┐
│                    EINGANG                              │
│  E-Mail │ Datei │ Foto │ Sprache │ Formular            │
└────────────────────────┬────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────┐
│                 LLM-VERARBEITUNG                        │
│                                                         │
│  1. Analysieren (was ist das?)                          │
│  2. Extrahieren (Daten rausziehen)                      │
│  3. Klassifizieren (wohin gehoert es?)                  │
│  4. Vorschlag machen (was tun?)                         │
│                                                         │
│  OUTPUT: Strukturierte Daten + Confidence-Score         │
└────────────────────────┬────────────────────────────────┘
                         │
              ┌──────────┴──────────┐
              │                     │
         Confidence              Confidence
         > 95%                   < 95%
              │                     │
              ▼                     ▼
┌─────────────────────┐  ┌─────────────────────┐
│  AUTO-AKTION        │  │  MENSCH-REVIEW      │
│  (mit Audit-Log)    │  │  (Vorschlag zeigen) │
└─────────────────────┘  └─────────────────────┘
```

### Confidence-Score Regeln

| Confidence | Aktion |
|------------|--------|
| > 95% | Auto-Ausfuehrung, nur Logging |
| 80-95% | Auto-Ausfuehrung, aber in "Review-Queue" |
| < 80% | Mensch muss bestaetigen |
| < 50% | Warnung: "LLM unsicher, bitte pruefen" |

### Stufenweise Einfuehrung

| Stufe | Beschreibung | Wann |
|-------|--------------|------|
| **1** | LLM schlaegt vor, Mensch bestaetigt | Start |
| **2** | LLM handelt autonom bei "sicheren" Aufgaben | Nach 3-6 Monaten |
| **3** | Volle Autonomie mit Ausnahme-Eskalation | Spaeter |

---

## Sicherheitsmechanismen

### 1. Audit-Log (PFLICHT!)

Jede LLM-Aktion wird protokolliert:

```
{
  "timestamp": "2025-12-21T10:30:00Z",
  "action": "ticket_created",
  "source": "email",
  "source_id": "msg-123456",
  "llm_model": "claude-sonnet-4",
  "confidence": 0.92,
  "auto_executed": true,
  "data": { "kunde": "Müller", "betreff": "Fenster klemmt" },
  "w4a_projekt": "P241234"
}
```

### 2. Konsistenz-Check (Taeglich)

Automatischer Abgleich jeden Morgen:

```
07:00 Uhr - KONSISTENZ-CHECK
┌─────────────────────────────────────────┐
│ ✅ 45 Auftraege synchron                │
│ ⚠️  2 nur in Supabase (W4A fehlt)      │
│ ⚠️  1 nur in W4A (nicht importiert)    │
│ ❌ 0 mit Daten-Konflikt                 │
└─────────────────────────────────────────┘
→ Bei Warnungen: E-Mail an Andreas
```

### 3. W4A nur LESEN

| Operation | Erlaubt? |
|-----------|----------|
| Kunde suchen | ✅ |
| Projekt-Status lesen | ✅ |
| Bestellung anlegen | ❌ Nur durch Menschen |
| Rechnung erstellen | ❌ Nur durch Menschen |
| Daten loeschen | ❌ NIEMALS |

**Grund:** Wenn LLM in W4A schreibt und Fehler macht → schwer rueckgaengig, DATEV-Probleme.

---

## LLM-geeignete Aufgaben (Priorisiert)

| Prio | Aufgabe | Idee | Risiko |
|------|---------|------|--------|
| 1 | E-Mail klassifizieren + Ticket erstellen | #12, #24 | Niedrig |
| 2 | Dokumente analysieren (AB, Rechnung) | #27, #56 | Niedrig |
| 3 | Buchungskonto vorschlagen | #82 | Niedrig |
| 4 | Schadensmeldung aus Foto/Sprache | #77 | Mittel |
| 5 | Bauplan analysieren | #5 | Hoch |

---

## W4A-Kosten & Strategie-Optionen

### Aktuelle Kosten

| Posten | Kosten/Jahr |
|--------|-------------|
| **W4A Lizenz** | >4.000€ netto |
| Server, Wartung | Zusaetzlich |

### Kosten eigenes System (Cloud)

| Posten | Kosten/Jahr |
|--------|-------------|
| Supabase Pro | ~300€ |
| Cloudflare | ~100€ |
| Sonstiges | ~50€ |
| **Summe** | **~450€/Jahr** |

---

## Option A: W4A behalten + eigene Tools

> **Strategie:** W4A bleibt Kernsystem, eigene Tools nur fuer operative Prozesse.

```
┌─────────────────────────────────────────┐
│           EIGENE TOOLS                  │
│  Planung, Tickets, Dashboards, LLM      │
│            (~450€/Jahr)                 │
└────────────────┬────────────────────────┘
                 │ lesen
                 ▼
┌─────────────────────────────────────────┐
│              W4A (ERP)                  │
│  Stammdaten, Angebote, Auftraege,       │
│  Rechnungen, Buchhaltung, DATEV         │
│            (>4.000€/Jahr)               │
└─────────────────────────────────────────┘
```

| Pro | Contra |
|-----|--------|
| Kein Migrationsrisiko | 4.000€+/Jahr bleiben |
| Schnell umsetzbar | Zwei Systeme parallel |
| DATEV funktioniert | Abhaengigkeit bleibt |
| Team kennt W4A | |

**Gesamtkosten: ~4.500€/Jahr**

---

## Option B: W4A schrittweise ersetzen

> **Strategie:** Modul fuer Modul aus W4A raus, am Ende nur noch FIBU-Loesung.

```
Phase 1-3 (18-24 Monate)
┌─────────────────────────────────────────┐
│         EIGENES SYSTEM                  │
│  Stammdaten, Angebote, Auftraege,       │
│  Bestellungen, Planung, Tickets, LLM    │
│            (~450€/Jahr)                 │
└────────────────┬────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────┐
│         FIBU-LOESUNG                    │
│  lexoffice / sevDesk / W4A-FIBU-only    │
│          (200-500€/Jahr?)               │
└─────────────────────────────────────────┘
```

### Phasen

| Phase | Dauer | Was raus aus W4A |
|-------|-------|------------------|
| **1** | 3-6 Mon | Planung, Tickets, Operative Tools |
| **2** | 6-12 Mon | Stammdaten, Dokumente |
| **3** | 6-12 Mon | Angebote, Auftraege, Bestellungen |
| **4** | Entscheidung | Buchhaltung (siehe Optionen) |

### FIBU-Optionen (Phase 4)

| Option | Kosten/Jahr | Bemerkung |
|--------|-------------|-----------|
| W4A nur FIBU-Lizenz | ? | Nachfragen ob moeglich |
| lexoffice / sevDesk | 200-500€ | Steuerberater muss OK geben |
| Eigene FIBU | ❌ | Nicht empfohlen (GoBD!) |

| Pro | Contra |
|-----|--------|
| **~3.000€+ Ersparnis/Jahr** | Migrationsaufwand |
| Volle Kontrolle | 18-24 Monate Entwicklung |
| Keine W4A-Abhaengigkeit | Steuerberater muss mitspielen |
| Moderne Technologie | Risiko bei FIBU-Wechsel |

**Gesamtkosten Ziel: ~650-950€/Jahr**

---

### Offene Fragen (vor Entscheidung klaeren)

- [ ] Gibt es W4A reine FIBU-Lizenz? Kosten?
- [ ] Steuerberater: Akzeptiert er lexoffice/sevDesk?
- [ ] Wie komplex ist die Buchhaltung?

---

## Warum nicht komplett neues ERP kaufen?

| Risiko | Auswirkung |
|--------|------------|
| Datenmigration | Fehleranfaellig, monatelange Arbeit |
| Schulung | Alle Mitarbeiter umlernen (6-12 Monate) |
| Kosten | 50-200k EUR + laufende Lizenzkosten |
| Steuerberater | Schnittstellen muessen angepasst werden |
| Stillstand | Tagesgeschaeft laeuft waehrend Umstellung weiter |

---

## Implementierungs-Reihenfolge

1. **Phase 0:** Infrastruktur (#58, #59, #60, #64, #68)
2. **Phase 1:** Kritische Tools (#36 Beschaffung, Montage-Suite)
3. **Phase 2-5:** Schrittweise weitere Tools

→ Details: [IDEEN.md](IDEEN.md) | [PROZESS_VISUALISIERUNG.html](PROZESS_VISUALISIERUNG.html)

---

## Detaillierte Architektur

Fuer Reparatur-spezifische Architektur siehe:
→ [analysen/Reparaturprozess_Analyse.md](analysen/Reparaturprozess_Analyse.md#vorgeschlagene-system-architektur)

---

## Zukunfts-Ueberlegung: Modul-Struktur

Statt 64 separate Tools → 6-8 groessere Module mit Tabs/Views:

| Modul | Ideen | Gemeinsamer Nenner |
|-------|-------|-------------------|
| **Beschaffung** | #36, #33, #53, #55, #56, #57 | Bestellung → Lieferung |
| **Montage** | #39/#40/#41, #66, #29 | Monteur-Tagesgeschaeft |
| **Service** | #9, #24 | Tickets, Reparaturen |
| **Planung** | #68, #11, #22 | Termine, Kalender, Routen |
| **Kunden** | #12, #23, #25, #47, #30 | CRM, Kommunikation |
| **Finanzen** | #31, #50, #51, #65 | Geld, Rechnungen |

**Vorteile:** Weniger Kontextwechsel, gemeinsame Datenbasis, einfachere Navigation.

> **Status:** Idee dokumentiert, nicht priorisiert. Erst Erfahrung mit einzelnen Tools sammeln.

---

## Changelog

| Datum | Aenderung |
|-------|-----------|
| 2025-12-21 | W4A-Kosten dokumentiert: >4.000€/Jahr, zwei Strategie-Optionen |
| 2025-12-21 | Option A: W4A behalten + eigene Tools |
| 2025-12-21 | Option B: W4A schrittweise ersetzen (Phasen, FIBU-Optionen) |
| 2025-12-21 | LLM-Architektur: Agentic AI, Confidence-Score, Audit-Log |
| 2025-12-21 | Source of Truth Prinzip: W4A vs. eigenes System |
| 2025-12-21 | Sicherheitsmechanismen: Konsistenz-Check, W4A nur lesen |
| 2025-12-16 | Grundsatzentscheidungen: Outlook ersetzen, Responsive Web, Cloud |
| 2025-12-13 | Modul-Struktur als Zukunfts-Ueberlegung dokumentiert |
| 2025-12-13 | Dokument erstellt, ERP-Strategie dokumentiert |
