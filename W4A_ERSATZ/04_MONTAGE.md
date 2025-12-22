# Workflow: Montage

> **Zurueck:** [README.md](README.md)

---

## Schmerzpunkte heute → Neue Loesung

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

---

## Prozess-Schritte

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

---

## Wetter-Integration (#66)

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

---

## Monteur-App Konzept

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

---

## Rueckmeldung-Bildschirm

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

---

## Montage-Board (Buero-Ansicht)

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

---

## Spracheingabe fuer Monteure

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

---

## Hardware-Anforderung

| Geraet | Aktuell | Empfehlung |
|--------|---------|------------|
| Monteur-Smartphones | Schlecht (privat?) | Robuste Firmen-Smartphones |
| Tablets | Keine | 2-3 robuste Tablets (IP68) fuer Unterschrift |
| Headset/Kopfhoerer | - | Optional fuer Spracheingabe in lauter Umgebung |

**Option A:** Nur Smartphones (guenstiger, aber kleine Bildschirme)
**Option B:** Tablets fuer Unterschrift + Mappe, Smartphone fuer Kommunikation
**Option C:** Smartphone mit Bluetooth-Headset (beste Spracheingabe)

---

## Tool-Referenzen (aus IDEEN.md)

| Tool | Funktion | Autonomie |
|------|----------|-----------|
| #22 Routenplanung | Optimale Reihenfolge der Montagen | 🤖 Autonom |
| #34 GPS-Zeiterfassung | Auto-Start/Stop bei Kunde (kein manuelles Stempeln) | 🤖 Autonom |
| #39 Digitale Montage-Mappe | Alle Dokumente auf Tablet/Smartphone | 🤖 Autonom |
| #41 Status Live | Echtzeit-Status aller Montagen im Buero | 🤖 Autonom |
| #66 Wetter-Integration | Warnung bei Regen/Sturm/Frost | 🤖 Autonom |
| #72 Referenz-Fotos | Nach Montage Fotos fuer Website | 🤖 Autonom |
| #73 Google-Bewertung | Nach positiver Rueckmeldung Link senden | 🤖 Autonom |
