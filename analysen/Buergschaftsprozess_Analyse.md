# Buergschaftsprozess - IST-Analyse

**Erstellt:** 2025-12-16 | **Quelle:** Gespraech mit Andreas, Screenshots R+V Portal + W4A

---

## Prozess-Uebersicht

```
AUSLOESER
├─ Bauvertrag (VOB oder BGB) abgeschlossen
├─ Baumassnahme fertig + Schlussrechnung geschrieben
│
▼
BEANTRAGUNG (R+V Kreditportal)
├─ Login: R+V Kreditportal
├─ Buergschaft beantragen (5% der Bausumme)
├─ Schlussrechnung hochladen
│
▼
EINGANG URKUNDE
├─ R+V sendet 2x Buergschaftsurkunde
├─ Original → Kunde (mit Begleitschreiben)
├─ Kopie → Scannen + W4A Dokumente
│
▼
TRACKING
├─ W4A-Aufgabe anlegen (Faelligkeit = Laufzeit-Ende)
├─ R+V erinnert auch (aber eigene Erinnerung besser)
│
▼
LAUFZEIT (4-5 Jahre)
├─ BGB-Vertraege: 5 Jahre
├─ VOB-Vertraege: 4 Jahre
├─ Meist "unbefristet" → Auto-Freigabe am Ende
│
▼
ENDE (nur bei befristet)
├─ Original vom Kunden zurueckfordern
├─ Freigabe bei R+V beantragen
└─ Limit wird wieder frei
```

---

## R+V Kreditportal

### Zugangsdaten

| Aspekt | Details |
|--------|---------|
| **Portal** | R+V Kreditportal (Online) |
| **Versicherungsschein-Nr.** | 408 97 576194536 |
| **Firma** | J.S. Fenster & Tueren GmbH |

### Limit-Status (Stand 2025-12-16)

| Aspekt | Wert |
|--------|------|
| **Gesamtlimit** | 15.000,00 EUR |
| **Aktuell belegt** | 15.429,56 EUR |
| **Frei verfuegbar** | 0,00 EUR |
| **Status** | Komplett ausgeschoepft! |

**Hinweis:** Limit kann bei R+V erhoeht werden (Beitrag steigt entsprechend)

### Ansprechpartner R+V

| Kontakt | Details |
|---------|---------|
| **Name** | Sylvia Vetter |
| **Adresse** | Vilsanger 23, 92245 Kuemmersbruck |
| **Telefon** | +49611 533-4466 |
| **E-Mail** | G_Kreditportal-Kontakt@ruv.de |
| **Servicezeiten** | Mo-Do 07:30-18:00, Fr 07:30-17:30 |

---

## Buergschafts-Typen

### Laufzeiten

| Vertragsart | Laufzeit | Haeufigkeit |
|-------------|----------|-------------|
| **BGB-Vertraege** | 5 Jahre | Haeufiger |
| **VOB-Vertraege** | 4 Jahre | Seltener |

### Befristet vs. Unbefristet

| Typ | Beschreibung | Aktion am Ende |
|-----|--------------|----------------|
| **Unbefristet** | Standard | Automatische Freigabe durch R+V |
| **Befristet** | Auf Kundenwunsch | Aktiv zurueckfordern + freimelden |

---

## Tracking in W4A

### Aufgaben-System

| Aspekt | Details |
|--------|---------|
| **Filter** | "buerg" in Aufgaben-Suche |
| **Status** | OFFEN / ERLEDIGT |
| **Faelligkeit** | Laufzeit-Ende der Buergschaft |
| **Zugewiesen** | Sandra Stolarczyk |

### Beispiel-Aufgabe (aus Screenshot)

```
AUFGABE: Buergschaftsurkunde Markt Lauterhofen zurueckfordern

DATUM:           Montag, 11. Oktober 2027
VON:             Stolarczyk Sandra
AN:              Stolarczyk Sandra
GESCHAEFTSPARTNER: Markt Lauterhofen, Marktplatz 11, 92283 Lauterhofen

CHECKLISTE:
- nochmal Online pruefen
- Originale Buergschaftsurkunde zurueckfordern vom Kunden
- an R+V schicken

REFERENZ: siehe Buergschaftsordner, W4A (KD-Nr. 15112)
```

---

## Verantwortlichkeiten

| Aufgabe | Verantwortlich |
|---------|----------------|
| Buergschaft beantragen | Sandra |
| Portal-Verwaltung | Sandra |
| Offene Fragen klaeren | Sandra + Andreas |
| W4A-Aufgaben anlegen | Sandra |
| Urkunde an Kunde senden | Sandra |

---

## Haeufigkeit & Volumen

| Aspekt | Wert |
|--------|------|
| **Neue Buergschaften/Jahr** | 1-2 |
| **Aktive Buergschaften** | ~5-6 (geschaetzt, Limit ausgeschoepft) |
| **Durchschnittliche Summe** | ~2.500-3.000 EUR pro Buergschaft |

---

## Dokumentenablage

### Ordnerstruktur

| Ordner | Inhalt |
|--------|--------|
| `Intern/Buergschaften/000 Allgemein/` | Vorlagen, Begleitschreiben |
| `Intern/Buergschaften/` | Laufende Faelle |
| `Intern/Buergschaften - alt - abgelaufen/` | Abgeschlossene |

### Vorlagen

| Dokument | Zweck |
|----------|-------|
| Uebersendung Buergschaftsurkunde an Kunden | Begleitschreiben |
| Rueckforderung der Buergschaftsurkunde | Wenn befristet abgelaufen |
| Rueckgabe der Buergschaft R+V | Freimeldung |

---

## Erkannte Probleme

| # | Problem | Auswirkung | Status |
|---|---------|------------|--------|
| 1 | **Limit ausgeschoepft** | Keine neuen Buergschaften moeglich | Limit erhoehen? |
| 2 | **Nur R+V-Erinnerung** | Abhaengig von externem System | Eigene Erinnerung waere besser |
| 3 | **Seltener Prozess** | Wird evtl. vergessen wie es geht | Doku vorhanden |

---

## Verbesserungspotential

| Bereich | Idee | Prioritaet |
|---------|------|------------|
| **Erinnerungen** | In #74 integrieren (allg. Frist-Erinnerungen) | Niedrig (1-2x/Jahr) |
| **Limit** | Bei R+V erhoehen wenn noetig | Bei Bedarf |
| **Doku** | Prozess ist gut dokumentiert | OK |

---

## Prozess-Checkliste (Zusammenfassung)

### Neue Buergschaft beantragen

- [ ] Bauvertrag pruefen (VOB/BGB?)
- [ ] Schlussrechnung erstellt?
- [ ] R+V Portal: Buergschaft beantragen
- [ ] Schlussrechnung hochladen
- [ ] Warten auf Urkunde (2x)
- [ ] Original an Kunde senden (mit Begleitschreiben)
- [ ] Kopie scannen + W4A Dokumente
- [ ] W4A-Aufgabe anlegen (Faelligkeit = Laufzeit-Ende)
- [ ] Uebersichtsblatt aktualisieren (falls vorhanden)

### Buergschaft abschliessen (befristet)

- [ ] R+V Portal pruefen
- [ ] Original vom Kunden zurueckfordern
- [ ] An R+V zur Freimeldung senden
- [ ] W4A-Aufgabe als erledigt markieren
- [ ] Fall in "abgelaufen" Ordner verschieben

---

## Change Log

| Datum | Aenderung |
|-------|-----------|
| 2025-12-16 | Initiale Erstellung |
