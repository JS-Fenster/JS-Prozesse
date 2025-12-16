# Inventarprozess - IST-Analyse

**Erstellt:** 2025-12-16 | **Quelle:** Gespraech mit Andreas, Screenshot W4A

---

## Prozess-Uebersicht

```
ERFASSUNG (Mario)
│
├─ Alte Ordnerstruktur → W4A migrieren
├─ Karteileichen aufraeumen
├─ Inventarnummern vergeben + physisch anbringen
│
▼
DOKUMENTATION
├─ Foto 1: Gute Ansicht (Erkennbarkeit)
├─ Foto 2: Typenbezeichnung
├─ Foto 3: Typenschild
├─ Rechnung vom Lieferanten verlinken
├─ Zertifikate + weitere Dokumente
│
▼
ZUORDNUNG
├─ Feste Zuordnung: Fahrzeug/Montage-Team/Lager
├─ Wanderinventar: Lager (oder Checkout-System)
│
▼
WARTUNG/PRUEFUNG
├─ Aktuell: NICHT systematisch erfasst
└─ SOLL: Automatische Erinnerungen
```

---

## W4A Inventar-Modul

### Vorhandene Felder (aus Screenshot)

| Spalte | Beschreibung | Beispiel |
|--------|--------------|----------|
| **Bezeichnung** | Name des Geraets | Bosch GAS 18V-1 |
| **Inventar-Nr.** | Eindeutige Nummer | 74 |
| **Kaufdatum** | Anschaffungsdatum | 05.09.2019 |
| **Lieferant** | Haendler | Bueromarkt AG |
| **Rechnungsnr.** | Zuordnung zur Rechnung | 251348 |
| **Gruppe** | Kategorie | Akku-Handstaubsauger |
| **Nutzung** | Standort/Zuordnung (Freitext) | Montage 3, Lager |
| **Akt. Wert** | Aktueller Wert | 54,54 EUR |
| **Seriennummer** | Hersteller-SN | 903003719 |
| **Zustand** | Erhaltungszustand | gebraucht |
| **Kreditor** | Lieferant (W4A-intern) | Bueromarkt AG |

### Vorhandene Gruppen

| Gruppe | Inhalt |
|--------|--------|
| Fuhrpark | Fahrzeuge, Anhaenger |
| Maschinen | Elektrowerkzeug, Geraete |
| EDV | IT-Equipment |
| Verwertet | Ausgemusterte Geraete |
| Neu | Neuanschaffungen |

### Gesamtwert (Stand 2025-12-16)
**83.070,18 EUR**

---

## Aktuelle Migration (Mario)

### Reihenfolge der Erfassung

| Phase | Kategorie | Status |
|-------|-----------|--------|
| 1 | Werkzeug | In Arbeit |
| 2 | Fahrzeuge | In Arbeit |
| 3 | Maschinen | Geplant |
| 4 | Hilfsgeraete (Leitern) | Geplant |
| 5 | IT | Geplant |

### Foto-Standard (3 Bilder)

| Nr. | Inhalt | Zweck |
|-----|--------|-------|
| 1 | Gute Ansicht | Schnelle Erkennung |
| 2 | Typenbezeichnung | Modell identifizieren |
| 3 | Typenschild | Seriennummer, techn. Daten |

### Dokumente pro Inventar

| Dokument | Pflicht | Quelle |
|----------|---------|--------|
| Rechnung | Ja | Lieferant |
| Zertifikate | Wenn vorhanden | Hersteller/Pruefer |
| Bedienungsanleitung | Optional | Hersteller |
| Pruefprotokolle | Bei pruefpflichtigen Geraeten | Pruefer |

---

## Zuordnungs-Konzept

### Feste Zuordnung

| Nutzung | Beispiel |
|---------|----------|
| Montage 1 | Team Jaroslaw |
| Montage 2 | Team X |
| Montage 3 | Team Y |
| Lager | Nicht zugeordnet |
| [Mitarbeitername] | Persoenliche Ausstattung |

### Wanderinventar

| Geraet | Eigenschaft |
|--------|-------------|
| Handkreissaege | Wird nach Bedarf ausgeliehen |
| Spezialwerkzeug | Nicht dauerhaft zugeordnet |

**Aktuelle Loesung:** Freitext "Nutzung" aendern oder immer "Lager"

**Offene Frage:** Checkout-Log gewuenscht? (Historie wer wann)

---

## Erkannte Probleme

| # | Problem | Auswirkung | Loesung |
|---|---------|------------|---------|
| 1 | **Alte Ordnerstruktur** | Keine Uebersicht, Karteileichen | Migration nach W4A (laeuft) |
| 2 | **Keine Inventarnummern** | Geraete nicht eindeutig identifizierbar | Nummern vergeben + anbringen (laeuft) |
| 3 | **Standort unklar** | Nicht nachvollziehbar welche Maschinen in welchem Auto | "Nutzung"-Feld pflegen |
| 4 | **W4A Bilder-Bug** | Erste Ansicht zeigt mal Foto, mal PDF | W4A-Limitierung (nicht loesbar) |
| 5 | **Keine Prueffristen** | Pruefungen werden vergessen | → #74 Prueffristen-Automatik |
| 6 | **Kein Wartungs-Tracking** | Keine Uebersicht wann was gewartet | → #74 |

---

## Pruefpflichtige Geraete

| Kategorie | Pruefung | Intervall | Rechtsgrundlage |
|-----------|----------|-----------|-----------------|
| **Leitern/Tritte** | Sichtpruefung + Dokumentation | Jaehrlich | DGUV Information 208-016 |
| **Elektrowerkzeug** | DGUV V3 Pruefung | Jaehrlich | DGUV Vorschrift 3 |
| **Fahrzeuge** | TUeV/HU | 2 Jahre (Nutzfahrzeuge: 1 Jahr) | StVZO |
| **Fahrzeuge** | UVV-Pruefung | Jaehrlich | DGUV Vorschrift 70 |
| **Anhaenger** | TUeV/HU | 2 Jahre | StVZO |
| **Hebezeuge** | Sachkundigen-Pruefung | Jaehrlich | BetrSichV |

---

## Verantwortlichkeiten

| Aufgabe | Verantwortlich |
|---------|----------------|
| Inventar-Erfassung | Mario |
| Inventar-Pflege | Mario |
| Prueftermine koordinieren | Mario (SOLL) |
| Pruefung durchfuehren | Externer Pruefer / Intern |

---

## Verbesserungspotential (Ideen-Verknuepfung)

| Bereich | Tool-Idee | Verbesserung |
|---------|-----------|--------------|
| Prueffristen | #74 Prueffristen-Automatik | Auto-Erinnerung X Wochen vorher |
| Inventar-Erweiterung | #13 Inventar-Verwaltung | W4A erweitern oder eigenes Tool |
| Wanderinventar | (offen) | Checkout-Log wenn gewuenscht |

---

## Naechste Schritte

1. Migration abschliessen (Werkzeug + Fahrzeuge)
2. Prueffristen erfassen (naechste Faelligkeit)
3. #74 implementieren (Erinnerungen)
4. Schrittweise erweitern (Maschinen → Leitern → IT)

---

## Change Log

| Datum | Aenderung |
|-------|-----------|
| 2025-12-16 | Initiale Erstellung |
