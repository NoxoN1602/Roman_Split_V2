---
typ: index
titel: "Kapitelplan"
status: leer
tags:
  - reihenfolge
  - index
---

# Kapitelplan

> Definiert, welche Szenen in welchem Kapitel erscheinen.

## Kapitel 1 – _Titel noch offen_

_Noch keine Szenen zugeordnet._

## Dataview: Alle Szenen nach Kapitel

```dataview
TABLE titel AS "Szene", romanzeit_start AS "Romanzeit", status AS "Status"
FROM "szenen"
SORT file.name ASC
```
