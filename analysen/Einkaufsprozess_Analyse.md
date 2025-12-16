# Einkaufsprozess - IST-Analyse

**Erstellt:** 2025-12-14 | **Quelle:** Gespraech mit Andreas

---

## Prozess-Uebersicht

```
BEDARF ERKANNT
│
├─ Bauelemente: Verkäufer entscheidet bei Angebot
│   └─ Verkäufer: Enrico, Andreas, Vater
│
├─ Montagematerial: Vater + Andreas verwalten
│   └─ Mario: Preisverhandlungen
│
▼
LIEFERANTEN-AUSWAHL
├─ Kriterien: Preis, Qualitaet, Lieferzeit
├─ Meist Standardlieferant bereits festgelegt
├─ Keine systematische Lieferanten-Bewertung
│
▼
PREIS ERMITTELN
├─ Konfiguratoren (Weru, etc.)
├─ Preislisten / Online-Shops
├─ Oder: Preisanfrage beim Lieferanten/AD
│   └─ PROBLEM: Dauert Tage bis Wochen!
│
▼
BESTELLUNG → (siehe Bestellprozess)
│
▼
ZAHLUNG
├─ Zahlungsziele + Skonto hinterlegt
└─ Jolanta prueft und beruecksichtigt bei Zahlung
```

---

## Beteiligte Personen

| Person | Rolle im Einkauf |
|--------|------------------|
| **Enrico, Andreas, Vater** | Verkäufer - entscheiden Lieferant bei Angebot |
| **Mario** | Preisverhandlungen, Artikel-Pflege in W4A |
| **Andreas** | Import der Preise nach W4A |
| **Vater + Andreas** | Montagematerial-Verwaltung |
| **Jolanta** | Zahlungsziele/Skonto pruefen (unbezahlt) |

---

## Lieferanten & Portale

### Genutzte Online-Portale/Shops

| Lieferant | Portal/Shop | Besonderheit |
|-----------|-------------|--------------|
| Weru | Portal (neu in Arbeit) | Hauptlieferant Fenster |
| Wuerth | Shop vorhanden | Rabatte nicht hinterlegt → staendig AD fragen |
| Foerch | Portal | |
| Gruen Beschlaege | Portal | |
| Febes | Portal | |
| Warema | Portal | Sonnenschutz |
| Kadeco | Portal | |
| Kompotherm | Portal | |
| Trendtueren | Portal | |

### Lieferanten-Anzahl
- Pruefbar via Eingangsrechnungen in W4A

### Lieferanten-Bewertung
- **IST:** Keine systematische Bewertung
- **SOLL:** Evtl. in W4A abbildbar (zu pruefen)

---

## Preise & Konditionen

### Preisquellen

| Quelle | Verwendung |
|--------|------------|
| Konfiguratoren | Bauelemente (Weru WoT, etc.) |
| Preislisten | Hersteller-Listen |
| Online-Shops | Direkte Preisabfrage |
| Preisanfrage | Bei Sonderkonditionen, Grossmengen |

### Konditionen-Ablage (verstreut!)

| Ort | Was |
|-----|-----|
| W4A Dokumente | Rahmenvertraege, Vereinbarungen |
| W4A Artikel | Einkaufspreise pro Artikel |
| Excel | Zusaetzliche Konditionslisten |

**Problem:** Keine zentrale Stelle!

### Preislisten-Workflow

```
Neue Preisliste vom Lieferanten
        ↓
Mario: Artikel in W4A pflegen, Preise eintragen
        ↓
Andreas: Import nach W4A
        ↓
2 Personen involviert!
```

### Rahmenvertraege

- Meist allgemeine Rahmenvertraege
- Sonderkonditionen bei Grossprojekten
- Preisaenderungen: ca. 1-2x pro Jahr

---

## Bestellentscheidung

### Wer entscheidet?

| Produktart | Entscheider | Zeitpunkt |
|------------|-------------|-----------|
| Bauelemente | Verkäufer | Bei Angebotserstellung |
| Montagematerial | Vater, Andreas | Bei Bedarf |

### Mindestbestellwerte

- Kaum relevant
- Falls vorhanden: Mindermengenzuschlaege

### Bestellbuendelung

