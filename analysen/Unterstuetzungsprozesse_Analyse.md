# Unterstuetzungsprozesse - Sammel-Analyse

**Erstellt:** 2025-12-21 | **Quelle:** Gespraech mit Andreas

> Diese Analyse fasst 12 Unterstuetzungsprozesse zusammen, die nicht als Kernprozesse gelten, aber fuer den Betrieb wichtig sind.

---

## Uebersicht

| # | Prozess | Status | Schmerzpunkt | Idee |
|---|---------|--------|--------------|------|
| 1 | Marketing/Akquise | Passiv | Kein Tracking | #23 |
| 2 | Nachkalkulation | W4A, unvollstaendig | Keine Alerts | #86 |
| 3 | Vertragsmanagement | Dezentral | Fristen | #87 |
| 4 | Qualitaetsmanagement | Informell | Keine Checklisten | #29 |
| 5 | Dokumentenmanagement | W4A | Keine Suche | #88 |
| 6 | Schulung | Andreas | Muehsam | #89 |
| 7 | Kommunikation | OK | Infos vergessen | #71 |
| 8 | IT | Extern | - | - |
| 9 | Gebaeudemanagement | Vermieter | - | - |
| 10 | Versicherung | Sandra | - | - |
| 11 | Strategie | Informell | - | - |
| 12 | Werkstatt | Nicht koordiniert | Vergessen! | #90 |

---

## 1. Marketing/Akquise-Prozess

### IST-Zustand

| Aspekt | Details |
|--------|---------|
| **Neukunden-Quellen** | E-Mail, Website-Formular, Telefon, Laufkundschaft, Empfehlungen |
| **Werbung** | Sponsoring, Branchenverzeichnis (Zeitung monatlich) |
| **Akquise-Art** | Nur eingehend (passiv), keine aktive Akquise |
| **Website** | js-fenster.de, wird gerade ueberarbeitet (Andreas) |
| **Social Media** | Nur Drittanbieter, keine Zeit/Wissen |
| **Anfrage-Tracking** | Kaum vorhanden |

### Schmerzpunkte

| Problem | Auswirkung |
|---------|------------|
| Kein Anfrage-Tracking | Unbekannt woher Kunden kommen |
| Social Media fehlt | Keine Zeit/Wissen, Drittanbieter teuer? |
| Keine aktive Akquise | Abhaengig von eingehenden Anfragen |

### Verbesserungspotenzial

| Idee | Verbesserung |
|------|--------------|
| #23 erweitern | Anfrage-Quelle tracken ("Woher kennen Sie uns?") |
| Neu? | Social Media Automatisierung (Posts planen) |

---

## 2. Nachkalkulation/Controlling-Prozess

### IST-Zustand

| Aspekt | Details |
|--------|---------|
| **Tool** | W4A Projekt-Controlling (Soll-Ist-Vergleich) |
| **Was fliesst ein** | Fremdleistungen, Material, Erloese |
| **Was fehlt** | Montagezeiten (stehen auf Montagescheinen, aber nicht erfasst) |
| **Was fehlt** | Interne Bearbeitungszeiten |
| **Pruefung** | Andreas, hin und wieder manuell |
| **KPIs** | Nur Gesamtumsatz (GuV Steuerberater) |

### Screenshot W4A Projekt-Controlling

```
Soll-Ist-Vergleich
------------------
                        Plan        Ist         Differenz
Eigenleistungen h       293         2           291
Eigenleistungen EUR     14.773      105         14.668
Fremdleist./Material    42.269      43.840      -1.571
Summe Kosten            57.042      43.945      13.097
Ausgangsrechnungen      84.424      60.000      24.424
Saldo                   27.382      16.055
```

### Schmerzpunkte

| Problem | Auswirkung |
|---------|------------|
| Montagezeiten fehlen | Echte Marge unbekannt, Lohnkosten erscheinen als Gewinn |
| Keine Alerts | Projekt laeuft aus dem Ruder → keine Warnung |
| Kein systematisches Controlling | Nur reaktiv, nicht proaktiv |

### Verbesserungspotenzial

| Idee | Verbesserung |
|------|--------------|
| #86 Projekt-Alerts | Auto-Warnung bei Budget-Ueberschreitung |
| #39 erweitern | Montagezeiten von Montagescheinen uebernehmen |

### Wichtiger Hinweis

> Montagezeiten stehen bereits auf den Montagescheinen! Koennten automatisch ins System uebernommen werden. Das waere der einfachste Weg zur echten Nachkalkulation.

---

## 3. Vertragsmanagement-Prozess

### IST-Zustand

