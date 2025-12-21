# Buchhaltungsprozess - IST-Analyse

**Erstellt:** 2025-12-20 | **Quelle:** Gespraech mit Andreas

---

## Prozess-Uebersicht

```
EINGANGSRECHNUNG
│
├─ E-Mail (Standard)
├─ Portale (hin und wieder)
├─ Post (sehr selten)
│
▼
ERFASSUNG (Roland)
├─ In W4A anlegen
├─ Buchungskonto zuweisen
├─ Dokument anhaengen
│
▼
PRUEFUNG (Jolanta)
├─ Rechnung pruefen
├─ Reklamation? → Rechnung sperren
├─ OK → Freigabe zur Zahlung
│
▼
ZAHLUNGSLAUF (Jolanta)
├─ Nach Faelligkeit
├─ Skonto-Fristen beachten
├─ Ueberweisung ausfuehren
│
▼
DATEV-UEBERMITTLUNG (monatlich)
├─ Ein-/Ausgangsrechnungen aus W4A
├─ Anhaenge separat (wenn noetig)
└─ Steuerberater ruft Bankdaten selbst ab
```

---

## Beteiligte Personen

| Person | Rolle |
|--------|-------|
| **Roland** | Eingangsrechnungen erfassen, Buchungskonto zuweisen |
| **Jolanta (Mutter)** | Pruefen, Freigabe, Zahlungslauf (hauptsaechlich) |
| **Vater** | Zahlungslauf (selten) |
| **Sandra** | Zahlungslauf (sehr selten), Ausgangsrechnungen |
| **Steuerberater** | Erkiert & Mainka |

---

## Eingangsrechnungen

### Eingangskanaele

| Kanal | Haeufigkeit | Trend |
|-------|-------------|-------|
| **E-Mail** | Standard | ↑ |
| **Portale** | Hin und wieder | → |
| **Post** | Sehr selten | ↓ |

### Erfassungs-Workflow

| Schritt | Wer | Was |
|---------|-----|-----|
| 1 | Roland | Rechnung in W4A anlegen |
| 2 | Roland | Buchungskonto zuweisen |
| 3 | Roland | Dokument (PDF) anhaengen |
| 4 | Jolanta | Pruefung |
| 5 | Jolanta | Freigabe oder Sperrung |

### Buchungskonten (Beispiele)

| Konto | Beschreibung | Hinweis |
|-------|--------------|---------|
| **3400** | Wareneingang | Standard fuer Waren |
| **4985** | Geringwertige Wirtschaftsgueter / Maschinen | Oft faelschlich auf 3400 gebucht |
| ... | ... | ... |

**Problem:** Keine klare Zuordnungsregel - muss individuell geprueft werden (Erfahrungswissen).

---

## Pruefung & Freigabe

| Aspekt | Details |
|--------|---------|
| **Wer prueft** | Jolanta |
| **Pruefkriterien** | Rechnung korrekt, Lieferung erhalten, keine Reklamation |
| **Bei Reklamation** | Rechnung wird gesperrt (wenn keine Abbuchung vereinbart) |
| **Nach Freigabe** | Zur Zahlung vorgemerkt |

---

## Zahlungslauf

| Aspekt | Details |
|--------|---------|
| **Hauptverantwortlich** | Jolanta |
| **Alternativ** | Vater (selten), Sandra (sehr selten) |
| **Entscheidungskriterien** | Faelligkeit, Skonto-Fristen |
| **Methode** | Ueberweisung aus W4A |

### Zahlungsprioritaet

1. Skonto-Frist laeuft ab → Zahlen um Skonto zu sichern
2. Faelligkeit erreicht → Zahlen
3. Gesperrte Rechnungen → Warten auf Klaerung

---

## Konten in W4A

| Konto | Typ | Verwendung |
|-------|-----|------------|
| **VR-Bank Amberg-Sulzbach** | Hauptkonto | Ueberweisungen, Lastschriften |
| **PayPal** | Online | Online-Zahlungen |
| **Kreditkarte** | Karte | Geschaeftsausgaben |
| **eBay** | Marktplatz | Verkaeufe |
| **eBay Punktekonto** | Marktplatz | Punkte-System |
| **Kasse** | Bar | Bareinnahmen |
| **Zettle** | Kartenzahlung | Kartenzahlung im Buero |

