# Workflow: Anfrage / CRM

> **Zurueck:** [README.md](README.md) | **Siehe auch:** [KI_ASSISTENT.md](KI_ASSISTENT.md)

---

## Schmerzpunkte heute → Neue Loesung

| Problem (W4A/Outlook) | Neue Loesung |
|-----------------------|--------------|
| Zettelwirtschaft bei Tel. Anfragen | Digitale Erfassung direkt am Telefon |
| E-Mail-Sortierung in Outlook manuell | Auto-Kategorisierung + Ticket-System |
| Kein Tracking wer was bearbeitet | Zuweisung + Status sichtbar |
| Kaum Nachverfolgung | Automatische Follow-up Reminder |
| Auftrag fehlt oft → Soll-Ist falsch | Pflicht-Workflow: Angebot → Auftrag |
| Projekt fuer Preisanfrage noetig | Automatisch wenn Lieferant-Anfrage |
| 2-3 Wochen Aufmass-Wartezeit | Kapazitaets-Uebersicht + Online-Buchung |
| "Wie auf uns aufmerksam?" nicht erfasst | Pflichtfeld (Marketing-Analyse) |
| Konfiguratoren nur Copy&Paste | XML-Import wo moeglich |

---

## Prozess-Schritte

```
1. ANFRAGE-EINGANG (Multi-Channel)
   📧 E-MAIL:
   🤖 AUTONOM: E-Mail analysieren (Absender, Betreff, Keywords)
   🤖 AUTONOM: Bestandskunde? → Auto-Zuordnung
   🤖 AUTONOM: Kategorie vorschlagen (Anfrage/Rechnung/Lieferant)
   🤖 AUTONOM: Ticket erstellen, Zuweisung nach Regeln

   📞 TELEFON (mit KI-Chatbot):

   VARIANTE A - Mitarbeiter nimmt ab:
   👤 USER: Schnell-Erfassungsmaske waehrend Gespraech
      - Bestandskunde suchen (Autovervollstaendigung)
      - Neukunde anlegen (minimal: Name + Tel/E-Mail)
      - Checkboxen: Produkte, Projekttyp
      - "Wie gefunden?" (Pflicht bei Neukunden)
   🤖 AUTONOM: Gespraech wird transkribiert (Whisper)
   🤖 AUTONOM: Aus Transkript weitere Daten extrahieren
   🤖 AUTONOM: Ticket + Termin-Vorschlag

   VARIANTE B - Niemand nimmt ab → KI-CHATBOT:
   🤖 AUTONOM: Nach X Klingeln → Chatbot nimmt ab
   🤖 AUTONOM: Begruessung: "JS Fenster, wie kann ich helfen?"
   🤖 AUTONOM: Gespraech fuehren + transkribieren
   🤖 AUTONOM: Genuegend Daten? → Budget-Angebot generieren!
   → Details siehe [KI_ASSISTENT.md](KI_ASSISTENT.md)

   🚶 LAUFKUNDSCHAFT:
   👤 USER: Tablet in Ausstellung - gleiche Maske
   🤖 AUTONOM: Nach Beratung → Angebot oder Follow-up Ticket

   🌐 WEBSITE:
   🤖 AUTONOM: Formular → Ticket → Zuweisung
   🤖 AUTONOM: Auto-Antwort mit Bearbeitungszeit

2. QUALIFIZIERUNG
   🤖 AUTONOM: Anfrage bewerten nach:
      - Bestandskunde (Umsatzhistorie)
      - Projektgroesse (Produktauswahl)
      - Zeitrahmen (dringend?)
      - Budget genannt?
   🤖 AUTONOM: Prioritaet setzen (Hot/Warm/Cold)
   🤖 AUTONOM: Empfehlung: Aufmass / Ausstellung / Telefon-Beratung

3. BUDGET-ANGEBOT (optional, schnell)
   👤 USER: Wenn Infos reichen → Schnell-Kalkulation
   🤖 AUTONOM: Ca.-Preise aus Preislisten-Cache
   🤖 AUTONOM: E-Mail mit Budget-Angebot
   👤 KUNDE: Interesse? → Aufmass vereinbaren

4. AUFMASS-TERMINIERUNG
   🤖 AUTONOM: Freie Slots anzeigen (Kapazitaet Enrico/Jaroslaw/Andreas)
   🤖 AUTONOM: Online-Buchung moeglich (Kunde waehlt selbst)
   🤖 AUTONOM: Route beruecksichtigen (Nachbar-Termine gruppieren)
   🤖 AUTONOM: Termin-Bestaetigung per E-Mail/SMS
   🤖 AUTONOM: 24h vorher Erinnerung

5. ANGEBOT ERSTELLEN
   👤 USER: Konfigurator-Daten importieren:
      - Weru WoT: XML Drag&Drop
      - Andere: PDF-Upload → KI-Extraktion
      - Manuell bei Bedarf
   🤖 AUTONOM: Positionen vorausfuellen
   🤖 AUTONOM: Rabatt-Regeln anwenden (gelernt)
   🤖 AUTONOM: PDF generieren (mit Wasserzeichen)
   🤖 AUTONOM: E-Mail-Versand mit Nachverfolgung

6. NACHVERFOLGUNG (automatisch!)
   🤖 AUTONOM: Follow-up Sequenz:
      - Tag 3: Auto-Check ob E-Mail geoeffnet
      - Tag 7: Freundliche Nachfrage ("Noch Fragen?")
      - Tag 14: Erinnerung ("Angebot noch aktuell?")
      - Tag 21: Letzte Chance ("Interesse noch da?")
   🤖 AUTONOM: Kunde antwortet → Sequenz pausiert
   🤖 AUTONOM: Kunde sagt ab → Grund erfassen (optional)
   🤖 AUTONOM: Keine Reaktion → "Cold" Status nach 30 Tagen

7. KUNDE SAGT ZU
   🤖 AUTONOM: Angebot → Auftrag (Pflicht!)
   🤖 AUTONOM: Checkliste pruefen:
      - Anzahlung noetig? (bei > X €)
      - Lieferbedingungen geklaert?
      - Montage-Termin grob?
   🤖 AUTONOM: Bestellung vorbereiten (naechster Workflow)

8. ANALYSE / REPORTING
   🤖 AUTONOM: Dashboard-Daten sammeln:
      - Anfragen pro Kanal (Telefon/E-Mail/Web)
      - "Wie gefunden?" Auswertung
      - Conversion Rate (Anfrage → Angebot → Auftrag)
      - Durchlaufzeiten (Anfrage → Auftrag)

9. KUNDEN-REAKTIVIERUNG (#84)
   🤖 AUTONOM: Alte Projekte scannen (>5 Jahre, >10 Jahre)
   🤖 AUTONOM: Personalisierte Nachricht generieren:
      "Ihre Fenster von 2015 sind jetzt 10 Jahre alt.
       Zeit fuer einen Energie-Check?"
   🤖 AUTONOM: E-Mail/Brief-Kampagne ausloesen
   🤖 AUTONOM: Reaktionen tracken → Pipeline
   → Potenzial: ~2.700 Projekte reaktivierbar!
```

