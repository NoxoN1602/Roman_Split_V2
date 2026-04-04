# Changelog

## 2026-04-03 – v1.5
- **Neu:** [[szenen-lebenszyklus]] – Regel fuer Szenen-Status (entwurf → abgenommen → revision → archiviert)
- **Neu:** [[szenen-pipeline]] – Pipeline-Regel nach Szenen-Abnahme (Kontinuitaet → Charakter-Auswertung → Kanon-Ableitung)
- **Aktualisiert:** [[charakterentwickler]] v1.1 – Neuer Slash-Befehl `/szene-auswerten`, Leserechte fuer `szenen/`, Abschnitt "Automatische Trigger", `/check` um Szenen-Abdeckung erweitert

## 2026-04-03 – v1.4
- **Neu:** [[charakterentwickler]] – Agenten-Definition mit 9 Slash-Befehlen, Phasen-Logik, Dateizugriff und Zusammenspiel

## 2026-04-03 – v1.3
- **Korrektur:** [[TEMPLATE-charakter]] – Dateiname von TEMPLATE_charakter auf TEMPLATE-charakter (ADR-0003-konform)
- **Aktualisiert:** [[TEMPLATE-charakter]] – Frontmatter gestrafft (nur Systemfelder), Templater-Syntax fuer Datumsfelder, Beispielwerte in Klammern bei allen Tabellenfeldern
- **Aktualisiert:** [[naming-conventions]] v2.1 – Template-Muster auf Bindestrich korrigiert
- **Aktualisiert:** [[ADR-0003-einheitliche-prefixe-und-dateinamen]] – Template-Zeile korrigiert

## 2026-04-03 – v1.2
- **Neu:** [[ADR-0003-einheitliche-prefixe-und-dateinamen]] – Standardisierte Prefixe, Kleinschreibung, Bindestrich-Konvention
- **Aktualisiert:** [[naming-conventions]] v2.0 – Vollstaendige Prefix-Tabelle inkl. Templates, Agenten, Regeln; Migrationshinweis; Verweisformate
- **Neu:** [[TEMPLATE-charakter]] – Fusioniertes Charakter-Template (15 Abschnitte, MUSS/KANN-Logik, Frontmatter)

## 2026-04-03 – v1.1
- **Ergaenzt:** Konzept- und Entscheidungsdokumentation ([[KON-0001-systemkonzept]] v1.1)
- **Neu:** [[ADR-0001-kanon-objektiv-subjektiv]] – Kanon getrennt in objektiv und subjektiv
- **Neu:** [[ADR-0002-keine-umlaute-dateinamen]] – ASCII-only Dateinamen
- **Neu:** Verzeichnisse `_system/konzept/` und `_system/entscheidungen/`

## 2026-04-03 – v1.0
- **Initial:** Systemkonzept erstellt ([[KON-0001-systemkonzept]] v1.0)
- Verzeichnisstruktur definiert
- Frontmatter-Standards fuer alle Dateitypen
- Kanon-System mit Zeitstempeln und Verbindlichkeitsstufen
- 6 Agenten definiert (Plot-Architekt, Charakter-Entwickler, Beziehungs-Manager, Ghostwriter, Kanon-Waechter, Kontinuitaets-Pruefer)
- Workflow fuer nicht-lineare Szenen-Erstellung
