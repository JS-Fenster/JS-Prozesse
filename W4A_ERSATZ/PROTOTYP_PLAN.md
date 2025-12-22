# Prototyp-Plan

> **Zurueck:** [README.md](README.md)

---

## Ziel des Prototyps

```
┌─────────────────────────────────────────────────────────────────┐
│  ZIEL: Proof of Concept - Funktioniert das Konzept?             │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ✅ BEWEISEN:                                                   │
│  - KI-Features funktionieren (Embeddings, Klassifizierung)      │
│  - Mobile-App ist nutzbar fuer Monteure                         │
│  - Autonome Workflows sparen tatsaechlich Zeit                  │
│  - Historische Daten sind nutzbar                               │
│                                                                 │
│  ❌ NOCH NICHT:                                                 │
│  - Alle Workflows implementieren                                │
│  - Perfektes Design                                             │
│  - 100% Datenmigration                                          │
│  - Produktiv-Betrieb                                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## MVP-Scope: Reparatur-Workflow

**Warum Reparatur als erstes?**

| Grund | Erklaerung |
|-------|------------|
| **MAXIMAL autonom** | Hoechstes Automatisierungspotential (80% Aufwand weg) |
| **Klar abgegrenzt** | Ein Workflow, ein User (Stefan), ueberschaubar |
| **Alle KI-Features** | Bild-Erkennung, Spracheingabe, Auto-Recherche |
| **Schneller Nutzen** | Stefan sieht sofort Verbesserung |
| **Wenig Abhaengigkeiten** | Braucht nicht den ganzen ERP-Unterbau |

---

## Phasen-Uebersicht

```
PHASE 0          PHASE 1          PHASE 2          PHASE 3
──────────       ──────────       ──────────       ──────────
SETUP            REPARATUR-MVP    ERWEITERUNG      ROLLOUT

Infrastruktur    Stefan-App       + Montage-App    Alle Workflows
einrichten       Reparatur-Flow   + Dashboard      Produktiv-Betrieb
                 KI-Features      + CRM Basics

~1-2 Wochen      ~3-4 Wochen      ~4-6 Wochen      Fortlaufend
```

---

## Phase 0: Setup & Infrastruktur

### 0.1 Entwicklungsumgebung

| Task | Tool | Hinweis |
|------|------|---------|
| Node.js installieren | v20 LTS | Falls nicht aktuell |
| pnpm installieren | `npm i -g pnpm` | Schneller als npm |
| VS Code Extensions | ESLint, Prettier, Tailwind | Produktivitaet |
| Git Repository | GitHub `JS-Fenster/erp-system` | Neues Repo |

### 0.2 Projekt initialisieren

```bash
# Next.js Projekt erstellen
pnpm create next-app@latest erp-system --typescript --tailwind --eslint --app --src-dir

# In Projektordner wechseln
cd erp-system

# Wichtige Dependencies
pnpm add @prisma/client prisma
pnpm add socket.io socket.io-client
pnpm add @tanstack/react-query
pnpm add zod react-hook-form @hookform/resolvers
pnpm add next-auth
pnpm add lucide-react

# shadcn/ui initialisieren
pnpm dlx shadcn@latest init

# Erste Komponenten hinzufuegen
pnpm dlx shadcn@latest add button input card table dialog toast
```

### 0.3 Datenbank Setup

```bash
# PostgreSQL auf Hetzner (Docker)
docker run -d \
  --name postgres \
  -e POSTGRES_USER=erp \
  -e POSTGRES_PASSWORD=<sicheres-passwort> \
  -e POSTGRES_DB=erp_system \
  -p 5432:5432 \
  -v postgres_data:/var/lib/postgresql/data \
  postgres:16

# pgvector Extension installieren
docker exec -it postgres psql -U erp -d erp_system -c "CREATE EXTENSION vector;"

# Prisma Schema erstellen
npx prisma init
```

### 0.4 Prisma Schema (Basis)

```prisma
// prisma/schema.prisma

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

