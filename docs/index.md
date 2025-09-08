---
title: Welcome
hide:
  - toc
---
<div id="filter-docs"></div>

# Welcome to Verve Docs

Find topics about your integrations. Choose your **role**, **brand**, and **content type** to jump straight to the right docs.

<div class="selector">
  <div class="row">
    <label>Role</label>
    <select id="roleSelect">
      <option value="" selected disabled>Choose…</option>
      <option value="publisher">Publisher</option>
      <option value="demand">Demand Partner</option>
      <option value="marketer">Marketer</option>
    </select>
  </div>

  <div class="row">
    <label>Brand</label>
    <select id="brandSelect" disabled>
      <option value="" selected disabled>Choose…</option>
      <option value="smaato">Smaato</option>
      <option value="pubnative">Pubnative</option>
    </select>
  </div>

  <div class="row">
    <label>Content</label>
    <select id="typeSelect" disabled>
      <option value="" selected disabled>Choose…</option>
      <option value="guides">Guides</option>
      <option value="api">API Reference</option>
    </select>
  </div>
</div>

<div id="resultWrap">

  <!-- =============== RESULTS: SMAATO =============== -->
  <div class="result" data-brand="smaato" data-type="guides" hidden>
    <div class="card">
      <h3>Smaato — Guides</h3>
      <p>Implementation and optimization content for publishers and demand partners.</p>
      <ul class="link-list">
        <li><a class="md-button" href="smaato/getting-started/">Getting Started</a></li>
        <li><a class="md-button" href="smaato/inventory-setup/">Inventory Setup</a></li>
        <li><a class="md-button" href="smaato/spx-mediation/">SPX Mediation</a></li>
        <li><a class="md-button" href="smaato/spx-ott/">SPX OTT Platform</a></li>
        <li><a class="md-button" href="smaato/reporting-ui/">Reporting UI</a></li>
        <li><a class="md-button" href="smaato/privacy-sandbox/">Google Privacy Sandbox</a></li>
        <li><a class="md-button" href="smaato/sdk/ios/">SDK – iOS</a></li>
        <li><a class="md-button" href="smaato/sdk/android/">SDK – Android</a></li>
      </ul>
    </div>
  </div>

  <div class="result" data-brand="smaato" data-type="api" hidden>
    <div class="card">
      <h3>Smaato — API Reference</h3>
      <p>Endpoints and schemas.</p>
      <a class="md-button md-button--primary" href="smaato/api-reference/">Open Smaato API Reference</a>
    </div>
  </div>

  <!-- =============== RESULTS: PUBNATIVE =============== -->
  <div class="result" data-brand="pubnative" data-type="guides" hidden>
    <div class="card">
      <h3>Pubnative — Guides</h3>
      <ul class="link-list">
        <li><a class="md-button" href="pubnative/getting-started/">Getting Started</a></li>
        <li><a class="md-button" href="pubnative/inventory-setup/">Inventory Setup</a></li>
        <li><a class="md-button" href="pubnative/mediation/">Mediation</a></li>
        <li><a class="md-button" href="pubnative/reporting-ui/">Reporting UI</a></li>
        <li><a class="md-button" href="pubnative/privacy-sandbox/">Google Privacy Sandbox</a></li>
        <li><a class="md-button" href="pubnative/sdk/ios/">SDK – iOS</a></li>
        <li><a class="md-button" href="pubnative/sdk/android/">SDK – Android</a></li>
      </ul>
    </div>
  </div>

  <div class="result" data-brand="pubnative" data-type="api" hidden>
    <div class="card">
      <h3>Pubnative — API Reference</h3>
      <a class="md-button md-button--primary" href="pubnative/api-reference/">Open Pubnative API Reference</a>
    </div>
  </div>

  <!-- Optional: marketer routes could point to brand-agnostic or to both -->
  <div class="result" data-brand="smaato" data-type="marketer" hidden></div>
  <div class="result" data-brand="pubnative" data-type="marketer" hidden></div>
</div>

<script>
// Enable cascading selects
const roleSel  = document.getElementById('roleSelect');
const brandSel = document.getElementById('brandSelect');
const typeSel  = document.getElementById('typeSelect');
const results  = document.querySelectorAll('#resultWrap .result');

function reset(el){ el.selectedIndex = 0; el.disabled = true; }
function hideAll(){ results.forEach(r => r.hidden = true); }

roleSel.addEventListener('change', () => {
  // For now, role only gates enabling brand; adjust if you need role-specific routing
  brandSel.disabled = false;
  reset(typeSel);
  hideAll();
});

brandSel.addEventListener('change', () => {
  typeSel.disabled = false;
  hideAll();
});

typeSel.addEventListener('change', () => {
  hideAll();
  const brand = brandSel.value;
  const type = typeSel.value === 'guides' ? 'guides' : 'api';
  const match = document.querySelector(`.result[data-brand="${brand}"][data-type="${type}"]`);
  if (match) match.hidden = false;
});
</script>
