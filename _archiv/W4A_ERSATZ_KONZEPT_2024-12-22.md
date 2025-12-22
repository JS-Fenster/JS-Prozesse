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

### Entkopplungs-Strategie

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

## GPS-Tracking & Echtzeit-Analyse

> **Zentrales Feature:** GPS-Tracking ermoeglicht viele autonome Funktionen

### Verspätungs-Benachrichtigung (Auto!)

```
MONTEUR/STEFAN UNTERWEGS
     │
     ▼
🤖 AUTONOM: GPS-Position tracken
     │
     ▼
🤖 AUTONOM: Aktuelle Position vs. naechster Termin
     │
     ├── ETA berechnen (Google Maps API)
     │
     └── Vergleich mit geplantem Termin
              │
              ├── Im Plan → Nichts tun
              │
              └── Verspaetung >15 Min
                       │
                       ▼
              🤖 AUTONOM: Kunde informieren!
              SMS/E-Mail: "Unser Monteur ist noch beim
              vorherigen Termin. Neue Ankunft ca. 11:15 Uhr.
              Wir bitten um Verstaendnis."
```

**Schwellenwerte (konfigurierbar):**

| Verspaetung | Aktion |
|-------------|--------|
| < 15 Min | Nichts (normal) |
| 15-30 Min | SMS an Kunde |
| 30-60 Min | SMS + Anruf-Option anbieten |
| > 60 Min | Termin-Verschiebung vorschlagen |

### GPS-basierte Analysen (Auto!)

```
GPS-DATEN SAMMELN
     │
     ▼
🤖 AUTONOM: Taegliche/Woechentliche Auswertung

ANALYSEN:
├── FAHRZEIT-ANALYSE (#22 Routenplanung)
│   - Durchschnittliche Fahrzeit pro Team
│   - Ineffiziente Routen erkennen
│   - Vorschlag: Termine besser clustern
│
├── PROJEKT-ZEITERFASSUNG (#34 GPS-Zeiterfassung)
│   - Ankunft beim Kunden → Auto-Start
│   - Abfahrt vom Kunden → Auto-Stop
│   - Keine manuelle Eingabe noetig!
│
├── AUSLASTUNGS-ANALYSE (#44 Kapazitaets-Cockpit)
│   - Wer hat wie viel Fahrzeit vs. Arbeitszeit?
│   - Engpaesse erkennen
│   - Optimierungspotential
│
├── TERMIN-GENAUIGKEIT
│   - Wie oft puenktlich? Wie oft verspaetet?
│   - Welche Kunden/Regionen problematisch?
│   - Puffer-Empfehlungen
│
└── LIEFERANTEN-BEWERTUNG (#19)
    - Bei Abholungen: Wartezeit beim Lieferant tracken
    - Automatisches Scoring
```

### Dashboard: GPS-Echtzeit

```
┌────────────────────────────────────────────────────────────────────┐
│  GPS-UEBERSICHT                                  Live 🔴          │
├────────────────────────────────────────────────────────────────────┤
│                                                                    │
│  [Karte mit Fahrzeug-Positionen]                                  │
│                                                                    │
│  🚐 Team 1 (Mariusz+Manfred)                                      │
│     📍 Beim Kunden: Mueller, Amberg                               │
│     ⏱️ Seit 45 Min | Geplant: 60 Min | ✅ Im Plan                 │
│                                                                    │
│  🚐 Team 2 (Christian+Michael)                                    │
│     📍 Unterwegs zu: Schmidt, Weiden                              │
│     ⏱️ ETA: 10:25 | Geplant: 10:00 | ⚠️ 25 Min spaet            │
│     → Kunde wurde automatisch informiert                          │
│                                                                    │
│  🚐 Stefan (Service)                                              │
│     📍 Beim Kunden: Weber, Sulzbach                               │
│     ⏱️ Seit 20 Min | Geplant: 30 Min | ✅ Im Plan                 │
│                                                                    │
│  ── HEUTE ──────────────────────────────────────────────────────  │
│  Termine: 12 | Erledigt: 5 | Aktiv: 3 | Offen: 4                  │
│  Fahrzeit gesamt: 4h 20min | Arbeitszeit: 18h 45min               │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

### Wochenanalyse (Auto-Report)

```
┌────────────────────────────────────────────────────────────────────┐
│  WOCHEN-ANALYSE KW 51                           Auto-generiert    │
├────────────────────────────────────────────────────────────────────┤
│                                                                    │
│  PUENKTLICHKEIT                                                    │
│  ████████████████████ 85%  puenktlich (< 15 Min)                  │
│  ████                 12%  leicht verspaetet (15-30 Min)          │
│  █                     3%  stark verspaetet (> 30 Min)            │
│                                                                    │
│  FAHRZEIT vs. ARBEITSZEIT                                          │
│  Team 1:  Fahrzeit 22%  ████░░░░░░░░░░░░░░░░  Arbeitszeit 78%    │
│  Team 2:  Fahrzeit 31%  ██████░░░░░░░░░░░░░░  Arbeitszeit 69%    │
│  Stefan:  Fahrzeit 28%  █████░░░░░░░░░░░░░░░  Arbeitszeit 72%    │
│                                                                    │
│  🔍 OPTIMIERUNGS-VORSCHLAG:                                       │
│  "Team 2 hat 31% Fahrzeit - 9% ueber Durchschnitt.               │
│   Empfehlung: Termine in Weiden + Neustadt clustern."            │
│                                                                    │
│  DURCHSCHNITTLICHE TERMIN-DAUER                                    │
│  Fenster-Montage:     4,2h  (Plan: 4h)    ✅                      │
│  Raffstore-Montage:   2,8h  (Plan: 2,5h)  ⚠️ +12%                │
│  Reparatur:           0,9h  (Plan: 1h)    ✅                      │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

### Technische Umsetzung GPS

| Komponente | Option | Kosten |
|------------|--------|--------|
| **GPS-Hardware** | Smartphone der Monteure | 0€ (vorhanden) |
| **Tracking-App** | Eigene PWA oder fertige App | 0-10€/User/Monat |
| **Karten-API** | Google Maps / OpenStreetMap | 0-200€/Monat |
| **Datenschutz** | Nur waehrend Arbeitszeit, DSGVO-konform | Einwilligung noetig |

### Autonomie-Hierarchie

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

## Kostenvergleich

| Posten | W4A aktuell | Eigenes System |
|--------|-------------|----------------|
| ERP-Lizenz | >4.000€/Jahr | 0€ |
| FIBU-Loesung | inklusive | 300-500€/Jahr |
| Hosting (Cloud) | ~100€ | ~450€ |
| **Gesamt** | **~4.100€/Jahr** | **~950€/Jahr** |
| **Ersparnis** | - | **~3.150€/Jahr** |

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

### Konzept: Stille Sammlung + Wöchentlicher Review

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
- ✅ Header (Logo, "J.S. Fenster & Tueren", Slogan)
- ✅ Kontaktdaten rechts
- ✅ Footer (Geschaeftsfuehrer, Bank, IBAN, USt-IdNr)

**Was W4A NICHT kann:**
- ❌ Wasserzeichen in der Mitte (stilisierte Fenster-Grafik in Grau/Orange)

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

**Technisch:** Wasserzeichen-Grafik aus PDF extrahieren oder als separates PNG/SVG hinterlegen, dann als Hintergrund-Layer unter Content rendern.

**Vorteile:**
- E-Mail-PDFs sehen professionell aus (mit Wasserzeichen)
- Druck auf Normalpapier moeglich
- Konsistentes Design ueberall

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

## Workflow: Angebot erstellen (neu gedacht)

### Stufe 1: Budget-Angebot (5 Minuten)

```
Kunde ruft an: "Was kosten 4 Fenster ca. 1,2m x 1,4m?"

┌─────────────────────────────────────────────────┐
│  SCHNELL-KALKULATION                            │
├─────────────────────────────────────────────────┤
│  Produkt: [Fenster]   Lieferant: [Drutex]      │
│  Breite: [1200]  Hoehe: [1400]  Anzahl: [4]    │
│  ────────────────────────────────────────────  │
│  Ca.-Preis:          ~1.800€/Stueck            │
│  Mit Montage (+30%): ~2.340€/Stueck            │
│  GESAMT ca.:         ~9.400€ brutto            │
│  ────────────────────────────────────────────  │
│  [Per E-Mail]  [Aufmass-Termin anlegen]        │
└─────────────────────────────────────────────────┘
```

### Stufe 2: Richtiges Angebot (nach Aufmass)

```
┌─────────────────────────────────────────────────┐
│  ANGEBOT ERSTELLEN                              │
├─────────────────────────────────────────────────┤
│  Kunde: Mueller    Projekt: EFH Amberg          │
│                                                 │
│  Quelle waehlen:                                │
│  ○ Weru API    → Konfigurator oeffnet sich     │
│  ○ Warema PDF  → Datei hochladen               │
│  ○ Aus Budget  → Budget uebernehmen            │
│  ○ Manuell     → Freie Eingabe                 │
└─────────────────────────────────────────────────┘
```

### Vereinfachte Positions-Ansicht

Statt 20+ Spalten gleichzeitig (wie in W4A):