generator client {
  provider        = "prisma-client-js"
  previewFeatures = ["postgresqlExtensions"]
}

// ============ USERS ============
model User {
  id        String   @id @default(cuid())
  email     String   @unique
  name      String
  role      Role     @default(USER)
  createdAt DateTime @default(now())

  repairs   Repair[] @relation("CreatedBy")
}

enum Role {
  ADMIN
  OFFICE
  TECHNICIAN
  USER
}

// ============ CUSTOMERS ============
model Customer {
  id        String   @id @default(cuid())
  name      String
  company   String?
  street    String?
  zip       String?
  city      String?
  phone     String?
  email     String?
  createdAt DateTime @default(now())

  // W4A Migration
  w4aCode   Int?     @unique

  projects  Project[]
  repairs   Repair[]
}

// ============ PROJECTS ============
model Project {
  id          String   @id @default(cuid())
  number      String   @unique
  name        String
  customerId  String
  customer    Customer @relation(fields: [customerId], references: [id])
  status      ProjectStatus @default(INQUIRY)
  createdAt   DateTime @default(now())

  // W4A Migration
  w4aCode     Int?     @unique

  repairs     Repair[]
}

enum ProjectStatus {
  INQUIRY
  OFFER
  ORDER
  IN_PROGRESS
  COMPLETED
  CANCELLED
}

// ============ REPAIRS (MVP!) ============
model Repair {
  id            String       @id @default(cuid())
  ticketNumber  String       @unique
  customerId    String
  customer      Customer     @relation(fields: [customerId], references: [id])
  projectId     String?
  project       Project?     @relation(fields: [projectId], references: [id])

  // Erfassung
  description   String
  voiceNote     String?      // URL to audio file
  transcript    String?      // Speech-to-Text result

  // KI-Analyse
  aiAnalysis    Json?        // { problem, suggestedParts, confidence }

  // Status
  status        RepairStatus @default(NEW)
  priority      Priority     @default(NORMAL)

  // Zuweisung
  assignedToId  String?
  assignedTo    User?        @relation("AssignedRepairs", fields: [assignedToId], references: [id])

  // Timestamps
  createdAt     DateTime     @default(now())
  createdById   String
  createdBy     User         @relation("CreatedBy", fields: [createdById], references: [id])
  scheduledAt   DateTime?
  completedAt   DateTime?

  // Verknuepfungen
  photos        RepairPhoto[]
  parts         RepairPart[]
  notes         RepairNote[]
}

enum RepairStatus {
  NEW
  ANALYZING      // KI analysiert
  PARTS_NEEDED   // Ersatzteil wird beschafft
  SCHEDULED      // Termin vereinbart
  IN_PROGRESS    // Techniker vor Ort
  COMPLETED      // Erledigt
  CANCELLED
}

enum Priority {
  LOW
  NORMAL
  HIGH
  URGENT
}

model RepairPhoto {
  id        String   @id @default(cuid())
  repairId  String
  repair    Repair   @relation(fields: [repairId], references: [id])
  url       String
  caption   String?
  aiTags    Json?    // KI-erkannte Objekte
  createdAt DateTime @default(now())
}

model RepairPart {
  id          String  @id @default(cuid())
  repairId    String
  repair      Repair  @relation(fields: [repairId], references: [id])
  name        String
  partNumber  String?
  quantity    Int     @default(1)
  price       Decimal?
  source      String? // Lieferant
  ordered     Boolean @default(false)
  delivered   Boolean @default(false)
}

model RepairNote {
  id        String   @id @default(cuid())
  repairId  String
  repair    Repair   @relation(fields: [repairId], references: [id])
  content   String
  createdAt DateTime @default(now())
  createdBy String
}

