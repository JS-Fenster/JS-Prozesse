# GPS-Tracking & Echtzeit-Analyse

> **Zurueck:** [README.md](README.md)

> **Zentrales Feature:** GPS-Tracking ermoeglicht viele autonome Funktionen

---

## Verspaetungs-Benachrichtigung (Auto!)

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

---

## GPS-basierte Analysen (Auto!)

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

---

## Dashboard: GPS-Echtzeit

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

---

## Wochenanalyse (Auto-Report)

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

---

## Technische Umsetzung GPS

| Komponente | Option | Kosten |
|------------|--------|--------|
| **GPS-Hardware** | Smartphone der Monteure | 0€ (vorhanden) |
| **Tracking-App** | Eigene PWA oder fertige App | 0-10€/User/Monat |
| **Karten-API** | Google Maps / OpenStreetMap | 0-200€/Monat |
| **Datenschutz** | Nur waehrend Arbeitszeit, DSGVO-konform | Einwilligung noetig |

---

## Tool-Referenzen (aus IDEEN.md)

| Tool | Funktion | Autonomie |
|------|----------|-----------|
| #19 Lieferanten-Bewertung | Wartezeit bei Abholungen tracken | 🤖 Autonom |
| #22 Routenplanung | Ineffiziente Routen erkennen | 🤖 Autonom |
| #34 GPS-Zeiterfassung | Auto-Start/Stop bei Kunde | 🤖 Autonom |
| #44 Kapazitaets-Cockpit | Auslastungs-Analyse | 🤖 Autonom |
