# W4A-Ersatz Konzept

**Erstellt:** 2025-12-22 | **Status:** Konzeptphase | **Strategie:** Option B (schrittweise ersetzen)

---

## Zielsetzung

Vollstaendiger Ersatz von Work4All (W4A) durch ein eigenes System mit folgenden Grundprinzipien:

| Prinzip | Beschreibung |
|---------|--------------|
| **Autonomie-First** | System handelt selbststaendig wo moeglich |
| **Lernendes System** | Verbessert sich durch User-Korrekturen |
| **Einfache Bedienung** | So wenig Klicks wie moeglich |
| **Ueberall erreichbar** | Responsive: Smartphone, Tablet, Laptop, PC |
| **Workflows neu denken** | Nicht 1:1 kopieren, sondern optimieren |
| **Komplett entkoppelt** | Eigenstaendiges System, KEIN W4A-Addon |

---

## Dokument-Uebersicht

| Datei | Inhalt |
|-------|--------|
| [01_ANGEBOT.md](01_ANGEBOT.md) | Workflow: Angebot erstellen (Budget + Voll) |
| [02_BESTELLUNG.md](02_BESTELLUNG.md) | Workflow: Bestellung → AB → Wareneingang |
| [03_RECHNUNG.md](03_RECHNUNG.md) | Workflow: Rechnung → Zahlung → Mahnung |
| [04_MONTAGE.md](04_MONTAGE.md) | Workflow: Montageplanung + Monteur-App |
| [05_ANFRAGE_CRM.md](05_ANFRAGE_CRM.md) | Workflow: Anfrage/CRM + Pipeline |
| [06_REPARATUR.md](06_REPARATUR.md) | Workflow: Reparatur (MAXIMAL autonom!) |
| [GPS_TRACKING.md](GPS_TRACKING.md) | GPS-Tracking & Echtzeit-Analyse |
| [KI_ASSISTENT.md](KI_ASSISTENT.md) | Multi-Channel: Telefon, E-Mail, WhatsApp, Telegram |
| [DATENMODELL.md](DATENMODELL.md) | Technische DB-Struktur |
| [TECHNISCHE_ARCHITEKTUR.md](TECHNISCHE_ARCHITEKTUR.md) | Tech-Stack, Hosting, KI-Integration |
| [UI_UX_DESIGN.md](UI_UX_DESIGN.md) | Design-Prinzipien, Wireframes, Komponenten |
| [PROTOTYP_PLAN.md](PROTOTYP_PLAN.md) | MVP-Plan: Reparatur-Workflow, Erste Schritte |

---

## Entkopplungs-Strategie

**WICHTIG:** Das neue System ist KEIN Addon/Plugin fuer W4A!

```
┌─────────────────┐     ┌─────────────────┐
│   ALTES SYSTEM  │     │   NEUES SYSTEM  │
│      (W4A)      │     │   (Eigenbau)    │
├─────────────────┤     ├─────────────────┤
│ - Altdaten      │     │ - Eigene DB     │
│ - Parallel      │ ──► │ - Eigene UI     │
│   laeuft noch   │     │ - Eigene Logik  │
│                 │     │ - KI-Assistent  │
└─────────────────┘     └─────────────────┘
        │                       │
        │    MIGRATION          │
        └───────────────────────┘
              (einmalig)
```

| Aspekt | Entscheidung |
|--------|--------------|
| **Datenhaltung** | Eigene Datenbank (PostgreSQL) |
| **W4A-Zugriff** | NUR Lesen fuer Migration, dann Abkoppeln |
| **Parallelbetrieb** | Moeglich waehrend Uebergang |
| **Abhaengigkeit** | KEINE - System laeuft ohne W4A |
| **DATEV** | Eigener Export (nicht ueber W4A) |
| **Dokumente** | Eigener Storage (nicht W4A Server-Pool) |

---

## Kostenvergleich

