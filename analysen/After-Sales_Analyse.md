# After-Sales Prozess - IST-Analyse

**Erstellt:** 2025-12-20 | **Quelle:** Gespraech mit Andreas

---

## Prozess-Uebersicht

```
AFTER-SALES (IST-Zustand)
│
├─ Wartungsvertraege: ❌ NICHT VORHANDEN
├─ Proaktive Kontaktierung: ❌ NICHT VORHANDEN
├─ Zufriedenheits-Follow-up: ❌ NICHT VORHANDEN
├─ Cross-Selling: ❌ NICHT IMPLEMENTIERT
│
▼
EINZIGE AKTIVITAET: Reaktiv bei Reklamation
├─ Garantie wird geprueft (Ausfuehrungsdatum)
├─ 2 Jahre Standardgarantie
└─ Herstellergarantien variieren
```

**Fazit:** After-Sales existiert aktuell NICHT als Prozess. Reine Luecke mit grossem Potenzial.

---

## Datengrundlage

| Aspekt | Details |
|--------|---------|
| **W4A-Projekte** | ~2.700 Projekte |
| **Ordnersystem** | Bis 2004 rueckwirkend |
| **Strukturqualitaet** | Ab 2013 gut, aelter = schwerer nachvollziehbar |
| **Nutzbar fuer After-Sales** | Ja! Ausfuehrungsdatum, Kunde, Produkte vorhanden |

---

## IST-Zustand (Luecken)

### Wartungsvertraege

| Aspekt | IST |
|--------|-----|
| **Gibt es Vertraege?** | Nein |
| **Grund** | Keine Verwaltungsmoeglichkeit |
| **Folge** | Nur Einmal-Reparaturen, kein planbares Geschaeft |
| **Wunsch** | Ja! Feste Termine fuer Stefan (Reparatur-Monteur) |

### Proaktive Kundenkontaktierung

| Aspekt | IST |
|--------|-----|
| **Nach X Jahren kontaktieren?** | Nein |
| **"Fenster 10 Jahre alt"** | Wird nicht gemacht |
| **Potenzial** | 2.700 Projekte = grosser Kundenstamm |

### Zufriedenheits-Follow-up