```
┌─────────────────────────────────────────────────────────────┐
│  NEUER AUFTRAG                              [Speichern]     │
├─────────────────────────────────────────────────────────────┤
│  Kunde: Lebenshilfe          Projekt: BV Jahnstraße         │
│                                                             │
│  📁 XML hier ablegen oder [Datei waehlen]                   │
│                                                             │
│  ── Positionen ─────────────────────────────────────────    │
│                                                             │
│  [+] 1. Fensterfront (Drutex)           € 35.009,70         │
│      └─ 4 Elemente, 5% Rabatt                               │
│                                                             │
│  [+] 2. Montagematerial                 €  6.511,12         │
│      └─ Auto-vorgeschlagen ✓                                │
│                                                             │
│  [+] 3. Warema Raffstoren               € 33.844,32         │
│      └─ 32 St., 5% Rabatt                                   │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  Netto: € 87.372  │  MwSt: € 16.600  │  Brutto: € 103.973  │
└─────────────────────────────────────────────────────────────┘
```

Klick auf [+] → Details ausklappen (nur bei Bedarf)

### Tool-Referenzen (aus IDEEN.md)

| Tool | Funktion | Autonomie |
|------|----------|-----------|
| #1 Preislisten-Import | Lieferanten-Preise automatisch einlesen | 🤖 Autonom |
| #2 XML-Konfigurator-Import | Weru/Drutex XML direkt einlesen | 🤖 Autonom |
| #5 Bauplan-KI | Massangaben aus Bauplan extrahieren | 🤖 Autonom |
| #7 Spracheingabe | Angebot per Diktat erfassen | 🤖 Autonom |
| #71 Einkaufs-Workflow | Preis-Cache fuer Schnell-Kalkulation | 🤖 Autonom |

---

## Datenmodell (Auszug)

### Regeln (Lernsystem)

```sql
TABLE rules
  id              UUID PRIMARY KEY
  name            VARCHAR         -- "Dachfenster Montagepauschale"
  category        VARCHAR         -- "kalkulation" | "lieferant" | "rabatt"
  condition       JSONB           -- {"product_type": "Dachfenster"}
  action          JSONB           -- {"multiply": "pauschale", "by": 1.5}
  confidence      DECIMAL         -- 0.94
  sample_count    INT             -- 12
  status          VARCHAR         -- "active" | "pending" | "disabled"
  autonomy_level  VARCHAR         -- "auto" | "suggest" | "disabled"
  created_by      UUID            -- wer hat vorgeschlagen
  approved_by     UUID            -- wer hat freigegeben
  created_at      TIMESTAMP
  approved_at     TIMESTAMP
```

### Aenderungs-Beobachtungen

```sql
TABLE change_observations
  id              UUID PRIMARY KEY
  document_type   VARCHAR         -- "angebot" | "auftrag" | ...
  document_id     UUID
  position_id     UUID
  field_name      VARCHAR         -- "montage_pauschale" | "lieferant"
  old_value       JSONB
  new_value       JSONB
  changed_by      UUID
  changed_at      TIMESTAMP
  priority        VARCHAR         -- "critical" | "normal"
  status          VARCHAR         -- "pending" | "reviewed" | "ignored"
  cluster_id      UUID            -- fuer Konsolidierung
  is_reverted     BOOLEAN         -- User hat selbst zurueckgeaendert
```

---

## Workflow: Bestellung → Wareneingang (neu gedacht)

### Schmerzpunkte heute → Neue Loesung

| Problem (W4A) | Neue Loesung |
|---------------|--------------|
| Offene ABs nicht getrackt | Auto-Erinnerung nach X Tagen |
| Portal-ABs vergessen | Auto-Download oder Reminder |
| Abholungen nicht getrackt | Separater Abhol-Status |
| Outlook unzuverlaessig | Eigenes System, kein Outlook |
| Eingangslieferschein fehlerhaft | Scan → Auto-Erfassung |
| Keine Lagerbuchungen | Automatisch bei Wareneingang |
| Teilmengen falsch | Position fuer Position abhaken |
| Anzahlung vergessen | Pflichtfeld / Auto-Check |
| Lieferwoche fehlt | Pflichtfeld |
| Lieferadresse falsch | Auto-Logik nach Artikeltyp |
| AB manuell geprueft | KI-Abgleich mit Bestellung |

### Prozess-Schritte

```
1. BESTELLUNG VORBEREITEN
   🤖 AUTONOM: Positionen aus Auftrag, EK-Preise, Lieferant (gelernt)
   🤖 AUTONOM: Lieferadresse (Fenster→Lager, Pakete→Buero)
   🤖 AUTONOM: Lieferwoche (Montage-1 oder Pflichtfeld)
   👤 USER: Pruefen + Freigeben (1 Klick)

2. BESTELLUNG VERSENDEN
   🤖 AUTONOM: Versandweg (Portal-API oder E-Mail)
   🤖 AUTONOM: AB-Frist setzen (3-5 Werktage)

3. AB UEBERWACHEN
   🤖 AUTONOM: Taeglicher Check
   🤖 AUTONOM: Frist ueberschritten → Auto-Erinnerung an Lieferant
   🤖 AUTONOM: 2x ueberschritten → KRITISCH → Andreas

4. AB PRUEFEN (KI-gestuetzt)
   🤖 AUTONOM: AB hochladen (Drag&Drop)
   🤖 AUTONOM: KI-Abgleich Bestellung vs. AB
   ⚠️ Abweichungen → User entscheidet
   ✅ <5% Abweichung → Auto-OK (Stufe 3)

5. LIEFERUNG UEBERWACHEN
   🤖 AUTONOM: Lieferdatum tracken, Countdown
   🤖 AUTONOM: "Abholung" = separater Status + taeglicher Reminder

6. WARENEINGANG
   👤 USER: Lieferschein scannen/fotografieren
   🤖 AUTONOM: Bestellung erkennen, Positionen abgleichen
   🤖 AUTONOM: Teillieferung? → Status anpassen, Bestellung bleibt offen
   🤖 AUTONOM: Lagerbestand buchen

7. MONTAGE-FREIGABE
   🤖 AUTONOM: Alle Positionen da? → "Montagebereit"
   🤖 AUTONOM: Fehlt was? → Warnung mit Liste
```

### Beschaffungs-Dashboard (Echtzeit)

```
┌────────────────────────────────────────────────────────────┐
│  BESCHAFFUNGS-DASHBOARD                                    │
├────────────────────────────────────────────────────────────┤
│  🔴 KRITISCH (3)     AB ueberfaellig, Abholung vergessen  │
│  🟡 ACHTUNG (7)      Abweichungen, Lieferung morgen       │
│  🟢 IM PLAN (23)     Alles OK                             │
│  📍 ABHOLUNGEN (2)   Offen bei Lieferanten                │
└────────────────────────────────────────────────────────────┘
```

### Tool-Referenzen (aus IDEEN.md)

| Tool | Funktion | Autonomie |
|------|----------|-----------|
| #19 Lieferanten-Bewertung | Auto-Scoring nach Liefertreue, Preis, Abweichungen | 🤖 Autonom |
| #36 Beschaffungs-Workflow | Bestellung → AB → Lieferung (Kern) | 🤖 Autonom |
| #53 Mindestbestand-Alert | Auto-Warnung wenn Lager unter Schwelle | 🤖 Autonom |
| #54 Preis-Vergleich | Parallele Anfragen an alle Lieferanten | 🤖 Autonom |
| #71 Einkaufs-Workflow | Preis-Cache, Anfrage-Tracking | 🤖 Autonom |

---

## Workflow: Rechnung → Zahlung → Mahnung (neu gedacht)

### Schmerzpunkte heute → Neue Loesung

| Problem (W4A) | Neue Loesung |
|---------------|--------------|
| Roland fehlen Infos | Digitale Montage-Rueckmeldung mit allen Daten |
| Haengeakt wandert zurueck | Kein Papier - alles digital, Status sichtbar |
| Mehrere Auftraege komplex | Dashboard: Was ist montiert + nicht abgerechnet |
| Anzahlung vergessen | Auto-Check bei Auftrag + Sperre bis bezahlt |
| Firma in Vorleistung | Teilrechnungs-Automatik |
| E-Mails ausgedruckt | Alles digital verlinkt |
| ~4,4% Korrekturen | Bessere Daten vorab (Montage-Rueckmeldung) |

### Prozess-Schritte

```
1. RECHNUNGS-VORBEREITUNG (nach Montage)
   🤖 AUTONOM: Vollstaendigkeits-Check
      - Positionen: bestellt ✓ geliefert ✓ montiert ✓
      - Arbeitszeit aus digitaler Rueckmeldung
      - Zusatzpositionen markiert
   🤖 AUTONOM: Rechnungsentwurf generieren
   👤 USER (Roland): Pruefen + Freigeben (1-Klick wenn Standard)

2. RECHNUNG ERSTELLEN
   🤖 AUTONOM: PDF mit Wasserzeichen generieren
   🤖 AUTONOM: Pruefungen (MwSt, IBAN, Zahlungsbedingungen)

3. RECHNUNG VERSENDEN
   🤖 AUTONOM: E-Mail bevorzugt (wenn vorhanden)
   🤖 AUTONOM: Standard-Text + PDF anhängen

4. ZAHLUNGS-UEBERWACHUNG
   🤖 AUTONOM: Kontoauszug taeglich abrufen (HBCI)
   🤖 AUTONOM: Automatische Zuordnung
   🤖 AUTONOM: Skonto-Pruefung

5. MAHNWESEN (bei Nichtzahlung)
   Tag 14: Zahlungsziel
   Tag 21: 🤖 AUTONOM: Zahlungserinnerung (freundlich)
   Tag 28: 🤖 AUTONOM: Mahnung 1
   Tag 35: 🤖 AUTONOM: Mahnung 2 + KRITISCH → Andreas
   Tag 42+: ⚠️ Inkasso? → Manuelle Entscheidung

6. DATEV-EXPORT (#81, #82)
   🤖 AUTONOM: Buchungskonto-Assistent (#82)
      - Lieferant erkannt → Konto vorschlagen
      - Artikelart erkannt → Konto vorschlagen
      - Lernt aus Korrekturen (Roland bucht oft falsch!)
   🤖 AUTONOM: PDF-Merger (#81)
      - Rechnung + alle Anhaenge (Tankbelege, Listen)
      - Zu EINER Datei zusammenfassen
      - DATEV kann nur 1 Datei pro Buchung!
   🤖 AUTONOM: Export ohne W4A (eigener DATEV-Export)
```