| Posten | W4A aktuell | Eigenes System |
|--------|-------------|----------------|
| ERP-Lizenz | >4.000€/Jahr | 0€ |
| FIBU-Loesung | inklusive | 300-500€/Jahr |
| Hosting (Cloud) | ~100€ | ~450€ |
| **Gesamt** | **~4.100€/Jahr** | **~950€/Jahr** |
| **Ersparnis** | - | **~3.150€/Jahr** |

---

## Autonomie-Hierarchie

```
AUTONOM          System handelt selbststaendig
    ↓
AUTOMATISCH      System handelt nach Trigger
    ↓
HALBAUTOMATISCH  User startet, System fuehrt aus
    ↓
MANUELL          Nur als Notfall-Fallback
```

---

## W4A-Probleme (dokumentiert)

### Performance & UX

| Problem | Auswirkung |
|---------|------------|
| Ladezeiten (~8 Sek/Element) | Zeitverlust, Frustration |
| Kein Rueckgaengig | Fehler muessen manuell korrigiert werden |
| Nur 1 Aufgabe sichtbar | Keine Uebersicht |
| Fenster blockiert bei Operationen | Warten |

### Positionsnummern (kritisch!)

| Problem | Beispiel |
|---------|----------|
| Nummern werden "korrigiert" | User gibt "1.5" ein → W4A macht "1.1" |
| Dritte Ebene nicht moeglich | "1.1.1" wird zu "1.1" |
| Bei Speichern/Laden zerstoert | Ausschreibungs-LV-Nummern gehen kaputt |
| **Workaround aktuell** | Nummer manuell im Positionstext verstecken |

### Positions-Tracking (kritisch!)

| Problem | Auswirkung |
|---------|------------|
| Geloeschte Position = Verknuepfung weg | Nicht nachvollziehbar ob bestellt/geliefert |
| Keine Versionierung | Aenderungen nicht nachvollziehbar |
| Kein Soft-Delete | Daten sind wirklich weg |

---

## Kern-Architektur (Neues System)

### Positions-Management

**Grundprinzip:** Positionen werden NIE geloescht, nur Status geaendert.

```
Position #4711
├── Version 1: "Fenster 1200x1400"  [ERSETZT]
│   └── Angebot 240504
│
└── Version 2: "Fenster 1200x1600"  [AKTIV]
    ├── Auftrag 240286
    ├── Bestellung 240312
    └── Lieferung (offen)
```

**Positions-Lifecycle:**

```
ANGEBOT → AUFTRAG → BESTELLUNG → LIEFERUNG → RECHNUNG
   │         │          │            │           │
   └─────────┴──────────┴────────────┴───────────┘
                Gleiche Position-ID durchgaengig
```

**Status-Werte:**
- `angebot` → `beauftragt` → `bestellt` → `geliefert` → `abgerechnet`
- Unter-Status: `aktiv`, `ersetzt`, `storniert`

### Positionsnummern

| Aspekt | W4A (kaputt) | Neues System |
|--------|--------------|--------------|
| Datentyp | Berechnet | **VARCHAR (Freitext)** |
| Format | Nur X.X | **Beliebig** (1.1.1.1, A.1, etc.) |
| Speichern | Wird "korrigiert" | **Exakt wie eingegeben** |
| Ausschreibungen | Zerstoert LV-Nummern | **Uebernimmt 1:1** |

### Nummernkreise (Dokumente)

Dokument-Nummern (Angebot, Auftrag, etc.) funktionieren in W4A - Konzept beibehalten:
- Atomare Vergabe (keine Race Conditions)
- Einmal vergeben = nie wieder freigeben
- Konfigurierbar pro Dokumenttyp
- Luecken sind OK (besser als Duplikate)

---

## Lernendes System

### Konzept: Stille Sammlung + Woechentlicher Review

```
USER AENDERT ETWAS
       │
       ▼
  Aenderung erfasst ──── User merkt nichts
       │
       ▼
  ┌─────────────┐
  │  KRITISCH?  │
  └─────────────┘
       │
   ────┴────
   │       │
  JA      NEIN
   │       │
   ▼       ▼
SOFORT   SAMMELN
Andreas  fuer
fragen   Wochen-Review
```

### Kritisch vs. Normal

