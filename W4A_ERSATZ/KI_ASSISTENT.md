# KI-Assistent (Multi-Channel)

> **Zurueck:** [README.md](README.md) | **Siehe auch:** [05_ANFRAGE_CRM.md](05_ANFRAGE_CRM.md)

**Ziel:** Kein verpasster Kontakt, keine verlorene Anfrage - auch ohne Mitarbeiter

---

## Kanaele

| Kanal | Status | Besonderheit |
|-------|--------|--------------|
| **Telefon** | Vorhanden | Voice → Transkript |
| **E-Mail** | Vorhanden | Text-Analyse |
| **WhatsApp** | Einzurichten | Business API noetig |
| **Telegram** | Einzurichten | Bot einfach zu erstellen |
| **Website-Chat** | Optional | Widget auf js-fenster.de |

---

## Gleiche Logik, alle Kanaele

```
EINGANG (egal welcher Kanal)
         │
         ▼
┌─────────────────────────────────────┐
│  🤖 KI-ASSISTENT                    │
│                                     │
│  1. Kanal erkennen                  │
│  2. Absender identifizieren         │
│     → Bestandskunde? (Tel/E-Mail)   │
│  3. Anliegen klassifizieren         │
│     → Anfrage / Reparatur / Rekla   │
│  4. Daten sammeln (Dialog)          │
│  5. Aktion ausloesen                │
│     → Budget-Angebot / Ticket / ... │
└─────────────────────────────────────┘
```

---

## Telefon (Voice)

```
ANRUF EINGANG
     │
     ▼
┌─────────────┐
│ Klingelt... │
└─────────────┘
     │
     ├── Mitarbeiter nimmt ab → Normale Erfassung + Transkript
     │
     └── Nach X Klingeln niemand da
              │
              ▼
     ┌─────────────────────────────────────┐
     │  🤖 KI-CHATBOT NIMMT AB             │
     │                                     │
     │  "Guten Tag, JS Fenster und Tueren, │
     │   mein Name ist [KI-Name].          │
     │   Wie kann ich Ihnen helfen?"       │
     └─────────────────────────────────────┘
              │
              ▼
     ┌─────────────────────────────────────┐
     │  GESPRAECH FUEHREN                  │
     │                                     │
     │  - Anliegen erfassen                │
     │  - Kontaktdaten abfragen            │
     │  - Bei Reparatur: Details sammeln   │
     │  - Termin-Wunsch erfragen           │
     └─────────────────────────────────────┘
              │
              ▼
     ┌─────────────────────────────────────┐
     │  AUSWERTUNG                         │
     │                                     │
     │  Genuegend Infos fuer Budget?       │
     │  ├── JA → Budget-Angebot per Mail   │
     │  └── NEIN → Rueckruf-Aufgabe        │
     └─────────────────────────────────────┘
```

### Technische Umsetzung

| Komponente | Option | Bemerkung |
|------------|--------|-----------|
| **Telefonie** | VoIP/SIP Integration | Oder Cloud-Dienst (Twilio, etc.) |
| **Speech-to-Text** | Whisper (lokal/API) | Echtzeit-Transkription |
| **Chatbot-Logik** | Claude/GPT mit Prompt | Gespraechsfuehrung |
| **Text-to-Speech** | ElevenLabs / Azure | Natuerliche Stimme |

### Chatbot-Gespraechsfluss (Reparatur)

```
KI: "Handelt es sich um eine Reparatur oder ein neues Projekt?"
Kunde: "Reparatur, mein Fenster klemmt"

KI: "Verstehe. Koennen Sie mir sagen, um welches Fenster es geht?
     Zum Beispiel: Wohnzimmer, Kueche, oder welches Stockwerk?"
Kunde: "Kueche im Erdgeschoss"

KI: "Ist das Fenster von uns, JS Fenster, oder von einem anderen Anbieter?"
Kunde: "Ja, von euch, vor 3 Jahren eingebaut"

KI: "Perfekt, dann haben wir Ihre Daten vermutlich schon.
     Unter welcher Telefonnummer erreichen wir Sie am besten?"
Kunde: "0961 12345"

KI: [Sucht in DB → Kunde gefunden]
    "Herr Mueller, richtig? Ich sehe Ihr Projekt von 2022.
     Wir melden uns morgen bei Ihnen fuer einen Termin.
     Alternativ kann ich Ihnen gleich einen Kostenrahmen
     fuer die Reparatur nennen. Moechten Sie das?"
```

### Vorteile

| Vorteil | Auswirkung |
|---------|------------|
| 24/7 erreichbar | Kein verpasster Kunde |
| Sofort Daten im System | Kein Zettel, kein Vergessen |
| Budget-Angebot automatisch | Mitarbeiter nur bei Bedarf |
| Transkript als Dokumentation | Nachvollziehbar |
| Bestandskunde erkannt | Persoenliche Ansprache |

