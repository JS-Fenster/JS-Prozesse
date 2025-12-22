# Datenmodell (Auszug)

> **Zurueck:** [README.md](README.md)

---

## Regeln (Lernsystem)

```sql
TABLE rules
  id              UUID PRIMARY KEY
  name            VARCHAR         -- "Dachfenster Montagepauschale"
  category        VARCHAR         -- "kalkulation" | "lieferant" | "rabatt"
  condition       JSONB           -- {"product_type": "Dachfenster"}
  action          JSONB           -- {"multiply": "pauschale", "by": 1.5}
  confidence      DECIMAL         -- 0.94
  sample_count    INT             -- 12
  status          VARCHAR         -- "active" | "pending" | "disabled"
  autonomy_level  VARCHAR         -- "auto" | "suggest" | "disabled"
  created_by      UUID            -- wer hat vorgeschlagen
  approved_by     UUID            -- wer hat freigegeben
  created_at      TIMESTAMP
  approved_at     TIMESTAMP
```

---

## Aenderungs-Beobachtungen

```sql
TABLE change_observations
  id              UUID PRIMARY KEY
  document_type   VARCHAR         -- "angebot" | "auftrag" | ...
  document_id     UUID
  position_id     UUID
  field_name      VARCHAR         -- "montage_pauschale" | "lieferant"
  old_value       JSONB
  new_value       JSONB
  changed_by      UUID
  changed_at      TIMESTAMP
  priority        VARCHAR         -- "critical" | "normal"
  status          VARCHAR         -- "pending" | "reviewed" | "ignored"
  cluster_id      UUID            -- fuer Konsolidierung
  is_reverted     BOOLEAN         -- User hat selbst zurueckgeaendert
```

---

## Positionen

```sql
TABLE positions
  id              UUID PRIMARY KEY
  document_id     UUID            -- Angebot/Auftrag/Bestellung
  version         INT             -- Versionsnummer
  position_number VARCHAR         -- "1.1.1" (Freitext!)
  description     TEXT
  quantity        DECIMAL
  unit            VARCHAR
  unit_price      DECIMAL
  discount        DECIMAL
  status          VARCHAR         -- "angebot" | "beauftragt" | "bestellt" | "geliefert" | "abgerechnet"
  sub_status      VARCHAR         -- "aktiv" | "ersetzt" | "storniert"
  supplier_id     UUID
  created_at      TIMESTAMP
  updated_at      TIMESTAMP
```

---

## Dokumente

```sql
TABLE documents
  id              UUID PRIMARY KEY
  type            VARCHAR         -- "angebot" | "auftrag" | "bestellung" | "rechnung"
  number          VARCHAR         -- "240504" (aus Nummernkreis)
  customer_id     UUID
  project_id      UUID
  status          VARCHAR
  total_net       DECIMAL
  total_gross     DECIMAL
  created_at      TIMESTAMP
  created_by      UUID
```

---

## Kunden

```sql
TABLE customers
  id              UUID PRIMARY KEY
  customer_number VARCHAR
  company_name    VARCHAR
  first_name      VARCHAR
  last_name       VARCHAR
  street          VARCHAR
  zip_code        VARCHAR
  city            VARCHAR
  phone           VARCHAR
  email           VARCHAR
  how_found       VARCHAR         -- "empfehlung" | "google" | "werbung" | ...
  created_at      TIMESTAMP
  last_activity   TIMESTAMP
```

---

## Projekte

```sql
TABLE projects
  id              UUID PRIMARY KEY
  customer_id     UUID
  name            VARCHAR         -- "EFH Amberg"
  address         VARCHAR         -- Abweichende Adresse
  status          VARCHAR         -- "anfrage" | "angebot" | "auftrag" | "abgeschlossen"
  created_at      TIMESTAMP
```

---

## Lieferanten

```sql
TABLE suppliers
  id              UUID PRIMARY KEY
  name            VARCHAR
  category        VARCHAR         -- "fenster" | "beschlaege" | "sonnenschutz"
  portal_url      VARCHAR
  api_available   BOOLEAN
  rating_score    DECIMAL         -- Auto-Scoring
  avg_delivery    INT             -- Durchschnittliche Lieferzeit in Tagen
  created_at      TIMESTAMP
```

---

## Termine / Montagen

```sql
TABLE appointments
  id              UUID PRIMARY KEY
  project_id      UUID
  type            VARCHAR         -- "aufmass" | "montage" | "reparatur"
  team_id         UUID
  planned_start   TIMESTAMP
  planned_end     TIMESTAMP
  actual_start    TIMESTAMP       -- GPS-basiert
  actual_end      TIMESTAMP       -- GPS-basiert
  status          VARCHAR         -- "geplant" | "aktiv" | "fertig" | "restarbeit"
  notes           TEXT
  customer_notified BOOLEAN       -- Verspaetung kommuniziert?
```

---

## GPS-Tracking

```sql
TABLE gps_positions
  id              UUID PRIMARY KEY
  user_id         UUID
  latitude        DECIMAL
  longitude       DECIMAL
  accuracy        DECIMAL
  recorded_at     TIMESTAMP
  -- Nur waehrend Arbeitszeit speichern!
```

---

## Reparaturen

```sql
TABLE repairs
  id              UUID PRIMARY KEY
  customer_id     UUID
  project_id      UUID            -- Optional, kann auch ohne Projekt sein
  description     TEXT
  priority        VARCHAR         -- "normal" | "hoch" | "kritisch"
  status          VARCHAR         -- "neu" | "termin_vereinbart" | "ersatzteil_warten" | "termin_folge" | "erledigt"
  spare_part_id   UUID            -- Falls Ersatzteil noetig
  spare_part_status VARCHAR       -- "identifiziert" | "bestellt" | "eingetroffen"
  first_visit     TIMESTAMP
  follow_up_visit TIMESTAMP
  invoice_id      UUID
  created_at      TIMESTAMP
```