| Kritisch (sofort) | Normal (sammeln) |
|-------------------|------------------|
| Preis-Aenderung > 20% | Kleine Preis-Anpassungen |
| Lieferant bei laufender Bestellung | Lieferant bei neuem Angebot |
| Termin verschoben > 1 Woche | Termin um 1-2 Tage |
| Kunde storniert | Rabatt geaendert |
| Regel wuerde deaktiviert | Neue Regel-Idee |
| Sicherheitsrelevant (BAFA!) | Formular-Feld-Vorschlaege |

### Woechentlicher Digest

**Zeitpunkt:** Konfigurierbar (Freitag Feierabend ODER Montag morgen)

**Inhalt:**
1. **Muster erkannt** - Mehrfach gleiche Aenderung → Regel-Vorschlag
2. **Selbst revidiert** - User hat zurueckgeaendert → nur Info, keine Aktion
3. **Einzelne Aenderungen** - Unklar ob Muster → Beobachten oder Regel
4. **Formular-Vorschlaege** - Felder die oft nachtraeglich ergaenzt werden

### Intelligente Konsolidierung

```
Rohdaten:                          Konsolidiert:
Mo: Sandra, Haustuer 300→450€      "Haustuer-Pauschale"
Di: Sandra, Haustuer 300→450€      4 Aenderungen, 2 Personen
Mi: Roland, Haustuer 300→400€      Tendenz: ~425€
Fr: Sandra, Haustuer 300→450€      → Klare Regel erkennbar
```

Selbst revidierte Aenderungen werden gefiltert (kein Rauschen).

### Confidence-basierte Autonomie

| Confidence | Verhalten |
|------------|-----------|
| < 70% | User muss bestaetigen |
| 70-90% | Auto, aber in Review-Queue |
| > 90% | Volle Autonomie |

### Weg zur Autonomie (Phasen)

| Phase | Zeitraum | Beschreibung | Ziel |
|-------|----------|--------------|------|
| 1 | Monat 1-3 | System schlaegt vor, User bestaetigt alles | Muster erkennen |
| 2 | Monat 3-6 | Regeln >90% Confidence → automatisch | ~30% autonom |
| 3 | Monat 6-12 | Schwellenwert auf 80% senken | ~70% autonom |
| 4 | Monat 12+ | System handelt selbststaendig | ~95% autonom |

---

## Berechtigungen (Lernsystem)

| Rolle | Lern-Fragen | Regeln aendern | Freigabe noetig |
|-------|-------------|----------------|-----------------|
| **System-Admin** (Andreas) | Ja | Ja | Nein |
| **Co-Trainer** (Jaroslaw) | Ja (Kalkulation) | Vorschlagen | Ja → Andreas |
| **User** (Alle anderen) | Nein | Nein | - |

### Schutz vor Rueckschritten

- User-Aenderungen landen still bei Andreas als Vorschlag
- User erhaelt keine Info dazu
- Autonomie-Konflikte werden erkannt
- Rueckschritte nur mit Andreas-Freigabe
- Alles wird protokolliert

---

## Konfigurator-Integration

| Konfigurator | Aktuell | Zukunft | Strategie |
|--------------|---------|---------|-----------|
| **Weru WoT** | XML-Import | Neue Software mit API | API-ready bauen |
| **Warema** | Kryptisch/PDF | Evtl. API? | PDF-OCR als Fallback |
| **Drutex** | WoT-Workaround | Preisliste? | Ca.-Preise aus Upload |
| **Klaiber** | ? | ? | Klaeren |

### Drutex-Workaround (aktuell)

Drutex hat keinen eigenen Konfigurator. Wird in Weru WoT konfiguriert mit:
- Weru-Preisen (falsch)
- Angepasstem Rabatt um Drutex-EK zu simulieren

### PDF-Fallback mit KI

Fuer Konfiguratoren ohne API/XML:
1. PDF hochladen
2. Claude Vision analysiert
3. Positionen mit Confidence-Score vorschlagen
4. User prueft und uebernimmt

### Preislisten-Upload

