# Technische Architektur

> **Zurueck:** [README.md](README.md)

---

## Uebersicht der Entscheidungen

| Nr | Entscheidung | Optionen | Status |
|----|--------------|----------|--------|
| 1 | Frontend-Framework | React / Vue / Svelte | Offen |
| 2 | Backend-Framework | Node.js / Python / .NET | Offen |
| 3 | Datenbank | PostgreSQL / MySQL / MongoDB | Offen |
| 4 | Hosting | Cloud / On-Premise / Hybrid | Offen |
| 5 | KI-Integration | API / Lokal / Hybrid | Offen |
| 6 | Echtzeit-Kommunikation | WebSockets / Polling / SSE | Offen |
| 7 | Mobile App | Native / PWA / Hybrid | Offen |
| 8 | Authentifizierung | Eigen / OAuth / Beides | Offen |

---

## 1. Frontend-Framework

> **Was ist das?** Das Frontend ist das, was der Benutzer sieht und bedient - die Oberflaeche im Browser oder auf dem Handy. Ein Framework ist ein "Baukasten" mit fertigen Bausteinen, damit man nicht alles von Null programmieren muss.

### Option A: React

```
Entwickelt von: Facebook/Meta (2013)
Verbreitung:    Marktfuehrer, ~40% aller Web-Apps
Beispiele:      Facebook, Instagram, Netflix, Airbnb
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Riesige Community | Wenn du ein Problem hast, haben es 1000 andere schon geloest. Tutorials, Antworten, fertige Loesungen gibt es massenhaft. |
| Viele fertige Komponenten | Brauchst du eine Tabelle, einen Kalender, ein Formular? Es gibt fertige Bausteine die du einfach einbaust. |
| Viele Entwickler verfuegbar | Wenn du spaeter jemanden brauchst der das weiterentwickelt, findest du leicht React-Entwickler. |
| Langzeit-Support | Facebook nutzt React selbst, es wird also nicht "sterben". |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Steile Lernkurve | React hat viele Konzepte die man verstehen muss (Components, State, Props, Hooks). Fuer Anfaenger erstmal verwirrend. |
| Viele Entscheidungen | React sagt dir nicht WIE du etwas bauen sollst. Du musst selbst entscheiden welche Zusatz-Tools du nutzt. Das kann ueberfordern. |
| Bundle-Groesse | Die fertige App kann gross werden wenn man nicht aufpasst. Groesser = laengere Ladezeit. |

---

### Option B: Vue.js

```
Entwickelt von: Evan You (Ex-Google, 2014)
Verbreitung:    Platz 2, ~20% der Web-Apps
Beispiele:      Alibaba, Xiaomi, GitLab
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Einfacher Einstieg | Vue ist "sanfter" als React. Die Dokumentation ist sehr gut, die Konzepte sind leichter zu verstehen. |
| Alles aus einer Hand | Vue sagt dir genau welche Tools du nutzen sollst. Weniger Entscheidungen = weniger Verwirrung. |
| Gute deutsche Community | Viele Tutorials auch auf Deutsch verfuegbar. |
| Leichtgewichtig | Kleinere Apps, schnellere Ladezeiten. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Kleinere Community | Weniger fertige Komponenten als bei React. Manchmal musst du selbst bauen. |
| Weniger Jobs/Entwickler | Wenn du spaeter jemanden suchst, gibt es weniger Vue-Entwickler als React-Entwickler. |
| Ein-Mann-Projekt Ursprung | Wurde von einer Person gestartet. Mittlerweile grosses Team, aber manche Firmen sind skeptisch. |

---

### Option C: Svelte

```
Entwickelt von: Rich Harris (2016)
Verbreitung:    Newcomer, ~5% aber stark wachsend
Beispiele:      NY Times (Grafiken), Apple (Teile)
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Sehr schnell | Svelte "kompiliert" den Code vorab. Das Ergebnis ist schneller als React/Vue. |
| Weniger Code | Du schreibst weniger Code fuer das gleiche Ergebnis. Weniger Code = weniger Fehler. |
| Einfach zu lernen | Liest sich fast wie normales HTML. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Kleine Community | Noch weniger Ressourcen als Vue. Bei Problemen findest du schwerer Hilfe. |
| Wenige Entwickler | Fast unmoeglich jemanden zu finden der Svelte kann. |
| Unreif | Noch jung, manche Features fehlen, kann sich stark aendern. |

---

### Empfehlung Frontend

```
┌─────────────────────────────────────────────────────────────────┐
│  EMPFEHLUNG: React                                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  WARUM:                                                         │
│                                                                 │
│  1. Zukunftssicherheit                                          │
│     → React wird nicht verschwinden. Du investierst in          │
│       etwas das in 10 Jahren noch existiert.                    │
│                                                                 │
│  2. Auftragsmanagement bereits in React                         │
│     → Du hast schon ein React-Projekt. Gleiche Technologie      │
│       = Code kann wiederverwendet werden.                       │
│                                                                 │
│  3. KI-Unterstuetzung                                           │
│     → Claude, ChatGPT etc. koennen React-Code sehr gut          │
│       generieren weil es so verbreitet ist.                     │
│                                                                 │
│  4. Fertige Komponenten                                         │
│     → Fuer alles was du brauchst (Tabellen, Kalender,           │
│       Formulare) gibt es fertige Bausteine.                     │
│                                                                 │
│  KONKRET NUTZEN:                                                │
│  - React 18+ (aktuelle Version)                                 │
│  - Next.js (React-Framework, macht vieles einfacher)            │
│  - Tailwind CSS (fuer das Styling/Design)                       │
│  - shadcn/ui (fertige, schoene Komponenten)                     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 2. Backend-Framework

> **Was ist das?** Das Backend ist der "unsichtbare" Teil. Es verarbeitet Daten, speichert sie in der Datenbank, kommuniziert mit anderen Systemen (W4A, E-Mail, KI). Der Benutzer sieht das Backend nie direkt.

### Option A: Node.js (JavaScript/TypeScript)

```
Entwickelt von: Ryan Dahl (2009)
Verbreitung:    Sehr hoch, besonders bei Startups
Beispiele:      Netflix, PayPal, LinkedIn, Uber
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Gleiche Sprache wie Frontend | Wenn du React nutzt (JavaScript), ist das Backend auch JavaScript. Du musst nur EINE Sprache lernen. |
| Sehr schnell bei vielen gleichzeitigen Anfragen | Node.js kann tausende Anfragen gleichzeitig verarbeiten. Gut fuer Echtzeit-Features (GPS-Tracking). |
| NPM Paketmanager | Ueber 2 Millionen fertige Pakete. Brauchst du PDF-Generierung? E-Mail-Versand? Es gibt ein Paket dafuer. |
| Schnelle Entwicklung | Man kommt schnell zu Ergebnissen. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Nicht ideal fuer CPU-intensive Aufgaben | Wenn du schwere Berechnungen machst (Bild-Analyse, grosse Datenmengen), ist Node.js langsamer als andere. |
| "Callback Hell" | Aelterer Node.js-Code kann sehr unuebersichtlich werden. Mit modernem Code (async/await) aber kein Problem mehr. |
| Qualitaet der Pakete schwankt | Manche NPM-Pakete sind schlecht gepflegt. Man muss aufpassen was man nutzt. |

---

### Option B: Python (FastAPI/Django)

```
Entwickelt von: Guido van Rossum (1991)
Verbreitung:    Hoch, besonders bei KI/Data Science
Beispiele:      Instagram, Spotify, Dropbox
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Beste KI-Integration | ALLE KI-Bibliotheken sind in Python. Wenn du KI lokal laufen lassen willst, fuehrt kein Weg an Python vorbei. |
| Lesbare Syntax | Python-Code liest sich fast wie Englisch. Sehr anfaengerfreundlich. |
| Wissenschaftliche Bibliotheken | Datenanalyse, Machine Learning, Statistik - alles in Python verfuegbar. |
| Django = "Batterien inklusive" | Django bringt ALLES mit: Admin-Oberflaeche, Benutzerverwaltung, Datenbank-Anbindung. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Langsamer als Node.js | Bei vielen gleichzeitigen Anfragen ist Python langsamer. Fuer eure Groesse aber irrelevant. |
| Zwei Sprachen noetig | Frontend = JavaScript, Backend = Python. Du musst zwei Sprachen lernen. |
| Deployment komplexer | Python-Apps zu installieren ist etwas aufwaendiger als Node.js. |

---

### Option C: .NET (C#)

```
Entwickelt von: Microsoft (2002)
Verbreitung:    Hoch in Unternehmen/Konzernen
Beispiele:      Stack Overflow, Intuit
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Enterprise-tauglich | Sehr robust, skalierbar, wird von Konzernen genutzt. |
| Gute Microsoft-Integration | Wenn du viel mit Windows/Office/Azure arbeitest, passt .NET gut. |
| Typsicherheit | Viele Fehler werden schon beim Programmieren erkannt, nicht erst wenn die App laeuft. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Hohe Komplexitaet | .NET ist maechtig, aber auch komplex. Viel Einarbeitung noetig. |
| Weniger Community-Pakete | Weniger fertige Loesungen als bei Node.js oder Python. |
| Weniger KI-freundlich | KI-Assistenten koennen Node.js/Python-Code besser generieren. |

---

### Empfehlung Backend

```
┌─────────────────────────────────────────────────────────────────┐
│  EMPFEHLUNG: Node.js + Python Hybrid                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  WARUM HYBRID (zwei Systeme)?                                   │
│                                                                 │
│  Node.js fuer:                                                  │
│  ├── API-Server (Schnittstelle zwischen Frontend und Daten)     │
│  ├── Echtzeit-Features (GPS-Tracking, Live-Status)              │
│  ├── Schnelle Anfragen (Dashboard, Listen, Formulare)           │
│  └── Gleiche Sprache wie Frontend = einfacher                   │
│                                                                 │
│  Python fuer:                                                   │
│  ├── KI-Aufgaben (Bild-Analyse, Sprache-zu-Text)                │
│  ├── PDF-Analyse (Lieferscheine, Rechnungen auslesen)           │
│  ├── E-Mail-Klassifizierung (NLP = Natural Language Processing) │
│  └── Daten-Analyse (Reports, Statistiken)                       │
│                                                                 │
│  WIE KOMMUNIZIEREN DIE BEIDEN?                                  │
│                                                                 │
│  ┌──────────┐    API-Call    ┌──────────┐                       │
│  │ Node.js  │ ─────────────► │  Python  │                       │
│  │ (Haupt-  │ ◄───────────── │  (KI-    │                       │
│  │  server) │    Ergebnis    │  Worker) │                       │
│  └──────────┘                └──────────┘                       │
│                                                                 │
│  Beispiel: Monteur laedt Foto hoch                              │
│  1. Node.js empfaengt Foto                                      │
│  2. Node.js schickt Foto an Python-Service                      │
│  3. Python analysiert Foto mit KI ("Das ist ein Fenstergriff")  │
│  4. Python schickt Ergebnis zurueck                             │
│  5. Node.js zeigt Ergebnis dem Monteur                          │
│                                                                 │
│  KONKRET NUTZEN:                                                │
│  - Node.js: Express.js oder Fastify                             │
│  - Python: FastAPI (modern, schnell, gut dokumentiert)          │
│  - TypeScript fuer beide (weniger Fehler)                       │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 3. Datenbank

> **Was ist das?** Die Datenbank speichert alle Daten dauerhaft: Kunden, Projekte, Rechnungen, etc. Ohne Datenbank wuerde alles bei einem Neustart verschwinden.

