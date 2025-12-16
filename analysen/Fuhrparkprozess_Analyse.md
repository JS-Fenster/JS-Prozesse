# Fuhrparkprozess - IST-Analyse

**Erstellt:** 2025-12-16 | **Quelle:** Screenshots W4A, Gespraech mit Andreas

---

## Prozess-Uebersicht

```
FAHRZEUGBESTAND (W4A Inventar)
│
├─ Gruppe "Fuhrpark" in Inventarliste
├─ Pro Fahrzeug: Internes Projekt (IP00XX)
│   └─ Alle Dokumente (Versicherung, TUeV, Rechnungen)
│
▼
LAUFENDER BETRIEB
├─ Tanken: UTA-Tankkarten
├─ Kilometerstand: Nur bei Tankvorgang erfasst
├─ Werkstatt: Susann koordiniert
│
▼
WARTUNG & PRUEFUNG
├─ TUeV/HU: → #74 Prueffristen-Automatik
├─ UVV: → #74 Prueffristen-Automatik
├─ Inspektionen: Tickets pro Auto
└─ Reifenwechsel: Susann organisiert
```

---

## Fahrzeugbestand

### Uebersicht (Stand 2025-12-16)

**Gesamtwert Fuhrpark:** 74.146,71 EUR

| Fahrzeug | Kennzeichen | Baujahr | Zuordnung | Akt. Wert | Zustand |
|----------|-------------|---------|-----------|-----------|---------|
| Opel Movano Cargo | AM-JS 63 | 2025 | Montage 4 (Manfred) | 26.553,78 | neu |
| Ford Connect | AM-JS 69 | 2025 | Andreas | 35.489,50 | neu |
| Mercedes Citan | AM-JS 41 | 2021 | Jaroslaw | 0,00 | gebraucht |
| Fiat Ducato | AM-JS 17 | 2020 | Team 3 (Stefan) | 0,00 | gebraucht |
| Fiat Ducato | AM-JS 7 | 2019 | Team 2 (Christian) | 0,00 | gebraucht |
| Ford Connect | AM-JS 19 | 2019 | Enrico | 0,00 | gebraucht |
| Ford Connect | AS-JS 217 | 2018 | Lager | 0,00 | gebraucht |
| Fiat Ducato | AS-JS 124 | 2014 | Team 1 (Mariusz) | 0,00 | stark gebraucht |
| Fiat Punto | AS-JS 114 | 2013 | Roland | 0,00 | gebraucht |

### Sonderfahrzeuge

| Fahrzeug | Kennzeichen/ID | Baujahr | Zuordnung | Akt. Wert |
|----------|----------------|---------|-----------|-----------|
| Stapler Toyota 7FBMF25 | - | 2025 | Lager | 5.000,00 |
| Anhaenger | AM-J 16 | 2020 | Lager | 2.269,00 |
| Anhaenger | AS-J 134 | 2002 | Lager | 1.831,93 |
| Fahrrad LTD Corratec | - | 2023 | Roland (Privat) | 3.002,50 |

### Team-Zuordnung (Montage)

| Team | Fahrer | Fahrzeug |
|------|--------|----------|
| Team 1 | Mariusz (+ Manfred) | Fiat Ducato AS-JS 124 |
| Team 2 | Christian (+ Michael) | Fiat Ducato AM-JS 7 |
| Team 3 | Stefan | Fiat Ducato AM-JS 17 |
| Team 4 | Manfred | Opel Movano AM-JS 63 |
| Einzeln | Jaroslaw | Mercedes Citan AM-JS 41 |
| Einzeln | Enrico | Ford Connect AM-JS 19 |
| Einzeln | Andreas | Ford Connect AM-JS 69 |
| Einzeln | Roland | Fiat Punto AS-JS 114 |
| Reserve | Lager | Ford Connect AS-JS 217 |

---

## Dokumentenverwaltung (W4A)

### Pro Fahrzeug: Internes Projekt