Lieferanten-Preislisten (Excel/CSV) hochladen fuer:
- Ca.-Preise bei Budget-Angeboten
- Schnelle Erstkalkulationen
- KI hilft beim Spalten-Mapping

---

## Dokument-Ausgabe (PDF)

### Wasserzeichen-Integration (W4A kann das nicht!)

**Was W4A bereits generiert:**
- Header (Logo, "J.S. Fenster & Tueren", Slogan)
- Kontaktdaten rechts
- Footer (Geschaeftsfuehrer, Bank, IBAN, USt-IdNr)

**Was W4A NICHT kann:**
- Wasserzeichen in der Mitte (stilisierte Fenster-Grafik in Grau/Orange)

**Loesung neues System:** Wasserzeichen-Grafik als Hintergrund-Layer

```
┌─────────────────────────┐
│  [Header]               │
│  [Kontakt]              │
│                         │
│        ╔═══╗            │  ← Wasserzeichen (halbtransparent)
│       ╔╝   ║            │     aus Briefpapier-Vorlage extrahieren
│       ║    ╚═══╗        │
│       ╚════════╝        │
│                         │
│  [Content darueber]     │
│                         │
│  [Footer]               │
└─────────────────────────┘
```

**Vorlagen-Pfad:** `Z:\Vorlagen\Briefpapier\`
- Seite 1: `JS Briefpapier SEPA fuer Druckerei - GmbH.pdf`
- Seite 2+: `JS Briefpapier Seite 2 fuer Druckerei - GmbH.pdf`

### Pflicht-Elemente (aus W4A uebernehmen)

| Element | Status |
|---------|--------|
| Briefkopf + Logo | Muss (aus Briefpapier-Vorlage) |
| Wasserzeichen (Fenster-Grafik) | Muss (aus Briefpapier-Vorlage) |
| Kunde + Anschrift | Muss |
| Projekt-Zuordnung | Muss |
| Hierarchische Positionen | Muss |
| Technische Details | Muss |
| Fenster-Skizzen (aus XML) | Muss |
| Alternativ-Positionen (Klammern) | Muss |
| Rabatt-Ausweis | Muss |
| MwSt + Gesamtbetrag | Muss |
| Zahlungsbedingungen | Muss |
| Unterschriftsfeld | Muss |
| Footer (IBAN, USt-IdNr, HRB) | Muss (aus Briefpapier-Vorlage) |

---

## Offene Punkte

### Zu klaeren

- [ ] DATEV: Steuerberater akzeptiert lexoffice/sevDesk?
- [ ] W4A: Kuendigungsfrist? Naechster Termin?
- [ ] Warema: XML-Format pruefbar?
- [ ] Klaiber: Welches Format?
- [ ] Drutex: Preisliste verfuegbar?

### Noch zu konzeptionieren

- [x] Workflow: Bestellung → AB-Abgleich → Wareneingang
- [x] Workflow: Rechnung → Mahnung → DATEV
- [x] Workflow: Montageplanung (inkl. Monteur-App + Spracheingabe)
- [x] Workflow: Anfrage/CRM (inkl. Pipeline, Marketing-Auswertung)
- [x] Workflow: Reparatur (MAXIMAL autonom - 80% Aufwand weg!)
- [x] Technische Architektur (Detail)
- [x] UI/UX Design

---

## Changelog

| Datum | Aenderung |
|-------|-----------|
| 2025-12-22 | Dokument erstellt |
| 2025-12-22 | Grundprinzipien: Autonomie, Lernendes System |
| 2025-12-22 | Alle 6 Workflows dokumentiert |
| 2025-12-22 | GPS-Tracking & Echtzeit-Analyse |
| 2025-12-22 | KI-Assistent Multi-Channel |
| 2025-12-22 | Entkopplungs-Strategie dokumentiert |
| 2025-12-22 | Tool-Referenzen zu allen Workflows |
| 2025-12-22 | Aufteilung in einzelne Dateien |
| 2025-12-22 | Technische Architektur dokumentiert |
| 2025-12-22 | UI/UX Design mit Wireframes erstellt |
| 2025-12-22 | Prototyp-Plan mit MVP-Scope (Stefan-App) |
