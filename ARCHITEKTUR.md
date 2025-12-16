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
| 2025-12-16 | Grundsatzentscheidungen: Outlook ersetzen, Responsive Web, Cloud |
| 2025-12-13 | Modul-Struktur als Zukunfts-Ueberlegung dokumentiert |
| 2025-12-13 | Dokument erstellt, ERP-Strategie dokumentiert |
