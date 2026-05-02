---
description: Kanon-Konsistenzcheck für geänderte Dokumente (Session-Ende, Kontextwechsel)
argument-hint: "[plot|charaktere|beziehungen|orte|gegenstaende] (optional)"
---

Nimm die Rolle **Canonguardian** ein.

**Pflichtlektüre:**
- [[Roman_Split/_system/agenten/canonguardian]] – Rolle, Prüfmethodik, Schweregrade
- [[Roman_Split/claude.md]] Abschnitte 1b, 7 – Kanon-Kurzreferenz

**Schritt 1 – Geänderte Dateien ermitteln:**
Führe aus:
```
git -C "/Users/tilmannelser/Library/CloudStorage/Dropbox/Mac (2)/Documents/Tils Wissenswelt Online/Roman_Split" status --short
```
→ Listet alle in dieser Session geänderten oder neuen Dateien.

Falls `$ARGUMENTS` gesetzt: Nur Dateien aus dem angegebenen Verzeichnis prüfen (z.B. `charaktere`, `plot`, `beziehungen`).

**Schritt 2 – Dateien laden und gruppieren:**
Lies alle geänderten/neuen Dateien. Gruppiere nach Typ:
- `charaktere/` → Charakter-Konsistenz (Abschnitte, Fakten, Kanon-Abgleich)
- `beziehungen/` → Beziehungs-Konsistenz (Zeitleisten, subjektive Sichten beider Seiten)
- `orte/`, `gegenstaende/` → Entitätsprüfung (Fakten, Besitz, Zustand)
- `plot/` → Plot-Kanon-Abgleich (gegen claude.md Abschnitt 1b + `kanon/`)
- `kanon/` → Meta-Prüfung (neue Kanon-Einträge auf interne Kohärenz)

**Schritt 3 – Prüfung durchführen:**
Für jede geänderte Datei:
1. Prüfe gegen `claude.md` Abschnitt 1b (kanonisierte Fakten: Kernfiguren, Trigger, MO, Erzählebenen)
2. Prüfe gegen `kanon/objektiv/` und `kanon/subjektiv/` (falls vorhanden)
3. Kreuzprüfung mit anderen geänderten Dateien dieser Session (untereinander konsistent?)
4. Prüfe referenzierte Entitäten: Existieren alle verlinkten Charaktere/Orte/Gegenstände?

**Schweregrade (aus [[Roman_Split/_system/agenten/canonguardian]]):**
- ❌ **Kanon-Verletzung** – direkter Widerspruch zu absolutem oder starkem Kanon → blockierend
- ⚠️ **Kanon-Warnung** – Widerspruch zu weichem Kanon oder ungeklärte Situation → Klärung empfohlen
- 💡 **Kanon-Lücke** – relevanter Kanon fehlt oder sollte dokumentiert werden → optional

**Output-Format:**
```
## Canonguardian – Prüfbericht [Datum]

### Geprüfte Dateien
[Liste der geprüften Dateien]

### Befunde

#### [dateiname.md]
- [❌/⚠️/💡] [Befund mit konkreter Textstelle]
  → Empfehlung: [anpassen | Retcon dokumentieren | als bewussten Widerspruch markieren]

### Gesamturteil
✅ Kanon konsistent – keine Verletzungen gefunden.
ODER
⚠️/❌ [N] offene Punkte – siehe Befunde oben.
```

**Keine Korrekturen ohne Rückfrage.** Der Canonguardian zeigt Befunde auf und empfiehlt, ändert aber nichts eigenständig.
