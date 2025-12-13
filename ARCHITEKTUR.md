# Architektur-Strategie

**Stand:** 2025-12-13 | **Entscheidung:** W4A behalten + eigene Tools

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
| **Hosting** | On-Premise (Firmenserver) |

---

## Warum nicht neues ERP?

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
| 2025-12-13 | Modul-Struktur als Zukunfts-Ueberlegung dokumentiert |
| 2025-12-13 | Dokument erstellt, ERP-Strategie dokumentiert |
