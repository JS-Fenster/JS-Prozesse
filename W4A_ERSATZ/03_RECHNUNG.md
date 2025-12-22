# Workflow: Rechnung → Zahlung → Mahnung

> **Zurueck:** [README.md](README.md)

---

## Schmerzpunkte heute → Neue Loesung

| Problem (W4A) | Neue Loesung |
|---------------|--------------|
| Roland fehlen Infos | Digitale Montage-Rueckmeldung mit allen Daten |
| Haengeakt wandert zurueck | Kein Papier - alles digital, Status sichtbar |
| Mehrere Auftraege komplex | Dashboard: Was ist montiert + nicht abgerechnet |
| Anzahlung vergessen | Auto-Check bei Auftrag + Sperre bis bezahlt |
| Firma in Vorleistung | Teilrechnungs-Automatik |
| E-Mails ausgedruckt | Alles digital verlinkt |
| ~4,4% Korrekturen | Bessere Daten vorab (Montage-Rueckmeldung) |

---

## Prozess-Schritte

```
1. RECHNUNGS-VORBEREITUNG (nach Montage)
   🤖 AUTONOM: Vollstaendigkeits-Check
      - Positionen: bestellt ✓ geliefert ✓ montiert ✓
      - Arbeitszeit aus digitaler Rueckmeldung
      - Zusatzpositionen markiert
   🤖 AUTONOM: Rechnungsentwurf generieren
   👤 USER (Roland): Pruefen + Freigeben (1-Klick wenn Standard)

2. RECHNUNG ERSTELLEN
   🤖 AUTONOM: PDF mit Wasserzeichen generieren
   🤖 AUTONOM: Pruefungen (MwSt, IBAN, Zahlungsbedingungen)

3. RECHNUNG VERSENDEN
   🤖 AUTONOM: E-Mail bevorzugt (wenn vorhanden)
   🤖 AUTONOM: Standard-Text + PDF anhaengen

4. ZAHLUNGS-UEBERWACHUNG
   🤖 AUTONOM: Kontoauszug taeglich abrufen (HBCI)
   🤖 AUTONOM: Automatische Zuordnung
   🤖 AUTONOM: Skonto-Pruefung

5. MAHNWESEN (bei Nichtzahlung)
   Tag 14: Zahlungsziel
   Tag 21: 🤖 AUTONOM: Zahlungserinnerung (freundlich)
   Tag 28: 🤖 AUTONOM: Mahnung 1
   Tag 35: 🤖 AUTONOM: Mahnung 2 + KRITISCH → Andreas
   Tag 42+: ⚠️ Inkasso? → Manuelle Entscheidung

6. DATEV-EXPORT (#81, #82)
   🤖 AUTONOM: Buchungskonto-Assistent (#82)
      - Lieferant erkannt → Konto vorschlagen
      - Artikelart erkannt → Konto vorschlagen
      - Lernt aus Korrekturen (Roland bucht oft falsch!)
   🤖 AUTONOM: PDF-Merger (#81)
      - Rechnung + alle Anhaenge (Tankbelege, Listen)
      - Zu EINER Datei zusammenfassen
      - DATEV kann nur 1 Datei pro Buchung!
   🤖 AUTONOM: Export ohne W4A (eigener DATEV-Export)
```

---

## Teilrechnungs-Logik

System erkennt automatisch:
- Was ist geliefert + montiert? → abrechenbar
- Was fehlt noch? → in Restrechnung
- Anzahlung bereits gezahlt? → Auto-Abzug
- Option: "Automatisch Restrechnung wenn [Position] geliefert"

---

## Montagematerial-Pauschale (#70)

**Problem:** Bei Nicht-Fenster-Produkten wird Montagematerial vergessen → Umsatzverlust!

```
POSITION ERKANNT (z.B. Innentuer, Markise, Raffstore)
     │
     ▼
🤖 AUTONOM: Ist Standard-Fenster?
     │
     ├── JA → Pauschale bereits inkludiert
     │
     └── NEIN → Montagematerial-Position ergaenzen!
              "Montagematerial Innentuer"  € 45,-
              "Montagematerial Markise"    € 85,-
              etc.
```

---

## BAFA-Foerderantrag (#3) ⭐ KRITISCH!

**Problem:** NachweisService nach Zahlung vergessen → Kunde verliert Foerderung!

```
FOERDER-POSITION IN AUFTRAG ERKANNT
     │
     ▼
🤖 AUTONOM: BAFA-Tracking aktivieren
     │
     ▼
RECHNUNG BEZAHLT
     │
     ▼
🤖 AUTONOM: SOFORT Erinnerung an Andreas!
     "BAFA NachweisService faellig fuer Projekt Mueller!"
     │
     ▼
🤖 AUTONOM: Checkliste anzeigen:
     ☐ Rechnung hochladen
     ☐ Fotos der Montage
     ☐ Fachunternehmererklarung
     ☐ NachweisService abschliessen
     │
     ▼
🤖 AUTONOM: Taeglich erinnern bis erledigt!
```

**Warum KRITISCH:** Kunde hat 6 Monate Zeit nach Zahlung. Wird das vergessen, verliert der Kunde 15-20% Foerderung (mehrere Tausend Euro)!

---

## Rechnungs-Dashboard

```
┌────────────────────────────────────────────────────────────┐
│  RECHNUNGS-DASHBOARD                                       │
├────────────────────────────────────────────────────────────┤
│  📝 ZU ERSTELLEN (5)   Montage fertig, keine Rechnung     │
│  💳 OFFEN (12)         Versendet, nicht bezahlt           │
│     🟢 Faellig in >7d   🟡 Faellig bald   🔴 Ueberfaellig │
│  ✅ BEZAHLT (8)        Diese Woche: 45.200€               │
│  ⏳ ANZAHLUNGEN (3)    Offen - Bestellung wartet!         │
└────────────────────────────────────────────────────────────┘
```

---

## Tool-Referenzen (aus IDEEN.md)

| Tool | Funktion | Autonomie |
|------|----------|-----------|
| #3 BAFA-Tracking | Auto-Erinnerung nach Zahlung (KRITISCH!) | 🤖 Autonom |
| #50 Zahlungserinnerung | Sanfte Mahnung nach Frist | 🤖 Autonom |
| #51 Cashflow-Prognose | Erwartete Zahlungseingaenge | 🤖 Autonom |
| #70 Montagematerial-Pauschale | Auto-Position bei Nicht-Fenster | 🤖 Autonom |
| #81 PDF-Merger | DATEV 1-Datei-Limitierung umgehen | 🤖 Autonom |
| #82 Buchungskonto-Assistent | Konto-Vorschlag aus Lieferant/Artikelart | 🤖 Autonom |
