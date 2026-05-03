---
doc_type: index
doc_id: "Index-BEZ"
version: "1.1"
status: aktuell
kanon_stufe: objektiv
erstellt: "2026-05-03"
letzte_aenderung: "2026-05-03"
autor_agent: charakterentwickler
tags:
  - index
  - beziehung
---

# Beziehungen – Übersicht

```dataviewjs
// ============================================================
// Hilfsfunktionen
// ============================================================

const VALENZ_FARBEN = {
  positiv:   "#4caf50",
  negativ:   "#e53935",
  neutral:   "#9e9e9e",
  angespannt:"#ff9800",
  komplex:   "#ab47bc"
};

// Entity-Lookup: doc_id → Page
function buildEntityMap() {
  const map = new Map();
  for (const folder of ["Roman_Split/charaktere", "Roman_Split/gegenstaende", "Roman_Split/orte"]) {
    for (const p of dv.pages(`"${folder}"`)) {
      if (p.doc_id) map.set(p.doc_id, p);
    }
  }
  return map;
}

// Entity-ID → lesbarer Name ("CHAR-johannes-breier" → "Johannes Breier")
function formatName(entityId) {
  const match = (entityId || "").match(/^(?:CHAR|GGS|ORT)-(.+)$/);
  if (!match) return entityId || "–";
  return match[1].split("-").map(w => w.charAt(0).toUpperCase() + w.slice(1)).join(" ");
}

// Entity-ID → Bild-HTML
function imgHtml(entityId, entityMap, w, h) {
  w = w || 80; h = h || 100;
  const page = entityMap.get(entityId);
  if (page && page.bild) {
    const url = app.vault.adapter.getResourcePath(page.file.folder + "/" + page.bild);
    return `<img src="${url}" style="width:${w}px;height:${h}px;object-fit:cover;border-radius:6px;display:block;">`;
  }
  return `<div style="width:${w}px;height:${h}px;background:#2a2a2a;border-radius:6px;
    display:flex;align-items:center;justify-content:center;
    color:#666;font-size:0.65em;text-align:center;flex-shrink:0;">kein<br>Bild</div>`;
}

// valenz_verlauf → HTML-Progressionskette ("negativ → komplex")
function valenzKette(verlauf) {
  if (!verlauf || !Array.isArray(verlauf) || verlauf.length === 0)
    return `<span style="color:#555;font-size:0.65em;">–</span>`;

  function badge(wert) {
    const c = VALENZ_FARBEN[wert] || "#666";
    return `<span style="color:${c};font-weight:600;font-size:0.65em;">${wert || "?"}</span>`;
  }

  const pfeil = `<span style="color:#555;font-size:0.65em;"> → </span>`;

  if (verlauf.length === 1) return badge(verlauf[0].wert);
  if (verlauf.length <= 3)  return verlauf.map(v => badge(v.wert)).join(pfeil);
  // Längere Ketten: Anfang → … → Ende
  return badge(verlauf[0].wert)
    + `<span style="color:#555;font-size:0.65em;"> → … → </span>`
    + badge(verlauf[verlauf.length - 1].wert);
}

// Sektion rendern (Galerie-Kacheln)
function renderSection(title, bezType, entityMap) {
  const pages = dv.pages('"Roman_Split/beziehungen"')
    .where(p => p.doc_type !== "index" && p.beziehungstyp === bezType)
    .sort(p => p.file.name, "asc");

  let html = `<h2 style="margin-top:32px;margin-bottom:12px;border-bottom:1px solid #333;padding-bottom:6px;">
    ${title} <span style="font-size:0.7em;color:#666;font-weight:normal;">(${pages.length})</span>
  </h2>`;

  if (pages.length === 0) {
    html += `<p style="color:#666;font-style:italic;padding:8px 0;">Keine Beziehungen angelegt.</p>`;
    return html;
  }

  html += `<div style="display:grid;grid-template-columns:repeat(3,1fr);gap:16px;padding:8px 0;">`;

  for (const p of pages) {
    const idA = p.entitaet_a || "";
    const idB = p.entitaet_b || "";
    const filePath = p.file.path;

    html += `
      <div style="border:1px solid #333;border-radius:10px;padding:12px;text-align:center;background:#1e1e1e;">
        <a data-href="${filePath}" href="${filePath}" class="internal-link" style="text-decoration:none;color:inherit;">
          <div style="display:flex;gap:8px;justify-content:center;align-items:center;margin-bottom:10px;">
            ${imgHtml(idA, entityMap)}
            <div style="font-size:1.4em;color:#555;flex-shrink:0;">↔</div>
            ${imgHtml(idB, entityMap)}
          </div>
          <div style="font-size:0.75em;font-weight:600;line-height:1.4;color:#ccc;">
            ${formatName(idA)}<br><span style="color:#555;">↔</span><br>${formatName(idB)}
          </div>
        </a>
        <div style="margin-top:8px;">${valenzKette(p.valenz_verlauf)}</div>
        <div style="font-size:0.6em;color:#555;margin-top:4px;">v${p.version || "?"} · ${p.status || "?"}</div>
      </div>`;
  }

  html += `</div>`;
  return html;
}

// ============================================================
// Ausgabe
// ============================================================
const entityMap = buildEntityMap();
let output = "";
output += renderSection("Charaktere ↔ Charaktere", "charakter-charakter", entityMap);
output += renderSection("Charaktere ↔ Orte", "charakter-ort", entityMap);
output += renderSection("Charaktere ↔ Gegenstände", "charakter-gegenstand", entityMap);
dv.container.innerHTML = output;
```

---

## Alle Beziehungen – Tabelle

```dataviewjs
const VALENZ_FARBEN = {
  positiv:   "#4caf50",
  negativ:   "#e53935",
  neutral:   "#9e9e9e",
  angespannt:"#ff9800",
  komplex:   "#ab47bc"
};

function formatName(entityId) {
  const match = (entityId || "").match(/^(?:CHAR|GGS|ORT)-(.+)$/);
  if (!match) return entityId || "–";
  return match[1].split("-").map(w => w.charAt(0).toUpperCase() + w.slice(1)).join(" ");
}

function valenzKetteText(verlauf) {
  if (!verlauf || !Array.isArray(verlauf) || verlauf.length === 0) return "–";
  if (verlauf.length === 1) return verlauf[0].wert || "–";
  if (verlauf.length <= 3)  return verlauf.map(v => v.wert || "?").join(" → ");
  return (verlauf[0].wert || "?") + " → … → " + (verlauf[verlauf.length - 1].wert || "?");
}

const pages = dv.pages('"Roman_Split/beziehungen"')
  .where(p => p.doc_type !== "index")
  .sort(p => [p.beziehungstyp, p.file.name], "asc");

const rows = pages.map(p => {
  const verlauf = p.valenz_verlauf;
  const initialWert = (verlauf && Array.isArray(verlauf) && verlauf.length > 0)
    ? (verlauf[0].wert || "–") : "–";
  const farbe = VALENZ_FARBEN[initialWert] || "#666";
  const initialBadge = `<span style="color:${farbe};font-weight:600;">${initialWert}</span>`;

  return [
    p.file.link,
    formatName(p.entitaet_a),
    formatName(p.entitaet_b),
    p.beziehungstyp || "–",
    initialBadge,
    valenzKetteText(verlauf),
    p.version || "–",
    p.status || "–"
  ];
});

dv.table(
  ["Datei", "Entität A", "Entität B", "Typ", "Valenz (Start)", "Verlauf", "Version", "Status"],
  rows
);
```