### Option A: PostgreSQL

```
Typ:            Relationale Datenbank (Tabellen mit Beziehungen)
Entwickelt:     1996, Open Source
Verbreitung:    Sehr hoch, "die" Open-Source-Datenbank
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Kostenlos | Komplett Open Source, keine Lizenzkosten - egal wie gross du wirst. |
| Extrem zuverlaessig | Deine Daten sind sicher. PostgreSQL ist bekannt fuer Stabilitaet. |
| Unterstuetzt JSON | Du kannst strukturierte UND flexible Daten speichern. Das Beste aus beiden Welten. |
| Volle SQL-Unterstuetzung | SQL ist DIE Sprache fuer Datenbanken. PostgreSQL kann alles was SQL bietet. |
| Erweiterbar | Braucht du Volltextsuche? Geodaten? Es gibt Erweiterungen dafuer. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Muss selbst betrieben werden | Du brauchst einen Server der laeuft. Bei Cloud-Hostern aber kein Problem (die uebernehmen das). |
| Schema-Aenderungen aufwaendig | Wenn du spaeter die Tabellenstruktur aendern willst, ist das mehr Aufwand als bei MongoDB. |

---

### Option B: MySQL/MariaDB

```
Typ:            Relationale Datenbank
Entwickelt:     1995 (MySQL), 2009 (MariaDB Fork)
Verbreitung:    Sehr hoch, besonders bei Webhosting
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Weit verbreitet | Fast jeder Webhoster bietet MySQL. |
| Einfach zu starten | Viele Tutorials, leichter Einstieg. |
| W4A nutzt MS SQL | Aehnliches Konzept, Wissen ist uebertragbar. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Weniger Features als PostgreSQL | Bei komplexen Abfragen ist PostgreSQL besser. |
| Oracle-Abhaengigkeit (MySQL) | MySQL gehoert Oracle. Manche haben Bedenken wegen Lizenz-Zukunft. MariaDB ist die freie Alternative. |

---

### Option C: MongoDB

```
Typ:            Dokumenten-Datenbank (NoSQL)
Entwickelt:     2009
Verbreitung:    Hoch bei Startups, weniger bei Unternehmen
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Flexible Struktur | Du musst nicht vorab definieren wie deine Daten aussehen. Gut wenn sich Anforderungen oft aendern. |
| Skaliert horizontal | Wenn du SEHR viele Daten hast, kannst du einfach mehr Server hinzufuegen. |
| JSON-nativ | Daten werden so gespeichert wie JavaScript sie nutzt. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Keine echten Beziehungen | "Kunde hat Projekte hat Rechnungen" ist schwerer abzubilden. |
| Daten-Integritaet | Die Datenbank prueft nicht ob deine Daten "stimmen". Du musst selbst aufpassen. |
| Nicht ideal fuer ERP | ERP-Systeme haben viele Beziehungen. MongoDB ist dafuer weniger geeignet. |

---

### Empfehlung Datenbank

```
┌─────────────────────────────────────────────────────────────────┐
│  EMPFEHLUNG: PostgreSQL                                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  WARUM:                                                         │
│                                                                 │
│  1. Perfekt fuer ERP-Daten                                      │
│     → Kunden, Projekte, Positionen, Rechnungen - alles hat      │
│       Beziehungen zueinander. PostgreSQL kann das perfekt.      │
│                                                                 │
│  2. Kostenlos fuer immer                                        │
│     → Keine Lizenzkosten, egal wie gross du wirst.              │
│       W4A kostet pro User - PostgreSQL nie.                     │
│                                                                 │
│  3. JSON fuer flexible Daten                                    │
│     → Die "rules" und "change_observations" aus deinem          │
│       Datenmodell koennen als JSON gespeichert werden.          │
│       Flexibel UND strukturiert.                                │
│                                                                 │
│  4. Zukunftssicher                                              │
│     → PostgreSQL existiert seit 1996 und wird immer besser.     │
│       Viele grosse Firmen setzen darauf.                        │
│                                                                 │
│  5. Gute KI-Unterstuetzung                                      │
│     → Es gibt pgvector fuer KI-Embeddings. Wenn du spaeter      │
│       semantische Suche willst ("finde aehnliche Projekte"),    │
│       ist das schon eingebaut.                                  │
│                                                                 │
│  KONKRET:                                                       │
│  - PostgreSQL 16 (aktuelle Version)                             │
│  - Prisma als ORM (macht Datenbankzugriff einfacher)            │
│  - pgAdmin fuer Verwaltung (grafische Oberflaeche)              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 4. Hosting (Wo laeuft das System?)

> **Was ist das?** Dein System braucht Computer auf denen es laeuft. Die Frage ist: Eigene Server bei euch (On-Premise), gemietete Server im Internet (Cloud), oder eine Mischung?

### Option A: Cloud (z.B. Hetzner, AWS, Azure)

```
Was bedeutet das?  Server werden gemietet, stehen beim Anbieter
Bezahlung:         Monatlich nach Verbrauch
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Kein Hardware-Kauf | Du kaufst keine Server, du mietest Rechenleistung. Weniger Anfangsinvestition. |
| Skalierbar | Brauchst du mehr Power? Ein Klick. Brauchst du weniger? Runterskalieren. |
| Backup/Sicherheit inklusive | Cloud-Anbieter machen automatische Backups, haben Brandschutz, Notstrom, etc. |
| Von ueberall erreichbar | Monteure koennen von ueberall zugreifen (wichtig fuer Mobile-App!). |
| Wartung beim Anbieter | Der Anbieter kuemmert sich um Hardware-Updates, Sicherheitspatches, etc. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Laufende Kosten | Du zahlst jeden Monat. Bei langer Nutzung teurer als eigene Hardware. |
| Abhaengigkeit | Wenn der Anbieter Probleme hat, hast du Probleme. |
| Datenschutz-Bedenken | Daten liegen "woanders". Bei deutschem Anbieter (Hetzner) aber kein Problem. |
| Internet-Abhaengigkeit | Ohne Internet kein Zugriff (aber: das ist heute normal). |

---

### Option B: On-Premise (eigene Server)

```
Was bedeutet das?  Server stehen bei euch in der Firma
Bezahlung:         Einmalig Hardware-Kauf + Strom/Wartung
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Volle Kontrolle | Deine Daten liegen bei dir. Du entscheidest alles. |
| Keine laufenden Mietkosten | Nach dem Kauf nur noch Strom und Wartung. |
| Schnell im lokalen Netz | Im Buero ist der Zugriff blitzschnell. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Hohe Anfangskosten | Server kaufen kostet mehrere Tausend Euro. |
| Wartung selbst machen | Updates, Backups, Hardware-Tausch - dein Problem. |
| Von aussen erreichbar machen ist komplex | Damit Monteure draussen zugreifen koennen, brauchst du VPN, Firewall, etc. |
| Kein Schutz vor Feuer/Einbruch | Brennt die Firma, sind die Daten weg (ausser du hast externes Backup). |

---

### Option C: Hybrid

```
Was bedeutet das?  Beides kombiniert - Hauptsystem in Cloud,
                   lokaler Cache/Sync fuer schnellen Zugriff
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Beste aus beiden Welten | Cloud fuer Erreichbarkeit, lokal fuer Geschwindigkeit. |
| Ausfallsicherheit | Wenn Cloud kurz weg ist, funktioniert lokal noch. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Komplexer zu bauen | Zwei Systeme die synchron bleiben muessen. Mehr Aufwand. |
| Mehr Fehlerquellen | Sync-Konflikte moeglich. |

---

### Hosting-Vergleich: Cloud vs. Eigener Server

#### Option A: Cloud (Hetzner)

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Immer erreichbar | 99,9% Uptime garantiert. Monteure haben immer Zugriff. |
| Professionelle Backups | Taegliche Backups, Disaster Recovery inklusive. |
| Kein Hardware-Risiko | Festplatte kaputt? Hetzners Problem, nicht deins. |
| Skalierbar | Brauchst mehr Power? Ein Klick. |
| Weniger Wartung | Betriebssystem-Updates, Sicherheitspatches - Hetzner kuemmert sich. |
| Brandschutz/Einbruch | Rechenzentrum hat Sicherheit die du nie hast. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Laufende Kosten | ~60-100€/Monat dauerhaft. |
| Daten extern | Firmendaten liegen bei Hetzner (aber: deutscher Anbieter, DSGVO ok). |
| Internet-Abhaengigkeit | Ohne Internet kein Zugriff (aber: ist heute normal). |

**Kosten Cloud:**
| Posten | Monatlich |
|--------|-----------|
| Hetzner CPX31 (4 vCPU, 8 GB RAM) | 15€ |
| Hetzner CPX41 (8 vCPU, 16 GB RAM) | 30€ |
| Managed PostgreSQL (optional) | 20€ |
| Backups | 5-10€ |
| **Gesamt** | **40-60€** |

---

#### Option B: Eigener Server (On-Premise)

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Keine laufenden Kosten | Nach Hardware-Kauf nur Strom (~10-20€/Monat). |
| Volle Kontrolle | Deine Daten, dein Server, deine Regeln. |
| Bestehendes Setup | Hyper-V Host existiert, VMs laufen schon. |
| Schnell im lokalen Netz | Im Buero blitzschnelle Ladezeiten. |
| W4A-Naehe | Direkter Zugriff auf W4A-Datenbank fuer Historie. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Externe Erreichbarkeit | Cloudflare Tunnel noetig fuer Monteure. Funktioniert, aber zusaetzliche Komplexitaet. |
| Backup-Verantwortung | Du musst selbst fuer Backups sorgen (externes NAS, Cloud-Backup). |
| Hardware-Risiko | Festplatte/Server kaputt = dein Problem. Ersatzteile, Downtime. |
| Wartungsaufwand | Updates, Sicherheit, Monitoring - alles selbst. |
| Kein Brandschutz | Brennt die Firma, sind Daten weg (ausser externes Backup). |
| Single Point of Failure | Ein Server, keine Redundanz. |

**Kosten On-Premise:**
| Posten | Einmalig | Monatlich |
|--------|----------|-----------|
| Neuer Server (falls noetig) | 1.500-3.000€ | - |
| Externe Backup-Loesung | 200-500€ | 10-30€ |
| Strom | - | 15-25€ |
| Cloudflare Tunnel | 0€ | 0€ |
| **Gesamt** | **~2.000€** | **~30-50€** |

---

#### Option C: Hybrid (EMPFOHLEN)

```
┌─────────────────────────────────────────────────────────────────┐
│  EMPFEHLUNG: Hybrid-Ansatz                                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌─────────────────────┐      ┌─────────────────────┐           │
│  │   EIGENER SERVER    │      │   CLOUD (Hetzner)   │           │
│  │   (On-Premise)      │      │                     │           │
│  ├─────────────────────┤      ├─────────────────────┤           │
│  │                     │      │                     │           │
│  │  • W4A (Altdaten)   │      │  • Neues ERP-System │           │
│  │  • Historien-DB     │      │  • PostgreSQL (neu) │           │
│  │  • Dokumente/PDFs   │      │  • Frontend (Next)  │           │
│  │  • Lokale Backups   │      │  • API-Server       │           │
│  │                     │      │  • KI-Worker        │           │
│  │                     │      │                     │           │
│  └─────────┬───────────┘      └──────────┬──────────┘           │
│            │                             │                      │
│            │    Cloudflare Tunnel        │                      │
│            └─────────────────────────────┘                      │
│                                                                 │
│  WARUM HYBRID:                                                  │
│                                                                 │
│  1. Neues System in der Cloud                                   │
│     → Immer erreichbar fuer Monteure                            │
│     → Professionelle Backups                                    │
│     → Kein Hardware-Risiko                                      │
│                                                                 │
│  2. Historische Daten lokal                                     │
│     → W4A laeuft weiter fuer Archiv-Zugriff                     │
│     → Dokumente bleiben auf Server                              │
│     → Kein teurer Daten-Transfer in die Cloud                   │
│                                                                 │
│  3. Verbindung ueber Cloudflare Tunnel                          │
│     → Cloud-System kann bei Bedarf auf Historie zugreifen       │
│     → Sicher, verschluesselt, kein VPN noetig                   │
│                                                                 │
│  KOSTEN HYBRID:                                                 │
│  - Cloud (neues System): ~40-60€/Monat                          │
│  - Lokal (existiert schon): ~20€/Monat Strom                    │
│  - Gesamt: ~60-80€/Monat                                        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### Entscheidungshilfe Hosting