Jedes Fahrzeug hat ein eigenes Projekt in W4A (Gruppe "Interne Projekte → Fuhrpark"):

| Projekt-Nr | Fahrzeug | Projektleiter | Beginn |
|------------|----------|---------------|--------|
| IP0018 | Anhaenger AS-J 134 | Susann Zielinski | 18.02.2002 |
| IP0020 | Fahrrad Corratec Trekking | Susann Zielinski | 27.01.2023 |
| IP0023 | Fiat Ducato AM-JS 17 | Susann Zielinski | 23.11.2020 |
| IP0022 | Fiat Ducato AM-JS 7 | Susann Zielinski | 30.04.2020 |
| IP0024 | Fiat Ducato AS-JS 124 | Susann Zielinski | 03.07.2018 |
| IP0025 | Fiat Punto AS-JS 114 | Susann Zielinski | 07.06.2013 |
| IP0026 | Ford Connect AM-JS 19 | Susann Zielinski | 03.03.2021 |
| IP0038 | Ford Connect AM-JS 69 | Andreas Stolar... | 21.10.2024 |
| IP0027 | Ford Connect AS-JS 217 | Susann Zielinski | 14.09.2018 |
| IP0028 | Mercedes Citan AM-JS 41 | Susann Zielinski | 13.01.2022 |
| IP0042 | Opel Movano AM-JS 63 | Andreas Stolar... | 20.12.2024 |
| IP0050 | Stapler Toyota 7FBMF25 | Sandra Stolarc... | 25.07.2025 |
| IP0049 | Anhaenger AM-J 16 | Andreas Stolar... | 22.07.2025 |

### Dokumente pro Fahrzeug-Projekt

| Dokumenttyp | Ablageort | Bemerkung |
|-------------|-----------|-----------|
| Fahrzeugschein | W4A Projekt | Kopie |
| Versicherungspolice | W4A Projekt | Jaehrlich aktualisieren |
| TUeV-Berichte | W4A Projekt | Nach jeder HU |
| UVV-Pruefprotokolle | W4A Projekt | Jaehrlich |
| Werkstattrechnungen | W4A Projekt | Laufend |
| Kaufvertrag/Rechnung | W4A Projekt | Einmalig |

---

## Tanken & Kilometerstand

### UTA-Tankkarten

| Aspekt | Details |
|--------|---------|
| **Anbieter** | UTA |
| **Karten** | Pro Fahrzeug eine Karte |
| **Abrechnung** | Monatliche Sammelrechnung (PDF) |
| **Ausland** | 5-10 Fahrten pro Jahr |
| **Land-Splitting** | Benoetigt fuer Buchhaltung → #69 |

### Kilometerstand

| Aspekt | IST | Problem |
|--------|-----|---------|
| **Erfassung** | Nur bei Tankvorgang (UTA) | Keine aktive Ueberwachung |
| **Auswertung** | Nicht vorhanden | Wartungsintervalle schwer planbar |
| **Laufleistung** | Unbekannt | Keine Restwert-Schaetzung moeglich |

---

## Wartung & Werkstatt

### Verantwortlichkeiten