| Aspekt | Details |
|--------|---------|
| **Vertragsarten** | Miete, Leasing, Finanzierung, Software, etc. |
| **Ablage** | Ordnerstruktur + W4A (immer mehr in W4A) |
| **Zentrale Uebersicht** | Nein |
| **Fristen-Pruefung** | Aktuell nicht aktiv (alle Vertraege gewollt) |
| **Historie** | Frueher Fristen verpasst, jetzt besser |

### Schmerzpunkte

| Problem | Auswirkung |
|---------|------------|
| Keine zentrale Uebersicht | Vertraege verstreut |
| Fristen manuell | Kuendigungsfristen koennten verpasst werden |

### Verbesserungspotenzial

| Idee | Verbesserung |
|------|--------------|
| #87 Vertrags-Dashboard | Zentrale Liste mit Fristen-Erinnerung |

---

## 4. Qualitaetsmanagement-Prozess

### IST-Zustand

| Aspekt | Details |
|--------|---------|
| **QM-System** | Keins (kein ISO, kein internes) |
| **Montage-Pruefung gross** | Regelmaessig geprueft |
| **Montage-Pruefung klein** | Nur Monteur-Abnahme |
| **Checklisten** | Keine |
| **Reklamations-Auswertung** | Nicht systematisch (Rate eh gering) |

### Wunsch

> Andreas: "Ein internes QM-System waere nicht schlecht"

### Was waere ein internes QM?

- Dokumentierte Arbeitsanweisungen
- Montage-Checklisten (Dichtungen, Beschlaege, Silikon)
- Abnahmeprotokoll mit Kundenunterschrift
- Fehler-Tracking (Muster erkennen)

### Verbesserungspotenzial

| Idee | Verbesserung |
|------|--------------|
| #29 Montage-Checklisten | Qualitaet dokumentieren, Einarbeitung verbessern |

---

## 5. Dokumentenmanagement-Prozess

### IST-Zustand

| Aspekt | Details |
|--------|---------|
| **Primaer-System** | W4A seit 2022 |
| **Frueher** | Eigene Ordnerstruktur (000 Tonne, 00 Archiv, 01 Auftraege, etc.) |
| **Archiv** | Bis ca. 2000 zurueck, revisionssicher via DATEV |
| **Loeschung** | Wird archiviert, nicht geloescht |

### Ordnerstruktur (alt, vor 2022)

```
├── 000 Tonne
├── 00 Archiv
├── 01 Auftraege
├── Arbeitskraefte
├── Briefe
├── Dateien
├── Forderungen von Kunden
├── Fotoalbum
├── Intern
├── IT-Sammlung
├── Lieferanten
├── Scanner
├── Statistiken
├── Vorlagen
├── Warenlisten
└── Werbematerial
```

### Schmerzpunkte

| Problem | Auswirkung |
|---------|------------|
| Keine uebergreifende Suche | W4A nur Listen-Suche, nicht alle Dateien |
| Alte Struktur uebersichtlicher | Dateien direkt sichtbar vs. Verweise |

### Verbesserungspotenzial

| Idee | Verbesserung |
|------|--------------|
| #88 Dokumentensuche | Volltextsuche ueber alle Projektdokumente |

---

## 6. Schulungs-/Weiterbildungsprozess

### IST-Zustand

| Aspekt | Details |
|--------|---------|
| **Pflichtschulungen** | Keine (aber Wahl: Stapler, Arbeitsbuehne, EFK) |
| **Organisation** | Andreas |
| **Zertifikate** | Im Mitarbeiter-Projekt (W4A) |
| **Produktschulungen** | Weru, Somfy, Suehac, Trendtueren |
| **Einarbeitung Buero** | Andreas |
| **Einarbeitung Monteure** | Kollegen |

### Schmerzpunkte

| Problem | Auswirkung |
|---------|------------|
| Fuelle an Angeboten | Schwer zu ueberblicken |
| Planung muehsam | Zeitaufwand fuer Andreas |

### Verbesserungspotenzial

| Idee | Verbesserung |
|------|--------------|
| #89 Schulungs-Planer | Angebote sammeln, Termine planen, Erinnerungen |
| #74 erweitern | Zertifikate-Tracking bereits enthalten |

---

## 7. Kommunikationsprozess

### IST-Zustand

| Aspekt | Details |
|--------|---------|
| **Intern Monteure** | Fruehbesprechung |
| **Intern Buero** | E-Mail, Teams, Telefon |
| **WhatsApp-Gruppe** | Nein |
| **Extern** | Telefon, E-Mail, persoenlich |
| **Vorlagen** | W4A moeglich, aber umstaendlich |

### Schmerzpunkte