// ============ EMBEDDINGS ============
model Embedding {
  id         String   @id @default(cuid())
  entityType String   // 'repair', 'project', 'customer'
  entityId   String
  content    String   // Original text
  vector     Unsupported("vector(1536)")
  model      String   @default("text-embedding-3-small")
  createdAt  DateTime @default(now())

  @@index([entityType, entityId])
}
```

### 0.5 API-Keys einrichten

```env
# .env.local

# Database
DATABASE_URL="postgresql://erp:password@localhost:5432/erp_system"

# Auth
NEXTAUTH_SECRET="<generieren mit: openssl rand -base64 32>"
NEXTAUTH_URL="http://localhost:3000"

# OpenAI (Embeddings + Whisper)
OPENAI_API_KEY="sk-..."

# Anthropic (Claude)
ANTHROPIC_API_KEY="sk-ant-..."

# Optional: ElevenLabs (Voice)
ELEVENLABS_API_KEY="..."
```

### 0.6 Deployment-Vorbereitung

```bash
# Auf Hetzner Server
# Docker Compose fuer alle Services

# docker-compose.yml
version: '3.8'
services:
  postgres:
    image: pgvector/pgvector:pg16
    environment:
      POSTGRES_USER: erp
      POSTGRES_PASSWORD: ${DB_PASSWORD}
      POSTGRES_DB: erp_system
    volumes:
      - postgres_data:/var/lib/postgresql/data
    ports:
      - "5432:5432"

  app:
    build: .
    environment:
      DATABASE_URL: postgresql://erp:${DB_PASSWORD}@postgres:5432/erp_system
    ports:
      - "3000:3000"
    depends_on:
      - postgres

volumes:
  postgres_data:
```

---

## Phase 1: Reparatur-MVP

### 1.1 Stefan-App (Mobile PWA)

**Screens zu implementieren:**

| Screen | Funktion | Prioritaet |
|--------|----------|------------|
| Login | Einfacher PIN-Login | P0 |
| Dashboard | Offene Reparaturen | P0 |
| Neue Reparatur | Erfassung mit Sprache/Foto | P0 |
| Reparatur-Detail | Status, Notizen, Fotos | P0 |
| Kundensuche | Autocomplete | P0 |

**API-Endpoints:**

```
POST   /api/repairs              Neue Reparatur erstellen
GET    /api/repairs              Liste (mit Filtern)
GET    /api/repairs/[id]         Detail
PATCH  /api/repairs/[id]         Update Status/Infos
POST   /api/repairs/[id]/photos  Foto hochladen
POST   /api/repairs/[id]/voice   Sprachnotiz hochladen

GET    /api/customers/search     Kundensuche
GET    /api/customers/[id]       Kunden-Detail + Historie

POST   /api/ai/transcribe        Whisper API (Audio → Text)
POST   /api/ai/analyze-photo     Vision API (Bild → Beschreibung)
POST   /api/ai/suggest-parts     Ersatzteil-Vorschlag
```

### 1.2 KI-Features implementieren

#### Sprache-zu-Text

```typescript
// app/api/ai/transcribe/route.ts

import OpenAI from 'openai';

const openai = new OpenAI();

export async function POST(request: Request) {
  const formData = await request.formData();
  const audio = formData.get('audio') as File;

  const transcription = await openai.audio.transcriptions.create({
    file: audio,
    model: 'whisper-1',
    language: 'de',
  });

  return Response.json({ text: transcription.text });
}
```

#### Bild-Analyse

```typescript
// app/api/ai/analyze-photo/route.ts

import Anthropic from '@anthropic-ai/sdk';

const anthropic = new Anthropic();

