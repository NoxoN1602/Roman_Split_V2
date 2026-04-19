---
doc_type: index
doc_id: "Index-CHAR"
version: "1.0"
status: aktuell
kanon_stufe: objektiv
erstellt: "2026-04-19"
letzte_aenderung: "2026-04-19"
autor_agent: charakterentwickler
tags:
  - index
  - character
---

# Charaktere – Übersicht

## Galerie

```dataviewjs
const pages = dv.pages('#charakter')
  .where(p => p.file.folder === "Roman_Split/charaktere")
  .sort(p => p.file.name, "asc");

let html = '<div style="display:grid;grid-template-columns:repeat(8,1fr);gap:16px;padding:16px 0;">';
for (const p of pages) {
  const name = p.file.name
    .split("-")
    .map(w => w.charAt(0).toUpperCase() + w.slice(1))
    .join(" ");
  const imgVaultPath = p.bild ? p.file.folder + "/" + p.bild : null;
  const imgHtml = imgVaultPath
    ? `<img src="${app.vault.adapter.getResourcePath(imgVaultPath)}"
           style="width:100%;aspect-ratio:3/4;object-fit:cover;border-radius:8px;display:block;">`
    : `<div style="width:100%;aspect-ratio:3/4;background:#2a2a2a;border-radius:8px;
           display:flex;align-items:center;justify-content:center;
           color:#666;font-size:0.7em;text-align:center;">kein<br>Bild</div>`;
  html += `<div style="text-align:center;">
    <a data-href="${p.file.path}" href="${p.file.path}" class="internal-link"
       style="text-decoration:none;">${imgHtml}</a>
    <div style="margin-top:6px;font-weight:600;font-size:0.8em;line-height:1.3;">${name}</div>
  </div>`;
}
html += '</div>';
dv.container.innerHTML = html;
```

---

## Steckbriefe

```dataviewjs
function calcAlter(geburtsdatum) {
  if (!geburtsdatum || geburtsdatum === "unbekannt") return "unbekannt";
  const birth = new Date(geburtsdatum);
  if (isNaN(birth.getTime())) return "unbekannt";
  const ref = new Date();
  let alter = ref.getFullYear() - birth.getFullYear();
  const m = ref.getMonth() - birth.getMonth();
  if (m < 0 || (m === 0 && ref.getDate() < birth.getDate())) alter--;
  return alter;
}

const pages = dv.pages('#charakter')
  .where(p => p.file.folder === "Roman_Split/charaktere")
  .sort(p => p.file.name, "asc");

const rows = pages.map(p => {
  const typen = (p.tags || [])
    .filter(t => t !== "charakter" && t !== "index")
    .join(", ");
  return [
    p.file.link,
    calcAlter(p.geburtsdatum),
    typen || "–",
    p.version  || "–",
    p.status   || "–"
  ];
});

dv.table(["Name", "Alter", "Typ", "Version", "Status"], rows);
```