| Kriterium | Cloud | On-Premise | Hybrid |
|-----------|-------|------------|--------|
| Monteur-Zugriff | ⭐⭐⭐ Perfekt | ⭐⭐ Mit Tunnel | ⭐⭐⭐ Perfekt |
| Historien-Zugriff | ⭐ Muss migrieren | ⭐⭐⭐ Direkt | ⭐⭐⭐ Direkt |
| Backup-Sicherheit | ⭐⭐⭐ Profi | ⭐ Selbst | ⭐⭐⭐ Beides |
| Laufende Kosten | ⭐⭐ 60-100€ | ⭐⭐⭐ 30-50€ | ⭐⭐ 60-80€ |
| Wartungsaufwand | ⭐⭐⭐ Minimal | ⭐ Hoch | ⭐⭐ Mittel |
| Ausfallsicherheit | ⭐⭐⭐ Hoch | ⭐ Niedrig | ⭐⭐ Mittel |
| **GESAMT** | ⭐⭐ | ⭐⭐ | ⭐⭐⭐ |

---

## 5. KI-Integration

> **Was ist das?** KI-Features wie Bild-Erkennung, Sprache-zu-Text, E-Mail-Klassifizierung - das sind die "intelligenten" Teile. Die Frage ist: Nutzt du fertige Dienste (API) oder laesst du KI selbst laufen?

### Option A: Nur Cloud-API (OpenAI, Anthropic, Google)

```
Was bedeutet das?  Du schickst Daten an einen KI-Anbieter,
                   der schickt das Ergebnis zurueck
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Sofort einsatzbereit | Account erstellen, API-Key holen, los geht's. |
| Beste Qualitaet | GPT-4, Claude - das sind die besten Modelle die es gibt. |
| Keine eigene Hardware | Du brauchst keine teuren GPUs. |
| Immer aktuell | Die Anbieter verbessern ihre Modelle staendig. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Kosten pro Anfrage | Jede Anfrage kostet Geld. Bei vielen Anfragen summiert sich das. |
| Daten verlassen dein System | Kundendaten gehen zu OpenAI/Anthropic. Datenschutz-Bedenken moeglich. |
| Abhaengigkeit | Wenn OpenAI die Preise erhoeht oder den Dienst aendert, bist du betroffen. |
| Latenz | Anfrage geht uebers Internet, Antwort kommt zurueck. Dauert 1-5 Sekunden. |

---

### Option B: Nur lokal (Ollama, llama.cpp)

```
Was bedeutet das?  KI-Modelle laufen auf deinem eigenen Server
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Keine laufenden KI-Kosten | Nach Hardware-Kauf ist jede Anfrage "kostenlos". |
| Daten bleiben bei dir | Nichts verlaesst deinen Server. Perfekter Datenschutz. |
| Keine Abhaengigkeit | Du bist unabhaengig von Anbietern. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Schlechtere Qualitaet | Lokale Modelle sind (noch) nicht so gut wie GPT-4/Claude. |
| Hohe Hardware-Kosten | Eine gute GPU kostet 1.000-3.000€. Fuer grosse Modelle noch mehr. |
| Wartungsaufwand | Du musst Modelle selbst updaten, Probleme selbst loesen. |
| Langsamer ohne teure GPU | Ohne gute Grafikkarte sind lokale Modelle sehr langsam. |

---

### Option C: Hybrid (empfohlen)

```
Was bedeutet das?  Einfache Aufgaben lokal, komplexe via API
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Kosten-Optimierung | Haeufige, einfache Aufgaben lokal (kostenlos). Komplexe Aufgaben via API (beste Qualitaet). |
| Datenschutz wo noetig | Sensible Daten bleiben lokal, nur "unkritische" gehen zur API. |
| Flexibilitaet | Du kannst je nach Aufgabe entscheiden. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Mehr Komplexitaet | Du musst entscheiden wann welches Modell. |
| Zwei Systeme warten | Lokale Modelle UND API-Integration pflegen. |

---

### Empfehlung KI-Integration

```
┌─────────────────────────────────────────────────────────────────┐
│  EMPFEHLUNG: Hybrid - Start mit API, spaeter lokal ergaenzen    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  PHASE 1 (JETZT): Nur Cloud-API                                 │
│  ─────────────────────────────────────────────                  │
│  - Claude API (Anthropic) fuer Text-Aufgaben                    │
│    → E-Mail-Klassifizierung, Antwort-Generierung                │
│  - OpenAI Whisper API fuer Sprache-zu-Text                      │
│    → Telefon-Transkription                                      │
│  - Claude/GPT-4 Vision fuer Bild-Analyse                        │
│    → Ersatzteil-Erkennung                                       │
│  - OpenAI/Voyage Embeddings fuer Vektorsuche                    │
│    → Semantische Suche, aehnliche Projekte                      │
│                                                                 │
│  WARUM JETZT NUR API:                                           │
│  - Schneller Start (sofort nutzbar)                             │
│  - Beste Qualitaet (fuer den Anfang wichtig!)                   │
│  - Keine Hardware-Investition                                   │
│  - Kosten bei eurem Volumen ueberschaubar:                      │
│    ~50-150€/Monat geschaetzt                                    │
│                                                                 │
│  PHASE 2 (SPAETER): Lokal ergaenzen                             │
│  ─────────────────────────────────────────────                  │
│  Wenn das System laeuft und du siehst welche                    │
│  KI-Aufgaben am haeufigsten sind:                               │
│                                                                 │
│  - Whisper lokal (Sprache-zu-Text)                              │
│    → Ollama oder whisper.cpp auf GPU-Server                     │
│  - Llama 3 lokal (einfache Klassifizierung)                     │
│    → E-Mail: "Anfrage oder Rechnung?"                           │
│  - LLaVA lokal (Bild-Beschreibung)                              │
│    → "Was ist auf diesem Foto?"                                 │
│  - Lokale Embeddings (nomic-embed, bge-m3)                      │
│    → Kostenlos, schnell, datenschutzkonform                     │
│                                                                 │
│  FAZIT:                                                         │
│  Erst beweisen dass die Features funktionieren (API),           │
│  dann optimieren (lokal) wo es sich lohnt.                      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Embeddings & Vektorsuche (Moderne KI-Technik)

> **Was sind Embeddings?** Eine Technik um Text, Bilder oder andere Daten in Zahlen (Vektoren) umzuwandeln. Aehnliche Dinge haben aehnliche Zahlen. Damit kann man "Aehnlichkeit" berechnen - nicht nur exakte Treffer finden.

### Warum Embeddings wichtig sind

```
KLASSISCHE SUCHE (Keyword):
─────────────────────────
Suche: "Fenster klemmt"
→ Findet NUR Dokumente mit genau diesen Woertern
→ Findet NICHT: "Fluegel laesst sich schwer oeffnen"
→ Findet NICHT: "Beschlag defekt"

SEMANTISCHE SUCHE (Embeddings):
────────────────────────────────
Suche: "Fenster klemmt"
→ Findet: "Fluegel laesst sich schwer oeffnen" (aehnliche Bedeutung!)
→ Findet: "Beschlag schwergaengig" (aehnliches Problem!)
→ Findet: "Fenstergriff blockiert" (verwandtes Thema!)

WARUM? Embeddings verstehen BEDEUTUNG, nicht nur Woerter.
```

---

### Anwendungsfaelle im W4A-Ersatz

#### 1. Aehnliche Projekte finden (Budget-Angebot)

```
HEUTE (ohne Embeddings):
Kunde: "Ich brauche neue Fenster, Altbau 1920er"

System sucht: WHERE beschreibung LIKE '%Fenster%' AND beschreibung LIKE '%Altbau%'
→ Findet nur exakte Matches
→ Verpasst: "Sanierung Gruenderzeit", "Denkmalschutz", "historisches Gebaeude"

MIT EMBEDDINGS:
System wandelt "neue Fenster, Altbau 1920er" in Vektor um
→ Sucht aehnliche Vektoren in history.projects
→ Findet ALLE semantisch aehnlichen Projekte:
  - "Fenstertausch Jugendstil-Villa" (95% aehnlich)
  - "Sanierung Denkmalschutz Amberg" (92% aehnlich)
  - "Fenster Altbau mit Stuck" (89% aehnlich)

→ Budget-Angebot basiert auf WIRKLICH vergleichbaren Projekten!
```

#### 2. Ersatzteil-Erkennung (Reparatur)

```
SZENARIO: Monteur macht Foto von defektem Beschlag

1. Bild → Embedding (Vision-Modell)
2. Vergleich mit Datenbank bekannter Ersatzteile
3. "Das sieht aus wie Siegenia Titan AF (87% Match)"

ODER: Monteur beschreibt verbal:
"Der Griff ist so ein silberner, der nach unten geht"
→ Embedding findet: Winkhaus Olive, Hoppe SecuSelect, etc.
```

#### 3. E-Mail-Klassifizierung (Intelligenter)

```
HEUTE (Regel-basiert):
IF betreff CONTAINS "Rechnung" → Kategorie: Rechnung
IF betreff CONTAINS "Angebot" → Kategorie: Anfrage
→ Was ist mit "RE: Ihre Nachricht vom..."? Unklar!

MIT EMBEDDINGS:
E-Mail-Text → Embedding
Vergleich mit Beispiel-Embeddings pro Kategorie:
→ "Diese E-Mail ist zu 94% eine Reklamation"
→ "Diese E-Mail ist zu 78% eine Anfrage"
→ Automatische Zuordnung auch bei unklarem Betreff!
```

#### 4. Kunden-Duplikate erkennen

```
PROBLEM: Gleicher Kunde, verschiedene Schreibweisen
- "Müller, Hans" vs "Hans Mueller" vs "H. Müller"
- "Hauptstr. 5" vs "Hauptstraße 5" vs "Hauptstrasse 5"

MIT EMBEDDINGS:
Alle Kundendaten → Embeddings
System erkennt: "Diese 3 Eintraege sind wahrscheinlich die gleiche Person"
→ Vorschlag zur Zusammenfuehrung
```

#### 5. Intelligente Dokumentensuche

```
SUCHE: "Was haben wir letztes Jahr bei der Lebenshilfe gemacht?"

MIT EMBEDDINGS durchsucht das System:
- Projekt-Beschreibungen
- E-Mails
- Angebote
- Montage-Berichte
- Rechnungen

→ Findet ALLES was mit "Lebenshilfe" zusammenhaengt
→ Auch wenn "Lebenshilfe" nicht woertlich vorkommt
   (z.B. "Behinderteneinrichtung Jahnstrasse")
```

#### 6. RAG (Retrieval Augmented Generation)