### Teilrechnungs-Logik

System erkennt automatisch:
- Was ist geliefert + montiert? → abrechenbar
- Was fehlt noch? → in Restrechnung
- Anzahlung bereits gezahlt? → Auto-Abzug
- Option: "Automatisch Restrechnung wenn [Position] geliefert"

### Montagematerial-Pauschale (#70)

**Problem:** Bei Nicht-Fenster-Produkten wird Montagematerial vergessen → Umsatzverlust!

```
POSITION ERKANNT (z.B. Innentuer, Markise, Raffstore)
     │
     ▼
🤖 AUTONOM: Ist Standard-Fenster?
     │
     ├── JA → Pauschale bereits inkludiert
     │
     └── NEIN → Montagematerial-Position ergaenzen!
              "Montagematerial Innentuer"  € 45,-
              "Montagematerial Markise"    € 85,-
              etc.
```

### BAFA-Foerderantrag (#3) ⭐ KRITISCH!

**Problem:** NachweisService nach Zahlung vergessen → Kunde verliert Foerderung!

```
FOERDER-POSITION IN AUFTRAG ERKANNT
     │
     ▼
🤖 AUTONOM: BAFA-Tracking aktivieren
     │
     ▼
RECHNUNG BEZAHLT
     │
     ▼
🤖 AUTONOM: SOFORT Erinnerung an Andreas!
     "BAFA NachweisService faellig fuer Projekt Mueller!"
     │
     ▼
🤖 AUTONOM: Checkliste anzeigen:
     ☐ Rechnung hochladen
     ☐ Fotos der Montage
     ☐ Fachunternehmererklarung
     ☐ NachweisService abschliessen
     │
     ▼
🤖 AUTONOM: Taeglich erinnern bis erledigt!
```

**Warum KRITISCH:** Kunde hat 6 Monate Zeit nach Zahlung. Wird das vergessen, verliert der Kunde 15-20% Foerderung (mehrere Tausend Euro)!

### Rechnungs-Dashboard

```
┌────────────────────────────────────────────────────────────┐
│  RECHNUNGS-DASHBOARD                                       │
├────────────────────────────────────────────────────────────┤
│  📝 ZU ERSTELLEN (5)   Montage fertig, keine Rechnung     │
│  💳 OFFEN (12)         Versendet, nicht bezahlt           │
│     🟢 Fällig in >7d   🟡 Fällig bald   🔴 Überfällig     │
│  ✅ BEZAHLT (8)        Diese Woche: 45.200€               │
│  ⏳ ANZAHLUNGEN (3)    Offen - Bestellung wartet!         │
└────────────────────────────────────────────────────────────┘
```

---

## Workflow: Montage (neu gedacht)

### Schmerzpunkte heute → Neue Loesung

| Problem (W4A/Outlook) | Neue Loesung |
|-----------------------|--------------|
| Outlook als Planungs-Dashboard missbraucht | Dediziertes Montage-Board |
| Unterlagen manuell zusammengestellt | Auto-generierte digitale Montage-Mappe |
| Falsche Aufmass-Blaetter (Angebot statt Bestellung) | Immer aktuellste Version verlinkt |
| Papier-Zettel Rueckmeldung | Digitale Erfassung per App |
| Montageschein verschollen im Auto | Kein Papier das verschwinden kann |
| Rueckmeldung bis 18h verzoegert | Echtzeit-Sync |
| Zusatzarbeiten vergessen | Pflichtfeld vor Abschluss |
| Material zurueckgelegt ohne Doku | Foto-Dokumentation in App |
| Kunde weiss nicht wann Monteur kommt | Auto-Benachrichtigung |
| Restarbeiten-Zettel → Kalender | Direkt im System als Task |

### Prozess-Schritte

```
1. MONTAGE-PLANUNG
   🤖 AUTONOM: "Montagebereit" wenn alle Positionen geliefert
   🤖 AUTONOM: Team-Vorschlag basierend auf:
      - Verfuegbarkeit (Kalender)
      - Faehigkeiten (Fenster/Tueren/Raffstore)
      - Auslastung (gleichmaessig verteilen)
      - Entfernung (Route optimieren)
   👤 USER (Susann): Prueft + passt an (Drag & Drop)
   🤖 AUTONOM: Lieferant hat Liefertermin → Auto-Vorschlag Montage

2. MONTAGE-MAPPE (Auto-generiert)
   🤖 AUTONOM: Digitale Mappe mit:
      - Montageauftrag (aktueller Stand!)
      - Richtige Aufmass-Blaetter (Bestellung, nicht Angebot)
      - Lieferscheine (nur relevante)
      - Fotos (direkt verlinkt)
      - Ansprechpartner + Telefon
      - Anfahrt (Google Maps verlinkt)
   👤 USER: Kann auf Tablet/Smartphone abrufen

3. MORGEN-BRIEFING (vereinfacht)
   🤖 AUTONOM: Tages-Uebersicht pro Team generieren
      - Reihenfolge der Montagen
      - Besonderheiten farblich markiert
      - Material-Checkliste (Was ins Auto?)
   👤 USER: Briefing dauert nur noch 5-10 Min

4. ANFAHRT + DURCHFUEHRUNG
   🤖 AUTONOM: Kunde erhaelt SMS/E-Mail "Monteur unterwegs"
   🤖 AUTONOM: GPS-basierte Ankunfts-Schaetzung (optional)
   👤 MONTEUR: Arbeitet mit digitaler Mappe

5. RUECKMELDUNG (Monteur-App)
   👤 MONTEUR: Vor Ort erfassen:
      - Status: ✅ Fertig / ⚠️ Restarbeit / ❌ Problem
      - Arbeitszeit (Start/Ende pro Mitarbeiter)
      - Zusatzarbeiten (Pflichtfeld wenn > Pauschale)
      - Fotos (Ergebnis + eventuelle Schaeden)
      - Unterschrift (digital auf Tablet)
   🤖 AUTONOM: Sofort im System sichtbar

6. RESTARBEITEN-MANAGEMENT
   🤖 AUTONOM: Restarbeit angelegt → "Was fehlt?"
      - Material bestellen → Bestellvorschlag
      - Externer Vorgang (Verputz) → Termin-Wecker
      - Nur Zeit gefehlt → Direkt neu einplanen
   🤖 AUTONOM: Kunde erhaelt Info "Wir melden uns wenn..."

7. ABSCHLUSS
   🤖 AUTONOM: Vollstaendig? → "Rechnung erstellen" aktiviert
   🤖 AUTONOM: Montage-Daten direkt in Rechnungs-Vorbereitung
   🤖 AUTONOM: Referenz-Fotos Reminder (#72)
      "Montage erfolgreich - Fotos fuer Website machen?"
   🤖 AUTONOM: Google-Bewertung Vorschlag (#73)
      Nach positiver Rueckmeldung → Link an Kunde
```

### Wetter-Integration (#66)

```
VOR MONTAGE-TERMIN (24h/12h/3h vorher):
     │
     ▼
🤖 AUTONOM: Wetter-API abfragen fuer Montage-Ort
     │
     ├── ☀️ Gut → Nichts tun
     │
     ├── 🌧️ Regen >60% → Warnung an Planer
     │   "Morgen Regen in Amberg, Montage verschieben?"
     │
     ├── 💨 Sturm/Wind >50km/h → KRITISCH
     │   "Aussenmontage gefaehrlich! Auto-Verschiebung?"
     │
     └── ❄️ Frost <0°C → Warnung
         "Montageschaum haertet nicht aus unter 5°C"
```

### Monteur-App Konzept

```
┌─────────────────────────────────────────────────────────────┐
│  📱 MONTEUR-APP                     🔋 87%  📶  08:15      │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  HEUTE: 3 Montagen                                          │
│                                                             │
│  ┌───────────────────────────────────────────────────────┐  │
│  │ 1. Mueller, Amberg              08:30    [AKTUELL]    │  │
│  │    5 Fenster, 2 Tueren                                │  │
│  │    📄 Mappe   📍 Navigation   📞 Anrufen             │  │
│  └───────────────────────────────────────────────────────┘  │
│                                                             │
│  ┌───────────────────────────────────────────────────────┐  │
│  │ 2. Schmidt, Weiden              13:00    [GEPLANT]    │  │
│  │    3 Raffstoren                                       │  │
│  │    📄 Mappe   📍 Navigation   📞 Anrufen             │  │
│  └───────────────────────────────────────────────────────┘  │
│                                                             │
│  ┌───────────────────────────────────────────────────────┐  │
│  │ 3. Lebenshilfe, Jahnstrasse     15:30    [GEPLANT]    │  │
│  │    Restarbeit: Silikonarbeiten                        │  │
│  │    📄 Mappe   📍 Navigation   📞 Anrufen             │  │
│  └───────────────────────────────────────────────────────┘  │
│                                                             │
│                    [⏱️ Zeit erfassen]                       │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Rueckmeldung-Bildschirm

```
┌─────────────────────────────────────────────────────────────┐
│  📱 RUECKMELDUNG                                           │
│  Mueller, Amberg - 5 Fenster, 2 Tueren                      │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  STATUS:  [✅ Fertig]  [⚠️ Restarbeit]  [❌ Abbruch]       │
│                                                             │
│  ── Arbeitszeit ────────────────────────────────────────   │
│  Mariusz    08:30 - 15:45    7h 15m                        │
│  Manfred    08:30 - 15:45    7h 15m                        │
│  [+ Helfer hinzufuegen]                                    │
│                                                             │
│  ── Zusatzarbeiten ─────────────────────────────────────   │
│  ☐ Keine                                                   │
│  ☑ Montagematerial (Pauschale)                            │
│  ☐ Zusatzposition: ________________  €_____               │
│                                                             │
│  ── Fotos ──────────────────────────────────────────────   │
│  [📷 Foto aufnehmen]  3 Fotos hinzugefuegt                │
│                                                             │
│  ── Unterschrift Kunde ─────────────────────────────────   │
│  ┌─────────────────────────────────────┐                   │
│  │                                     │                   │
│  │      [Hier unterschreiben]          │                   │
│  │                                     │                   │
│  └─────────────────────────────────────┘                   │
│                                                             │
│              [Montage abschliessen]                         │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Montage-Board (Buero-Ansicht)