| Aufgabe | Verantwortlich | Methode |
|---------|----------------|---------|
| Werkstatt-Termine | Susann | Telefonisch/Online |
| Reifenwechsel | Susann | Saisonal koordinieren |
| Inspektionen | Susann | W4A Tickets pro Auto |
| TUeV-Termine | Mario (via #74) | Prueffristen-Tracking |

### Werkstaetten

| Werkstatt | Fuer | Bemerkung |
|-----------|------|-----------|
| Auto Scharl | Alle | Stammwerkstatt |
| Vertragswerkstaetten | Neufahrzeuge | Solange Gewaehrleistung |

### Wartungs-Tracking (IST)

Aktuell: **W4A Tickets pro Fahrzeug**
- Pro Auto ein Ticket fuer laufende Wartung
- Termine werden dort notiert

---

## Prueffristen (→ #74)

| Pruefung | Intervall | Fahrzeuge | Verantwortlich |
|----------|-----------|-----------|----------------|
| TUeV/HU | 1 Jahr (Nutzfahrzeuge) | Alle Transporter | Mario |
| TUeV/HU | 2 Jahre | PKW, Anhaenger | Mario |
| UVV | Jaehrlich | Alle Fahrzeuge | Mario |
| Stapler-Pruefung | Jaehrlich | Toyota Stapler | Mario |

---

## Erkannte Probleme

| # | Problem | Auswirkung | Loesung |
|---|---------|------------|---------|
| 1 | **Schadensmeldung unklar** | Susann meint Sandra, Sandra meint Susann → keiner fuehlt sich zustaendig | Klare Zustaendigkeit definieren! |
| 2 | **Kilometerstand passiv** | Nur bei Tanken erfasst, keine Auswertung | Optional: Monatliche Erfassung |
| 3 | **Fuehrerschein-Kontrolle fehlt** | Gesetzliche Pflicht! Arbeitgeber haftet | → #75 Fuehrerschein-Kontrolle |
| 4 | **Verbandskästen nicht getrackt** | Material verfaellt, Bussgeld moeglich | → #74 erweitern |
| 5 | **Keine Laufleistungs-Uebersicht** | Wartungsintervalle, Restwert unklar | Nice-to-have |

### Schadensmeldung - Prozess definieren

**VORSCHLAG:**

```
SCHADEN PASSIERT
     │
     ▼
FAHRER meldet sofort an SUSANN
├─ Telefonisch oder WhatsApp
├─ Mit Fotos
└─ Unfallbericht wenn noetig
     │
     ▼
SUSANN erfasst in W4A
├─ Im Fahrzeug-Projekt dokumentieren
├─ Versicherung informieren wenn noetig
└─ Werkstatt-Termin koordinieren
```

**Verantwortlich:** Susann (eindeutig!)

---

## Verbesserungspotential (Ideen-Verknuepfung)

| Bereich | Tool-Idee | Verbesserung |
|---------|-----------|--------------|
| Prueffristen | #74 Prueffristen-Automatik | TUeV, UVV, Verbandskästen auto-erinnern |
| Tankrechnungen | #69 UTA-PDF-Tool | Nach Land splitten fuer Buchhaltung |
| Fuehrerschein | #75 Fuehrerschein-Kontrolle | Gesetzliche Pflicht erfuellen |
| Inventar | #13 Inventar-Verwaltung | Fahrzeuge sind Teil davon |

---

## Sonstige Hinweise

### Fuehrerschein-Kontrolle (gesetzliche Pflicht)

**Hintergrund:**
- Arbeitgeber muss sicherstellen, dass Fahrer gueltigen Fuehrerschein haben
- Empfehlung: Mind. 2x jaehrlich pruefen
- Bei Unfall ohne gueltige Fahrerlaubnis: Arbeitgeber haftet!

**Zu erfassen:**
- Wer faehrt welches Fahrzeug?
- Fuehrerschein gueltig bis?
- Letzte Kontrolle am?
- Naechste Kontrolle faellig?

→ Siehe #75 Fuehrerschein-Kontrolle

### Verbandskästen

**Pflicht:**
- Jedes Fahrzeug braucht Verbandskasten
- Inhalt hat Ablaufdatum (ca. 4-5 Jahre)
- Bei TUeV-Pruefung relevant

**Zu erfassen:**
- Verbandskasten vorhanden?
- Ablaufdatum Inhalt?
- Auto-Erinnerung X Monate vorher

→ In #74 integrieren

---

## Naechste Schritte

1. **Sofort:** Schadensmeldungs-Prozess klaeren (Susann = verantwortlich)
2. **Kurzfristig:** #74 um Verbandskästen erweitern
3. **Kurzfristig:** #75 Fuehrerschein-Kontrolle umsetzen
4. **Optional:** Kilometerstand-Tracking einfuehren

---

## Change Log

| Datum | Aenderung |
|-------|-----------|
| 2025-12-16 | Initiale Erstellung |
