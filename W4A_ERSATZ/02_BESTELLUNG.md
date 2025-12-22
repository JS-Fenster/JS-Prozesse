# Workflow: Bestellung → Wareneingang

> **Zurueck:** [README.md](README.md)

---

## Schmerzpunkte heute → Neue Loesung

| Problem (W4A) | Neue Loesung |
|---------------|--------------|
| Offene ABs nicht getrackt | Auto-Erinnerung nach X Tagen |
| Portal-ABs vergessen | Auto-Download oder Reminder |
| Abholungen nicht getrackt | Separater Abhol-Status |
| Outlook unzuverlaessig | Eigenes System, kein Outlook |
| Eingangslieferschein fehlerhaft | Scan → Auto-Erfassung |
| Keine Lagerbuchungen | Automatisch bei Wareneingang |
| Teilmengen falsch | Position fuer Position abhaken |
| Anzahlung vergessen | Pflichtfeld / Auto-Check |
| Lieferwoche fehlt | Pflichtfeld |
| Lieferadresse falsch | Auto-Logik nach Artikeltyp |
| AB manuell geprueft | KI-Abgleich mit Bestellung |

---

## Prozess-Schritte

```
1. BESTELLUNG VORBEREITEN
   🤖 AUTONOM: Positionen aus Auftrag, EK-Preise, Lieferant (gelernt)
   🤖 AUTONOM: Lieferadresse (Fenster→Lager, Pakete→Buero)
   🤖 AUTONOM: Lieferwoche (Montage-1 oder Pflichtfeld)
   👤 USER: Pruefen + Freigeben (1 Klick)

2. BESTELLUNG VERSENDEN
   🤖 AUTONOM: Versandweg (Portal-API oder E-Mail)
   🤖 AUTONOM: AB-Frist setzen (3-5 Werktage)

3. AB UEBERWACHEN
   🤖 AUTONOM: Taeglicher Check
   🤖 AUTONOM: Frist ueberschritten → Auto-Erinnerung an Lieferant
   🤖 AUTONOM: 2x ueberschritten → KRITISCH → Andreas

4. AB PRUEFEN (KI-gestuetzt)
   🤖 AUTONOM: AB hochladen (Drag&Drop)
   🤖 AUTONOM: KI-Abgleich Bestellung vs. AB
   ⚠️ Abweichungen → User entscheidet
   ✅ <5% Abweichung → Auto-OK (Stufe 3)

5. LIEFERUNG UEBERWACHEN
   🤖 AUTONOM: Lieferdatum tracken, Countdown
   🤖 AUTONOM: "Abholung" = separater Status + taeglicher Reminder

6. WARENEINGANG
   👤 USER: Lieferschein scannen/fotografieren
   🤖 AUTONOM: Bestellung erkennen, Positionen abgleichen
   🤖 AUTONOM: Teillieferung? → Status anpassen, Bestellung bleibt offen
   🤖 AUTONOM: Lagerbestand buchen

7. MONTAGE-FREIGABE
   🤖 AUTONOM: Alle Positionen da? → "Montagebereit"
   🤖 AUTONOM: Fehlt was? → Warnung mit Liste
```

---

## Beschaffungs-Dashboard (Echtzeit)

```
┌────────────────────────────────────────────────────────────┐
│  BESCHAFFUNGS-DASHBOARD                                    │
├────────────────────────────────────────────────────────────┤
│  🔴 KRITISCH (3)     AB ueberfaellig, Abholung vergessen  │
│  🟡 ACHTUNG (7)      Abweichungen, Lieferung morgen       │
│  🟢 IM PLAN (23)     Alles OK                             │
│  📍 ABHOLUNGEN (2)   Offen bei Lieferanten                │
└────────────────────────────────────────────────────────────┘
```

---

## Tool-Referenzen (aus IDEEN.md)

| Tool | Funktion | Autonomie |
|------|----------|-----------|
| #19 Lieferanten-Bewertung | Auto-Scoring nach Liefertreue, Preis, Abweichungen | 🤖 Autonom |
| #36 Beschaffungs-Workflow | Bestellung → AB → Lieferung (Kern) | 🤖 Autonom |
| #53 Mindestbestand-Alert | Auto-Warnung wenn Lager unter Schwelle | 🤖 Autonom |
| #54 Preis-Vergleich | Parallele Anfragen an alle Lieferanten | 🤖 Autonom |
| #71 Einkaufs-Workflow | Preis-Cache, Anfrage-Tracking | 🤖 Autonom |
