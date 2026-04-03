---
typ: index
titel: "Kanon-Index"
status: leer
tags:
  - kanon
  - index
---

# Kanon-Index

> Master-Index aller kanonischen Einträge. Wird vom Kanon-Wächter gepflegt.

## Objektiver Kanon

_Noch keine Einträge._

```dataview
TABLE romanzeit AS "Romanzeit", thema AS "Thema", verbindlichkeit AS "Stufe"
FROM "kanon/objektiv"
SORT romanzeit ASC
```

## Subjektiver Kanon (nach Charakter)

_Noch keine Einträge._

```dataview
TABLE charakter AS "Charakter", romanzeit AS "Romanzeit", thema AS "Thema", objektiv_korrekt AS "Korrekt?"
FROM "kanon/subjektiv"
SORT charakter ASC, romanzeit ASC
```