```
WAS IST RAG?
Ein KI-Assistent der auf EURE Daten zugreifen kann.

BEISPIEL:
User: "Was ist unser Standard-Rabatt fuer Weru-Fenster?"

OHNE RAG:
KI: "Das kann ich nicht wissen, ich habe keinen Zugriff auf Ihre Daten."

MIT RAG:
1. Frage → Embedding
2. Suche in euren Dokumenten/Daten nach relevanten Infos
3. Gefunden: Kalkulationsrichtlinien, alte Angebote, Preislisten
4. KI beantwortet MIT KONTEXT:
   "Basierend auf euren Angeboten der letzten 12 Monate:
    - Standard-Rabatt: 8-12%
    - Grosskunden: bis 18%
    - Neukundenaktionen: teilweise 15%"
```

---

### Technische Umsetzung

#### Vektor-Datenbank: pgvector (PostgreSQL Extension)

```
WARUM PGVECTOR:
✅ Laeuft in PostgreSQL (keine extra Datenbank!)
✅ Kostenlos / Open Source
✅ SQL-kompatibel (normale Queries + Vektorsuche kombiniert)
✅ Gut fuer eure Groesse (bis ~1 Million Vektoren problemlos)

ALTERNATIVEN (nicht noetig fuer euch):
- Pinecone (Cloud, teuer)
- Weaviate (komplex)
- Milvus (fuer riesige Datenmengen)
→ pgvector reicht voellig!
```

#### Schema-Erweiterung fuer Embeddings

```sql
-- pgvector Extension aktivieren
CREATE EXTENSION IF NOT EXISTS vector;

-- Embeddings-Tabelle fuer Projekte
CREATE TABLE project_embeddings (
    id SERIAL PRIMARY KEY,
    project_id INTEGER REFERENCES projects(id),
    content TEXT,                    -- Der Text der embedded wurde
    embedding vector(1536),          -- OpenAI: 1536 Dimensionen
    model VARCHAR(50),               -- z.B. "text-embedding-3-small"
    created_at TIMESTAMP DEFAULT NOW()
);

-- Index fuer schnelle Vektorsuche
CREATE INDEX idx_project_embedding ON project_embeddings
USING ivfflat (embedding vector_cosine_ops) WITH (lists = 100);

-- Embeddings fuer Positionen (Artikel-Beschreibungen)
CREATE TABLE position_embeddings (
    id SERIAL PRIMARY KEY,
    position_id INTEGER,
    description TEXT,
    embedding vector(1536),
    source VARCHAR(20)               -- 'history' oder 'current'
);

-- Embeddings fuer Dokumente (E-Mails, PDFs, etc.)
CREATE TABLE document_embeddings (
    id SERIAL PRIMARY KEY,
    document_id INTEGER,
    document_type VARCHAR(50),       -- 'email', 'offer_pdf', 'manual'
    chunk_text TEXT,                 -- Text-Abschnitt (Chunking!)
    embedding vector(1536),
    metadata JSONB                   -- Zusatz-Infos
);
```

#### Beispiel-Query: Aehnliche Projekte finden

```sql
-- 1. Zuerst: Embedding fuer Suchanfrage generieren (via API)
-- Python: embedding = openai.embed("Fenster Altbau Sanierung")

-- 2. Dann: Aehnliche Projekte in PostgreSQL suchen
SELECT
    p.project_number,
    p.name,
    p.customer_name,
    1 - (pe.embedding <=> '[0.023, -0.041, ...]'::vector) as similarity
FROM project_embeddings pe
JOIN projects p ON p.id = pe.project_id
WHERE 1 - (pe.embedding <=> '[...]'::vector) > 0.7  -- Mindest-Aehnlichkeit 70%
ORDER BY pe.embedding <=> '[...]'::vector
LIMIT 10;

-- Operator <=> = Kosinus-Distanz (kleiner = aehnlicher)
-- 1 - Distanz = Similarity Score (0-1, hoeher = aehnlicher)
```

---

### Embedding-Modelle im Vergleich

| Modell | Anbieter | Dimensionen | Kosten | Qualitaet | Empfehlung |
|--------|----------|-------------|--------|-----------|------------|
| **text-embedding-3-small** | OpenAI | 1536 | ~0,02$/1M Token | Sehr gut | ⭐ Bestes P/L |
| **text-embedding-3-large** | OpenAI | 3072 | ~0,13$/1M Token | Exzellent | Fuer kritische Suchen |
| **voyage-3** | Voyage AI | 1024 | ~0,06$/1M Token | Exzellent | Alternative |
| **nomic-embed-text** | Lokal | 768 | Kostenlos | Gut | ⭐ Spaeter lokal |
| **bge-m3** | Lokal | 1024 | Kostenlos | Sehr gut | Multilingual |

**Empfehlung:**
- **Start:** OpenAI `text-embedding-3-small` (guenstig, einfach, gut)
- **Spaeter:** Lokal mit `nomic-embed-text` oder `bge-m3` (kostenlos, Datenschutz)

---

### Kosten-Schaetzung Embeddings

```
EINMALIGES EMBEDDING (Historische Daten):
─────────────────────────────────────────
~120.000 Positionen × ~100 Tokens = 12 Mio Tokens
~2.500 Projekte × ~200 Tokens = 0,5 Mio Tokens
~5.000 E-Mails × ~500 Tokens = 2,5 Mio Tokens
────────────────────────────────────────────────
GESAMT: ~15 Mio Tokens
KOSTEN: 15 × 0,02$ = ~0,30$ (einmalig!)

LAUFENDE EMBEDDINGS (Neue Daten):
─────────────────────────────────
~50 neue Projekte/Monat × 200 Tokens = 10.000 Tokens
~200 E-Mails/Monat × 500 Tokens = 100.000 Tokens
~500 Positionen/Monat × 100 Tokens = 50.000 Tokens
────────────────────────────────────────────────────
GESAMT: ~160.000 Tokens/Monat
KOSTEN: ~0,003$/Monat (praktisch kostenlos!)
```

---

### Chunking-Strategie (fuer lange Dokumente)

```
PROBLEM: Ein Embedding kann nur begrenzt viel Text erfassen
         (meist 8.000-8.192 Tokens Maximum)

LOESUNG: Lange Dokumente in Chunks aufteilen

BEISPIEL E-Mail mit Anhang:
┌─────────────────────────────────────────┐
│ E-Mail (2.000 Zeichen)                  │
│ + PDF-Anhang (50.000 Zeichen)           │
└─────────────────────────────────────────┘
                    ↓
┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐
│ Chunk 1  │ │ Chunk 2  │ │ Chunk 3  │ │ Chunk 4  │
│ E-Mail   │ │ PDF S.1-2│ │ PDF S.3-4│ │ PDF S.5-6│
│ Header   │ │          │ │          │ │          │
└──────────┘ └──────────┘ └──────────┘ └──────────┘
     ↓            ↓            ↓            ↓
  Embedding   Embedding   Embedding   Embedding

SUCHE findet den relevanten Chunk!
```

---

### Zusammenfassung Embeddings

| Aspekt | Entscheidung |
|--------|--------------|
| **Vektor-DB** | pgvector (in PostgreSQL integriert) |
| **Embedding-Modell Start** | OpenAI text-embedding-3-small |
| **Embedding-Modell Spaeter** | Lokal (nomic-embed / bge-m3) |
| **Was wird embedded** | Projekte, Positionen, E-Mails, Dokumente |
| **Einmalige Kosten** | ~0,30$ fuer alle historischen Daten |
| **Laufende Kosten** | ~0,003$/Monat (vernachlaessigbar) |
| **Haupt-Anwendungen** | Budget-Angebot, Suche, RAG, Duplikat-Erkennung |

---

## Aktuelle KI-Tools & Frameworks (Stand 2025)

> Basierend auf KI_Wissen.md - die relevantesten Tools fuer W4A-Ersatz

### Empfohlene Tool-Landschaft

```
┌─────────────────────────────────────────────────────────────────┐
│                    W4A-ERSATZ KI-STACK                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  LLM / TEXT-GENERATION                                          │
│  ─────────────────────                                          │
│  Claude Opus 4.5 (Anthropic)                                    │
│  ├── Haupt-LLM fuer komplexe Aufgaben                           │
│  ├── E-Mail-Antworten generieren                                │
│  ├── Dokumente analysieren                                      │
│  └── Budget-Begruendungen formulieren                           │
│                                                                 │
│  Claude Haiku 4.5                                               │
│  ├── Schnelle, guenstige Aufgaben                               │
│  ├── E-Mail-Klassifizierung                                     │
│  └── Einfache Extraktionen                                      │
│                                                                 │
│  ────────────────────────────────────────────────────────────   │
│                                                                 │
│  SPRACHE-ZU-TEXT                                                │
│  ───────────────                                                │
│  OpenAI Whisper API                                             │
│  ├── Telefon-Transkription                                      │
│  └── Sprachnotizen der Monteure                                 │
│                                                                 │
│  ElevenLabs Scribe v2 (Realtime)                                │
│  ├── Echtzeit-Transkription                                     │
│  └── Fuer Live-Telefonate mit KI-Assistent                      │
│                                                                 │
│  ────────────────────────────────────────────────────────────   │
│                                                                 │
│  TEXT-ZU-SPRACHE (TTS)                                          │
│  ─────────────────────                                          │
│  ElevenLabs Eleven v3                                           │
│  ├── Natuerliche Stimme fuer KI-Telefonassistent                │
│  ├── Deutsche Stimmen verfuegbar                                │
│  └── Conversational AI 2.0 fuer Dialoge                         │
│                                                                 │
│  ────────────────────────────────────────────────────────────   │
│                                                                 │
│  DOKUMENT-PARSING                                               │
│  ────────────────                                               │
│  LlamaParse (LlamaIndex)                                        │
│  ├── PDFs intelligent parsen                                    │
│  ├── Lieferscheine, Rechnungen auslesen                         │
│  ├── Tabellen korrekt extrahieren                               │
│  └── Besser als einfaches PDF-to-Text                           │
│                                                                 │
│  ────────────────────────────────────────────────────────────   │
│                                                                 │
│  WORKFLOW-AUTOMATION                                            │
│  ───────────────────                                            │
│  n8n 2.0                                                        │
│  ├── Bereits installiert auf Hetzner!                           │
│  ├── AI-fokussierte Features                                    │
│  ├── E-Mail-Trigger, Webhooks                                   │
│  ├── Datenbank-Verbindungen                                     │
│  └── Kann mit neuem System integriert werden                    │
│                                                                 │
│  ────────────────────────────────────────────────────────────   │
│                                                                 │
│  RAG & AGENTS                                                   │
│  ───────────                                                    │
│  LangChain 0.3+                                                 │
│  ├── RAG-Pipelines bauen                                        │
│  ├── Agent-Orchestrierung                                       │
│  └── Tool-Integration                                           │
│                                                                 │
│  LlamaIndex                                                     │
│  ├── Alternative zu LangChain                                   │
│  ├── Enterprise RAG (LlamaCloud)                                │
│  └── Besseres Dokument-Handling                                 │
│                                                                 │
│  ────────────────────────────────────────────────────────────   │
│                                                                 │
│  TOOL-INTEGRATION                                               │
│  ────────────────                                               │
│  MCP (Model Context Protocol)                                   │
│  ├── Anthropic-Standard fuer Tool-Use                           │
│  ├── Filesystem, Postgres, Puppeteer Integrationen              │
│  ├── Claude kann direkt auf Tools zugreifen                     │
│  └── Google Cloud bietet Managed MCP                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### Tool-Empfehlungen im Detail

#### 1. MCP (Model Context Protocol) - NEU & WICHTIG!

> **Was ist das?** Ein Standard von Anthropic (Nov 2025) der definiert, wie KI-Modelle auf externe Tools zugreifen koennen. Statt Code zu schreiben der "Claude, analysiere diese Datei" macht, sagst du einfach "lies Datei X" und MCP kuemmert sich darum.

```
OHNE MCP:
─────────
1. User fragt: "Was steht in der letzten Rechnung an Mueller?"
2. Dein Code: Datenbank abfragen
3. Dein Code: Ergebnis an Claude schicken
4. Claude: Antwortet