---

## Anfrage-Erfassung (Schnell-Maske)

```
┌─────────────────────────────────────────────────────────────┐
│  📞 NEUE ANFRAGE                     [Kunde suchen: ____]   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  KUNDE:  [Mueller, Hans_____________]  ✅ Bestandskunde    │
│          Letzte Aktivitaet: Auftrag 12/2023 (8.500€)       │
│                                                             │
│  KONTAKT: 0961 / 12345   │   mueller@example.de            │
│                                                             │
│  ── Anfrage ────────────────────────────────────────────   │
│                                                             │
│  PRODUKTE:  ☑ Fenster  ☐ Tueren  ☑ Raffstore  ☐ Sonstig   │
│                                                             │
│  PROJEKT:   ○ Neubau   ● Sanierung   ○ Reparatur           │
│                                                             │
│  ZEITRAHMEN: [Q1 2025______]                               │
│                                                             │
│  NOTIZEN:   [5 Fenster EG, Kunde hat Masse____________]    │
│             [_________________________________________]     │
│                                                             │
│  ── Naechster Schritt ──────────────────────────────────   │
│                                                             │
│  ○ Angebot (Infos reichen)                                 │
│  ● Aufmass vereinbaren         [Verfuegbarkeit anzeigen]  │
│  ○ Kunde meldet sich                                       │
│  ○ Lieferant-Preisanfrage                                  │
│                                                             │
│           [Speichern + Ticket erstellen]                   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## Neukunde-Erfassung

```
┌─────────────────────────────────────────────────────────────┐
│  ➕ NEUKUNDE ANLEGEN                                        │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  KONTAKT (Pflicht):                                        │
│  Name:      [________________]  Vorname: [______________]  │
│  Telefon:   [________________]  ODER                       │
│  E-Mail:    [________________]                             │
│                                                             │
│  ADRESSE (optional jetzt, spaeter Pflicht):                │
│  Strasse:   [________________]  Nr: [___]                  │
│  PLZ:       [_____]  Ort: [_________________________]      │
│                                                             │
│  WIE AUF UNS AUFMERKSAM? (Pflicht)                         │
│  ○ Empfehlung   ○ Google   ○ Werbung   ○ Vorbeigefahren   │
│  ○ Bestandskunde (anderes Projekt)   ○ Sonstiges: [____]  │
│                                                             │
│                          [Anlegen + weiter zur Anfrage]    │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## CRM-Pipeline (Dashboard)