| Problem | Auswirkung |
|---------|------------|
| Infos vergessen | Z.B. Preiserhoehungen nicht kommuniziert |

### Verbesserungspotenzial

| Idee | Verbesserung |
|------|--------------|
| #71 erweitern | Preisinfo-Verteiler bereits angedacht |

**Status:** Kommunikation funktioniert insgesamt gut.

---

## 8. IT-Prozess

### IST-Zustand

| Aspekt | Details |
|--------|---------|
| **Verantwortlich** | Andreas (einfach), IT-Preischl (Server, gross) |
| **Hardware** | IT-Preischl (gross), Andreas (Rest) |
| **Software-Updates** | Automatisch via ITler |
| **Backup** | Synology + Synology Cloud |
| **Probleme** | Erst selbst, dann Preischl |
| **Passwoerter** | LastPass |
| **Lizenzen** | Weniger dokumentiert |
| **Netzwerkplan** | Weniger dokumentiert |

### Status

Gut organisiert mit externem ITler. Backup vorhanden.

### Nice-to-have

- Lizenz-Uebersicht (wann laeuft was aus?)
- Netzwerkplan dokumentieren

---

## 9. Gebaeudemanagement-Prozess

### IST-Zustand

| Aspekt | Details |
|--------|---------|
| **Immobilie** | Miete (Buero + Lager separat) |
| **Wartung** | Vermieter |
| **Reinigung Buero** | Intern |
| **Reinigung Lager** | Mario (teilweise), Toiletten nicht geregelt |
| **Werkstatt** | Im Lager vorhanden |
| **Wartungsvertraege** | Nein (Vermieter zustaendig) |

### Kleiner Schmerzpunkt

Toiletten-Reinigung Lager nicht geregelt.

**Status:** Kein grosser Handlungsbedarf (Vermieter kuemmert sich).

---

## 10. Versicherungsprozess

### IST-Zustand

| Aspekt | Details |
|--------|---------|
| **Versicherungen** | Diverse vorhanden |
| **Policen-Ablage** | Immer mehr in W4A |
| **Verwaltung** | Sandra |
| **Schadensmeldung** | Sandra oder Andreas |
| **Makler** | Peter Wesoly |

**Status:** Gut organisiert, kein Handlungsbedarf.

---

## 11. Strategieprozess

### IST-Zustand

| Aspekt | Details |
|--------|---------|
| **Jahresplanung** | Nein (ab und zu Steuerberater) |
| **Investitionen** | Vater + Andreas entscheiden |
| **GF-Besprechungen** | Bei Bedarf |
| **Unternehmensziele** | Nicht formell definiert |
| **Auftragslage** | W4A-Zahlen verfuegbar |

**Status:** Informell, typisch fuer Handwerksbetrieb. Funktioniert.

### Optional

Einfaches Jahres-Dashboard: Umsatz vs. Vorjahr, Auftragsbestand.

---

## 12. Werkstatt-/Fertigungsprozess

### IST-Zustand

| Aspekt | Details |
|--------|---------|
| **Standort** | Im Lager |
| **Arbeiten** | Raffstore/Rollos reparieren, Blenden herstellen, Holzbretter zuschneiden |
| **Personal** | Mario, Monteure, Vater, Andreas |
| **Material** | Aus Lager oder auftragsbezogen bestellt |

### Maschinen

- Formatkreissaege
- Tischkreissaege
- Kappsaege
- Schleifer
- Standbohrmaschine
- Hobel
- etc.

### Schmerzpunkte

| Problem | Auswirkung |
|---------|------------|
| **Nicht koordiniert** | Auftraege werden vergessen |
| **Improvisation** | Muss kurzfristig geloest werden |
| **Keine Planung** | Wer macht was wann? |

### Verbesserungspotenzial

| Idee | Verbesserung |
|------|--------------|
| #90 Werkstatt-Planung | Liste offener Arbeiten, Prioritaet, Verknuepfung mit Montage |

---

## Neue Ideen (Zusammenfassung)

| # | Idee | Prozess | Prioritaet |
|---|------|---------|------------|
| #86 | Projekt-Controlling Alerts | Nachkalkulation | Mittel |
| #87 | Vertrags-Dashboard | Vertragsmanagement | Niedrig |
| #88 | Dokumenten-Volltextsuche | Dokumentenmanagement | Mittel |
| #89 | Schulungs-Planer | Schulung | Mittel |
| #90 | Werkstatt-Auftragsplanung | Werkstatt | Hoch! |

---

## Change Log

| Datum | Aenderung |
|-------|-----------|
| 2025-12-21 | Initiale Erstellung - 12 Prozesse dokumentiert |