```
┌────────────────────────────────────────────────────────────────────┐
│  MONTAGE-BOARD                                     [+ Neu planen]  │
├────────────────────────────────────────────────────────────────────┤
│                                                                    │
│  DIESE WOCHE: KW 52                              [< Woche >]       │
│                                                                    │
│  ╔══════════════════╦═══════════════════╦═══════════════════╗     │
│  ║    Team 1        ║     Team 2        ║     Team 3        ║     │
│  ║  Mariusz+Manfred ║ Christian+Michael ║     Stefan        ║     │
│  ╠══════════════════╬═══════════════════╬═══════════════════╣     │
│  ║ MO               ║ MO                ║ MO                ║     │
│  ║ ████ Mueller     ║ ▓▓▓ Schmidt       ║ ░░ Werkstatt     ║     │
│  ║ ████             ║ ▓▓▓               ║                   ║     │
│  ╠══════════════════╬═══════════════════╬═══════════════════╣     │
│  ║ DI               ║ DI                ║ DI                ║     │
│  ║ ████ Lebenshilfe ║ ▓▓▓ Weber         ║ ░░ Wartung Meier ║     │
│  ║ ████████         ║                   ║                   ║     │
│  ╚══════════════════╩═══════════════════╩═══════════════════╝     │
│                                                                    │
│  LEGENDE: ████ Fenster/Tueren  ▓▓▓ Raffstore  ░░ Service          │
│                                                                    │
│  ── MONTAGEBEREIT (5) ──────────────────────────────────────────  │
│  ⬜ Bauer, Sulzbach    Fensterfront    Lieferung: 27.12.          │
│  ⬜ Klein, Amberg      3 Tueren        Lieferung: 28.12.          │
│                                                                    │
│  ── RESTARBEITEN (3) ───────────────────────────────────────────  │
│  🟡 Huber, Weiden      Silikon         Material da, einplanen!    │
│  🔴 Schulze, Nabburg   Fensterbrett    Wartet auf Lieferung       │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

### Spracheingabe fuer Monteure

**Warum wichtig:** Monteure haben oft keine Hand frei (Werkzeug, Material)

```
SPRACH-FEATURES:
├── Zeiterfassung
│   "Hey App, Zeit starten fuer Mueller Amberg"
│   "Zeit stoppen"
│
├── Notizen
│   "Notiz: Fensterbrett muss nachbestellt werden"
│   "Notiz: Kunde fragt nach Angebot fuer Raffstore"
│
├── Problemmeldung
│   "Problem: Fenster passt nicht, 5mm zu breit"
│   → System erstellt automatisch Ticket
│
├── Fotos mit Beschreibung
│   [Foto aufnehmen]
│   "Beschreibung: Schaden an Fensterbank vorher"
│
└── Status-Aenderung
    "Mueller fertig, weiter zu Schmidt"
```

**Technisch:**
- Speech-to-Text (Whisper oder Browser-API)
- Offline-faehig (lokale Erkennung, spaeter sync)
- Bestaetigung vor kritischen Aktionen ("Montage abschliessen?")

### Hardware-Anforderung

| Geraet | Aktuell | Empfehlung |
|--------|---------|------------|
| Monteur-Smartphones | Schlecht (privat?) | Robuste Firmen-Smartphones |
| Tablets | Keine | 2-3 robuste Tablets (IP68) fuer Unterschrift |
| Headset/Kopfhoerer | - | Optional fuer Spracheingabe in lauter Umgebung |

**Option A:** Nur Smartphones (guenstiger, aber kleine Bildschirme)
**Option B:** Tablets fuer Unterschrift + Mappe, Smartphone fuer Kommunikation
**Option C:** Smartphone mit Bluetooth-Headset (beste Spracheingabe)

### Tool-Referenzen (aus IDEEN.md)

| Tool | Funktion | Autonomie |
|------|----------|-----------|
| #22 Routenplanung | Optimale Reihenfolge der Montagen | 🤖 Autonom |
| #34 GPS-Zeiterfassung | Auto-Start/Stop bei Kunde (kein manuelles Stempeln) | 🤖 Autonom |
| #39 Digitale Montage-Mappe | Alle Dokumente auf Tablet/Smartphone | 🤖 Autonom |
| #41 Status Live | Echtzeit-Status aller Montagen im Buero | 🤖 Autonom |
| #66 Wetter-Integration | Warnung bei Regen/Sturm/Frost | 🤖 Autonom |
| #72 Referenz-Fotos | Nach Montage Fotos fuer Website | 🤖 Autonom |
| #73 Google-Bewertung | Nach positiver Rueckmeldung Link senden | 🤖 Autonom |

---

## Workflow: Anfrage / CRM (neu gedacht)

### Schmerzpunkte heute → Neue Loesung

| Problem (W4A/Outlook) | Neue Loesung |
|-----------------------|--------------|
| Zettelwirtschaft bei Tel. Anfragen | Digitale Erfassung direkt am Telefon |
| E-Mail-Sortierung in Outlook manuell | Auto-Kategorisierung + Ticket-System |
| Kein Tracking wer was bearbeitet | Zuweisung + Status sichtbar |
| Kaum Nachverfolgung | Automatische Follow-up Reminder |
| Auftrag fehlt oft → Soll-Ist falsch | Pflicht-Workflow: Angebot → Auftrag |
| Projekt fuer Preisanfrage noetig | Automatisch wenn Lieferant-Anfrage |
| 2-3 Wochen Aufmass-Wartezeit | Kapazitaets-Uebersicht + Online-Buchung |
| "Wie auf uns aufmerksam?" nicht erfasst | Pflichtfeld (Marketing-Analyse) |
| Konfiguratoren nur Copy&Paste | XML-Import wo moeglich |

### Prozess-Schritte

```
1. ANFRAGE-EINGANG (Multi-Channel)
   📧 E-MAIL:
   🤖 AUTONOM: E-Mail analysieren (Absender, Betreff, Keywords)
   🤖 AUTONOM: Bestandskunde? → Auto-Zuordnung
   🤖 AUTONOM: Kategorie vorschlagen (Anfrage/Rechnung/Lieferant)
   🤖 AUTONOM: Ticket erstellen, Zuweisung nach Regeln

   📞 TELEFON (mit KI-Chatbot):

   VARIANTE A - Mitarbeiter nimmt ab:
   👤 USER: Schnell-Erfassungsmaske waehrend Gespraech
      - Bestandskunde suchen (Autovervollstaendigung)
      - Neukunde anlegen (minimal: Name + Tel/E-Mail)
      - Checkboxen: Produkte, Projekttyp
      - "Wie gefunden?" (Pflicht bei Neukunden)
   🤖 AUTONOM: Gespraech wird transkribiert (Whisper)
   🤖 AUTONOM: Aus Transkript weitere Daten extrahieren
   🤖 AUTONOM: Ticket + Termin-Vorschlag

   VARIANTE B - Niemand nimmt ab → KI-CHATBOT:
   🤖 AUTONOM: Nach X Klingeln → Chatbot nimmt ab
   🤖 AUTONOM: Begruessung: "JS Fenster, wie kann ich helfen?"
   🤖 AUTONOM: Gespraech fuehren + transkribieren:
      - Name + Kontakt erfassen
      - "Neubau, Sanierung oder Reparatur?"
      - "Welche Produkte interessieren Sie?"
      - Bei Reparatur: "Was ist kaputt? Welches Fenster/Tuer?"
      - "Wann passt Ihnen ein Termin?"
   🤖 AUTONOM: Bestandskunde? → Telefonnummer matchen
   🤖 AUTONOM: Ticket erstellen mit allen Infos
   🤖 AUTONOM: Genuegend Daten? → Budget-Angebot generieren!
   🤖 AUTONOM: E-Mail an Kunde: "Danke fuer Ihren Anruf, hier Ihr Budget-Angebot"
   🤖 AUTONOM: Falls Rueckruf noetig → Aufgabe fuer naechsten Morgen

   🚶 LAUFKUNDSCHAFT:
   👤 USER: Tablet in Ausstellung - gleiche Maske
   🤖 AUTONOM: Nach Beratung → Angebot oder Follow-up Ticket

   🌐 WEBSITE:
   🤖 AUTONOM: Formular → Ticket → Zuweisung
   🤖 AUTONOM: Auto-Antwort mit Bearbeitungszeit

