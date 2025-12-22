# Workflow: Reparatur (MAXIMAL autonom!)

> **Zurueck:** [README.md](README.md) | **Siehe auch:** [KI_ASSISTENT.md](KI_ASSISTENT.md)

> **WICHTIG:** Reparaturen haben wenig Marge aber viel Aufwand.
> Ziel: Stefan macht NUR die Reparatur vor Ort. ALLES andere laeuft automatisch.

---

## Schmerzpunkte heute → Neue Loesung

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

---

## Prozess-Schritte (End-to-End autonom)

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

---

## Reparatur-Board (Echtzeit-Uebersicht)

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

---

## Stefan-App (Monteur vor Ort)

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

---

## Ersatzteil-Identifikation per KI (#62)

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

---

## Automatische Lieferanten-Recherche

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

---

## Autonomie-Level Reparatur

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

---

## Tool-Referenzen (aus IDEEN.md)

| Tool | Funktion | Autonomie |
|------|----------|-----------|
| #22 Routenplanung | Optimale Reihenfolge Stefan-Termine | 🤖 Autonom |
| #34 GPS-Zeiterfassung | Auto-Start/Stop bei Kunde | 🤖 Autonom |
| #50 Zahlungserinnerung | Sanfte Mahnung nach Frist | 🤖 Autonom |
| #54 Preis-Vergleich | Parallele Lieferanten-Recherche | 🤖 Autonom |
| #62 KI-Vision Ersatzteil | Foto → Bauteil-Erkennung | 🤖 Autonom |
| #77 Schadens-ChatBot | Bilder + Sprache → Auto-Meldung | 🤖 Autonom |