export async function POST(request: Request) {
  const { imageBase64 } = await request.json();

  const response = await anthropic.messages.create({
    model: 'claude-sonnet-4-20250514',
    max_tokens: 1024,
    messages: [{
      role: 'user',
      content: [
        {
          type: 'image',
          source: {
            type: 'base64',
            media_type: 'image/jpeg',
            data: imageBase64,
          },
        },
        {
          type: 'text',
          text: `Analysiere dieses Bild eines Fenster-/Tueren-Bauteils.
                 Beschreibe:
                 1. Was ist zu sehen?
                 2. Welches Problem/Defekt ist erkennbar?
                 3. Welches Ersatzteil koennte noetig sein?
                 4. Geschaetzter Hersteller (Weru, Siegenia, Hoppe, etc.)?

                 Antworte als JSON.`
        }
      ]
    }]
  });

  return Response.json(response.content[0]);
}
```

#### Ersatzteil-Vorschlag (mit Embeddings)

```typescript
// app/api/ai/suggest-parts/route.ts

import { prisma } from '@/lib/prisma';
import OpenAI from 'openai';

const openai = new OpenAI();

export async function POST(request: Request) {
  const { description, photoAnalysis } = await request.json();

  // 1. Embedding erstellen
  const embeddingResponse = await openai.embeddings.create({
    model: 'text-embedding-3-small',
    input: `${description} ${photoAnalysis}`,
  });

  const embedding = embeddingResponse.data[0].embedding;

  // 2. Aehnliche Reparaturen finden (pgvector)
  const similarRepairs = await prisma.$queryRaw`
    SELECT
      r.id,
      r.description,
      r.ai_analysis,
      1 - (e.vector <=> ${embedding}::vector) as similarity
    FROM "Repair" r
    JOIN "Embedding" e ON e.entity_id = r.id AND e.entity_type = 'repair'
    WHERE r.status = 'COMPLETED'
    ORDER BY e.vector <=> ${embedding}::vector
    LIMIT 5
  `;

  // 3. Claude fuer finale Empfehlung
  const prompt = `
    Basierend auf dieser Problembeschreibung:
    "${description}"

    Und aehnlichen geloesten Reparaturen:
    ${JSON.stringify(similarRepairs)}

    Welche Ersatzteile werden wahrscheinlich benoetigt?
    Antworte als JSON mit: name, geschaetzter_preis, lieferant_vorschlag
  `;

  // ... Claude API Call

  return Response.json({ suggestions, similarRepairs });
}
```

### 1.3 Basis-UI Komponenten

```
src/
├── app/
│   ├── (auth)/
│   │   └── login/
│   │       └── page.tsx
│   ├── (dashboard)/
│   │   ├── layout.tsx
│   │   ├── page.tsx              # Dashboard
│   │   └── repairs/
│   │       ├── page.tsx          # Liste
│   │       ├── new/
│   │       │   └── page.tsx      # Neue Reparatur
│   │       └── [id]/
│   │           └── page.tsx      # Detail
│   └── api/
│       ├── repairs/
│       ├── customers/
│       └── ai/
├── components/
│   ├── ui/                       # shadcn Komponenten
│   ├── repairs/
│   │   ├── repair-card.tsx
│   │   ├── repair-form.tsx
│   │   ├── photo-upload.tsx
│   │   └── voice-recorder.tsx
│   └── customers/
│       └── customer-search.tsx
├── lib/
│   ├── prisma.ts
│   ├── openai.ts
│   └── anthropic.ts
└── hooks/
    ├── use-repairs.ts
    └── use-voice-recorder.ts