2. QUALIFIZIERUNG
   🤖 AUTONOM: Anfrage bewerten nach:
      - Bestandskunde (Umsatzhistorie)
      - Projektgroesse (Produktauswahl)
      - Zeitrahmen (dringend?)
      - Budget genannt?
   🤖 AUTONOM: Prioritaet setzen (Hot/Warm/Cold)
   🤖 AUTONOM: Empfehlung: Aufmass / Ausstellung / Telefon-Beratung

3. BUDGET-ANGEBOT (optional, schnell)
   👤 USER: Wenn Infos reichen → Schnell-Kalkulation
   🤖 AUTONOM: Ca.-Preise aus Preislisten-Cache
   🤖 AUTONOM: E-Mail mit Budget-Angebot
   👤 KUNDE: Interesse? → Aufmass vereinbaren

4. AUFMASS-TERMINIERUNG
   🤖 AUTONOM: Freie Slots anzeigen (Kapazitaet Enrico/Jaroslaw/Andreas)
   🤖 AUTONOM: Online-Buchung moeglich (Kunde waehlt selbst)
   🤖 AUTONOM: Route beruecksichtigen (Nachbar-Termine gruppieren)
   🤖 AUTONOM: Termin-Bestaetigung per E-Mail/SMS
   🤖 AUTONOM: 24h vorher Erinnerung

5. ANGEBOT ERSTELLEN
   👤 USER: Konfigurator-Daten importieren:
      - Weru WoT: XML Drag&Drop
      - Andere: PDF-Upload → KI-Extraktion
      - Manuell bei Bedarf
   🤖 AUTONOM: Positionen vorausfuellen
   🤖 AUTONOM: Rabatt-Regeln anwenden (gelernt)
   🤖 AUTONOM: PDF generieren (mit Wasserzeichen)
   🤖 AUTONOM: E-Mail-Versand mit Nachverfolgung

6. NACHVERFOLGUNG (automatisch!)
   🤖 AUTONOM: Follow-up Sequenz:
      - Tag 3: Auto-Check ob E-Mail geoeffnet
      - Tag 7: Freundliche Nachfrage ("Noch Fragen?")
      - Tag 14: Erinnerung ("Angebot noch aktuell?")
      - Tag 21: Letzte Chance ("Interesse noch da?")
   🤖 AUTONOM: Kunde antwortet → Sequenz pausiert
   🤖 AUTONOM: Kunde sagt ab → Grund erfassen (optional)
   🤖 AUTONOM: Keine Reaktion → "Cold" Status nach 30 Tagen

7. KUNDE SAGT ZU
   🤖 AUTONOM: Angebot → Auftrag (Pflicht!)
   🤖 AUTONOM: Checkliste pruefen:
      - Anzahlung noetig? (bei > X €)
      - Lieferbedingungen geklaert?
      - Montage-Termin grob?
   🤖 AUTONOM: Bestellung vorbereiten (naechster Workflow)

8. ANALYSE / REPORTING
   🤖 AUTONOM: Dashboard-Daten sammeln:
      - Anfragen pro Kanal (Telefon/E-Mail/Web)
      - "Wie gefunden?" Auswertung
      - Conversion Rate (Anfrage → Angebot → Auftrag)
      - Durchlaufzeiten (Anfrage → Auftrag)