| Aspekt | IST |
|--------|-----|
| **Nach Montage nachfragen?** | Nein |
| **Nach Reparatur nachfragen?** | Nein |
| **Google-Bewertung anfragen?** | Nein (→ siehe #73) |

### Cross-Selling

| Aspekt | IST |
|--------|-----|
| **Implementiert?** | Nein |
| **Beispiel** | Haustuer-Kunde → Fenster anbieten |
| **Daten vorhanden?** | Ja, in W4A (was hat Kunde gekauft) |

### Garantie-Management

| Aspekt | IST |
|--------|-----|
| **Standardgarantie** | 2 Jahre |
| **Herstellergarantien** | Variieren, laenger moeglich |
| **Tracking** | ❌ Nicht vorhanden |
| **Pruefung** | Nur reaktiv bei Reklamation |
| **Fristen hinterlegt?** | Nein, muessten einmal erfasst werden |

---

## Beteiligte Personen

| Person | Aktuelle Rolle | Potenzielle Rolle |
|--------|----------------|-------------------|
| **Stefan Haeckl** | Reparaturen (5-8/Tag) | Wartungsvertrags-Termine |
| **-** | - | Kundenkontaktierung? |
| **-** | - | Zufriedenheitsabfrage? |

**Problem:** Niemand ist fuer After-Sales zustaendig!

---

## Erkannte Schmerzpunkte / Luecken

| # | Luecke | Auswirkung | Potenzial |
|---|--------|------------|-----------|
| 1 | **Keine Wartungsvertraege** | Unplanbare Auslastung Stefan, entgangene Einnahmen | Hoch! Regelmaessige Einnahmen |
| 2 | **Keine Kundenkontaktierung** | Kunden werden "vergessen" nach Auftrag | 2.700 Projekte = Goldgrube |
| 3 | **Kein Garantie-Tracking** | Bei Reklamation manuell pruefen | Rechtssicherheit, Transparenz |
| 4 | **Kein Follow-up** | Unzufriedene Kunden bleiben still | Fruehwarnung, Bewertungen |
| 5 | **Kein Cross-Selling** | Umsatzpotenzial verschenkt | Bestandskunden kaufen mehr |

---

## SOLL-Zustand (Vision)

```
AFTER-SALES (SOLL)
│
├─ WARTUNGSVERTRAEGE
│   ├─ Vertragsverwaltung (Kunde, Intervall, Preis)
│   ├─ Automatische Terminplanung fuer Stefan
│   ├─ Erinnerung vor Faelligkeit
│   └─ Rechnung automatisch
│
├─ KUNDEN-REAKTIVIERUNG
│   ├─ Regel: Projekt > 10 Jahre → Kontaktieren
│   ├─ Mailing oder Anruf-Liste
│   └─ "Ihre Fenster sind X Jahre alt..."
│
├─ GARANTIE-TRACKER
│   ├─ Herstellerfristen hinterlegt
│   ├─ Pro Projekt: Garantie-Ende sichtbar
│   └─ Bei Reklamation: Sofort-Anzeige
│
├─ ZUFRIEDENHEITS-FOLLOW-UP
│   ├─ X Tage nach Montage: Kurze Umfrage
│   ├─ Positiv? → Google-Bewertung anfragen (#73)
│   └─ Negativ? → Alarm an Buero
│
└─ CROSS-SELLING
    ├─ Kaufhistorie analysieren
    ├─ Passende Angebote vorschlagen
    └─ Z.B. "Sie haben Fenster, wie waere Haustuer?"
```

---

## Verbesserungspotential (Ideen-Verknuepfung)

| Bereich | Tool-Idee | Verbesserung |
|---------|-----------|--------------|
| Wartung | #30 erweitern / #83 neu | Wartungsvertrags-Modul |
| Reaktivierung | #84 neu | Kunden nach X Jahren kontaktieren |
| Garantie | #85 neu | Garantie-Tracker mit Herstellerfristen |
| Follow-up | #73 erweitern | Nach Montage → Zufriedenheit + Bewertung |
| Cross-Selling | #30 enthalten | Kaufhistorie → Vorschlaege |

---

## Priorisierung (Empfehlung)

| Prio | Idee | Begruendung |
|------|------|-------------|
| 1 | **Wartungsvertrags-Modul** | Direkter Umsatz, planbare Auslastung Stefan |
| 2 | **Garantie-Tracker** | Rechtssicherheit, einmal einrichten |
| 3 | **Kunden-Reaktivierung** | Grosses Potenzial (2.700 Projekte) |
| 4 | **Zufriedenheits-Follow-up** | Kundenbindung, Bewertungen |
| 5 | **Cross-Selling** | Langfristig, braucht Datenanalyse |

---

## Technische Voraussetzungen

| Aspekt | Status |
|--------|--------|
| **Kundendaten in W4A** | ✅ Vorhanden |
| **Ausfuehrungsdatum** | ✅ Vorhanden |
| **Produkte/Artikel** | ✅ Vorhanden |
| **Herstellerfristen** | ❌ Muessen einmal erfasst werden |
| **Wartungsvertrags-Tabelle** | ❌ Neu erstellen |

---

## Prozess-Uebergaenge

### Rechnungsprozess → After-Sales
- Rechnung bezahlt → Follow-up starten (X Tage spaeter)

### After-Sales → Reparaturprozess
- Wartungsvertrag faellig → Termin fuer Stefan

### After-Sales → Anfrageprozess
- Cross-Selling → Neues Angebot

### Reklamationsprozess → After-Sales
- Reklamation abgeschlossen → Zufriedenheit pruefen

---

## Offene Fragen (fuer spaeter)

| # | Frage |
|---|-------|
| 1 | Welche Wartungsleistungen wuerden angeboten? (Beschlaege oelen, Dichtungen pruefen, ...) |
| 2 | Preismodell Wartungsvertrag? (Pauschale/Jahr, pro Besuch?) |
| 3 | Welche Hersteller haben welche Garantiefristen? |
| 4 | Wer soll Kunden kontaktieren? (Vertrieb, Buero, automatisch?) |

---

## Change Log

| Datum | Aenderung |
|-------|-----------|
| 2025-12-20 | Initiale Erstellung - Luecken-Analyse |