```

### 1.4 Meilensteine Phase 1

| Meilenstein | Beschreibung | Kriterium |
|-------------|--------------|-----------|
| **M1.1** | Login funktioniert | Stefan kann sich einloggen |
| **M1.2** | Kundensuche | Autocomplete findet W4A-Kunden |
| **M1.3** | Reparatur anlegen | Formular speichert in DB |
| **M1.4** | Foto-Upload | Bild wird gespeichert |
| **M1.5** | KI-Bildanalyse | Claude beschreibt Foto |
| **M1.6** | Sprachnotiz | Whisper transkribiert |
| **M1.7** | Ersatzteil-Vorschlag | KI schlaegt Teile vor |
| **M1.8** | Stefan-Test | Stefan nutzt App 1 Woche |

---

## Phase 2: Erweiterung

### 2.1 Monteur-App

Nach erfolgreichem Stefan-Test:
- Tagesuebersicht fuer Mariusz, Manfred, Christian
- Rueckmeldung mit Unterschrift
- GPS-Tracking (optional)

### 2.2 Buero-Dashboard

- Offene Aufgaben
- Live-Status Monteure
- Schnell-Erfassung Anfragen

### 2.3 Historien-Migration

- W4A-Daten exportieren
- In `history` Schema importieren
- Embeddings generieren

---

## Technische Entscheidungen (Zusammenfassung)

| Bereich | Entscheidung | Begruendung |
|---------|--------------|-------------|
| **Framework** | Next.js 14 App Router | Server Components, API Routes, einfach |
| **Styling** | Tailwind + shadcn/ui | Schnell, konsistent, anpassbar |
| **DB** | PostgreSQL + Prisma | Typsicher, Migrations, einfach |
| **Embeddings** | pgvector | In PostgreSQL integriert |
| **Auth** | NextAuth.js | Einfach, flexibel |
| **State** | TanStack Query | Caching, Optimistic Updates |
| **Forms** | React Hook Form + Zod | Validation, Performance |
| **KI** | Claude + OpenAI | Bestes Reasoning + Whisper |

---

## Risiken & Mitigationen

| Risiko | Wahrscheinlichkeit | Mitigation |
|--------|-------------------|------------|
| KI-Kosten hoeher als erwartet | Mittel | Monitoring, Haiku statt Opus wo moeglich |
| Stefan findet App kompliziert | Niedrig | Fruehe User-Tests, Iteration |
| W4A-Migration komplex | Mittel | Schrittweise, nur Stammdaten zuerst |
| Offline-Funktionalitaet fehlt | Mittel | Service Worker frueh einplanen |
| Performance-Probleme | Niedrig | Pagination, Caching, lazy loading |

---

## Ressourcen-Schaetzung

### Zeit

| Phase | Aufwand | Hinweis |
|-------|---------|---------|
| Phase 0: Setup | 1-2 Wochen | Einmalig |
| Phase 1: Reparatur-MVP | 3-4 Wochen | Kernfunktionen |
| Phase 2: Erweiterung | 4-6 Wochen | Monteur-App, Dashboard |
| Phase 3: Rollout | Fortlaufend | Iterativ |

### Kosten (monatlich nach Go-Live)

| Posten | Kosten |
|--------|--------|
| Hetzner Cloud | 40-60€ |
| KI-APIs | 70-140€ |
| Domain/SSL | ~2€ |
| **Gesamt** | **~120-200€** |

---

## Sofort starten: Erste Schritte

```
HEUTE:
──────
1. [ ] GitHub Repo erstellen: JS-Fenster/erp-system
2. [ ] Next.js Projekt initialisieren
3. [ ] Prisma Schema anlegen
4. [ ] PostgreSQL auf Hetzner starten

DIESE WOCHE:
────────────
5. [ ] Basis-Layout mit Sidebar
6. [ ] Login-Page (einfach, PIN reicht)
7. [ ] Erste API-Route: /api/health
8. [ ] Deployment auf Hetzner testen

NAECHSTE WOCHE:
───────────────
9. [ ] Kundensuche implementieren
10. [ ] Reparatur-Formular
11. [ ] Foto-Upload
12. [ ] Whisper-Integration testen
```

---

## Erfolgskriterien

| Kriterium | Messung | Ziel |
|-----------|---------|------|
| Stefan nutzt App | Reparaturen pro Woche | >5 |
| Zeit pro Reparatur-Erfassung | Minuten | <3 Min (vorher: 10+ Min) |
| KI-Vorschlaege korrekt | % korrekte Ersatzteile | >70% |
| App-Stabilitaet | Crashes/Fehler | <1 pro Woche |
| User-Zufriedenheit | Stefan-Feedback | "Besser als vorher" |