MIT MCP:
────────
1. User fragt: "Was steht in der letzten Rechnung an Mueller?"
2. Claude nutzt direkt MCP-Tool "database_query"
3. Claude: Antwortet mit Ergebnis

→ Weniger Code, mehr Flexibilitaet!
```

**Verfuegbare MCP-Server:**
| Server | Funktion | Nutzen fuer W4A-Ersatz |
|--------|----------|------------------------|
| `@modelcontextprotocol/server-postgres` | PostgreSQL Zugriff | Direkte DB-Abfragen |
| `@modelcontextprotocol/server-filesystem` | Datei-Zugriff | Dokumente lesen/schreiben |
| `@anthropics/mcp-puppeteer` | Browser-Automation | Lieferanten-Portale automatisieren |
| `@modelcontextprotocol/server-brave-search` | Web-Suche | Ersatzteil-Recherche |

**Beispiel: KI-Assistent mit MCP**
```
USER: "Schick Mueller eine Erinnerung fuer die offene Rechnung"

CLAUDE MIT MCP:
1. [database] SELECT * FROM invoices WHERE customer='Mueller' AND paid=false
2. [database] SELECT email FROM customers WHERE name='Mueller'
3. [email] Sendet Erinnerungs-E-Mail
4. [database] UPDATE invoices SET reminder_sent=NOW()

→ Claude orchestriert alles selbst!
```

---

#### 2. LlamaParse - Intelligentes PDF-Parsing

> **Was ist das?** Ein spezialisierter Service von LlamaIndex der PDFs WIRKLICH versteht - nicht nur Text extrahiert, sondern Tabellen, Layouts, Bilder erkennt.

```
PROBLEM: Lieferschein als PDF

EINFACHES PDF-TO-TEXT:
──────────────────────
"Lieferschein Nr 12345 Datum 15.12.2025
Pos Artikel Menge
1 Fenster 1200x1400 5
2 Haustuer 3"

→ Keine Struktur, Tabelle zerstoert

MIT LLAMAPARSE:
───────────────
{
  "document_type": "delivery_note",
  "number": "12345",
  "date": "2025-12-15",
  "positions": [
    {"pos": 1, "article": "Fenster 1200x1400", "quantity": 5},
    {"pos": 2, "article": "Haustuer", "quantity": 3}
  ]
}

→ Strukturierte Daten, sofort nutzbar!
```

**Anwendungen:**
- Lieferscheine automatisch einlesen
- Eingangsrechnungen verarbeiten
- Konfigurator-PDFs parsen (Warema, Klaiber)
- AB-Dokumente mit Bestellung abgleichen

---

#### 3. n8n 2.0 - Workflow-Automation (bereits vorhanden!)

> **Was ist das?** Open-Source Workflow-Automation (wie Zapier, aber self-hosted). Ihr habt es bereits auf dem Hetzner-Server!

```
BEISPIEL-WORKFLOWS FUER W4A-ERSATZ:

1. E-MAIL-EINGANG
   ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐
   │ E-Mail  │ →  │ Claude  │ →  │ Ticket  │ →  │ Notify  │
   │ Trigger │    │ Klassif.│    │ erstellen│   │ Team    │
   └─────────┘    └─────────┘    └─────────┘    └─────────┘

2. LIEFERANTEN-BESTELLUNG
   ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐
   │ Bestell │ →  │ PDF     │ →  │ E-Mail  │ →  │ Status  │
   │ freigabe│    │ generate│    │ senden  │    │ update  │
   └─────────┘    └─────────┘    └─────────┘    └─────────┘

3. MONTAGE-ERINNERUNG
   ┌─────────┐    ┌─────────┐    ┌─────────┐
   │ Cron    │ →  │ Check   │ →  │ SMS an  │
   │ 8:00    │    │ Termine │    │ Kunde   │
   └─────────┘    └─────────┘    └─────────┘
```

**Vorteile n8n:**
- Bereits installiert und bekannt
- 400+ Integrationen (E-Mail, SMS, Slack, etc.)
- AI-Nodes fuer Claude, OpenAI, etc.
- Kann neues System via Webhooks triggern
- Kein Code noetig fuer einfache Workflows

---

#### 4. ElevenLabs - Voice AI

> **Was ist das?** Der fuehrende Anbieter fuer KI-Stimmen und Sprach-Features.

**Relevante Produkte:**

| Produkt | Funktion | Nutzen |
|---------|----------|--------|
| **Eleven v3** | Text-to-Speech | Natuerliche Stimme fuer Telefon-Bot |
| **Scribe v2 Realtime** | Echtzeit-Transkription | Live-Telefonate mitschreiben |
| **Conversational AI 2.0** | Voice Agents | Kompletter Telefon-Assistent |

```
TELEFON-KI-ASSISTENT MIT ELEVENLABS:

Anruf eingehend
     │
     ▼
┌─────────────────────────────────────┐
│  ElevenLabs Conversational AI 2.0   │
│                                     │
│  1. Scribe v2: Hoert zu (Realtime)  │
│  2. Claude: Versteht + Antwortet    │
│  3. Eleven v3: Spricht (natuerlich) │
│                                     │
│  "Guten Tag, JS Fenster, wie kann   │
│   ich Ihnen helfen?"                │
└─────────────────────────────────────┘
     │
     ▼
Gespraech wird gefuehrt + transkribiert
     │
     ▼
Ticket/Budget-Angebot automatisch erstellt
```

---

#### 5. LangChain / LlamaIndex - RAG-Frameworks

> **Was sind das?** Frameworks um KI-Anwendungen zu bauen die auf eigene Daten zugreifen (RAG = Retrieval Augmented Generation).

**Vergleich:**

| Aspekt | LangChain | LlamaIndex |
|--------|-----------|------------|
| Fokus | Agents, Chains | Dokumente, RAG |
| Komplexitaet | Hoeher | Niedriger |
| Dokumentation | Gut | Sehr gut |
| Enterprise | LangSmith | LlamaCloud |
| **Empfehlung** | Fuer Agents | Fuer Dokumente |

**Fuer W4A-Ersatz:**
- **LlamaIndex** fuer: PDF-Parsing, Dokument-Suche, Knowledge Base
- **LangChain** fuer: Komplexe Agent-Workflows, Multi-Step Reasoning

---

### Architektur-Diagramm mit Tools

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           W4A-ERSATZ SYSTEM                                 │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   EINGAENGE                    VERARBEITUNG                 AUSGAENGE       │
│   ─────────                    ────────────                 ─────────       │
│                                                                             │
│   ┌─────────┐                 ┌─────────────────────┐                       │
│   │ Telefon │ ──────────────► │ ElevenLabs          │                       │
│   │         │  Sprache        │ Scribe v2 (STT)     │                       │
│   └─────────┘                 │ Eleven v3 (TTS)     │                       │
│                               │ Conversational AI   │                       │
│   ┌─────────┐                 └──────────┬──────────┘                       │
│   │ E-Mail  │ ──────────────────────────►│                                  │
│   │         │  Text                      │         ┌────────────────────┐   │
│   └─────────┘                            │         │                    │   │
│                                          ▼         │   NEUE DATENBANK   │   │
│   ┌─────────┐                 ┌─────────────────┐  │   ──────────────   │   │
│   │  PDFs   │ ──────────────► │ LlamaParse      │  │                    │   │
│   │         │  Dokumente      │ (PDF → JSON)    │──┼─► PostgreSQL       │   │
│   └─────────┘                 └─────────────────┘  │   + pgvector       │   │
│                                          │         │                    │   │
│   ┌─────────┐                            │         │   Embeddings       │   │
│   │ Fotos   │ ──────────────────────────►│         │                    │   │
│   │         │  Bilder                    ▼         └────────────────────┘   │
│   └─────────┘                 ┌─────────────────┐            │              │
│                               │ Claude Opus 4.5 │            │              │
│   ┌─────────┐                 │ + MCP Tools     │◄───────────┘              │
│   │  Chat   │ ──────────────► │                 │                           │
│   │         │  Text           │ - Klassifizieren│  ┌────────────────────┐   │
│   └─────────┘                 │ - Analysieren   │  │                    │   │
│                               │ - Generieren    │──┼─► n8n Workflows    │   │
│                               │ - Entscheiden   │  │   (Automation)     │   │
│                               └─────────────────┘  │                    │   │
│                                          │         │   - E-Mail senden  │   │
│                                          │         │   - SMS senden     │   │
│                                          ▼         │   - Webhooks       │   │
│                               ┌─────────────────┐  │   - Scheduler      │   │
│                               │ LangChain       │  │                    │   │
│                               │ / LlamaIndex    │  └────────────────────┘   │
│                               │                 │                           │
│                               │ RAG Pipeline:   │  ┌────────────────────┐   │
│                               │ - Suche         │  │                    │   │
│                               │ - Kontext       │──┼─► Frontend (Next)  │   │
│                               │ - Antwort       │  │   PWA Mobile       │   │
│                               └─────────────────┘  │                    │   │
│                                                    └────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### Kosten-Schaetzung KI-Tools (monatlich)

| Tool | Nutzung | Kosten | Hinweis |
|------|---------|--------|---------|
| **Claude API** | ~500k Tokens | 30-60€ | Opus fuer komplex, Haiku fuer einfach |
| **OpenAI Embeddings** | ~5M Tokens | <1€ | Praktisch kostenlos |
| **Whisper API** | ~10h Audio | 10-20€ | Oder lokal kostenlos |
| **ElevenLabs** | ~2h Sprache | 20-40€ | Starter Plan reicht |
| **LlamaParse** | ~500 Seiten | 10-20€ | Free Tier fuer Start |
| **n8n** | Self-hosted | 0€ | Bereits vorhanden! |
| **GESAMT** | | **70-140€** | |

---

### Zukunftssichere Entscheidungen

| Entscheidung | Warum zukunftssicher |
|--------------|---------------------|
| **MCP nutzen** | Anthropic-Standard, wird von Google Cloud unterstuetzt, wachsendes Oekosystem |
| **pgvector statt Pinecone** | Open Source, in PostgreSQL integriert, keine Vendor-Lock-in |
| **n8n statt Zapier** | Self-hosted, keine Limitierungen, AI-native |
| **LlamaIndex fuer Docs** | Enterprise-ready, aktive Entwicklung, LlamaCloud bei Bedarf |
| **Claude als Haupt-LLM** | Bestes Reasoning, MCP-native, starkes Tool-Use |

---

## 6. Echtzeit-Kommunikation

> **Was ist das?** Wenn der Monteur seinen Status aendert, soll das Buero das SOFORT sehen - nicht erst nach einem Seiten-Refresh. Das nennt man Echtzeit-Kommunikation.

### Option A: WebSockets

```
Was ist das?  Eine dauerhafte Verbindung zwischen Browser und Server.
              Beide koennen jederzeit Nachrichten schicken.
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Echte Echtzeit | Aenderungen erscheinen innerhalb von Millisekunden. |
| Bidirektional | Server kann Browser informieren OHNE dass der Browser fragt. |
| Effizient | Eine Verbindung bleibt offen, kein staendiges Neu-Verbinden. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Komplexer zu implementieren | Mehr Code noetig als bei einfachen Anfragen. |
| Verbindungs-Management | Was passiert wenn die Verbindung abbricht? Muss man behandeln. |
| Skalierung aufwaendiger | Bei sehr vielen Nutzern braucht man extra Infrastruktur. |

