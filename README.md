OSCAR ALESSANDRO CARRANZA ORELLANA 1890-22-5573
en el primer parcial de desarrollo web implementamos varias tecnologias que son el Visaul studi code donde utilice toda la estructura de 
mi codigo basado a HTML con boostrap ademas de esto tambien se utilizo una API.
Las caractersiticas son: 
Tablas interactivas 
Tablas creadas por sexo 
poblacion por grupos de edad 
Tambien hay tablas por cada uno de los pueblos(departamentos)

Tas tecnologias utilizadas son 
HTML
BOOSTRAP
API
BACKEND 

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Censo 2018 — El Progreso 1890-22-5573</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" />
  <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.5/font/bootstrap-icons.css" rel="stylesheet" />
  <style>
    /* ===== Paleta y tokens de diseño ===== */
    :root{
      --bg: #0b1020;                 /* fondo general */
      --bg-2: #0f152b;               /* fondo secundario */
      --card: rgba(255,255,255,.06); /* tarjetas traslúcidas */
      --card-border: rgba(255,255,255,.14);
      --text: #e9ecf8;
      --muted: #a9b1c7;
      --primary: #8b5cf6;            /* violeta */
      --primary-2:#6d28d9;
      --accent: #10b981;             /* verde */
      --accent-2:#059669;
      --table-head: rgba(139,92,246,.16);
      --chip-bg: rgba(16,185,129,.15);
      --chip-bd: rgba(16,185,129,.35);
      --striped: rgba(255,255,255,.04);
      --shadow: 0 10px 30px rgba(0,0,0,.35);
      --radius: 18px;
    }

    /* ===== Base ===== */
    html, body { height: 100%; }
    body {
      background:
        radial-gradient(1200px 600px at 10% -10%, rgba(16,185,129,.10), transparent 60%),
        radial-gradient(800px 500px at 110% 10%, rgba(139,92,246,.15), transparent 55%),
        var(--bg);
      color: var(--text);
    }
    .navbar {
      background: linear-gradient(90deg, var(--bg-2), #141b35 40%, #141b35 60%, var(--bg-2));
      border-bottom: 1px solid rgba(255,255,255,.08);
      box-shadow: var(--shadow);
    }
    .navbar-brand { letter-spacing:.3px; }

    /* ===== Tarjetas “glass” ===== */
    .card {
      background: var(--card);
      border: 1px solid var(--card-border);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      backdrop-filter: blur(6px);
    }
    .card-header {
      background: linear-gradient(135deg, var(--primary) 0%, var(--primary-2) 100%);
      color:#fff;
      border-top-left-radius: var(--radius);
      border-top-right-radius: var(--radius);
      font-weight: 600;
      letter-spacing:.2px;
    }

    /* ===== Tablas ===== */
    .table { color: var(--text); margin:0; }
    .table thead th{
      background: var(--table-head);
      color:#dfe6ff;
      border-bottom: 1px solid rgba(255,255,255,.15);
    }
    .table tbody tr:nth-child(odd){ background: var(--striped); }
    .table tbody tr:hover{ background: rgba(139,92,246,.10); }
    .table td, .table th { border-color: rgba(255,255,255,.08)!important; }
    .num { text-align:right; white-space:nowrap; }

    /* ===== Badges y chips ===== */
    .badge-soft{
      background: var(--chip-bg);
      color:#d1fae5;
      border: 1px solid var(--chip-bd);
      padding:.45rem .6rem;
      border-radius: 999px;
      font-weight:600;
    }

    /* ===== Botones ===== */
    .btn-primary{
      background: linear-gradient(135deg, var(--primary), var(--primary-2));
      border: 1px solid rgba(255,255,255,.18);
      border-radius: 14px;
      transition: transform .08s ease, filter .2s ease;
    }
    .btn-primary:hover{ filter: brightness(1.05); transform: translateY(-1px); }
    .btn-outline-secondary{
      color:#dbe3ff;
      border-color: rgba(255,255,255,.22);
      background: rgba(255,255,255,.03);
      border-radius: 14px;
    }
    .btn-outline-secondary:hover{
      background: rgba(255,255,255,.08);
      color:#fff;
    }

    /* ===== Inputs ===== */
    .form-select, .form-control{
      background: rgba(255,255,255,.05);
      color: var(--text);
      border: 1px solid rgba(255,255,255,.15);
      border-radius: 12px;
    }
    .form-select:focus, .form-control:focus{
      border-color: var(--primary);
      box-shadow: 0 0 0 .2rem rgba(139,92,246,.25);
    }
    label.form-label{ color: var(--muted); }

    /* ===== Alertas / status ===== */
    .alert{
      border-radius:12px;
      border:1px solid rgba(255,255,255,.18);
      color:#111827;
      font-weight:600;
    }
    .alert-info{ background: #dbeafe; }
    .alert-success{ background:#d1fae5; }
    .alert-danger{ background:#fee2e2; }

    /* ===== Footer ===== */
    footer{
      background: linear-gradient(90deg, var(--accent-2), var(--accent));
      color:#052016;
      font-weight:700;
      letter-spacing:.2px;
      border-top-left-radius: var(--radius);
      border-top-right-radius: var(--radius);
      box-shadow: var(--shadow);
    }

    /* ===== Pequeños toques ===== */
    .shadow-soft{ box-shadow: var(--shadow); }
    a, a:hover{ color:#c4b5fd; }
  </style>
</head>
<body>
  <nav class="navbar navbar-dark">
    <div class="container">
      <span class="navbar-brand fw-bold">
        <i class="bi bi-graph-up-arrow me-2"></i>XII Censo Nacional De Poblacion y VII De Vivienda — El Progreso 1890-22-5573
      </span>
      <span class="navbar-text text-white-50 small">Pagina web </span>
    </div>
  </nav>

  <main class="container my-4">
    <div class="card shadow-soft mb-3">
      <div class="card-body">
        <div class="row g-3 align-items-end">
          <div class="col-md-6">
            <label for="selMunicipio" class="form-label">Municipio</label>
            <select id="selMunicipio" class="form-select">
              <option value="201">201 — Guastatoya</option>
              <option value="202">202 — Morazán</option>
              <option value="203">203 — San Agustín Acasaguastlán</option>
              <option value="204">204 — San Cristóbal Acasaguastlán</option>
              <option value="205">205 — El Jícaro</option>
              <option value="206">206 — Sansare</option>
              <option value="207">207 — Sanarate</option>
              <option value="208">208 — San Antonio La Paz</option>
            </select>
          </div>
          <div class="col-md-3">
            <button id="btnCargar" class="btn btn-primary w-100">
              <i class="bi bi-arrow-repeat me-1"></i>Cargar datos
            </button>
          </div>
          <div class="col-md-3">
            <a id="apiLink" class="btn btn-outline-secondary w-100" target="_blank" rel="noreferrer">
              <i class="bi bi-box-arrow-up-right me-1"></i>Abrir URL API
            </a>
          </div>
        </div>
        <div id="status" class="mt-3"></div>
      </div>
    </div>

    <!-- Resumen -->
    <div class="card shadow-soft mb-4">
      <div class="card-body d-flex flex-wrap gap-3 align-items-baseline">
        <h5 class="mb-0 text-white">Municipio: 
  <span id="muniNombre" class="badge bg-danger text-white">—</span>
</h5>

        <div>Población total: <strong id="pobTotal">—</strong></div>
      </div>
    </div>

    <!-- Población por sexo -->
    <div class="card shadow-soft mb-3">
      <div class="card-header"><i class="bi bi-gender-ambiguous me-2"></i>Población por sexo</div>
      <div class="table-responsive">
        <table class="table table-sm table-striped align-middle mb-0">
          <thead><tr><th>Sexo</th><th class="num">Cantidad</th><th class="num">Porcentaje</th></tr></thead>
          <tbody id="tbodySexo"></tbody>
        </table>
      </div>
    </div>

    <!-- Población por área -->
    <div class="card shadow-soft mb-3">
      <div class="card-header"><i class="bi bi-geo-alt me-2"></i>Población por área</div>
      <div class="table-responsive">
        <table class="table table-sm table-striped align-middle mb-0">
          <thead><tr><th>Área</th><th class="num">Cantidad</th><th class="num">Porcentaje</th></tr></thead>
          <tbody id="tbodyArea"></tbody>
        </table>
      </div>
    </div>

    <!-- Población por grandes grupos de edad -->
    <div class="card shadow-soft mb-3">
      <div class="card-header"><i class="bi bi-people me-2"></i>Población por grandes grupos de edad</div>
      <div class="table-responsive">
        <table class="table table-sm table-striped align-middle mb-0">
          <thead><tr><th>Grupo</th><th class="num">Cantidad</th><th class="num">Porcentaje</th></tr></thead>
          <tbody id="tbodyEdad"></tbody>
        </table>
      </div>
    </div>

    <!-- Población por pueblos -->
    <div class="card shadow-soft mb-4">
      <div class="card-header"><i class="bi bi-globe-americas me-2"></i>Población por pueblos</div>
      <div class="table-responsive">
        <table class="table table-sm table-striped align-middle mb-0">
          <thead><tr><th>Pueblo</th><th class="num">Cantidad</th><th class="num">Porcentaje</th></tr></thead>
          <tbody id="tbodyPueblos"></tbody>
        </table>
      </div>
    </div>
  </main>

  <footer class="text-white text-center py-3 mt-4">
    Diseñado por: <strong>Oscar Alessandro Carranza Orellana</strong> — <span>1890-22-5573</span>
  </footer>

  <script>
    const API_BASE = 'https://censopoblacion.azurewebsites.net/API/indicadores/2/';

    const selMunicipio = document.getElementById('selMunicipio');
    const btnCargar    = document.getElementById('btnCargar');
    const apiLink      = document.getElementById('apiLink');
    const statusBox    = document.getElementById('status');

    const muniNombre = document.getElementById('muniNombre');
    const pobTotalEl = document.getElementById('pobTotal');

    const tbSexo = document.getElementById('tbodySexo');
    const tbArea = document.getElementById('tbodyArea');
    const tbEdad = document.getElementById('tbodyEdad');
    const tbPue  = document.getElementById('tbodyPueblos');

    // === helpers numéricos robustos
    const num = (v) => {
      if (typeof v === 'number') return v;
      if (v == null) return NaN;
      const n = Number(String(v).replace(/,/g, ''));
      return Number.isFinite(n) ? n : NaN;
    };
    const fmt = (n) => Number.isFinite(n) ? n.toLocaleString('es-GT') : '—';
    const pct = (part, total) =>
      (Number.isFinite(part) && Number.isFinite(total) && total > 0)
        ? (Math.round((part/total)*10000)/100).toFixed(2) + '%'
        : '—';

    function notify(msg, type='info'){
      statusBox.innerHTML = `<div class="alert alert-${type} py-2 my-0">${msg}</div>`;
      setTimeout(()=>statusBox.innerHTML='', 3000);
    }

    function updateApiLink(code){
      const url = API_BASE + code;
      apiLink.href = url;
      apiLink.textContent = `API: indicadores/2/${code}`;
    }

    // === fetch con doble parse cuando la API viene como string
    async function fetchMunicipio(code){
      const res = await fetch(API_BASE + code, { headers:{ 'Accept':'application/json' } });
      if (!res.ok) throw new Error('HTTP ' + res.status);
      const payload = await res.json();   // puede ser objeto o string
      return (typeof payload === 'string') ? JSON.parse(payload) : payload;
    }

    function render(d){
      const total = num(d.pob_total);

      // Encabezado
      muniNombre.textContent = d?.nombre || `Código ${d?.municipio_id ?? ''}`;
      pobTotalEl.textContent = fmt(total);

      // Sexo
      const h = num(d.total_sexo_hombre), m = num(d.total_sexo_mujeres);
      const ph = Number.isFinite(num(d.porc_sexo_hombre)) ? num(d.porc_sexo_hombre).toFixed(2)+'%' : pct(h,total);
      const pm = Number.isFinite(num(d.porc_sexo_mujeres)) ? num(d.porc_sexo_mujeres).toFixed(2)+'%' : pct(m,total);
      tbSexo.innerHTML = `
        <tr><td>Hombres</td><td class="num">${fmt(h)}</td><td class="num">${ph}</td></tr>
        <tr><td>Mujeres</td><td class="num">${fmt(m)}</td><td class="num">${pm}</td></tr>`;

      // Área
      const u = num(d.total_sector_urbano), r = num(d.total_sector_rural);
      const pu = Number.isFinite(num(d.porc_sector_urbano)) ? num(d.porc_sector_urbano).toFixed(2)+'%' : pct(u,total);
      const pr = Number.isFinite(num(d.porc_sector_rural))  ? num(d.porc_sector_rural).toFixed(2)+'%'  : pct(r,total);
      tbArea.innerHTML = `
        <tr><td>Urbana</td><td class="num">${fmt(u)}</td><td class="num">${pu}</td></tr>
        <tr><td>Rural</td><td class="num">${fmt(r)}</td><td class="num">${pr}</td></tr>`;

      // Edad
      const e014 = num(d.pob_edad_014), e1564 = num(d.pob_edad_1564), e65 = num(d.pob_edad_65);
      const pe014 = Number.isFinite(num(d.porc_edad_014)) ? num(d.porc_edad_014).toFixed(2)+'%' : pct(e014,total);
      const pe1564= Number.isFinite(num(d.porc_edad_1564))? num(d.porc_edad_1564).toFixed(2)+'%' : pct(e1564,total);
      const pe65  = Number.isFinite(num(d.porc_edad_65))  ? num(d.porc_edad_65).toFixed(2)+'%'  : pct(e65,total);
      tbEdad.innerHTML = `
        <tr><td>0–14 años</td><td class="num">${fmt(e014)}</td><td class="num">${pe014}</td></tr>
        <tr><td>15–64 años</td><td class="num">${fmt(e1564)}</td><td class="num">${pe1564}</td></tr>
        <tr><td>65 y más años</td><td class="num">${fmt(e65)}</td><td class="num">${pe65}</td></tr>`;

      // Pueblos
      const maya=num(d.pob_pueblo_maya), gar=num(d.pob_pueblo_garifuna),
            xin=num(d.pob_pueblo_xinca), afr=num(d.pob_pueblo_afrodescendiente),
            lad=num(d.pob_pueblo_ladino), ext=num(d.pob_pueblo_extranjero);
      const pmaya=Number.isFinite(num(d.porc_pueblo_maya)) ? num(d.porc_pueblo_maya).toFixed(2)+'%' : pct(maya,total);
      const pgar =Number.isFinite(num(d.porc_pueblo_garifuna)) ? num(d.porc_pueblo_garifuna).toFixed(2)+'%' : pct(gar,total);
      const pxin =Number.isFinite(num(d.porc_pueblo_xinca)) ? num(d.porc_pueblo_xinca).toFixed(2)+'%' : pct(xin,total);
      const pafr =Number.isFinite(num(d.porc_pueblo_afrodescendiente)) ? num(d.porc_pueblo_afrodescendiente).toFixed(2)+'%' : pct(afr,total);
      const plad =Number.isFinite(num(d.porc_pueblo_ladino)) ? num(d.porc_pueblo_ladino).toFixed(2)+'%' : pct(lad,total);
      const pext =Number.isFinite(num(d.porc_pueblo_extranjero)) ? num(d.porc_pueblo_extranjero).toFixed(2)+'%' : pct(ext,total);
      tbPue.innerHTML = `
        <tr><td>Maya</td><td class="num">${fmt(maya)}</td><td class="num">${pmaya}</td></tr>
        <tr><td>Garífuna</td><td class="num">${fmt(gar)}</td><td class="num">${pgar}</td></tr>
        <tr><td>Xinca</td><td class="num">${fmt(xin)}</td><td class="num">${pxin}</td></tr>
        <tr><td>Afrodescendiente/Criollo/Afromestizo</td><td class="num">${fmt(afr)}</td><td class="num">${pafr}</td></tr>
        <tr><td>Ladino</td><td class="num">${fmt(lad)}</td><td class="num">${plad}</td></tr>
        <tr><td>Extranjero</td><td class="num">${fmt(ext)}</td><td class="num">${pext}</td></tr>`;
    }

    async function loadMunicipio(code){
      try{
        notify(`Consultando API para código ${code}…`);
        updateApiLink(code);
        const data = await fetchMunicipio(code);  // <-- devuelve el OBJETO real
        render(data);
        notify('Datos cargados ✅', 'success');
      }catch(e){
        console.error(e);
        notify('No se pudo leer la API. Usa Live Server o GitHub Pages (CORS).', 'danger');
      }
    }

    // eventos + arranque
    btnCargar.addEventListener('click', ()=> loadMunicipio(Number(selMunicipio.value)));
    selMunicipio.addEventListener('change', ()=> updateApiLink(Number(selMunicipio.value)));
    updateApiLink(Number(selMunicipio.value));
    loadMunicipio(Number(selMunicipio.value));
  </script>
</body>
</html>