| Produktart | Buendelung | Grund |
|------------|------------|-------|
| Bauelemente | Weniger | Nachtraegliche Kundenzuordnung schwierig |
| Montagematerial/Zubehoer | Eher ja | Sinnvoll bei Verbrauchsmaterial |

---

## Erkannte Schmerzpunkte

| # | Schmerzpunkt | Auswirkung | Haeufigkeit | Relevante Ideen |
|---|--------------|------------|-------------|-----------------|
| 1 | **Preisanfragen dauern Tage/Wochen** | Angebote verzoegern sich, Kunde wartet | Oft | #71 Preis-Cache |
| 2 | **Wuerth: Staendige AD-Anfragen** | Zeitverlust trotz Shop | Bei jeder Bestellung | #71 |
| 3 | **Grossmengen-Rabatt vergessen** | Geld verschenkt | Manchmal | #71 Erinnerung |
| 4 | **Konditionen verstreut** | W4A + Excel = unuebersichtlich | Dauerhaft | #71 Zentralisierung |
| 5 | **Preislisten-Import 2-stufig** | Mario pflegt → Andreas importiert | Bei Preisaenderung | Workflow optimieren |
| 6 | **Gleiche Produkte schwer findbar** | Langtexte vergleichen = aufwaendig | Bei Lieferantenvergleich | #38 Lagerverwaltung? |
| 7 | **Keine Lieferanten-Bewertung** | Keine Datengrundlage fuer Entscheidung | - | #71 |
| 8 | **Preiserhoehungen per Post** | Nicht alle informiert → falsche Preise | Gelegentlich | #71 Preisinfo-Verteiler |

### Schmerzpunkt #8 Detail: Preiserhoehungen per Post (2025-12-16)

**IST-Situation:**
```
Post-Eingang (Roland oeffnet)
        ↓
Preiserhoehung erkannt → an zustaendige Person
        ↓
❌ Wird Sandra zum Digitalisieren gegeben
❌ Digitalisierung verzoegert/vergessen
❌ Relevante Personen NICHT informiert
        ↓
FOLGE: Angebote mit falschen Preisen → Marge weg!
```

**Beispiel:** Weru TZ (Teuerungszuschlag) per Brief - Vater wusste nichts davon

**Betroffene Empfaenger:**
- Verkauf: Roland, Andreas, Enrico
- Projektleiter: Jaroslaw, Andreas
- Lagerist: Mario

→ **Loesung:** #71 Preisinfo-Verteiler (Auto-Benachrichtigung)

---

## Verbesserungspotential

### Moegliche neue Idee: #71 Lieferanten-/Preismanagement

| Feature | Nutzen |
|---------|--------|
| Preis-Cache | Letzte Preise speichern, weniger Anfragen |
| Grossmengen-Erinnerung | "Bei >X Stueck Rabatt anfragen!" |
| Konditionen zentral | Alle Rabatte, Staffeln an einem Ort |
| Lieferanten-Bewertung | Lieferzeit, Qualitaet, Preis tracken |
| Preisanfrage-Tracking | Status: angefragt/beantwortet/ueberfaellig |

### Quick Wins (ohne neues Tool)

| Massnahme | Aufwand |
|-----------|---------|
| Wuerth-Rabatte einmalig komplett anfragen | Mittel |
| Excel-Konditionen nach W4A migrieren | Mittel |
| Preislisten-Import vereinfachen | Gering |

---

## Prozess-Uebergaenge

### Einkaufsprozess → Bestellprozess
- Lieferant + Preis festgelegt
- Bestellung wird ausgeloest

### Einkaufsprozess → Rechnungsprozess
- Zahlungsziele/Skonto fuer Eingangsrechnungen
- Jolanta prueft bei Zahlung

### Einkaufsprozess → Reklamationsprozess
- Bei Qualitaetsproblemen
- Bereits separat dokumentiert

---

## Offene Fragen (fuer naechstes Brainstorming)

| # | Frage |
|---|-------|
| 1 | Ist Lieferanten-Bewertung in W4A moeglich? Wie? |
| 2 | Kann man Wuerth-Rabatte komplett hinterlegen lassen? |
| 3 | Welche Konfiguratoren haben API/Export fuer Preise? |
| 4 | Wie viele verschiedene Lieferanten sind aktiv? (W4A-Analyse) |