---

### Option B: Server-Sent Events (SSE)

```
Was ist das?  Server schickt Updates an Browser (nur eine Richtung).
              Browser kann nicht zurueckschicken.
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Einfacher als WebSockets | Weniger Code, weniger Komplexitaet. |
| Automatische Reconnection | Browser verbindet sich automatisch neu bei Abbruch. |
| Funktioniert mit Standard-HTTP | Keine spezielle Infrastruktur noetig. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Nur eine Richtung | Browser kann keine Nachrichten zurueckschicken (muss normale Anfragen machen). |
| Weniger verbreitet | Weniger Tutorials und Beispiele als WebSockets. |

---

### Option C: Polling

```
Was ist das?  Browser fragt alle X Sekunden: "Gibt's was Neues?"
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Sehr einfach | Normale Anfragen, kein spezielles Protokoll. |
| Funktioniert ueberall | Selbst alte Browser, schlechte Verbindungen. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Nicht wirklich Echtzeit | Je nach Intervall (5-30 Sekunden) verzoegert. |
| Ineffizient | Viele unnoetige Anfragen wenn nichts passiert. |
| Mehr Serverlast | Server muss staendig Anfragen beantworten. |

---

### Empfehlung Echtzeit

```
┌─────────────────────────────────────────────────────────────────┐
│  EMPFEHLUNG: WebSockets (mit Socket.io)                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  WARUM:                                                         │
│                                                                 │
│  1. GPS-Tracking braucht Echtzeit                               │
│     → Position alle paar Sekunden, sofort im Dashboard.         │
│       Polling waere zu langsam und ineffizient.                 │
│                                                                 │
│  2. Status-Updates fuer Montagen                                │
│     → Wenn Mariusz auf "Fertig" klickt, sieht Sandra            │
│       das SOFORT. Nicht erst nach 30 Sekunden.                  │
│                                                                 │
│  3. Chat/Kommunikation (spaeter)                                │
│     → Falls ihr mal interne Kommunikation einbaut.              │
│                                                                 │
│  4. Socket.io macht es einfach                                  │
│     → Socket.io ist eine Bibliothek die WebSockets              │
│       "verpackt" und einfacher macht:                           │
│       - Automatische Reconnection                               │
│       - Fallback auf Polling wenn noetig                        │
│       - Raeume/Kanaele (GPS-Daten nur an Dashboard)             │
│       - Sehr gut dokumentiert                                   │
│                                                                 │
│  BEI EURER GROESSE KEIN PROBLEM:                                │
│  Mit ~15 gleichzeitigen Nutzern ist Skalierung                  │
│  kein Thema. Ein einfacher Server reicht.                       │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 7. Mobile App (Monteur-App)

> **Was ist das?** Die Monteure brauchen eine App auf ihrem Smartphone. Die Frage ist: Eigene App fuer iPhone UND Android, oder eine Loesung die beides abdeckt?

### Option A: Native Apps (Swift + Kotlin)

```
Was bedeutet das?  Eine App speziell fuer iPhone (Swift),
                   eine zweite App speziell fuer Android (Kotlin)
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Beste Performance | Apps laufen am schnellsten und fluessigsten. |
| Voller Zugriff auf Geraet | Kamera, GPS, Offline-Speicher - alles ohne Einschraenkungen. |
| App Store Praesenz | "Echte" App im Store, wirkt professionell. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Doppelter Aufwand | Du musst ZWEI Apps entwickeln und pflegen. |
| Zwei Sprachen lernen | Swift (Apple) und Kotlin (Android) sind komplett unterschiedlich. |
| Teuer | Doppelte Entwicklungszeit = doppelte Kosten. |
| Apple Developer Account | Kostet 99€/Jahr, App muss durch Pruefung. |

---

### Option B: PWA (Progressive Web App)

```
Was bedeutet das?  Eine Website die sich wie eine App anfuehlt.
                   Kann auf Homescreen installiert werden.
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Eine Codebasis | Du entwickelst einmal, laeuft auf allen Geraeten. |
| Kein App Store noetig | Keine Pruefung, keine Gebuehren, sofort verfuegbar. |
| Gleiche Technologie wie Web | React/Vue - du nutzt was du schon kannst. |
| Immer aktuell | Updates sind sofort da, kein "App updaten" noetig. |
| Offline-faehig | Mit Service Workers funktioniert vieles auch ohne Internet. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Kein App Store | Manche Nutzer erwarten eine "echte" App. |
| Eingeschraenkt auf iOS | Apple blockiert manche Features (Push, Hintergrund-GPS). |
| Weniger "native" Gefuehl | Fuehlt sich nicht 100% wie echte App an. |

---

### Option C: Hybrid (React Native, Flutter, Capacitor)

```
Was bedeutet das?  Eine Codebasis, aber wird zu "echten" Apps
                   fuer beide Plattformen kompiliert.
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Eine Codebasis, zwei Apps | Einmal entwickeln, iPhone UND Android App. |
| Voller Geraetezugriff | Kamera, GPS, Push-Notifications - alles geht. |
| App Store Praesenz | "Echte" Apps in beiden Stores. |
| React Native nutzt React | Wenn du React kannst, ist React Native aehnlich. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Performance-Kompromiss | Nicht ganz so schnell wie native Apps. |
| Abhaengigkeit vom Framework | Wenn React Native sich aendert, musst du anpassen. |
| Debugging komplexer | Fehler koennen an mehreren Stellen liegen. |

---

### Empfehlung Mobile App

```
┌─────────────────────────────────────────────────────────────────┐
│  EMPFEHLUNG: PWA mit Capacitor-Fallback                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  STRATEGIE:                                                     │
│                                                                 │
│  START: PWA (Progressive Web App)                               │
│  ─────────────────────────────────                              │
│  - Gleicher Code wie Web-App                                    │
│  - Monteur oeffnet Link, klickt "Zum Homescreen"                │
│  - Funktioniert auf iPhone UND Android                          │
│  - Sofort einsatzbereit, keine App-Store-Pruefung               │
│                                                                 │
│  WAS GEHT MIT PWA:                                              │
│  ✅ GPS-Tracking (funktioniert gut)                             │
│  ✅ Kamera/Fotos (funktioniert gut)                             │
│  ✅ Offline-Cache (Grundfunktionen)                             │
│  ✅ Push-Notifications auf Android                              │
│  ⚠️ Push auf iPhone (geht seit iOS 16.4, mit Einschraenkungen) │
│  ⚠️ Hintergrund-GPS auf iPhone (eingeschraenkt)                │
│                                                                 │
│  SPAETER (WENN NOETIG): Capacitor                               │
│  ─────────────────────────────────                              │
│  Wenn iPhone-Einschraenkungen stoeren:                          │
│  - Capacitor "verpackt" die PWA in eine echte App               │
│  - Gleicher Code, aber als App-Store-App                        │
│  - Dann voller Zugriff auf alle Features                        │
│                                                                 │
│  WARUM NICHT SOFORT NATIVE:                                     │
│  - Doppelter Aufwand fuer ~5 Monteure?                          │
│  - PWA reicht fuer eure Anforderungen                           │
│  - Spaeter upgraden ist einfach moeglich                        │
│                                                                 │
│  KONKRET:                                                       │
│  - Next.js PWA (next-pwa Plugin)                                │
│  - Service Worker fuer Offline                                  │
│  - Responsive Design (passt sich an)                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 8. Authentifizierung

> **Was ist das?** Wie loggen sich Benutzer ein? Wie wird sichergestellt dass nur Berechtigte Zugriff haben?

### Option A: Eigenes Login-System

```
Was bedeutet das?  Du baust selbst: Registrierung, Login,
                   Passwort-Reset, Session-Verwaltung
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Volle Kontrolle | Du entscheidest alles: wie Passwoerter gespeichert werden, was erlaubt ist. |
| Keine externe Abhaengigkeit | Kein Drittanbieter der ausfallen kann. |
| Einfach fuer Benutzer | Ein Passwort, fertig. Keine komplizierten Flows. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Sicherheitsrisiko | Wenn du Fehler machst, koennen Passwoerter gestohlen werden. |
| Aufwand | Passwort-Reset, Session-Timeout, Brute-Force-Schutz - alles selbst bauen. |
| Keine Single-Sign-On | Benutzer muessen sich extra einloggen (nicht mit Google etc.). |

---

### Option B: OAuth/Social Login (Google, Microsoft)

```
Was bedeutet das?  Benutzer loggen sich mit Google/Microsoft/etc.
                   ein. Du speicherst keine Passwoerter.
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Sicherer | Google/Microsoft kuemmern sich um Sicherheit. Kein Passwort bei dir. |
| Bequem fuer Benutzer | Ein Klick, eingeloggt. Kein neues Passwort merken. |
| Weniger Code | Login-Flow wird von Anbieter gehandhabt. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Abhaengigkeit | Wenn Google ausfaellt (selten), kein Login moeglich. |
| Nicht fuer alle Benutzer | Monteure haben vielleicht kein Google-Konto. |
| Datenschutz-Bedenken | Google weiss wann sich wer einloggt (manche stoert das). |

---

### Option C: Auth-Service (Auth0, Clerk, Supabase Auth)

```
Was bedeutet das?  Ein spezialisierter Dienst kuemmert sich
                   um alles: Login, Register, Passwort-Reset
```

**Vorteile:**
| Vorteil | Erklaerung |
|---------|------------|
| Beste Sicherheit | Experten kuemmern sich darum. Viel sicherer als selbst bauen. |
| Alle Features inklusive | 2-Faktor, Passwort-Reset, Brute-Force-Schutz, Social Login. |
| Schnell integriert | Oft nur wenige Zeilen Code. |

**Nachteile:**
| Nachteil | Erklaerung |
|----------|------------|
| Kosten | Manche Dienste kosten ab einer gewissen Nutzerzahl. |
| Abhaengigkeit | Noch ein externer Dienst von dem du abhaengig bist. |

---

### Empfehlung Authentifizierung

```
┌─────────────────────────────────────────────────────────────────┐
│  EMPFEHLUNG: Eigenes Login + Optional Microsoft                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  WARUM:                                                         │
│                                                                 │
│  1. Kleine, feste Benutzergruppe                                │
│     → ~15 Mitarbeiter, keine Registrierung noetig.              │
│       Admin legt Benutzer an, vergibt Passwort.                 │
│                                                                 │
│  2. Monteure brauchen einfachen Login                           │
│     → Benutzername + Passwort, fertig.                          │
│       Oder 4-stellige PIN fuer schnellen Zugang.                │
│                                                                 │
│  3. Fertige Bibliotheken machen es sicher                       │
│     → NextAuth.js (jetzt Auth.js) ist erprobt und sicher.       │
│       Du musst nicht selbst Krypto programmieren.               │
│                                                                 │
│  OPTIONAL: Microsoft-Login fuer Buero                           │
│  ─────────────────────────────────────                          │
│  - Ihr nutzt Microsoft 365?                                     │
│  - Dann koennen Buero-Mitarbeiter sich mit ihrem                │
│    Microsoft-Konto einloggen. Ein Klick, fertig.                │
│  - Monteure weiterhin mit einfachem Login/PIN.                  │
│                                                                 │
│  ROLLEN-KONZEPT:                                                │
│  ┌────────────┬────────────────────────────────────┐            │
│  │ Rolle      │ Berechtigungen                     │            │
│  ├────────────┼────────────────────────────────────┤            │
│  │ Admin      │ Alles (Andreas)                    │            │
│  │ Buero      │ Lesen + Bearbeiten (Sandra, Roland)│            │
│  │ Monteur    │ Nur eigene Auftraege + GPS         │            │
│  │ Kunde      │ Nur eigene Projekte (spaeter)      │            │
│  └────────────┴────────────────────────────────────┘            │
│                                                                 │
│  KONKRET:                                                       │
│  - Auth.js (NextAuth) mit Credentials Provider                  │
│  - Passwort-Hashing mit bcrypt                                  │
│  - JWT fuer Sessions (kein Session-Speicher noetig)             │
│  - Optional: Microsoft Azure AD fuer Buero-Login                │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Zusammenfassung: Der empfohlene Stack

