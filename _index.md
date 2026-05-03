---
doc_type: index
doc_id: "Index-START"
version: "1.0"
status: aktuell
erstellt: "2026-05-03"
letzte_aenderung: "2026-05-03"
tags:
  - index
  - startseite
---

```dataviewjs
// ============================================================
// Hilfsfunktionen
// ============================================================

function link(path, label) {
  return `<a data-href="${path}" href="${path}" class="internal-link" style="text-decoration:none;color:inherit;">${label}</a>`;
}

function navCard(path, label, sub, icon) {
  return `
    <div style="border:1px solid #333;border-radius:10px;padding:16px 14px;background:#1e1e1e;
                display:flex;flex-direction:column;gap:6px;">
      <div style="font-size:1.3em;line-height:1;">${icon || "📄"}</div>
      <div style="font-weight:700;font-size:0.85em;">${link(path, label)}</div>
      ${sub ? `<div style="font-size:0.7em;color:#666;line-height:1.4;">${sub}</div>` : ""}
    </div>`;
}

function countPages(folder) {
  return dv.pages(`"${folder}"`).where(p => p.doc_type !== "index").length;
}

function sectionHeader(title) {
  return `<h2 style="margin:32px 0 12px;border-bottom:1px solid #333;padding-bottom:6px;font-size:1em;
                     letter-spacing:.05em;text-transform:uppercase;color:#888;">${title}</h2>`;
}

function grid(cols, cards) {
  return `<div style="display:grid;grid-template-columns:repeat(${cols},1fr);gap:12px;">${cards.join("")}</div>`;
}

// ============================================================
// Header
// ============================================================
let html = `
<div style="padding:24px 0 8px;">
  <div style="font-size:0.72em;font-weight:600;letter-spacing:.12em;text-transform:uppercase;color:#666;margin-bottom:6px;">Psychologischer Beziehungs-Thriller</div>
  <h1 style="font-size:2em;margin:0 0 12px;line-height:1.15;">Roman – Arbeitswelt</h1>
  <div style="font-size:0.82em;color:#aaa;line-height:1.6;max-width:680px;border-left:3px solid #333;padding-left:14px;">
    Ein traumatisierter Journalist jagt einen Mörder – ohne zu wissen, dass er sich selbst jagt.
    Die ermittelnde Kommissarin jagt denselben Mann – und verliebt sich in ihn.
  </div>
</div>`;

// ============================================================
// Plot & Handlung
// ============================================================
html += sectionHeader("Plot & Handlung");
html += grid(5, [
  navCard("Roman_Split/plot/plot-hauptplot",  "Plot Übersicht",    "Kern, Methodik, Figuren",        "🗺️"),
  navCard("Roman_Split/plot/plot-beats",      "Beats",             "Makrostruktur · Stufe 3",        "🎬"),
  navCard("Roman_Split/plot/plot-struktur",   "Struktur",          "Erzählebenen, Konfabulation",    "🏗️"),
  navCard("Roman_Split/plot/PLOT_WORKING",    "Arbeitszustand",    "Session-Log · nächste Schritte", "⚡"),
  navCard("Roman_Split/plot/_plot-uebersicht","Plot-Index",        "Alle Plot-Dokumente",            "📋"),
]);

// ============================================================
// Szenen & Reihenfolge
// ============================================================
const szenenCount = dv.pages('"Roman_Split/szenen"').where(p => p.doc_type !== "index").length;

html += sectionHeader("Szenen & Reihenfolge");
html += grid(3, [
  navCard("Roman_Split/szenen",
    "Szenen",
    szenenCount > 0 ? `${szenenCount} Szene${szenenCount !== 1 ? "n" : ""} angelegt` : "Noch keine Szenen",
    "🎭"),
  navCard("Roman_Split/reihenfolge/kapitelplan",
    "Kapitelplan",
    "Kapitel & Strukturübersicht",
    "📖"),
  navCard("Roman_Split/reihenfolge/lesereihenfolge",
    "Lesereihenfolge",
    "Narrative Abfolge",
    "🔀"),
]);

// ============================================================
// Figuren & Welt
// ============================================================
const nChar = countPages("Roman_Split/charaktere");
const nOrt  = countPages("Roman_Split/orte");
const nGgs  = countPages("Roman_Split/gegenstaende");
const nBez  = countPages("Roman_Split/beziehungen");

html += sectionHeader("Figuren & Welt");
html += grid(4, [
  navCard("Roman_Split/charaktere/_character-index",
    "Charaktere",
    `${nChar} angelegt`,
    "👤"),
  navCard("Roman_Split/orte/_ort-index",
    "Orte",
    `${nOrt} angelegt`,
    "📍"),
  navCard("Roman_Split/gegenstaende/_gegenstand-index",
    "Gegenstände",
    `${nGgs} angelegt`,
    "🎁"),
  navCard("Roman_Split/beziehungen/_beziehungen-index",
    "Beziehungen",
    `${nBez} angelegt`,
    "🔗"),
]);

// ============================================================
// Zuletzt geändert
// ============================================================
html += sectionHeader("Zuletzt geändert");

const recent = dv.pages('"Roman_Split"')
  .where(p => p.doc_type !== "index"
           && !p.file.path.includes("/_system/")
           && !p.file.path.includes("/.claude/"))
  .sort(p => p.file.mtime, "desc")
  .limit(8);

html += `<table style="width:100%;border-collapse:collapse;font-size:0.78em;">
  <thead>
    <tr style="border-bottom:1px solid #333;">
      <th style="text-align:left;padding:6px 8px;color:#666;font-weight:600;">Datei</th>
      <th style="text-align:left;padding:6px 8px;color:#666;font-weight:600;">Typ</th>
      <th style="text-align:left;padding:6px 8px;color:#666;font-weight:600;">Geändert</th>
    </tr>
  </thead>
  <tbody>`;

for (const p of recent) {
  const dt = p.file.mtime;
  const datum = dt ? dt.toFormat("dd.MM.yyyy HH:mm") : "–";
  const typ = p.doc_type || p.typ || "–";
  html += `<tr style="border-bottom:1px solid #222;">
    <td style="padding:6px 8px;">${link(p.file.path, p.file.name)}</td>
    <td style="padding:6px 8px;color:#666;">${typ}</td>
    <td style="padding:6px 8px;color:#555;">${datum}</td>
  </tr>`;
}

html += `</tbody></table>`;

// ============================================================
dv.container.innerHTML = html;
```
