# Personalprozess - IST-Analyse

**Erstellt:** 2025-12-20 | **Quelle:** Gespraech mit Andreas, Screenshots W4A

---

## Prozess-Uebersicht

```
URLAUBSANTRAG
│
├─ Mitarbeiter stellt Antrag (W4A oder Stempeluhr)
├─ Zeigt: Anspruch, Uebertrag, Genommen, Rest
├─ Kollegen-Kalender sichtbar (wer fehlt schon?)
│
▼
GENEHMIGUNG
├─ Andreas prueft + genehmigt
├─ Kritische Faelle: Ruecksprache mit Vater
├─ Kapazitaet: Manuell in Kollegen-Ansicht pruefen
│
▼
ABWESENHEITSKALENDER
├─ Gruppenansicht: Alle Mitarbeiter nach Abteilung
├─ Einzelansicht: Jahresuebersicht pro Person
├─ Farbkodierung nach Abwesenheitsart
│
▼
ZEITERFASSUNG
├─ Buero: W4A Zeiterfassung
├─ Lager: Stempeluhr
├─ Zeitkarte: Soll/Ist/Differenz pro Tag
│
▼
JAHRESWECHSEL (manuell!)
├─ Resturlaub uebertragen
├─ Ueberstunden uebertragen
└─ Pro Mitarbeiter einzeln!
```

---

## W4A Module

### Urlaubsantrag

| Aspekt | Details |
|--------|---------|
| **Zugang** | W4A direkt oder Stempeluhr im Lager |
| **Felder** | Anspruch, Uebertrag Vorjahr, Genommen, Rest, Von/Bis |
| **Kollegen-Ansicht** | Zeigt wer im gewaehlten Zeitraum schon fehlt |
| **Genehmiger** | Hinterlegt: Vater, Praktisch: Andreas |

**Schmerzpunkt:** Zeitauswahl ist umstaendlich geloest

### Abwesenheitskalender

| Ansicht | Inhalt |
|---------|--------|
| **Gruppenansicht** | Alle Mitarbeiter, KW-basiert, Abteilungen |
| **Einzelansicht** | Jahreskalender einer Person |
| **FIBU-Export** | Vorhanden, wird nicht genutzt |

**Abteilungen:**
- 01 GF (Geschaeftsfuehrung)
- 02 Vertrieb/Verwaltung
- 03 Montage

**Farbkodierung:**

| Farbe | Bedeutung |
|-------|-----------|
| Gruen | Genehmigter Urlaub |
| Rosa | Krankheit |
| Rot | Nicht genehmigt / Konflikt |
| Hellgruen | Sonderurlaub |
| ½ | Halber Tag |

**Abwesenheitsarten:**
- Urlaub
- Krankheit
- Weihnachten/Silvester
- Freistellung
- Sonderurlaub
- Ueberstundenausgleich
- Unbezahlter Urlaub
- Kind-Krank

### Zeitkarte

| Aspekt | Details |
|--------|---------|
| **Ansicht** | Monatlich pro Mitarbeiter |
| **Spalten** | Datum, Von, Bis, Soll, Ist, Differenz, Saldo |
| **Kommentare** | Urlaub, Feiertag, Ueberstundenausgleich |
| **Kontensalden** | Zeitkonto (h), Urlaubskonto (Tage) |

---

## Beteiligte Personen

| Person | Rolle |
|--------|-------|
| **Andreas** | Genehmigt Antraege, Jahresabschluss |
| **Vater** | Hinterlegt als Genehmiger, bei kritischen Faellen |
| **Alle Mitarbeiter** | Stellen Antraege |

---

## Krankmeldung

| Aspekt | IST-Zustand |
|--------|-------------|
| **Wer meldet** | Mitarbeiter, Familie oder Kollege |
| **Wie** | Anruf oder persoenlich in der Frueh |
| **Attest** | Ab Tag 1 erforderlich! |
| **Erfassung** | In W4A Abwesenheitskalender |

---

## Zeiterfassung

| Bereich | Methode |
|---------|---------|
| **Buero** | W4A Zeiterfassung (Login am PC) |
| **Lager** | Stempeluhr (RFID) |
| **Monteure** | Stempeluhr bei Ankunft/Abfahrt |

**Problem Stempeluhr (aus W4A-Doku):**
- RFID-Karten koennen von anderen genutzt werden
- Anmeldefenster poppt nicht automatisch auf
- Sollzeit-Aenderung erfordert neuen MA-Datensatz

---

## Jahreswechsel-Prozess

### IST (manuell)

```
JAHRESENDE
     │
     ▼
Andreas: Fuer JEDEN Mitarbeiter:
├─ Resturlaub berechnen
├─ In neues Jahr uebertragen
├─ Ueberstunden berechnen
├─ In neues Jahr uebertragen
     │
     ▼
Ca. 15+ Mitarbeiter = viel Arbeit!
```

**Schmerzpunkt:** Kein automatischer Uebertrag in W4A

### SOLL (automatisch)