```
┌────────────────────────────────────────────────────────────────────┐
│  VERKAUFS-PIPELINE                        Wert: 487.300€          │
├────────────────────────────────────────────────────────────────────┤
│                                                                    │
│  ANFRAGE (12)    ANGEBOT (8)     NACHFASS (5)    AUFTRAG (3)     │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐    │
│  │ Mueller  │ →  │ Schmidt  │ →  │ Weber    │ →  │ Klein    │    │
│  │ 15.000€  │    │ 42.000€  │    │ 8.500€   │    │ 95.000€  │    │
│  │ 🔥 Hot   │    │ ⏰ 3d    │    │ ⚠️ 14d   │    │ ✅ AZ ok │    │
│  ├──────────┤    ├──────────┤    ├──────────┤    ├──────────┤    │
│  │ Bauer    │    │ Huber    │    │ Meier    │    │ Schulze  │    │
│  │ 8.000€   │    │ 23.000€  │    │ 12.000€  │    │ 67.000€  │    │
│  │ Warm     │    │ ⏰ 5d    │    │ ⚠️ 21d   │    │ ⏳ AZ    │    │
│  └──────────┘    └──────────┘    └──────────┘    └──────────┘    │
│                                                                    │
│  ── HEUTE FAELLIG ──────────────────────────────────────────────  │
│  🔴 Weber (14d ueberfaellig) - Nachfragen!                        │
│  🟡 Schmidt (3d) - Erste Nachfrage heute                          │
│                                                                    │
│  ── AUFMASS-TERMINE DIESE WOCHE ─────────────────────────────────  │
│  DI 14:00  Mueller, Amberg (Enrico)                               │
│  MI 09:00  Neukunde Bauer, Weiden (Jaroslaw)                      │
│  FR 11:00  Reparatur Klein, Sulzbach (Andreas)                    │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

---

## Marketing-Auswertung

```
┌────────────────────────────────────────────────────────────────────┐
│  MARKETING-ANALYSE                              Zeitraum: 2024    │
├────────────────────────────────────────────────────────────────────┤
│                                                                    │
│  WIE GEFUNDEN?                                                     │
│  ████████████████████ Empfehlung        42%   (+5% vs. Vorjahr)  │
│  ████████████         Google            28%   (+12%)             │
│  ████████             Vorbeigefahren    18%   (-3%)              │
│  ███                  Werbung            8%   (-8%)              │
│  ██                   Website            4%   (+2%)              │
│                                                                    │
│  CONVERSION RATE                                                   │
│  Anfrage → Angebot:    78%  (245 von 315)                        │
│  Angebot → Auftrag:    34%  (83 von 245)                         │
│  Gesamt:               26%  (83 von 315)                         │
│                                                                    │
│  DURCHLAUFZEIT (Median)                                           │
│  Anfrage → Angebot:     8 Tage                                   │
│  Angebot → Auftrag:    21 Tage                                   │
│  Anfrage → Auftrag:    32 Tage                                   │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

---

## Besonderheit: Preisanfrage an Lieferant

Bei nicht-rechenbaren Produkten (kein Standardpreis):

```
1. PREISANFRAGE NOETIG
   👤 USER: Markiert Position als "Lieferant-Anfrage"
   🤖 AUTONOM: Projekt automatisch erstellt (falls noch nicht)
   🤖 AUTONOM: E-Mail-Vorlage an Lieferant generieren
   🤖 AUTONOM: Warte-Status im Ticket

2. ANTWORT EINGEHT
   🤖 AUTONOM: E-Mail erkennen → Ticket reaktivieren
   👤 USER: Preis uebernehmen
   🤖 AUTONOM: Angebot vervollstaendigen
```

---

## Tool-Referenzen (aus IDEEN.md)

| Tool | Funktion | Autonomie |
|------|----------|-----------|
| #12 E-Mail Auto-Klassifizierung | Eingehende E-Mails kategorisieren | 🤖 Autonom |
| #23 Verkaufs-Pipeline | Visualisierung Anfrage → Auftrag | 🤖 Autonom |
| #24 Digitale Checklisten | Telefon-Anfrage strukturiert erfassen | 🤖 Autonom |
| #47 Kunden-Historie | Alle Kontakte, Projekte, Umsatz auf einen Blick | 🤖 Autonom |
| #52 Conversion-Tracker | Anfrage → Angebot → Auftrag Quoten | 🤖 Autonom |
| #84 Kunden-Reaktivierung | Alte Projekte reaktivieren (5+/10+ Jahre) | 🤖 Autonom |
