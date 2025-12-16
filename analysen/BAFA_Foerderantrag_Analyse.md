# BAFA-Foerderantrag - IST-Analyse

**Erstellt:** 2025-12-16 | **Quelle:** Gespraech mit Andreas

---

## Prozess-Uebersicht

```
AUSLOESER (bei Angebotserstellung)
├─ Kunde fragt nach Foerderung
├─ Verkauf: "Mit BAFA/KfW moeglich"
│
▼
ANTRAG VORBEREITEN
├─ Kunde liefert: Hausdaten + Vollmacht
├─ Andreas: Baumassnahme im Weru Portal anlegen
│   └─ Portal: https://weru.foerderservice.de/
├─ Energieberater (Weru): Bearbeitet Antrag
├─ Weiterleitung an BAFA durch Energieberater
│
▼
WARTEN AUF BAFA-BESTAETIGUNG
├─ ⚠️ ERST NACH Bestaetigung darf bestellt werden!
├─ Dokumente herunterladen
├─ Ablage in W4A (Projektdokumente)
│
▼
NORMALER AUFTRAGSPROZESS
├─ Bestellung
├─ Montage
├─ Schlussrechnung
├─ Zahlung
│
▼
⚠️ KRITISCHER SCHRITT (WIRD VERGESSEN!)
├─ "Eingabe NachweisService" im Weru Portal
├─ MUSS nach vollstaendiger Zahlung erfolgen!
├─ Ohne dies: Kunde bekommt KEINE Foerderung!
└─ Verantwortlich: Andreas
```

---

## Verantwortlichkeiten

| Aufgabe | Verantwortlich |
|---------|----------------|
| Foerdermoeglichkeit ansprechen | Verkauf (Enrico, Andreas, Vater) |
| Kundendaten sammeln | Andreas |
| Baumassnahme im Portal anlegen | Andreas |
| Bearbeitung + BAFA-Weiterleitung | Energieberater (Weru extern) |
| Dokumente in W4A ablegen | Andreas |
| NachweisService nach Zahlung | Andreas |

---

## Weru FoerderService Portal

| Aspekt | Details |
|--------|---------|
| **URL** | https://weru.foerderservice.de/ |
| **Typ** | Session-basiert (Login erforderlich) |
| **Energieberater** | Externer Dienstleister von Weru |
| **Funktion** | Vermittlung zwischen Fachbetrieb und BAFA |

### Benoetigte Kundendaten

- Hausdaten (Baujahr, Wohnflaeche, etc.)
- Vollmacht zur Antragstellung
- Technische Angaben zum Vorhaben

---

## Volumen & Haeufigkeit

| Aspekt | Wert |
|--------|------|
| **Antraege pro Jahr** | 5-10 |
| **Foerdersumme** | Mehrere Tausend Euro pro Antrag |
| **Zeitraum** | Antrag bis NachweisService: mehrere Monate |

---

## KRITISCHES PROBLEM: NachweisService vergessen

### Problemstellung

| Aspekt | Details |
|--------|---------|
| **Was passiert** | NachweisService nach Zahlung wird vergessen |
| **Warum** | Projektakte wird nach Zahlung "geschlossen" |
| **Aber** | Foerderantrag muss DANACH noch abgeschlossen werden |
| **Folge** | Kunde verliert Foerderung (mehrere Tausend Euro!) |

### Zeitliche Luecke

```
Zahlung eingegangen
        ↓
Projektakte "geschlossen"
        ↓
❌ NachweisService wird vergessen
        ↓
Kunde bekommt KEINE Foerderung!
```

### Ursachen

1. Kein automatischer Reminder nach Zahlung
2. Keine Verknuepfung zwischen W4A-Auftrag und Foerder-Status
3. Langer Zeitraum zwischen Antrag und NachweisService

---

## Loesungsansatz: Auto-Erinnerung

### Erkennungsmerkmal in W4A

Im Auftragsdokument gibt es eine Position **"Pauschale fuer Foerderantraege"** die aus den Positionen ausgelesen werden kann.

### Automatisierungs-Stufen

| Stufe | Loesung | Aufwand |
|-------|---------|---------|
| **Vollautomatisch** | Zahlung erkannt + Foerder-Position vorhanden → Auto-Aufgabe an Andreas | Mittel |
| **Halbautomatisch** | Taeglicher Check: Foerder-Auftraege + bezahlt + kein Erledigungsvermerk → Liste | Gering |
| **Assistiert** | Manueller Haken "Foerderantrag vorhanden" → Erinnerung nach Zahlung | Gering |

### SQL-Konzept

```sql
-- Auftraege mit Foerder-Position die vollstaendig bezahlt sind
SELECT a.Nummer, k.Name, a.Betrag,
       'NachweisService pruefen!' AS Aktion
FROM dbo.Auftrag a
JOIN dbo.Kunden k ON a.KundenCode = k.Code
JOIN dbo.AuftragPos p ON a.Code = p.AuftragCode
WHERE p.Bezeichnung LIKE '%Pauschale%Förder%'
  AND a.BezahltKomplett = -1  -- oder entsprechendes Feld
  AND a.Code NOT IN (
    -- Bereits erledigte
    SELECT AuftragCode FROM BAFA_Erledigt  -- hypothetisch
  )
```

### W4A-Erweiterung (optional)

| Feld | Typ | Zweck |
|------|-----|-------|
| BAFA_Antrag | Ja/Nein | Foerderantrag vorhanden |
| BAFA_NachweisErledigt | Datum | Wann NachweisService gemacht |
| BAFA_Notizen | Text | Antragsnummer, Besonderheiten |

→ Aktuell keine Felder vorhanden, aber W4A erweiterbar

---

## Dokumentenablage

| Dokument | Ablageort |
|----------|-----------|
| BAFA-Bestaetigung | W4A Projektdokumente |
| Vollmacht | W4A Projektdokumente |
| NachweisService-Bestaetigung | W4A Projektdokumente |

---

## Prozess-Checkliste

### Bei Angebotserstellung

- [ ] Foerderung angesprochen?
- [ ] Position "Pauschale fuer Foerderantraege" im Angebot?

### Vor Bestellung

- [ ] Hausdaten vom Kunden erhalten?
- [ ] Vollmacht vom Kunden erhalten?
- [ ] Baumassnahme im Weru Portal angelegt?
- [ ] BAFA-Bestaetigung abwarten!

### Nach Zahlung (KRITISCH!)

- [ ] Montage komplett abgeschlossen?
- [ ] Schlussrechnung vollstaendig bezahlt?
- [ ] → **NachweisService im Weru Portal eingeben!**
- [ ] Bestaetigung in W4A ablegen

---

## Prozess-Uebergaenge

### BAFA-Prozess → Bestellprozess
- Erst nach BAFA-Bestaetigung darf bestellt werden
- Wartezeit beachten!

### Rechnungsprozess → BAFA-Prozess (KRITISCH)
- Nach vollstaendiger Zahlung
- NachweisService ausloesen
- → Automatisierung dringend empfohlen (#3)

---

## Verknuepfte Ideen

| # | Idee | Bezug |
|---|------|-------|
| **#3** | Weru Foerderantraege ⭐ | Hauptidee fuer Automatisierung |
| #65 | Anzahlungsrechnung | Gleicher Trigger-Punkt (Zahlungsstatus) |
| #31 | Rechnungsbuch | Zahlungsstatus-Quelle |

---

## Change Log

| Datum | Aenderung |
|-------|-----------|
| 2025-12-16 | Initiale Erstellung |