### Eskalation an Mitarbeiter

| Situation | Aktion |
|-----------|--------|
| Kunde will Mitarbeiter | "Ich verbinde Sie" / Rueckruf-Aufgabe |
| Komplexe Fragen | Transkript + KRITISCH-Flag |
| Reklamation/Beschwerde | Sofort-Benachrichtigung an Andreas |
| Technische Probleme | Aufnahme + Entschuldigung |

---

## E-Mail (Text)

```
E-MAIL EINGANG
     │
     ▼
🤖 AUTONOM: Absender pruefen → Bestandskunde?
🤖 AUTONOM: Betreff + Inhalt analysieren
🤖 AUTONOM: Klassifizieren:
     ├── Lieferant → Ordner "Lieferanten"
     ├── Rechnung/AB → Ordner "Buchhaltung"
     ├── Anfrage → KI-Dialog starten
     └── Reklamation → KRITISCH + Andreas
          │
          ▼ (bei Anfrage)
🤖 AUTONOM: Auto-Antwort mit Rueckfragen
     "Danke fuer Ihre Anfrage. Um Ihnen ein Angebot
      erstellen zu koennen, benoetigen wir noch:
      - Anzahl der Fenster/Tueren
      - Ungefaehre Masse (Breite x Hoehe)
      - Neubau oder Sanierung?"
          │
          ▼
🤖 AUTONOM: Kunde antwortet → Daten extrahieren
🤖 AUTONOM: Genuegend Infos? → Budget-Angebot
🤖 AUTONOM: Sonst → Weitere Rueckfrage ODER Ticket
```

---

## WhatsApp / Telegram (Chat)

### Einrichtung noetig

| Dienst | Was | Aufwand |
|--------|-----|---------|
| **WhatsApp Business** | Telefonnummer verifizieren, Business API | Mittel |
| **Telegram Bot** | @BotFather, Token generieren | Einfach |

### Chat-Flow (gleich fuer beide)

```
NACHRICHT EINGANG
     │
     ▼
🤖 AUTONOM: "Hallo! Ich bin der digitale Assistent
             von JS Fenster. Wie kann ich helfen?"
     │
     ▼
👤 KUNDE: "Brauche neue Fenster"
     │
     ▼
🤖 AUTONOM: "Gerne! Ein paar kurze Fragen:
             1️⃣ Neubau oder Sanierung?
             2️⃣ Wie viele Fenster ungefaehr?
             3️⃣ In welcher Stadt/Region?"
     │
     ▼
👤 KUNDE: "Sanierung, 6 Fenster, Amberg"
     │
     ▼
🤖 AUTONOM: "Super! Fuer 6 Fenster bei Sanierung
             liegt der Rahmen bei ca. X-Y €.

             Moechten Sie:
             📧 Budget-Angebot per E-Mail
             📞 Rueckruf vereinbaren
             📅 Aufmass-Termin buchen"
     │
     ▼
👤 KUNDE: "Budget-Angebot"
     │
     ▼
🤖 AUTONOM: "Ihre E-Mail-Adresse bitte?"
👤 KUNDE: "test@example.de"
🤖 AUTONOM: Budget-Angebot generieren + versenden
🤖 AUTONOM: "Fertig! Sie erhalten gleich eine E-Mail.
             Bei Fragen einfach hier schreiben!"
```

### Vorteile Chat vs. Telefon

| Aspekt | Vorteil |
|--------|---------|
| Asynchron | Kunde antwortet wenn Zeit |
| Bilder | Kunde kann Fotos schicken (Reparatur!) |
| Link-Versand | Direkt Termin-Buchung verlinken |
| Historie | Chat bleibt erhalten |
| Junge Zielgruppe | Bevorzugt Chat vor Telefon |

### Foto-Upload bei Reparatur

```
👤 KUNDE: [Foto von kaputtem Fenster]
🤖 AUTONOM: "Danke fuer das Foto! Ich sehe:
             - Fenstergriff scheint gebrochen
             - Ist das korrekt?"
👤 KUNDE: "Ja genau"
🤖 AUTONOM: "Ein neuer Griff inkl. Einbau kostet
             ca. 80-120€. Soll ich einen Termin
             fuer unseren Servicetechniker Stefan
             vorschlagen?"
```

---

## Tool-Referenzen (aus IDEEN.md)

| Tool | Funktion | Autonomie |
|------|----------|-----------|
| #7 Spracheingabe | Speech-to-Text (Whisper) | 🤖 Autonom |
| #12 E-Mail Auto-Klassifizierung | Eingehende E-Mails kategorisieren | 🤖 Autonom |
| #62 KI-Vision | Fotos analysieren (Reparatur-Bilder) | 🤖 Autonom |
| #77 Schadens-ChatBot | Bilder + Sprache → Auto-Meldung | 🤖 Autonom |