---

## DATEV-Anbindung

### Uebermittlung

| Aspekt | Details |
|--------|---------|
| **Verbindung** | Direkt aus W4A |
| **Frequenz** | Monatlich |
| **Inhalt** | Ein- und Ausgangsrechnungen |
| **Bankdaten** | Steuerberater ruft selbst ab (keine Doppelbuchungen!) |

### Steuerberater

| Aspekt | Details |
|--------|---------|
| **Kanzlei** | Erkiert & Mainka |
| **Kommunikation** | DATEV-Verbindung, E-Mail, DATEV Unternehmen Online |

### Anhaenge-Problem

| Problem | Details |
|---------|---------|
| **W4A-Limitierung** | Nur 1 Datei pro Buchung an DATEV uebermittelt |
| **Betroffene Dokumente** | Tankbelege (Einzelnachweise), Teilnehmerlisten bei Veranstaltungen |
| **Haeufigkeit** | Woechentlich |

**Aktuelle Workarounds:**
1. Manuell per E-Mail an Steuerberater
2. In DATEV Unternehmen Online hochladen
3. PDFs zusammenfassen und in W4A neu speichern

---

## Ausgangsrechnungen

> Siehe auch: `Rechnungsprozess_Analyse.md`

| Aspekt | Details |
|--------|---------|
| **Erstellung** | Roland (hauptsaechlich), Andreas (selten) |
| **Zahlungspruefung** | Sandra |
| **Kontoabruf** | HBCI in W4A |
| **Zuordnung** | Automatisch bei Uebereinstimmung |
| **Mahnwesen** | Sandra |

---

## Erkannte Schmerzpunkte

| # | Schmerzpunkt | Auswirkung | Haeufigkeit | Loesung |
|---|--------------|------------|-------------|---------|
| 1 | **Nur 1 Datei an DATEV** | Anhaenge manuell uebermitteln oder PDFs zusammenfassen | Woechentlich | #81 PDF-Merger |
| 2 | **Buchungskonten falsch** | Roland bucht z.B. Maschinen auf 3400 statt 4985 | Regelmaessig | #82 Buchungskonto-Assistent |
| 3 | **Zahlungslauf-Erkennung** | W4A erkennt manche Zahlungen nicht/falsch | Bei jedem Abruf | W4A-Limitierung |
| 4 | **FIBU-Fenster blockiert** | Kann nicht parallel suchen, muss schliessen → Fehler beheben → neu oeffnen | Bei jedem Fehler | W4A-Limitierung |

---

## Was funktioniert GUT

| Aspekt | Details |
|--------|---------|
| DATEV-Verbindung | Direkte Uebermittlung ohne Export-Dateien |
| Konten in W4A | Alle Zahlungswege angebunden |
| Zahlungseingang | Automatische Zuordnung funktioniert meist |
| Arbeitsteilung | Roland erfasst, Jolanta prueft/zahlt |

---

## Verbesserungspotential (Ideen-Verknuepfung)

| Bereich | Tool-Idee | Verbesserung |
|---------|-----------|--------------|
| Anhaenge | #81 PDF-Merger fuer DATEV | Automatisch PDFs zusammenfassen vor Export |
| Buchungskonten | #82 Buchungskonto-Assistent | Vorschlag basierend auf Lieferant/Artikelart |
| Zahlungslauf | W4A-Limitierung | Nicht loesbar |
| FIBU-Fenster | W4A-Limitierung | Nicht loesbar |

---

## Prozess-Uebergaenge

### Einkaufsprozess → Buchhaltung
- Bestellung → Eingangsrechnung kommt
- Reklamation → Rechnung sperren

### Buchhaltung → Rechnungsprozess
- Ausgangsrechnungen → Zahlungspruefung → Mahnwesen

### Buchhaltung → Steuerberater
- Monatliche DATEV-Uebermittlung
- Anhaenge separat wenn noetig

---

## Offene Fragen (fuer spaeter)

| # | Frage |
|---|-------|
| 1 | Gibt es eine Kontenliste vom Steuerberater die als Referenz dienen koennte? |
| 2 | Koennte W4A-Support das Anhaenge-Problem loesen? (Feature-Request?) |

---

## Change Log

| Datum | Aenderung |
|-------|-----------|
| 2025-12-20 | Initiale Erstellung |