9. KUNDEN-REAKTIVIERUNG (#84)
   🤖 AUTONOM: Alte Projekte scannen (>5 Jahre, >10 Jahre)
   🤖 AUTONOM: Personalisierte Nachricht generieren:
      "Ihre Fenster von 2015 sind jetzt 10 Jahre alt.
       Zeit fuer einen Energie-Check?"
   🤖 AUTONOM: E-Mail/Brief-Kampagne auslösen
   🤖 AUTONOM: Reaktionen tracken → Pipeline
   → Potenzial: ~2.700 Projekte reaktivierbar!
```

### Anfrage-Erfassung (Schnell-Maske)

```
┌─────────────────────────────────────────────────────────────┐
│  📞 NEUE ANFRAGE                     [Kunde suchen: ____]   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  KUNDE:  [Mueller, Hans_____________]  ✅ Bestandskunde    │
│          Letzte Aktivitaet: Auftrag 12/2023 (8.500€)       │
│                                                             │
│  KONTAKT: 0961 / 12345   │   mueller@example.de            │
│                                                             │
│  ── Anfrage ────────────────────────────────────────────   │
│                                                             │
│  PRODUKTE:  ☑ Fenster  ☐ Tueren  ☑ Raffstore  ☐ Sonstig   │
│                                                             │
│  PROJEKT:   ○ Neubau   ● Sanierung   ○ Reparatur           │
│                                                             │
│  ZEITRAHMEN: [Q1 2025______]                               │
│                                                             │
│  NOTIZEN:   [5 Fenster EG, Kunde hat Masse____________]    │
│             [_________________________________________]     │
│                                                             │
│  ── Naechster Schritt ──────────────────────────────────   │
│                                                             │
│  ○ Angebot (Infos reichen)                                 │
│  ● Aufmass vereinbaren         [Verfuegbarkeit anzeigen]  │
│  ○ Kunde meldet sich                                       │
│  ○ Lieferant-Preisanfrage                                  │
│                                                             │
│           [Speichern + Ticket erstellen]                   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Neukunde-Erfassung

```
┌─────────────────────────────────────────────────────────────┐
│  ➕ NEUKUNDE ANLEGEN                                        │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  KONTAKT (Pflicht):                                        │
│  Name:      [________________]  Vorname: [______________]  │
│  Telefon:   [________________]  ODER                       │
│  E-Mail:    [________________]                             │
│                                                             │
│  ADRESSE (optional jetzt, spaeter Pflicht):                │
│  Strasse:   [________________]  Nr: [___]                  │
│  PLZ:       [_____]  Ort: [_________________________]      │
│                                                             │
│  WIE AUF UNS AUFMERKSAM? (Pflicht)                         │
│  ○ Empfehlung   ○ Google   ○ Werbung   ○ Vorbeigefahren   │
│  ○ Bestandskunde (anderes Projekt)   ○ Sonstiges: [____]  │
│                                                             │
│                          [Anlegen + weiter zur Anfrage]    │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### CRM-Pipeline (Dashboard)

```
┌────────────────────────────────────────────────────────────────────┐
│  VERKAUFS-PIPELINE                        Wert: 487.300€          │
├────────────────────────────────────────────────────────────────────┤
│                                                                    │
│  ANFRAGE (12)    ANGEBOT (8)     NACHFASS (5)    AUFTRAG (3)     │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐    │
│  │ Mueller  │ →  │ Schmidt  │ →  │ Weber    │ →  │ Klein    │    │
│  │ 15.000€  │    │ 42.000€  │    │ 8.500€   │    │ 95.000€  │    │
│  │ 🔥 Hot   │    │ ⏰ 3d    │    │ ⚠️ 14d   │    │ ✅ AZ ok │    │
│  ├──────────┤    ├──────────┤    ├──────────┤    ├──────────┤    │
│  │ Bauer    │    │ Huber    │    │ Meier    │    │ Schulze  │    │
│  │ 8.000€   │    │ 23.000€  │    │ 12.000€  │    │ 67.000€  │    │
│  │ Warm     │    │ ⏰ 5d    │    │ ⚠️ 21d   │    │ ⏳ AZ    │    │
│  ├──────────┤    ├──────────┤    └──────────┘    └──────────┘    │
│  │ ...+10   │    │ ...+6    │                                    │
│  └──────────┘    └──────────┘                                    │
│                                                                    │
│  ── HEUTE FAELLIG ──────────────────────────────────────────────  │
│  🔴 Weber (14d ueberfaellig) - Nachfragen!                        │
│  🟡 Schmidt (3d) - Erste Nachfrage heute                          │
│                                                                    │
│  ── AUFMASS-TERMINE DIESE WOCHE ─────────────────────────────────  │
│  DI 14:00  Mueller, Amberg (Enrico)                               │
│  MI 09:00  Neukunde Bauer, Weiden (Jaroslaw)                      │
│  FR 11:00  Reparatur Klein, Sulzbach (Andreas)                    │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

### Marketing-Auswertung

```
┌────────────────────────────────────────────────────────────────────┐
│  MARKETING-ANALYSE                              Zeitraum: 2024    │
├────────────────────────────────────────────────────────────────────┤
│                                                                    │
│  WIE GEFUNDEN?                                                     │
│  ████████████████████ Empfehlung        42%   (+5% vs. Vorjahr)  │
│  ████████████         Google            28%   (+12%)             │
│  ████████             Vorbeigefahren    18%   (-3%)              │
│  ███                  Werbung            8%   (-8%)              │
│  ██                   Website            4%   (+2%)              │
│                                                                    │
│  CONVERSION RATE                                                   │
│  Anfrage → Angebot:    78%  (245 von 315)                        │
│  Angebot → Auftrag:    34%  (83 von 245)                         │
│  Gesamt:               26%  (83 von 315)                         │
│                                                                    │
│  DURCHLAUFZEIT (Median)                                           │
│  Anfrage → Angebot:     8 Tage                                   │
│  Angebot → Auftrag:    21 Tage                                   │
│  Anfrage → Auftrag:    32 Tage                                   │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

### KI-Assistent (Multi-Channel)

**Ziel:** Kein verpasster Kontakt, keine verlorene Anfrage - auch ohne Mitarbeiter

**Kanaele:**

| Kanal | Status | Besonderheit |
|-------|--------|--------------|
| **Telefon** | Vorhanden | Voice → Transkript |
| **E-Mail** | Vorhanden | Text-Analyse |
| **WhatsApp** | Einzurichten | Business API noetig |
| **Telegram** | Einzurichten | Bot einfach zu erstellen |
| **Website-Chat** | Optional | Widget auf js-fenster.de |

**Gleiche Logik, alle Kanaele:**

```
EINGANG (egal welcher Kanal)
         │
         ▼
┌─────────────────────────────────────┐
│  🤖 KI-ASSISTENT                    │
│                                     │
│  1. Kanal erkennen                  │
│  2. Absender identifizieren         │
│     → Bestandskunde? (Tel/E-Mail)   │
│  3. Anliegen klassifizieren         │
│     → Anfrage / Reparatur / Rekla   │
│  4. Daten sammeln (Dialog)          │
│  5. Aktion ausloesen                │
│     → Budget-Angebot / Ticket / ... │
└─────────────────────────────────────┘
```

---

#### Telefon (Voice)

```
ANRUF EINGANG
     │
     ▼
┌─────────────┐
│ Klingelt... │
└─────────────┘
     │
     ├── Mitarbeiter nimmt ab → Normale Erfassung + Transkript
     │
     └── Nach X Klingeln niemand da
              │
              ▼
     ┌─────────────────────────────────────┐
     │  🤖 KI-CHATBOT NIMMT AB             │
     │                                     │
     │  "Guten Tag, JS Fenster und Tueren, │
     │   mein Name ist [KI-Name].          │
     │   Wie kann ich Ihnen helfen?"       │
     └─────────────────────────────────────┘
              │
              ▼
     ┌─────────────────────────────────────┐
     │  GESPRAECH FUEHREN                  │
     │                                     │
     │  - Anliegen erfassen                │
     │  - Kontaktdaten abfragen            │
     │  - Bei Reparatur: Details sammeln   │
     │  - Termin-Wunsch erfragen           │
     └─────────────────────────────────────┘
              │
              ▼
     ┌─────────────────────────────────────┐
     │  AUSWERTUNG                         │
     │                                     │
     │  Genuegend Infos fuer Budget?       │
     │  ├── JA → Budget-Angebot per Mail   │
     │  └── NEIN → Rueckruf-Aufgabe        │
     └─────────────────────────────────────┘
```

**Technische Umsetzung:**

| Komponente | Option | Bemerkung |
|------------|--------|-----------|
| **Telefonie** | VoIP/SIP Integration | Oder Cloud-Dienst (Twilio, etc.) |
| **Speech-to-Text** | Whisper (lokal/API) | Echtzeit-Transkription |
| **Chatbot-Logik** | Claude/GPT mit Prompt | Gespraechsfuehrung |
| **Text-to-Speech** | ElevenLabs / Azure | Natuerliche Stimme |

**Chatbot-Gespraechsfluss (Reparatur):**

```
KI: "Handelt es sich um eine Reparatur oder ein neues Projekt?"
Kunde: "Reparatur, mein Fenster klemmt"

KI: "Verstehe. Koennen Sie mir sagen, um welches Fenster es geht?
     Zum Beispiel: Wohnzimmer, Kueche, oder welches Stockwerk?"
Kunde: "Kueche im Erdgeschoss"

KI: "Ist das Fenster von uns, JS Fenster, oder von einem anderen Anbieter?"
Kunde: "Ja, von euch, vor 3 Jahren eingebaut"

KI: "Perfekt, dann haben wir Ihre Daten vermutlich schon.
     Unter welcher Telefonnummer erreichen wir Sie am besten?"
Kunde: "0961 12345"

KI: [Sucht in DB → Kunde gefunden]
    "Herr Mueller, richtig? Ich sehe Ihr Projekt von 2022.
     Wir melden uns morgen bei Ihnen fuer einen Termin.
     Alternativ kann ich Ihnen gleich einen Kostenrahmen
     fuer die Reparatur nennen. Moechten Sie das?"
```

**Vorteile:**

| Vorteil | Auswirkung |
|---------|------------|
| 24/7 erreichbar | Kein verpasster Kunde |
| Sofort Daten im System | Kein Zettel, kein Vergessen |
| Budget-Angebot automatisch | Mitarbeiter nur bei Bedarf |
| Transkript als Dokumentation | Nachvollziehbar |
| Bestandskunde erkannt | Persoenliche Ansprache |

**Eskalation an Mitarbeiter:**

| Situation | Aktion |
|-----------|--------|
| Kunde will Mitarbeiter | "Ich verbinde Sie" / Rueckruf-Aufgabe |
| Komplexe Fragen | Transkript + KRITISCH-Flag |
| Reklamation/Beschwerde | Sofort-Benachrichtigung an Andreas |
| Technische Probleme | Aufnahme + Entschuldigung |

---

#### E-Mail (Text)

```
E-MAIL EINGANG
     │
     ▼
🤖 AUTONOM: Absender pruefen → Bestandskunde?
🤖 AUTONOM: Betreff + Inhalt analysieren
🤖 AUTONOM: Klassifizieren:
     ├── Lieferant → Ordner "Lieferanten"
     ├── Rechnung/AB → Ordner "Buchhaltung"
     ├── Anfrage → KI-Dialog starten
     └── Reklamation → KRITISCH + Andreas
          │
          ▼ (bei Anfrage)
🤖 AUTONOM: Auto-Antwort mit Rueckfragen
     "Danke fuer Ihre Anfrage. Um Ihnen ein Angebot
      erstellen zu koennen, benoetigen wir noch:
      - Anzahl der Fenster/Tueren
      - Ungefaehre Masse (Breite x Hoehe)
      - Neubau oder Sanierung?"
          │
          ▼
🤖 AUTONOM: Kunde antwortet → Daten extrahieren
🤖 AUTONOM: Genuegend Infos? → Budget-Angebot
🤖 AUTONOM: Sonst → Weitere Rueckfrage ODER Ticket
```

---

#### WhatsApp / Telegram (Chat)

**Einrichtung noetig:**

| Dienst | Was | Aufwand |
|--------|-----|---------|
| **WhatsApp Business** | Telefonnummer verifizieren, Business API | Mittel |
| **Telegram Bot** | @BotFather, Token generieren | Einfach |

**Chat-Flow (gleich fuer beide):**

```
NACHRICHT EINGANG
     │
     ▼
🤖 AUTONOM: "Hallo! Ich bin der digitale Assistent
             von JS Fenster. Wie kann ich helfen?"
     │
     ▼
👤 KUNDE: "Brauche neue Fenster"
     │
     ▼
🤖 AUTONOM: "Gerne! Ein paar kurze Fragen:
             1️⃣ Neubau oder Sanierung?
             2️⃣ Wie viele Fenster ungefaehr?
             3️⃣ In welcher Stadt/Region?"
     │
     ▼
👤 KUNDE: "Sanierung, 6 Fenster, Amberg"
     │
     ▼
🤖 AUTONOM: "Super! Fuer 6 Fenster bei Sanierung
             liegt der Rahmen bei ca. X-Y €.

             Moechten Sie:
             📧 Budget-Angebot per E-Mail
             📞 Rueckruf vereinbaren
             📅 Aufmass-Termin buchen"
     │
     ▼
👤 KUNDE: "Budget-Angebot"
     │
     ▼
🤖 AUTONOM: "Ihre E-Mail-Adresse bitte?"
👤 KUNDE: "test@example.de"
🤖 AUTONOM: Budget-Angebot generieren + versenden
🤖 AUTONOM: "Fertig! Sie erhalten gleich eine E-Mail.
             Bei Fragen einfach hier schreiben!"
```

**Vorteile Chat vs. Telefon:**

| Aspekt | Vorteil |
|--------|---------|
| Asynchron | Kunde antwortet wenn Zeit |
| Bilder | Kunde kann Fotos schicken (Reparatur!) |
| Link-Versand | Direkt Termin-Buchung verlinken |
| Historie | Chat bleibt erhalten |
| Junge Zielgruppe | Bevorzugt Chat vor Telefon |

**Foto-Upload bei Reparatur:**

```
👤 KUNDE: [Foto von kaputtem Fenster]
🤖 AUTONOM: "Danke fuer das Foto! Ich sehe:
             - Fenstergriff scheint gebrochen
             - Ist das korrekt?"
👤 KUNDE: "Ja genau"
🤖 AUTONOM: "Ein neuer Griff inkl. Einbau kostet
             ca. 80-120€. Soll ich einen Termin
             fuer unseren Servicetechniker Stefan
             vorschlagen?"
```

---

### Besonderheit: Preisanfrage an Lieferant

Bei nicht-rechenbaren Produkten (kein Standardpreis):

```
1. PREISANFRAGE NOETIG
   👤 USER: Markiert Position als "Lieferant-Anfrage"
   🤖 AUTONOM: Projekt automatisch erstellt (falls noch nicht)
   🤖 AUTONOM: E-Mail-Vorlage an Lieferant generieren
   🤖 AUTONOM: Warte-Status im Ticket

2. ANTWORT EINGEHT
   🤖 AUTONOM: E-Mail erkennen → Ticket reaktivieren
   👤 USER: Preis uebernehmen
   🤖 AUTONOM: Angebot vervollstaendigen
```

### Tool-Referenzen (aus IDEEN.md)

| Tool | Funktion | Autonomie |
|------|----------|-----------|
| #12 E-Mail Auto-Klassifizierung | Eingehende E-Mails kategorisieren | 🤖 Autonom |
| #23 Verkaufs-Pipeline | Visualisierung Anfrage → Auftrag | 🤖 Autonom |
| #24 Digitale Checklisten | Telefon-Anfrage strukturiert erfassen | 🤖 Autonom |
| #47 Kunden-Historie | Alle Kontakte, Projekte, Umsatz auf einen Blick | 🤖 Autonom |
| #52 Conversion-Tracker | Anfrage → Angebot → Auftrag Quoten | 🤖 Autonom |
| #84 Kunden-Reaktivierung | Alte Projekte reaktivieren (5+/10+ Jahre) | 🤖 Autonom |

---

## Workflow: Reparatur (MAXIMAL autonom!)

> **WICHTIG:** Reparaturen haben wenig Marge aber viel Aufwand.
> Ziel: Stefan macht NUR die Reparatur vor Ort. ALLES andere laeuft automatisch.

### Schmerzpunkte heute → Neue Loesung

| Problem (aktuell) | Neue Loesung |
|-------------------|--------------|
| Zettelwirtschaft bei Erfassung | KI-Chatbot erfasst komplett |
| Kunde wird erst spaet angelegt | Sofort beim Erstkontakt |
| Terminkoordinierung = Zeitfresser | Voice-Bot macht Termine |
| Outlook-Kalender als Status-Tracker | Eigenes Reparatur-Board |
| Ersatzteilsuche 15-45 Min/Teil | KI + Auto-Recherche bei Lieferanten |
| Keine Kunden-Info bei Wartezeit | Auto-Benachrichtigung |
| Dokumente manuell scannen | Foto direkt ins System |
| Rechnung manuell erstellen | Auto-generiert nach Abschluss |

### Prozess-Schritte (End-to-End autonom)

```
1. REPARATUR-ANFRAGE EINGANG
   📞 TELEFON (KI-Chatbot):
   🤖 AUTONOM: Chatbot erfasst:
      - Name, Telefon (Bestandskunde? → Auto-Match)
      - Was ist kaputt? (Fenster klemmt, Griff gebrochen, etc.)
      - Welche Etage? (Leiter/Geruest noetig?)
      - Adresse (wenn ≠ Kunde = Mietobjekt)
   🤖 AUTONOM: Prio ermitteln:
      - Gewerbe + Fluchttueren → HOCH
      - Haustuer zu → HOCH
      - Bestandskunde → MITTEL
      - Rest → NORMAL
   🤖 AUTONOM: Termin vorschlagen aus Stefan-Kalender
   🤖 AUTONOM: Kunde bestaetigt → Termin gebucht
   🤖 AUTONOM: SMS/E-Mail Bestaetigung an Kunde

   📧 E-MAIL / 💬 WHATSAPP / TELEGRAM:
   🤖 AUTONOM: Gleiche Logik wie Telefon
   🤖 AUTONOM: Bilder annehmen → KI-Voranalyse des Schadens

   🚶 AUSSTELLUNG:
   👤 USER: Tablet-Erfassung (gleiche Maske)
   🤖 AUTONOM: Rest wie oben

2. VOR-ORT-TERMIN (Stefan)
   🤖 AUTONOM: Morgens Tages-Briefing generieren
      - Reihenfolge der Termine (Route optimiert)
      - Kundendaten + Schadensbeschreibung
      - Anfahrt (Google Maps)

   👤 STEFAN: Vor Ort beim Kunden
      - Auftrag unterschreiben lassen (digital auf Tablet)
      - 100€ Pauschale → sofort abgedeckt

   SZENARIO A - Sofort reparierbar:
   👤 STEFAN: Reparatur durchfuehren
   👤 STEFAN: App: "Fertig" + Foto + Zeit
   🤖 AUTONOM: Rechnung generieren + versenden
   → ENDE

   SZENARIO B - Ersatzteil noetig:
   👤 STEFAN: Fotos vom defekten Teil
   👤 STEFAN: App: "Ersatzteil noetig" + Beschreibung
   🤖 AUTONOM: → Naechster Schritt

3. ERSATZTEIL-IDENTIFIKATION (#62 KI-Vision)
   🤖 AUTONOM: Fotos analysieren
   🤖 AUTONOM: Teil identifizieren:
      - Hersteller erkennen (Winkhaus, Siegenia, Roto, etc.)
      - Typ/Modell ableiten
      - Masse aus Foto schaetzen
   🤖 AUTONOM: Ersatzteil-Vorschlag mit Confidence
      - >90%: "Wahrscheinlich Winkhaus Getriebe Typ X"
      - <90%: "Koennte A oder B sein, bitte pruefen"
   👤 ANDREAS: Nur bei <90% kurz bestaetigen

4. ERSATZTEIL-RECHERCHE (Auto!)
   🤖 AUTONOM: Parallele Anfrage an alle Lieferanten:
      - Gruen Beschlaege
      - Ott
      - Tonitec
      - Febes
      - (eBay fuer Nachbauten)
   🤖 AUTONOM: Ergebnis-Matrix:
      | Lieferant | Preis | Lieferzeit | Verfuegbar |
      |-----------|-------|------------|------------|
      | Gruen     | 45€   | 3 Tage     | ✅         |
      | Ott       | 42€   | 5 Tage     | ✅         |
      | Tonitec   | -     | -          | ❌         |
   🤖 AUTONOM: Guenstigsten mit kuerzester Lieferzeit waehlen
   🤖 AUTONOM: Bei Standard-Teil (<50€): Auto-Bestellung!
   👤 ANDREAS: Bei teuren Teilen (>50€) nur Freigabe-Klick

5. ERSATZTEIL-BESTELLUNG
   🤖 AUTONOM: Bestellung an Lieferant (E-Mail/Portal)
   🤖 AUTONOM: Liefertermin tracken
   🤖 AUTONOM: Kunde informieren:
      "Ersatzteil bestellt, voraussichtlich KW X.
       Wir melden uns fuer den Folgetermin."

6. ERSATZTEIL EINGETROFFEN
   🤖 AUTONOM: Wareneingang erkannt (Lieferschein-Scan)
   🤖 AUTONOM: Voice-Bot ruft Kunden an:
      "Guten Tag Herr Mueller, hier JS Fenster.
       Ihr Ersatzteil ist da. Wann passt Ihnen
       ein Termin? Dienstag 10 Uhr oder Mittwoch 14 Uhr?"
   🤖 AUTONOM: Termin gebucht
   🤖 AUTONOM: SMS-Bestaetigung an Kunde
   🤖 AUTONOM: Stefan-Kalender aktualisiert

7. FOLGETERMIN (Stefan)
   👤 STEFAN: Reparatur durchfuehren
   👤 STEFAN: App: "Fertig" + Zeit + Fotos
   🤖 AUTONOM: Arbeitszeit berechnen
   🤖 AUTONOM: Material-Kosten addieren
   🤖 AUTONOM: Rechnung generieren

8. RECHNUNG (Auto!)
   🤖 AUTONOM: Rechnung erstellen:
      - Anfahrt (Zone aus PLZ)
      - Arbeitszeit × Stundensatz
      - Ersatzteil-Kosten
      - Abzug 100€ Pauschale (wenn bezahlt)
   🤖 AUTONOM: PDF generieren (mit Wasserzeichen)
   🤖 AUTONOM: E-Mail an Kunde
   🤖 AUTONOM: DATEV-Export vorbereiten

9. ZAHLUNG + NACHVERFOLGUNG
   🤖 AUTONOM: HBCI-Kontoabgleich
   🤖 AUTONOM: Zahlung erkannt → Abgeschlossen
   🤖 AUTONOM: Nicht bezahlt nach 14 Tagen → Auto-Mahnung
   🤖 AUTONOM: Google-Bewertung vorschlagen (wenn positiv)
```

### Reparatur-Board (Echtzeit-Uebersicht)

```
┌────────────────────────────────────────────────────────────────────┐
│  REPARATUR-BOARD                        Heute: 7 | Offen: 23      │
├────────────────────────────────────────────────────────────────────┤
│                                                                    │
│  HEUTE (Stefan)                                                    │
│  ┌──────────────────────────────────────────────────────────────┐ │
│  │ 08:30  Mueller, Amberg         Fenster klemmt      [AKTUELL] │ │
│  │ 10:00  Schmidt, Weiden         Griff gebrochen     [GEPLANT] │ │
│  │ 11:30  Weber, Sulzbach         Dichtung            [GEPLANT] │ │
│  │ 14:00  Klein, Amberg           Schloss defekt      [GEPLANT] │ │
│  └──────────────────────────────────────────────────────────────┘ │
│                                                                    │
│  ── ERSATZTEIL WARTEN (12) ─────────────────────────────────────  │
│  │ Bauer      Getriebe       Bestellt 18.12.  Lieferung: 23.12.  │
│  │ Huber      Griff          Bestellt 19.12.  Lieferung: 22.12.  │
│  │ Meier      Schliessblech  ⚠️ Nicht lieferbar → Nachbau?      │
│                                                                    │
│  ── ERSATZTEIL DA → TERMIN MACHEN (3) ──────────────────────────  │
│  │ Schulze    Getriebe       🤖 Voice-Bot ruft gerade an...     │
│  │ Fischer    Olive          🤖 Termin vorgeschlagen: 27.12.    │
│  │ Wagner     Dichtung       ✅ Termin bestaetigt: 24.12. 09:00 │
│                                                                    │
│  ── RECHNUNG OFFEN (5) ─────────────────────────────────────────  │
│  │ Braun      156,00€        Faellig: 28.12.   [Bezahlt ✓]      │
│  │ Krause     89,50€         Faellig: 02.01.   [Offen]          │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

### Stefan-App (Monteur vor Ort)

```
┌─────────────────────────────────────────────────────────────┐
│  📱 REPARATUR-APP                   🔋 92%  📶  08:15      │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  AKTUELL: Mueller, Amberg                                   │
│  Fenster klemmt (Kueche, EG)                               │
│                                                             │
│  📍 Musterstrasse 12, 92224 Amberg                         │
│  📞 0961 / 12345                                            │
│                                                             │
│  ── Aktion ────────────────────────────────────────────    │
│                                                             │
│  [📝 Auftrag unterschreiben]     ← Vor Arbeitsbeginn!      │
│                                                             │
│  [🔧 Sofort repariert]           [🔩 Ersatzteil noetig]    │
│                                                             │
│  ── Fotos ─────────────────────────────────────────────    │
│  [📷 Foto aufnehmen]   0 Fotos                             │
│                                                             │
│  ── Sprachnotiz ───────────────────────────────────────    │
│  [🎤 Aufnehmen]                                             │
│  "Fenster von 2015, Winkhaus Getriebe,                     │
│   muss getauscht werden, ca. 45€ Teil"                     │
│                                                             │
│  ── Zeit ──────────────────────────────────────────────    │
│  Start: 08:32    [⏱️ Laeuft: 00:15]    [⏹️ Stopp]          │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Ersatzteil-Identifikation per KI (#62)

```
FOTO HOCHGELADEN
     │
     ▼
🤖 KI-VISION ANALYSIERT:
     │
     ├── Hersteller-Logo erkannt? → "Winkhaus"
     │
     ├── Bauteil-Typ erkannt? → "Fenstergetriebe"
     │
     ├── Masse geschaetzt? → "ca. 40cm Laenge"
     │
     └── Verschleiss-Zustand? → "Zaehne abgenutzt"
          │
          ▼
ERGEBNIS:
┌─────────────────────────────────────────────────────────────┐
│  🔍 ERSATZTEIL-VORSCHLAG                                    │
│                                                             │
│  Erkannt: Winkhaus Getriebe FFH 1101-1400                  │
│  Confidence: 94%                                            │
│                                                             │
│  Moegliche Artikel:                                         │
│  ✅ Winkhaus Getriebe 1101-1400    ~42€   (94%)            │
│  ○  Winkhaus Getriebe 901-1100     ~38€   (12%)            │
│  ○  Siegenia Getriebe axxent       ~45€   (5%)             │
│                                                             │
│           [✓ Uebernehmen]    [✎ Korrigieren]               │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Automatische Lieferanten-Recherche

```
ERSATZTEIL IDENTIFIZIERT: "Winkhaus Getriebe FFH 1101-1400"
     │
     ▼
🤖 AUTONOM: Parallele Anfragen (5 Sekunden)
     │
     ├── Gruen-Beschlaege.de → Scraping/API
     ├── Ott-Beschlaege.de → Scraping
     ├── Tonitec.de → Scraping
     ├── Febes.de → Scraping
     └── eBay.de → API (Nachbauten)
          │
          ▼
ERGEBNIS-MATRIX:
┌────────────────────────────────────────────────────────────┐
│  VERFUEGBARKEIT: Winkhaus Getriebe FFH 1101-1400          │
├────────────────────────────────────────────────────────────┤
│  Lieferant      │ Preis  │ Lieferzeit │ Verfuegbar        │
│─────────────────┼────────┼────────────┼───────────────────│
│  Gruen          │ 42,50€ │ 2-3 Tage   │ ✅ Lager          │
│  Ott            │ 44,00€ │ 3-4 Tage   │ ✅ Lager          │
│  Tonitec        │ 41,80€ │ 5-7 Tage   │ ⏳ Bestellware    │
│  Febes          │ -      │ -          │ ❌ Nicht gefunden │
│  eBay (Nachbau) │ 28,00€ │ 7-10 Tage  │ ✅ 3 Anbieter     │
├────────────────────────────────────────────────────────────┤
│  🤖 EMPFEHLUNG: Gruen (42,50€, 2-3 Tage)                  │
│                                                            │
│  [✓ Auto-Bestellen]    [Andere waehlen]    [Abbrechen]    │
└────────────────────────────────────────────────────────────┘
```

### Autonomie-Level Reparatur

| Schritt | Autonomie | Begruendung |
|---------|-----------|-------------|
| Anfrage-Erfassung | 🤖 100% | KI-Chatbot |
| Termin-Erstbesuch | 🤖 100% | Voice-Bot/Chat |
| Prio-Einstufung | 🤖 100% | Regelbasiert |
| Unterschrift | 👤 Manuell | Rechtlich noetig |
| Reparatur vor Ort | 👤 Manuell | Handwerk |
| Ersatzteil-ID | 🤖 90% | KI-Vision, selten Pruefung |
| Lieferanten-Recherche | 🤖 100% | Auto-Scraping |
| Bestellung <50€ | 🤖 100% | Auto-Bestellung |
| Bestellung >50€ | 👤 1-Klick | Freigabe |
| Folgetermin | 🤖 100% | Voice-Bot |
| Rechnung | 🤖 100% | Auto-generiert |
| Mahnung | 🤖 100% | Auto nach Frist |

**Ergebnis:** Stefan macht nur noch die Reparatur. ~80% des Verwaltungsaufwands entfaellt!

### Tool-Referenzen (aus IDEEN.md)

| Tool | Funktion | Autonomie |
|------|----------|-----------|
| #62 KI-Vision Ersatzteil | Foto → Bauteil-Erkennung | 🤖 Autonom |
| #77 Schadens-ChatBot | Bilder + Sprache → Auto-Meldung | 🤖 Autonom |
| #54 Preis-Vergleich | Parallele Lieferanten-Recherche | 🤖 Autonom |
| #22 Routenplanung | Optimale Reihenfolge Stefan-Termine | 🤖 Autonom |
| #34 GPS-Zeiterfassung | Auto-Start/Stop bei Kunde | 🤖 Autonom |
| #50 Zahlungserinnerung | Sanfte Mahnung nach Frist | 🤖 Autonom |

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
- [ ] Technische Architektur (Detail)
- [ ] UI/UX Design

---

## Changelog

| Datum | Aenderung |
|-------|-----------|
| 2025-12-22 | Dokument erstellt |
| 2025-12-22 | Grundprinzipien: Autonomie, Lernendes System |
| 2025-12-22 | Positions-Management: Soft-Delete, Versionierung |
| 2025-12-22 | Positionsnummern: Freitext statt Auto-Korrektur |
| 2025-12-22 | Lernsystem: Stille Sammlung, Wochen-Digest |
| 2025-12-22 | Berechtigungen: Admin/Co-Trainer/User |
| 2025-12-22 | Konfigurator-Strategie dokumentiert |
| 2025-12-22 | Wasserzeichen-Integration praezisiert (nur Grafik, nicht ganzes Briefpapier) |
| 2025-12-22 | Workflow Bestellung → Wareneingang dokumentiert |
| 2025-12-22 | Workflow Rechnung → Zahlung → Mahnung dokumentiert |
| 2025-12-22 | Beschaffungs-Dashboard Konzept |
| 2025-12-22 | Rechnungs-Dashboard Konzept |
| 2025-12-22 | Teilrechnungs-Logik dokumentiert |
| 2025-12-22 | Workflow Montage dokumentiert |
| 2025-12-22 | Monteur-App Konzept (Tagesuebersicht, Rueckmeldung) |
| 2025-12-22 | Montage-Board Konzept (Buero-Ansicht) |
| 2025-12-22 | Spracheingabe fuer Monteure (Speech-to-Text) |
| 2025-12-22 | Hardware-Anforderung (Smartphones, Tablets, Headsets) |
| 2025-12-22 | Workflow Anfrage/CRM dokumentiert |
| 2025-12-22 | Anfrage-Erfassung Schnell-Maske Konzept |
| 2025-12-22 | CRM-Pipeline Dashboard Konzept |
| 2025-12-22 | Marketing-Auswertung ("Wie gefunden?") |
| 2025-12-22 | Nachverfolgung-Sequenz (automatisches Follow-up) |
| 2025-12-22 | Telefon-Chatbot Konzept (KI nimmt ab wenn niemand da) |
| 2025-12-22 | Sprach-Transkription bei Telefonaten |
| 2025-12-22 | Autonomes Budget-Angebot aus Chatbot-Daten |
| 2025-12-22 | KI-Assistent Multi-Channel (Telefon, E-Mail, WhatsApp, Telegram) |
| 2025-12-22 | E-Mail Auto-Klassifizierung + Dialog |
| 2025-12-22 | WhatsApp/Telegram Chat-Flow mit Foto-Upload |
| 2025-12-22 | Entkopplungs-Strategie (eigenstaendiges System, kein W4A-Addon) |
| 2025-12-22 | IDEEN.md Autonomie-Features integriert |
| 2025-12-22 | #66 Wetter-Integration bei Montage |
| 2025-12-22 | #72 Referenz-Fotos nach Montage |
| 2025-12-22 | #73 Google-Bewertung Vorschlag |
| 2025-12-22 | #81 PDF-Merger fuer DATEV |
| 2025-12-22 | #82 Buchungskonto-Assistent |
| 2025-12-22 | #84 Kunden-Reaktivierung (2.700 Projekte) |
| 2025-12-22 | #70 Montagematerial-Pauschale |
| 2025-12-22 | #3 BAFA-Tracking (KRITISCH!) |
| 2025-12-22 | Workflow Reparatur dokumentiert (MAXIMAL autonom) |
| 2025-12-22 | Reparatur-Board Konzept |
| 2025-12-22 | Stefan-App Konzept (Reparatur vor Ort) |
| 2025-12-22 | #62 KI-Vision Ersatzteil-Erkennung |
| 2025-12-22 | Auto-Lieferanten-Recherche (Scraping) |
| 2025-12-22 | Voice-Bot fuer Folgetermine |
| 2025-12-22 | Autonomie-Level: 80% Verwaltungsaufwand entfaellt |
| 2025-12-22 | Tool-Referenzen zu allen Workflows hinzugefuegt |