```
┌─────────────────────────────────────────────────────────────────┐
│                    W4A-ERSATZ TECH-STACK                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  FRONTEND                                                       │
│  ─────────                                                      │
│  Next.js 14 (React-Framework)                                   │
│  ├── TypeScript (weniger Fehler)                                │
│  ├── Tailwind CSS (schnelles Styling)                           │
│  ├── shadcn/ui (fertige Komponenten)                            │
│  └── PWA (Mobile-App ohne App-Store)                            │
│                                                                 │
│  BACKEND                                                        │
│  ────────                                                       │
│  Node.js (Haupt-API)                                            │
│  ├── Next.js API Routes ODER Fastify                            │
│  ├── TypeScript                                                 │
│  ├── Prisma (Datenbank-Zugriff)                                 │
│  └── Socket.io (Echtzeit)                                       │
│                                                                 │
│  Python (KI-Worker)                                             │
│  ├── FastAPI                                                    │
│  ├── Bild-Analyse, PDF-Extraktion                               │
│  └── E-Mail-Klassifizierung                                     │
│                                                                 │
│  DATENBANK                                                      │
│  ──────────                                                     │
│  PostgreSQL 16                                                  │
│  ├── Prisma als ORM                                             │
│  └── pgvector (spaeter fuer KI-Embeddings)                      │
│                                                                 │
│  KI-SERVICES                                                    │
│  ───────────                                                    │
│  Claude API (Anthropic) → Text-Generierung                      │
│  OpenAI Whisper API → Sprache-zu-Text                           │
│  GPT-4 Vision / Claude Vision → Bild-Analyse                    │
│  Spaeter: Lokale Modelle wo sinnvoll                            │
│                                                                 │
│  HOSTING                                                        │
│  ────────                                                       │
│  Hetzner Cloud                                                  │
│  ├── Docker + Docker Compose                                    │
│  ├── Coolify ODER Dokploy (Verwaltung)                          │
│  └── Automatische Backups                                       │
│                                                                 │
│  AUTHENTIFIZIERUNG                                              │
│  ─────────────────                                              │
│  Auth.js (NextAuth)                                             │
│  ├── Credentials (Username/Passwort)                            │
│  └── Optional: Microsoft Azure AD                               │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Kosten-Schaetzung (monatlich)

| Posten | Min | Max | Bemerkung |
|--------|-----|-----|-----------|
| Hetzner Server | 20€ | 60€ | Je nach Leistung |
| Hetzner Backup | 5€ | 10€ | Automatische Backups |
| Domain/SSL | 0€ | 2€ | SSL ist kostenlos (Let's Encrypt) |
| Claude API | 20€ | 80€ | Je nach Nutzung |
| OpenAI (Whisper) | 10€ | 40€ | Je nach Anruf-Volumen |
| **GESAMT** | **55€** | **192€** | |

**Vergleich:** W4A kostet pro User pro Monat + Wartung + Updates!

---

## Naechste Schritte

| Nr | Schritt | Beschreibung |
|----|---------|--------------|
| 1 | Stack-Entscheidung | Diese Empfehlungen bestaetigen oder anpassen |
| 2 | Entwicklungsumgebung | Tools installieren (Node.js, VS Code, Docker) |
| 3 | Projekt-Setup | Next.js Projekt erstellen, Datenbank einrichten |
| 4 | Erster Prototyp | Ein Workflow (z.B. Reparatur) als Proof-of-Concept |

---

## Geklaerte Rahmenbedingungen

| Frage | Antwort | Konsequenz |
|-------|---------|------------|
| Monteur-Smartphones | Nokia Android (schlechte Kamera) | **Geraete muessen ersetzt werden** |
| Domain | Subdomain von js-fenster.de | z.B. `erp.js-fenster.de` (neu, parallel zu Auftragsmanagement) |
| W4A-Zugriff | Cloudflare Tunnel existiert | `sql.js-fenster-intern.org` fuer einmalige Migration |
| Bestehende DBs | **ALLES NEU** | Keine Supabase/alte Strukturen wiederverwenden |

---

## Hardware-Beschaffung: Monteur-Smartphones

### Anforderungen

| Anforderung | Grund | Prioritaet |
|-------------|-------|------------|
| Gute Kamera (mind. 12 MP) | Reparatur-Fotos, Ersatzteil-Erkennung durch KI | MUSS |
| Android 12+ | PWA-Funktionen, aktuelle APIs | MUSS |
| Robustes Gehaeuse (IP67+) | Baustellen-Einsatz, Staub, Feuchtigkeit | SOLLTE |
| Grosser Akku (4000+ mAh) | Ganzer Arbeitstag ohne Laden | SOLLTE |
| Mind. 64 GB Speicher | Offline-Cache, Fotos | SOLLTE |
| NFC | Fuer spaetere Features (Inventar-Checkout) | OPTIONAL |

### Empfohlene Geraete (Preis-Leistung)

| Modell | Preis | Vorteile | Nachteile |
|--------|-------|----------|-----------|
| **Samsung Galaxy XCover 6 Pro** | ~350€ | IP68, Wechselakku, sehr robust | Teurer |
| **Samsung Galaxy A14** | ~150€ | Guenstig, gute Kamera | Nicht robust |
| **CAT S62 Pro** | ~450€ | Extrem robust, Waermebildkamera | Teuer |
| **Motorola Defy** | ~250€ | IP68, robust, guenstiger | Aelteres Android |

### Empfehlung

```
┌─────────────────────────────────────────────────────────────────┐
│  EMPFEHLUNG: Samsung Galaxy XCover 6 Pro                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  WARUM:                                                         │
│                                                                 │
│  1. Gebaut fuer Baustellen                                      │
│     → IP68 (wasserdicht, staubdicht)                            │
│     → MIL-STD-810H (Militaerstandard fuer Stuerze)              │
│     → Wechselakku (bei Defekt einfach tauschen)                 │
│                                                                 │
│  2. Gute Kamera                                                 │
│     → 50 MP Hauptkamera                                         │
│     → Ausreichend fuer KI-Ersatzteil-Erkennung                  │
│                                                                 │
│  3. Business-tauglich                                           │
│     → Samsung Knox (Sicherheit, MDM-faehig)                     │
│     → 4 Jahre Updates garantiert                                │
│                                                                 │
│  KOSTEN: ~350€ × 5 Monteure = ~1.750€ einmalig                  │
│                                                                 │
│  ALTERNATIVE (Budget):                                          │
│  Samsung Galaxy A14 (~150€) wenn Robustheit nicht kritisch      │
│  → Dann mit Schutzhuelle verwenden                              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## W4A-Migration (einmalig)

### Prinzip: KOMPLETT NEU

```
┌─────────────────────────────────────────────────────────────────┐
│  WICHTIG: Das neue System ist KEINE Kopie von W4A!              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ❌ NICHT:                                                      │
│  - Bestehende Supabase-Strukturen wiederverwenden               │
│  - Alte Datenbank-Schemata kopieren                             │
│  - W4A-Logik nachbauen                                          │
│                                                                 │
│  ✅ STATTDESSEN:                                                │
│  - Komplett neues PostgreSQL-Schema (siehe DATENMODELL.md)      │
│  - Neue Logik basierend auf Autonomie-Prinzipien                │
│  - Einmalige Datenmigration der relevanten Stammdaten           │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Was wird migriert (einmalig)?

| Daten | Anzahl (ca.) | Prioritaet | Hinweis |
|-------|--------------|------------|---------|
| Kunden | ~2.500 | MUSS | Name, Adresse, Kontakt |
| Projekte | ~2.500 | MUSS | Projekt-Historie |
| Lieferanten | ~200 | MUSS | Kontaktdaten |
| Artikel/Preise | ~500 | SOLLTE | Basis-Preisliste |
| Offene Angebote | ~50 | SOLLTE | Nur aktive |
| Offene Auftraege | ~30 | SOLLTE | Nur aktive |

### Was wird NICHT operativ migriert?

| Daten | Grund |
|-------|-------|
| Alte Rechnungen | Nicht fuer neues System, aber fuer Analyse! |
| Alte Positionen (~120k) | Nicht fuer neues System, aber fuer Lernen! |
| W4A-Dokumente | Auf Server bleiben, bei Bedarf verlinken |
| Komplexe Verknuepfungen | Neue Struktur ist anders |

---

## Historische Datennutzung (WICHTIG!)

### Das Problem

```
FRAGE: Wie erstellt das neue System ein Budget-Angebot
       wenn es keine historischen Daten hat?

FRAGE: Wie lernt das System Margen, wenn es keine
       alten Eingangs-/Ausgangsrechnungen kennt?

FRAGE: Was war bei Kunde Mueller vor 5 Jahren?
```

**Antwort:** Wir brauchen ZWEI Arten von Daten:

| Daten-Typ | Zweck | Wo |
|-----------|-------|-----|
| **Operative Daten** | Tagesgeschaeft, neue Projekte | Neue PostgreSQL |
| **Historische Daten** | Analyse, Lernen, Recherche | Historien-DB (Read-Only) |

---

### Loesung: Historien-Datenbank (Read-Only)

```
┌─────────────────────────────────────────────────────────────────┐
│  HISTORIEN-DB: Fuer Analyse + Lernen, NICHT fuer Operativ       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌─────────────┐                    ┌─────────────────────────┐ │
│  │    W4A      │  ══════════════►   │  HISTORIEN-DB           │ │
│  │  (MS SQL)   │  Einmaliger        │  (PostgreSQL Read-Only) │ │
│  │             │  Export            │                         │ │
│  │ • Projekte  │                    │  • Projekte + Kunde     │ │
│  │ • Angebote  │                    │  • Alle Positionen      │ │
│  │ • Auftraege │                    │  • Preise + Rabatte     │ │
│  │ • Rechnungen│                    │  • Rechnungen (AR + ER) │ │
│  │ • Positionen│                    │  • Bestellungen + EK    │ │
│  └─────────────┘                    └───────────┬─────────────┘ │
│                                                 │               │
│                                                 │               │
│                                                 ▼               │
│                          ┌─────────────────────────────────────┐│
│                          │         NEUES ERP-SYSTEM            ││
│                          │                                     ││
│                          │  Zugriff bei:                       ││
│                          │  • Budget-Angebot erstellen         ││
│                          │  • Aehnliche Projekte suchen        ││
│                          │  • Margen-Analyse                   ││
│                          │  • Kunden-Historie anzeigen         ││
│                          │  • Lernsystem trainieren            ││
│                          │                                     ││
│                          └─────────────────────────────────────┘│
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### Anwendungsfall 1: Budget-Angebot