```
JAHRESENDE (z.B. 31.12. 23:59)
     │
     ▼
Script/Tool:
├─ Liest alle Mitarbeiter
├─ Berechnet Resturlaub
├─ Berechnet Ueberstunden
├─ Traegt automatisch ins neue Jahr ein
     │
     ▼
Andreas: Nur noch pruefen
```

---

## Zeitnachweis-Ausgabe

### IST (umstaendlich)

```
W4A Zeitkarte
     │
     ▼
Export nach Excel
     │
     ▼
Excel bearbeiten (Format anpassen)
     │
     ▼
Drucken
```

**Schmerzpunkt:** Monatlich fuer jeden MA, keine A4-Druckansicht in W4A

### SOLL

```
Tool: Daten aus W4A
     │
     ▼
Automatisch formatiertes A4-PDF
     │
     ▼
Direkt drucken oder speichern
```

---

## Erkannte Schmerzpunkte

| # | Schmerzpunkt | Auswirkung | Haeufigkeit | Relevante Ideen |
|---|--------------|------------|-------------|-----------------|
| 1 | **Jahresuebertrag manuell** | Jeder MA einzeln: Resturlaub + Ueberstunden | 1x/Jahr, ~1h Arbeit | #78 |
| 2 | **Zeitauswahl ungünstig** | Umstaendliche Bedienung beim Antrag | Bei jedem Antrag | W4A-Limitierung |
| 3 | **Keine A4-Druckansicht** | Excel-Umweg fuer Zeitnachweise | 12x/Jahr | #79 |
| 4 | **Kapazitaet manuell** | Keine Warnung bei Unterbesetzung | Bei jedem Antrag | #16 erweitern |
| 5 | **Attest-Kontrolle** | Muss manuell geprueft werden | Bei jeder Krankmeldung | #80 |
| 6 | **Stempeluhr-Probleme** | RFID-Missbrauch, kein Auto-Popup | Dauerhaft | Eigene Zeiterfassung |

---

## Was funktioniert GUT

| Aspekt | Details |
|--------|---------|
| Digitaler Antrag | Kein Papier, direkt in W4A |
| Kollegen-Uebersicht | Beim Antrag sichtbar wer fehlt |
| Abwesenheitskalender | Gute Gruppenuebersicht |
| Verschiedene Arten | Urlaub, Krankheit, Sonderurlaub, etc. differenziert |
| Zeitkarte | Soll/Ist/Differenz transparent |
| Historie | Jahresuebersicht bis 2018 zurueck |

---

## Verbesserungspotential (Ideen-Verknuepfung)

| Bereich | Tool-Idee | Verbesserung |
|---------|-----------|--------------|
| Jahreswechsel | #78 Jahresuebertrag-Automatik | Script fuer auto. Uebertrag |
| Zeitnachweis | #79 Zeitnachweis-Generator | A4-PDF direkt aus Daten |
| Krankmeldung | #80 Attest-Reminder | Erinnerung wenn Attest fehlt |
| Urlaubsplanung | #16 erweitern | Kapazitaetswarnung |
| Zeiterfassung | #34 / Eigene Loesung | Bessere Erfassung als Stempeluhr |

---

## Mitarbeiter-Uebersicht (aus Screenshots)

### 01 GF (Geschaeftsfuehrung)

| Name | Anspruch | Vorjahr | Gesamt |
|------|----------|---------|--------|
| Stolarczyk Jolanta | - | - | - |
| Stolarczyk Sandra | 24 | 0 | 24 |
| Stolarczyk Jaroslaw | 30 | 5 | 35 |
| Stolarczyk Andreas | 30 | 2 | 32 |

### 02 Vertrieb/Verwaltung

| Name | Anspruch | Vorjahr | Gesamt |
|------|----------|---------|--------|
| Hoffmann Roland | 30 | 13,5 | 17,5 (Rest) |
| Rossow Enrico | 30 | 4 | 34 |
| Schmid Bianca | 6 | 2 | 3 (Rest) |
| Zielinski Susann | 27,5 | 0 | 27,5 |

### 03 Montage

| Name | Anspruch | Vorjahr | Gesamt |
|------|----------|---------|--------|
| Haeckl Stefan | 30 | 3,5 | 0,5 (Rest) |
| Heigl Manfred | 29 | 0 | 7 (Rest) |
| ... | ... | ... | ... |

---

## Prozess-Uebergaenge

### Personalprozess → Montageprozess
- Krankmeldung → Termin faellt aus / Ersatz organisieren
- Urlaub → Kapazitaetsplanung beruecksichtigen

### Personalprozess → Rechnungsprozess
- Arbeitszeiten → Projekt-Zeiterfassung fuer Rechnung

---

## Naechste Schritte

1. #78 Jahresuebertrag-Automatik konzipieren
2. #79 Zeitnachweis-Generator (A4 PDF)
3. Eigene Zeiterfassung evaluieren (Alternative zu W4A/Stempeluhr)

---

## Change Log

| Datum | Aenderung |
|-------|-----------|
| 2025-12-20 | Initiale Erstellung |