**Szenario:** Neuer Kunde will 5 Fenster (Sanierung)

```
NEUES SYSTEM fragt Historien-DB:

SELECT
    p.Name as Projekt,
    COUNT(pos.Code) as Anzahl_Fenster,
    SUM(pos.GesPreis) as Angebotssumme,
    AVG(pos.EinzPreis) as Durchschnittspreis
FROM Projekte p
JOIN Angebot a ON a.ProjektCode = p.Code
JOIN Positionen pos ON pos.BZObjMemberCode = a.Code AND pos.BZObjType = 6
WHERE p.Notiz LIKE '%DKF%'  -- Dreh-Kipp-Fenster
  AND a.AuftragsDatum IS NOT NULL  -- Nur erfolgreiche
  AND pos.Bezeichnung LIKE '%Fenster%'
GROUP BY p.Code
HAVING COUNT(pos.Code) BETWEEN 4 AND 6  -- Aehnliche Groesse

ERGEBNIS:
┌────────────────────┬─────────┬───────────┬──────────────┐
│ Projekt            │ Anzahl  │ Summe     │ Durchschnitt │
├────────────────────┼─────────┼───────────┼──────────────┤
│ Mueller 2023       │ 5       │ 8.500€    │ 1.700€       │
│ Schmidt 2024       │ 6       │ 9.200€    │ 1.533€       │
│ Weber 2024         │ 4       │ 7.800€    │ 1.950€       │
│ ...                │         │           │              │
└────────────────────┴─────────┴───────────┴──────────────┘

SYSTEM BERECHNET:
→ Durchschnitt: ~1.700€ pro Fenster (Sanierung)
→ Budget-Angebot: 5 × 1.700€ = 8.500€ (+-15%)
→ Zeigt Range: 7.200€ - 9.800€
```

---

### Anwendungsfall 2: Margen-Analyse (Ausgang vs. Eingang)

**Szenario:** System soll lernen welche Rabatte realistisch sind

```
ANALYSE-QUERY:

SELECT
    p.Nummer as Projekt,
    -- Ausgangsrechnung (was Kunde zahlt)
    SUM(CASE WHEN r.Code IS NOT NULL THEN r.Wert ELSE 0 END) as Umsatz,
    -- Eingangsrechnungen (was wir zahlen)
    SUM(CASE WHEN b.Code IS NOT NULL THEN b.Wert ELSE 0 END) as Einkauf,
    -- Marge
    (SUM(r.Wert) - SUM(b.Wert)) / SUM(r.Wert) * 100 as Marge_Prozent
FROM Projekte p
LEFT JOIN Rechnung r ON r.ProjektCode = p.Code
LEFT JOIN Bestellung b ON b.ProjektCode = p.Code
WHERE p.Datum > '2022-01-01'
GROUP BY p.Code
HAVING SUM(r.Wert) > 0

ERGEBNIS:
┌────────────────────┬──────────┬──────────┬─────────────┐
│ Projekt            │ Umsatz   │ Einkauf  │ Marge       │
├────────────────────┼──────────┼──────────┼─────────────┤
│ P240123            │ 12.500€  │ 7.800€   │ 37,6%       │
│ P240156            │ 8.900€   │ 6.200€   │ 30,3%       │
│ P240189            │ 45.000€  │ 28.000€  │ 37,8%       │
└────────────────────┴──────────┴──────────┴─────────────┘

SYSTEM LERNT:
→ Durchschnittsmarge: ~35%
→ Minimum akzeptabel: ~25%
→ Warnung wenn Angebot unter 25% Marge
```

---

### Anwendungsfall 3: Kunden-Historie

**Szenario:** Bestandskunde ruft an

```
SYSTEM SUCHT AUTOMATISCH:

SELECT
    p.Nummer, p.Name, p.Datum,
    a.Wert as Auftragswert,
    STRING_AGG(DISTINCT l.Firma1, ', ') as Lieferanten
FROM Projekte p
JOIN Angebot a ON a.ProjektCode = p.Code AND a.AuftragsDatum IS NOT NULL
LEFT JOIN Bestellung b ON b.ProjektCode = p.Code
LEFT JOIN Lieferanten l ON l.Code = b.SDObjMemberCode
WHERE p.KundenCode = [KundenCode_aus_Suche]
GROUP BY p.Code
ORDER BY p.Datum DESC

ANZEIGE IM NEUEN SYSTEM:
┌─────────────────────────────────────────────────────────────────┐
│  KUNDE: Mueller, Hans                    Tel: 0961 12345        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  HISTORIE (aus W4A):                                            │
│  ┌──────────┬────────────────────────┬──────────┬────────────┐  │
│  │ Datum    │ Projekt                │ Wert     │ Lieferant  │  │
│  ├──────────┼────────────────────────┼──────────┼────────────┤  │
│  │ 06/2023  │ 5 Fenster EG           │ 8.500€   │ Weru       │  │
│  │ 03/2020  │ Haustuer               │ 4.200€   │ Weru       │  │
│  │ 11/2018  │ Raffstore Terrasse     │ 2.800€   │ Warema     │  │
│  └──────────┴────────────────────────┴──────────┴────────────┘  │
│                                                                 │
│  GESAMT-UMSATZ: 15.500€ | PROJEKTE: 3 | KUNDE SEIT: 2018       │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### Anwendungsfall 4: Lernsystem fuettern

**Szenario:** System lernt typische Preise und Muster

```
EINMALIGES TRAINING:

1. POSITIONS-MUSTER EXTRAHIEREN
   → "Fenster 1200x1400 DK" wurde 47x verkauft
   → Durchschnittspreis: 890€ (Range: 750€-1.100€)
   → Typischer Rabatt: 8-12%

2. KONFIGURATIONS-MUSTER
   → 78% der Fenster sind weiss
   → 15% anthrazit
   → 7% andere Farben

3. PROJEKT-MUSTER
   → Sanierung: Ø 5,3 Fenster pro Projekt
   → Neubau: Ø 12,8 Fenster pro Projekt
   → Reparatur: Ø 1,2 Positionen

4. LIEFERANTEN-PRAEFERENZEN
   → Weru: 65% der Fenster-Projekte
   → Drutex: 25%
   → Andere: 10%

→ Diese Muster werden ins neue System als "Basis-Wissen" geladen
→ Danach lernt das System aus NEUEN Daten weiter
```

---

### Technische Umsetzung Historien-DB

**Option A: Direkt-Zugriff auf W4A (Live)**

```
VORTEILE:
✅ Immer aktuell
✅ Kein Migrations-Aufwand
✅ Kein zusaetzlicher Speicher

NACHTEILE:
❌ W4A muss laufen (Abhaengigkeit!)
❌ Langsamer (MS SQL ueber Tunnel)
❌ Wenn W4A abgeschaltet → keine Historie mehr
```

**Option B: Einmaliger Export nach PostgreSQL (EMPFOHLEN)**

```
VORTEILE:
✅ W4A kann spaeter abgeschaltet werden
✅ Schneller (lokale PostgreSQL)
✅ Kann optimiert/indexiert werden
✅ Keine Abhaengigkeit

NACHTEILE:
❌ Einmaliger Aufwand (~1-2 Tage)
❌ Nicht mehr aktuell (aber: alte Daten aendern sich nicht!)
```

**Option C: Hybrid (BESTE LOESUNG)**

```
UMSETZUNG:
1. Einmaliger Export aller Daten bis HEUTE → PostgreSQL Historien-DB
2. Waehrend Parallelbetrieb:
   - Neue Projekte → Neues System
   - Alte Projekte → W4A (Live-Zugriff bei Bedarf)
3. Nach komplettem Umstieg:
   - Final-Export der letzten W4A-Daten
   - W4A kann abgeschaltet werden
   - Alles in PostgreSQL (Historien-DB + Neue DB)
```

---

### Historien-DB Schema (vereinfacht)

```sql
-- Separates Schema fuer historische Daten
CREATE SCHEMA history;

-- Projekte (Read-Only, aus W4A)
CREATE TABLE history.projects (
    id SERIAL PRIMARY KEY,
    w4a_code INTEGER UNIQUE,        -- Original W4A Code
    project_number VARCHAR(20),
    name VARCHAR(255),
    customer_id INTEGER,
    date DATE,
    notes TEXT,
    imported_at TIMESTAMP DEFAULT NOW()
);

-- Positionen (Read-Only, aus W4A)
CREATE TABLE history.positions (
    id SERIAL PRIMARY KEY,
    w4a_code INTEGER,
    document_type VARCHAR(20),      -- 'offer', 'order', 'invoice'
    document_code INTEGER,
    position_number VARCHAR(20),
    description TEXT,
    quantity DECIMAL(10,2),
    unit_price DECIMAL(10,2),
    total_price DECIMAL(10,2),
    project_id INTEGER REFERENCES history.projects(id)
);

-- Rechnungen (Read-Only, aus W4A)
CREATE TABLE history.invoices (
    id SERIAL PRIMARY KEY,
    w4a_code INTEGER,
    invoice_number VARCHAR(20),
    date DATE,
    net_amount DECIMAL(10,2),
    gross_amount DECIMAL(10,2),
    project_id INTEGER REFERENCES history.projects(id),
    direction VARCHAR(10)           -- 'outgoing' oder 'incoming'
);

-- Indizes fuer schnelle Abfragen
CREATE INDEX idx_positions_project ON history.positions(project_id);
CREATE INDEX idx_positions_desc ON history.positions USING gin(to_tsvector('german', description));
CREATE INDEX idx_invoices_project ON history.invoices(project_id);
```

---

### Zusammenfassung Historien-Strategie

| Aspekt | Entscheidung |
|--------|--------------|
| **Operative Daten** | Komplett neue PostgreSQL, kein W4A-Schema |
| **Historische Daten** | Export nach PostgreSQL (Schema `history`) |
| **Zugriff** | Read-Only, nur fuer Analyse/Lernen |
| **Timing** | Einmaliger Export vor Go-Live |
| **W4A danach** | Kann abgeschaltet werden (kein Live-Zugriff noetig) |
| **Updates** | Keine - historische Daten aendern sich nicht |

### Migrations-Ablauf

```
PHASE 1: Stammdaten (einmalig)
─────────────────────────────
1. Cloudflare Tunnel starten
   cloudflared access tcp --hostname sql.js-fenster-intern.org --url localhost:1433

2. Python-Script liest W4A-Daten
   - Kunden (dbo.Kunden)
   - Projekte (dbo.Projekte)
   - Lieferanten (dbo.Lieferanten)

3. Transformation in neues Schema
   - Felder mappen
   - IDs neu vergeben
   - Beziehungen aufbauen

4. Import in neue PostgreSQL-DB

PHASE 2: Parallelbetrieb (optional)
───────────────────────────────────
- Neues System fuer neue Projekte
- W4A fuer alte Projekte bis abgeschlossen
- Kein Sync mehr nach initialer Migration!
```

### Verfuegbare W4A-Timestamp-Spalten

Fuer die Migration koennen wir nur AKTUELLE Daten holen:

| Spalte | Tabellen | Nutzen |
|--------|----------|--------|
| `UpdateTime` | Angebot, Bestellung, Projekte | Letzte Aenderung |
| `InsertTime` | Alle Haupttabellen | Erstelldatum |

```sql
-- Beispiel: Nur aktive Projekte der letzten 2 Jahre
SELECT * FROM Projekte
WHERE UpdateTime > DATEADD(year, -2, GETDATE())
```

