<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Encuesta de Mercado — PaletDo'27</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Josefin+Sans:wght@200;300;400;600&display=swap" rel="stylesheet">
<style>
  :root {
    --void: #080810;
    --deep: #0f0f1a;
    --panel: #13131f;
    --border: rgba(255,255,255,0.07);
    --gold: #c9a84c;
    --gold-soft: rgba(201,168,76,0.15);
    --gold-glow: rgba(201,168,76,0.4);
    --teal: #00c9b1;
    --teal-soft: rgba(0,201,177,0.12);
    --text: #e8e4da;
    --muted: rgba(232,228,218,0.45);
    --accent: #ff6b6b;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Josefin Sans', sans-serif;
    background: var(--void);
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* BACKGROUND EFFECT */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background:
      radial-gradient(ellipse 60% 40% at 20% 10%, rgba(201,168,76,0.06) 0%, transparent 60%),
      radial-gradient(ellipse 50% 35% at 80% 90%, rgba(0,201,177,0.05) 0%, transparent 60%);
    pointer-events: none;
    z-index: 0;
  }

  .wrap {
    position: relative;
    z-index: 1;
    max-width: 720px;
    margin: 0 auto;
    padding: 0 20px 80px;
  }

  /* ── HEADER ── */
  header {
    text-align: center;
    padding: 60px 0 48px;
    border-bottom: 1px solid var(--border);
    margin-bottom: 48px;
  }

  .brand-mark {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 24px;
  }
  .brand-mark .dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--gold);
    box-shadow: 0 0 8px var(--gold-glow);
  }
  .brand-mark span {
    font-size: 10px;
    letter-spacing: 5px;
    text-transform: uppercase;
    color: var(--gold);
    font-weight: 300;
  }

  header h1 {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(32px, 8vw, 52px);
    font-weight: 300;
    letter-spacing: 2px;
    line-height: 1.1;
    color: var(--text);
    margin-bottom: 8px;
  }
  header h1 em {
    font-style: italic;
    color: var(--gold);
  }

  header p {
    font-size: 11px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
    margin-top: 16px;
  }

  /* ── TABS ── */
  .tabs {
    display: flex;
    gap: 0;
    margin-bottom: 40px;
    border: 1px solid var(--border);
    border-radius: 4px;
    overflow: hidden;
  }
  .tab-btn {
    flex: 1;
    padding: 14px;
    background: transparent;
    border: none;
    color: var(--muted);
    font-family: 'Josefin Sans', sans-serif;
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    cursor: pointer;
    transition: all 0.3s;
    border-right: 1px solid var(--border);
  }
  .tab-btn:last-child { border-right: none; }
  .tab-btn.active {
    background: var(--gold-soft);
    color: var(--gold);
  }
  .tab-btn:hover:not(.active) {
    background: rgba(255,255,255,0.03);
    color: var(--text);
  }

  /* ── SECTION ── */
  .section-tag {
    font-size: 9px;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--teal);
    margin-bottom: 6px;
  }
  .section-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 22px;
    font-weight: 300;
    color: var(--text);
    margin-bottom: 28px;
    padding-bottom: 16px;
    border-bottom: 1px solid var(--border);
  }

  /* ── QUESTION CARD ── */
  .q-card {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 28px;
    margin-bottom: 20px;
    transition: border-color 0.3s;
  }
  .q-card:hover { border-color: rgba(201,168,76,0.2); }
  .q-card.answered { border-color: rgba(0,201,177,0.25); }

  .q-number {
    font-size: 9px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 10px;
  }
  .q-text {
    font-family: 'Cormorant Garamond', serif;
    font-size: 18px;
    font-weight: 400;
    color: var(--text);
    margin-bottom: 20px;
    line-height: 1.4;
  }

  /* OPTIONS */
  .options { display: flex; flex-direction: column; gap: 10px; }
  .opt {
    display: flex;
    align-items: center;
    gap: 14px;
    padding: 13px 16px;
    background: rgba(255,255,255,0.02);
    border: 1px solid var(--border);
    border-radius: 4px;
    cursor: pointer;
    transition: all 0.25s;
    font-size: 13px;
    letter-spacing: 0.5px;
    color: var(--muted);
    text-align: left;
  }
  .opt:hover {
    background: var(--gold-soft);
    border-color: rgba(201,168,76,0.3);
    color: var(--text);
  }
  .opt.selected {
    background: var(--gold-soft);
    border-color: var(--gold);
    color: var(--gold);
  }
  .opt .radio {
    width: 16px; height: 16px;
    border: 1px solid currentColor;
    border-radius: 50%;
    flex-shrink: 0;
    display: flex; align-items: center; justify-content: center;
    transition: all 0.2s;
  }
  .opt.selected .radio::after {
    content: '';
    width: 8px; height: 8px;
    background: var(--gold);
    border-radius: 50%;
    box-shadow: 0 0 6px var(--gold-glow);
  }

  /* SCALE QUESTION */
  .scale-opts {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
  }
  .scale-btn {
    flex: 1;
    min-width: 44px;
    padding: 12px 8px;
    background: rgba(255,255,255,0.02);
    border: 1px solid var(--border);
    border-radius: 4px;
    cursor: pointer;
    font-family: 'Cormorant Garamond', serif;
    font-size: 18px;
    color: var(--muted);
    transition: all 0.2s;
    text-align: center;
  }
  .scale-btn:hover { background: var(--gold-soft); color: var(--text); }
  .scale-btn.selected {
    background: var(--gold-soft);
    border-color: var(--gold);
    color: var(--gold);
    box-shadow: 0 0 12px var(--gold-soft);
  }
  .scale-labels {
    display: flex;
    justify-content: space-between;
    margin-top: 8px;
    font-size: 9px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
  }

  /* TEXTAREA */
  .q-textarea {
    width: 100%;
    background: rgba(255,255,255,0.02);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 14px 16px;
    color: var(--text);
    font-family: 'Josefin Sans', sans-serif;
    font-size: 13px;
    resize: vertical;
    min-height: 90px;
    transition: border-color 0.25s;
    letter-spacing: 0.5px;
  }
  .q-textarea:focus {
    outline: none;
    border-color: rgba(201,168,76,0.4);
  }
  .q-textarea::placeholder { color: var(--muted); }

  /* SUBMIT */
  .submit-zone { text-align: center; margin-top: 36px; }

  .btn-submit {
    display: inline-flex;
    align-items: center;
    gap: 12px;
    padding: 18px 48px;
    background: transparent;
    border: 1px solid var(--gold);
    border-radius: 3px;
    color: var(--gold);
    font-family: 'Josefin Sans', sans-serif;
    font-size: 10px;
    letter-spacing: 4px;
    text-transform: uppercase;
    cursor: pointer;
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
  }
  .btn-submit::before {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--gold);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.4s ease;
    z-index: -1;
  }
  .btn-submit:hover {
    color: var(--void);
  }
  .btn-submit:hover::before { transform: scaleX(1); }

  .progress-info {
    font-size: 10px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 16px;
  }
  .progress-bar-wrap {
    height: 2px;
    background: var(--border);
    border-radius: 1px;
    margin-bottom: 32px;
    overflow: hidden;
  }
  .progress-bar-fill {
    height: 100%;
    background: var(--gold);
    border-radius: 1px;
    transition: width 0.4s ease;
    box-shadow: 0 0 8px var(--gold-glow);
  }

  /* ── THANK YOU ── */
  #thankYou {
    display: none;
    text-align: center;
    padding: 60px 20px;
    animation: fadeIn 0.8s ease forwards;
  }
  #thankYou .big-icon {
    font-size: 48px;
    margin-bottom: 24px;
    filter: drop-shadow(0 0 12px var(--gold-glow));
  }
  #thankYou h2 {
    font-family: 'Cormorant Garamond', serif;
    font-size: 36px;
    font-weight: 300;
    color: var(--gold);
    margin-bottom: 12px;
  }
  #thankYou p {
    color: var(--muted);
    font-size: 12px;
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 32px;
  }
  .btn-results {
    display: inline-block;
    padding: 14px 36px;
    border: 1px solid var(--teal);
    border-radius: 3px;
    color: var(--teal);
    font-family: 'Josefin Sans', sans-serif;
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    cursor: pointer;
    background: transparent;
    transition: all 0.3s;
  }
  .btn-results:hover {
    background: var(--teal-soft);
  }

  /* ── RESULTS PANEL ── */
  #resultsPanel { display: none; }

  .results-header {
    text-align: center;
    padding: 40px 0 32px;
    margin-bottom: 32px;
    border-bottom: 1px solid var(--border);
  }
  .results-header h2 {
    font-family: 'Cormorant Garamond', serif;
    font-size: 38px;
    font-weight: 300;
    color: var(--text);
    margin-bottom: 8px;
  }
  .results-header p {
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
  }

  .stat-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
    margin-bottom: 40px;
  }
  .stat-box {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 20px;
    text-align: center;
  }
  .stat-box .val {
    font-family: 'Cormorant Garamond', serif;
    font-size: 36px;
    color: var(--gold);
    line-height: 1;
    margin-bottom: 6px;
  }
  .stat-box .lbl {
    font-size: 9px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
  }

  .result-card {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 28px;
    margin-bottom: 20px;
  }
  .result-card .rq-num {
    font-size: 9px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 6px;
  }
  .result-card .rq-text {
    font-family: 'Cormorant Garamond', serif;
    font-size: 17px;
    color: var(--text);
    margin-bottom: 20px;
  }

  .bar-item {
    margin-bottom: 14px;
  }
  .bar-label-row {
    display: flex;
    justify-content: space-between;
    margin-bottom: 6px;
    font-size: 12px;
    color: var(--muted);
  }
  .bar-label-row .pct { color: var(--gold); font-weight: 600; }
  .bar-track {
    height: 6px;
    background: rgba(255,255,255,0.05);
    border-radius: 3px;
    overflow: hidden;
  }
  .bar-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--gold), var(--teal));
    border-radius: 3px;
    transition: width 1s ease;
    box-shadow: 0 0 8px var(--gold-soft);
  }

  .responses-list {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  .response-bubble {
    background: rgba(255,255,255,0.03);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 12px 16px;
    font-size: 13px;
    color: var(--muted);
    font-style: italic;
    font-family: 'Cormorant Garamond', serif;
  }
  .no-responses {
    font-size: 11px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: rgba(255,255,255,0.2);
    text-align: center;
    padding: 20px;
  }

  .avg-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: var(--gold-soft);
    border: 1px solid rgba(201,168,76,0.3);
    border-radius: 3px;
    padding: 8px 14px;
    margin-top: 8px;
  }
  .avg-badge span:first-child {
    font-family: 'Cormorant Garamond', serif;
    font-size: 22px;
    color: var(--gold);
  }
  .avg-badge span:last-child {
    font-size: 9px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
  }

  .btn-back {
    display: inline-block;
    margin-top: 32px;
    padding: 14px 36px;
    border: 1px solid var(--border);
    border-radius: 3px;
    color: var(--muted);
    font-family: 'Josefin Sans', sans-serif;
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    cursor: pointer;
    background: transparent;
    transition: all 0.3s;
  }
  .btn-back:hover { color: var(--text); border-color: var(--text); }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(16px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .q-card { animation: fadeIn 0.5s ease both; }
  .q-card:nth-child(1)  { animation-delay: 0.05s; }
  .q-card:nth-child(2)  { animation-delay: 0.10s; }
  .q-card:nth-child(3)  { animation-delay: 0.15s; }
  .q-card:nth-child(4)  { animation-delay: 0.20s; }
  .q-card:nth-child(5)  { animation-delay: 0.25s; }
  .q-card:nth-child(6)  { animation-delay: 0.30s; }
  .q-card:nth-child(7)  { animation-delay: 0.35s; }
  .q-card:nth-child(8)  { animation-delay: 0.40s; }
  .q-card:nth-child(9)  { animation-delay: 0.45s; }
  .q-card:nth-child(10) { animation-delay: 0.50s; }

  @media (max-width: 480px) {
    .stat-row { grid-template-columns: 1fr 1fr; }
    .stat-row .stat-box:last-child { grid-column: span 2; }
  }
</style>
</head>
<body>
<div class="wrap">

  <!-- HEADER -->
  <header>
    <div class="brand-mark">
      <div class="dot"></div>
      <span>Investigación de Mercados</span>
      <div class="dot"></div>
    </div>
    <h1>Palet<em>Do</em>'27</h1>
    <p>Encuesta de preferencias del consumidor · Cócteles sin alcohol</p>
  </header>

  <!-- TABS -->
  <div class="tabs">
    <button class="tab-btn active" onclick="showTab('survey')">Responder Encuesta</button>
    <button class="tab-btn" onclick="showTab('results')">Ver Resultados</button>
  </div>

  <!-- ══════════════════════════════════════
       SURVEY PANEL
  ══════════════════════════════════════ -->
  <div id="surveyPanel">

    <div class="section-tag">Sección 01</div>
    <div class="section-title">Perfil del Consumidor</div>

    <!-- Q1 -->
    <div class="q-card" id="q1">
      <div class="q-number">Pregunta 01</div>
      <div class="q-text">¿Cuál es tu rango de edad?</div>
      <div class="options">
        <button class="opt" onclick="select(this,'q1','Menos de 15 años')"><span class="radio"></span>Menos de 15 años</button>
        <button class="opt" onclick="select(this,'q1','15 – 18 años')"><span class="radio"></span>15 – 18 años</button>
        <button class="opt" onclick="select(this,'q1','19 – 25 años')"><span class="radio"></span>19 – 25 años</button>
        <button class="opt" onclick="select(this,'q1','26 – 35 años')"><span class="radio"></span>26 – 35 años</button>
        <button class="opt" onclick="select(this,'q1','Más de 35 años')"><span class="radio"></span>Más de 35 años</button>
      </div>
    </div>

    <!-- Q2 -->
    <div class="q-card" id="q2">
      <div class="q-number">Pregunta 02</div>
      <div class="q-text">¿Con qué frecuencia consumes bebidas especiales (jugos, cócteles, etc.) en eventos o reuniones?</div>
      <div class="options">
        <button class="opt" onclick="select(this,'q2','Siempre que hay una reunión')"><span class="radio"></span>Siempre que hay una reunión</button>
        <button class="opt" onclick="select(this,'q2','Con frecuencia')"><span class="radio"></span>Con frecuencia</button>
        <button class="opt" onclick="select(this,'q2','Ocasionalmente')"><span class="radio"></span>Ocasionalmente</button>
        <button class="opt" onclick="select(this,'q2','Rara vez')"><span class="radio"></span>Rara vez</button>
      </div>
    </div>

    <div class="section-tag" style="margin-top:36px;">Sección 02</div>
    <div class="section-title">Conocimiento del Producto</div>

    <!-- Q3 -->
    <div class="q-card" id="q3">
      <div class="q-number">Pregunta 03</div>
      <div class="q-text">¿Conocías o habías probado antes cócteles sin alcohol con presentación de alta gama?</div>
      <div class="options">
        <button class="opt" onclick="select(this,'q3','Sí, los conozco y los he probado')"><span class="radio"></span>Sí, los conozco y los he probado</button>
        <button class="opt" onclick="select(this,'q3','Los conocía pero no los había probado')"><span class="radio"></span>Los conocía pero no los había probado</button>
        <button class="opt" onclick="select(this,'q3','No los conocía hasta ahora')"><span class="radio"></span>No los conocía hasta ahora</button>
      </div>
    </div>

    <!-- Q4 -->
    <div class="q-card" id="q4">
      <div class="q-number">Pregunta 04</div>
      <div class="q-text">¿Qué factor valoras más al elegir un cóctel sin alcohol?</div>
      <div class="options">
        <button class="opt" onclick="select(this,'q4','El sabor y combinación de frutas')"><span class="radio"></span>El sabor y combinación de frutas</button>
        <button class="opt" onclick="select(this,'q4','La presentación visual y estética')"><span class="radio"></span>La presentación visual y estética</button>
        <button class="opt" onclick="select(this,'q4','El precio accesible')"><span class="radio"></span>El precio accesible</button>
        <button class="opt" onclick="select(this,'q4','Que sea saludable y natural')"><span class="radio"></span>Que sea saludable y natural</button>
        <button class="opt" onclick="select(this,'q4','La exclusividad / experiencia de marca')"><span class="radio"></span>La exclusividad / experiencia de marca</button>
      </div>
    </div>

    <!-- Q5 -->
    <div class="q-card" id="q5">
      <div class="q-number">Pregunta 05</div>
      <div class="q-text">¿Cuánto estarías dispuesto/a a pagar por un cóctel sin alcohol de presentación premium?</div>
      <div class="options">
        <button class="opt" onclick="select(this,'q5','Menos de $5.000')"><span class="radio"></span>Menos de $5.000</button>
        <button class="opt" onclick="select(this,'q5','Entre $5.000 y $8.000')"><span class="radio"></span>Entre $5.000 y $8.000</button>
        <button class="opt" onclick="select(this,'q5','Entre $8.000 y $12.000')"><span class="radio"></span>Entre $8.000 y $12.000</button>
        <button class="opt" onclick="select(this,'q5','Más de $12.000 si la experiencia lo justifica')"><span class="radio"></span>Más de $12.000 si la experiencia lo justifica</button>
      </div>
    </div>

    <div class="section-tag" style="margin-top:36px;">Sección 03</div>
    <div class="section-title">Mercado y Distribución</div>

    <!-- Q6 -->
    <div class="q-card" id="q6">
      <div class="q-number">Pregunta 06</div>
      <div class="q-text">¿En qué espacios te gustaría encontrar PaletDo'27?</div>
      <div class="options">
        <button class="opt" onclick="select(this,'q6','Ferias y eventos escolares')"><span class="radio"></span>Ferias y eventos escolares</button>
        <button class="opt" onclick="select(this,'q6','Hoteles boutique y restaurantes')"><span class="radio"></span>Hoteles boutique y restaurantes</button>
        <button class="opt" onclick="select(this,'q6','Fiestas y reuniones privadas por encargo')"><span class="radio"></span>Fiestas y reuniones privadas por encargo</button>
        <button class="opt" onclick="select(this,'q6','Tiendas online con delivery')"><span class="radio"></span>Tiendas online con delivery</button>
        <button class="opt" onclick="select(this,'q6','Eventos corporativos y ferias de innovación')"><span class="radio"></span>Eventos corporativos y ferias de innovación</button>
      </div>
    </div>

    <!-- Q7 -->
    <div class="q-card" id="q7">
      <div class="q-number">Pregunta 07</div>
      <div class="q-text">¿Cuál de estos nombres de cóctel te parece más atractivo?</div>
      <div class="options">
        <button class="opt" onclick="select(this,'q7','Tropical Soul')"><span class="radio"></span>Tropical Soul</button>
        <button class="opt" onclick="select(this,'q7','Frutal Boom')"><span class="radio"></span>Frutal Boom</button>
        <button class="opt" onclick="select(this,'q7','Mint Kiss')"><span class="radio"></span>Mint Kiss</button>
        <button class="opt" onclick="select(this,'q7','Golden Fresa')"><span class="radio"></span>Golden Fresa</button>
      </div>
    </div>

    <div class="section-tag" style="margin-top:36px;">Sección 04</div>
    <div class="section-title">Percepción e Impacto</div>

    <!-- Q8 — SCALE -->
    <div class="q-card" id="q8">
      <div class="q-number">Pregunta 08</div>
      <div class="q-text">Del 1 al 5, ¿qué tan importante crees que es ofrecer bebidas sin alcohol en eventos sociales para jóvenes?</div>
      <div class="scale-opts">
        <button class="scale-btn" onclick="selectScale(this,'q8','1')">1</button>
        <button class="scale-btn" onclick="selectScale(this,'q8','2')">2</button>
        <button class="scale-btn" onclick="selectScale(this,'q8','3')">3</button>
        <button class="scale-btn" onclick="selectScale(this,'q8','4')">4</button>
        <button class="scale-btn" onclick="selectScale(this,'q8','5')">5</button>
      </div>
      <div class="scale-labels">
        <span>Poco importante</span>
        <span>Muy importante</span>
      </div>
    </div>

    <!-- Q9 — SCALE -->
    <div class="q-card" id="q9">
      <div class="q-number">Pregunta 09</div>
      <div class="q-text">¿Qué tan probable es que recomiendes PaletDo'27 después de probar el producto?</div>
      <div class="scale-opts">
        <button class="scale-btn" onclick="selectScale(this,'q9','1')">1</button>
        <button class="scale-btn" onclick="selectScale(this,'q9','2')">2</button>
        <button class="scale-btn" onclick="selectScale(this,'q9','3')">3</button>
        <button class="scale-btn" onclick="selectScale(this,'q9','4')">4</button>
        <button class="scale-btn" onclick="selectScale(this,'q9','5')">5</button>
      </div>
      <div class="scale-labels">
        <span>Poco probable</span>
        <span>Muy probable</span>
      </div>
    </div>

    <!-- Q10 — OPEN -->
    <div class="q-card" id="q10">
      <div class="q-number">Pregunta 10 — Opcional</div>
      <div class="q-text">¿Qué sabor o combinación de frutas te gustaría ver en PaletDo'27?</div>
      <textarea class="q-textarea" id="q10text" placeholder="Escribe tu sugerencia..." oninput="markAnswered('q10')"></textarea>
    </div>

    <!-- PROGRESS -->
    <div class="progress-info" id="progressInfo">0 de 9 preguntas respondidas</div>
    <div class="progress-bar-wrap">
      <div class="progress-bar-fill" id="progressFill" style="width:0%"></div>
    </div>

    <!-- SUBMIT -->
    <div class="submit-zone">
      <button class="btn-submit" onclick="submitSurvey()">
        <span>Enviar Respuestas</span>
        <span>→</span>
      </button>
    </div>

  </div><!-- /surveyPanel -->

  <!-- THANK YOU -->
  <div id="thankYou">
    <div class="big-icon">🥂</div>
    <h2>Gracias por tu aporte</h2>
    <p>Tu respuesta ha sido registrada · PaletDo'27</p>
    <button class="btn-results" onclick="showTab('results')">Ver Resultados en Tiempo Real →</button>
  </div>

  <!-- ══════════════════════════════════════
       RESULTS PANEL
  ══════════════════════════════════════ -->
  <div id="resultsPanel">
    <div class="results-header">
      <h2>Resultados</h2>
      <p id="totalCount">0 respuestas registradas</p>
    </div>

    <div class="stat-row" id="statRow"></div>
    <div id="resultsBody"></div>

    <div style="text-align:center;">
      <button class="btn-back" onclick="showTab('survey')">← Volver a la Encuesta</button>
    </div>
  </div>

</div><!-- /wrap -->

<script>
// ── DATA ──────────────────────────────────────────────────────────
const QUESTIONS = [
  { id:'q1',  type:'choice', text:'¿Cuál es tu rango de edad?',
    opts:['Menos de 15 años','15 – 18 años','19 – 25 años','26 – 35 años','Más de 35 años'] },
  { id:'q2',  type:'choice', text:'¿Con qué frecuencia consumes bebidas especiales en eventos?',
    opts:['Siempre que hay una reunión','Con frecuencia','Ocasionalmente','Rara vez'] },
  { id:'q3',  type:'choice', text:'¿Conocías cócteles sin alcohol de alta gama?',
    opts:['Sí, los conozco y los he probado','Los conocía pero no los había probado','No los conocía hasta ahora'] },
  { id:'q4',  type:'choice', text:'¿Qué factor valoras más en un cóctel sin alcohol?',
    opts:['El sabor y combinación de frutas','La presentación visual y estética','El precio accesible','Que sea saludable y natural','La exclusividad / experiencia de marca'] },
  { id:'q5',  type:'choice', text:'¿Cuánto pagarías por un cóctel sin alcohol premium?',
    opts:['Menos de $5.000','Entre $5.000 y $8.000','Entre $8.000 y $12.000','Más de $12.000 si la experiencia lo justifica'] },
  { id:'q6',  type:'choice', text:'¿Dónde te gustaría encontrar PaletDo\'27?',
    opts:['Ferias y eventos escolares','Hoteles boutique y restaurantes','Fiestas y reuniones privadas por encargo','Tiendas online con delivery','Eventos corporativos y ferias de innovación'] },
  { id:'q7',  type:'choice', text:'¿Cuál nombre de cóctel te parece más atractivo?',
    opts:['Tropical Soul','Frutal Boom','Mint Kiss','Golden Fresa'] },
  { id:'q8',  type:'scale',  text:'Importancia de bebidas sin alcohol en eventos (1-5)' },
  { id:'q9',  type:'scale',  text:'Probabilidad de recomendar PaletDo\'27 (1-5)' },
  { id:'q10', type:'open',   text:'¿Qué sabor o combinación sugerirías?' },
];

// ── STORAGE ───────────────────────────────────────────────────────
const STORE_KEY = 'paletdo27_survey_v2';

function loadData() {
  try { return JSON.parse(localStorage.getItem(STORE_KEY)) || { responses: [] }; }
  catch { return { responses: [] }; }
}
function saveData(d) {
  try { localStorage.setItem(STORE_KEY, JSON.stringify(d)); } catch {}
}

// ── STATE ─────────────────────────────────────────────────────────
const answers = {};

function select(btn, qid, val) {
  document.querySelectorAll(`#${qid} .opt`).forEach(b => b.classList.remove('selected'));
  btn.classList.add('selected');
  answers[qid] = val;
  document.getElementById(qid).classList.add('answered');
  updateProgress();
}

function selectScale(btn, qid, val) {
  btn.closest('.q-card').querySelectorAll('.scale-btn').forEach(b => b.classList.remove('selected'));
  btn.classList.add('selected');
  answers[qid] = val;
  document.getElementById(qid).classList.add('answered');
  updateProgress();
}

function markAnswered(qid) {
  const v = document.getElementById('q10text').value.trim();
  if (v) { answers[qid] = v; document.getElementById(qid).classList.add('answered'); }
  else { delete answers[qid]; }
  updateProgress();
}

function updateProgress() {
  const required = ['q1','q2','q3','q4','q5','q6','q7','q8','q9'];
  const done = required.filter(q => answers[q]).length;
  document.getElementById('progressInfo').textContent = `${done} de 9 preguntas respondidas`;
  document.getElementById('progressFill').style.width = (done / 9 * 100) + '%';
}

function submitSurvey() {
  const required = ['q1','q2','q3','q4','q5','q6','q7','q8','q9'];
  const missing = required.filter(q => !answers[q]);
  if (missing.length > 0) {
    const card = document.getElementById(missing[0]);
    card.scrollIntoView({ behavior: 'smooth', block: 'center' });
    card.style.borderColor = 'rgba(255,107,107,0.5)';
    setTimeout(() => card.style.borderColor = '', 2000);
    return;
  }
  const data = loadData();
  data.responses.push({ ...answers, ts: Date.now() });
  saveData(data);

  document.getElementById('surveyPanel').style.display = 'none';
  document.getElementById('thankYou').style.display = 'block';
  document.getElementById('thankYou').scrollIntoView({ behavior: 'smooth' });
}

// ── RESULTS ───────────────────────────────────────────────────────
function renderResults() {
  const data = loadData();
  const rs = data.responses;
  const total = rs.length;

  document.getElementById('totalCount').textContent =
    total === 0 ? 'Aún sin respuestas' :
    total === 1 ? '1 respuesta registrada' : `${total} respuestas registradas`;

  // Stats row
  let avgQ8 = 0, avgQ9 = 0;
  if (total > 0) {
    avgQ8 = (rs.reduce((s, r) => s + (parseInt(r.q8)||0), 0) / total).toFixed(1);
    avgQ9 = (rs.reduce((s, r) => s + (parseInt(r.q9)||0), 0) / total).toFixed(1);
  }
  document.getElementById('statRow').innerHTML = `
    <div class="stat-box"><div class="val">${total}</div><div class="lbl">Respuestas</div></div>
    <div class="stat-box"><div class="val">${avgQ8}</div><div class="lbl">Importancia promedio (Q8)</div></div>
    <div class="stat-box"><div class="val">${avgQ9}</div><div class="lbl">Recomendación promedio (Q9)</div></div>
  `;

  const body = document.getElementById('resultsBody');
  body.innerHTML = '';

  QUESTIONS.forEach((q, i) => {
    const card = document.createElement('div');
    card.className = 'result-card';

    if (q.type === 'choice') {
      const counts = {};
      q.opts.forEach(o => counts[o] = 0);
      rs.forEach(r => { if (r[q.id] && counts[r[q.id]] !== undefined) counts[r[q.id]]++; });
      const bars = q.opts.map(o => {
        const c = counts[o] || 0;
        const pct = total > 0 ? Math.round(c / total * 100) : 0;
        return `<div class="bar-item">
          <div class="bar-label-row">
            <span>${o}</span>
            <span class="pct">${pct}%</span>
          </div>
          <div class="bar-track"><div class="bar-fill" style="width:${pct}%"></div></div>
        </div>`;
      }).join('');
      card.innerHTML = `<div class="rq-num">Pregunta ${String(i+1).padStart(2,'0')}</div>
        <div class="rq-text">${q.text}</div>${bars}`;

    } else if (q.type === 'scale') {
      const counts = {1:0,2:0,3:0,4:0,5:0};
      rs.forEach(r => { if (r[q.id]) counts[parseInt(r[q.id])]++; });
      const avg = total > 0
        ? (rs.reduce((s,r) => s+(parseInt(r[q.id])||0), 0)/total).toFixed(2)
        : '—';
      const bars = [1,2,3,4,5].map(n => {
        const pct = total > 0 ? Math.round(counts[n]/total*100) : 0;
        return `<div class="bar-item">
          <div class="bar-label-row"><span>${n} estrella${n>1?'s':''}</span><span class="pct">${pct}%</span></div>
          <div class="bar-track"><div class="bar-fill" style="width:${pct}%"></div></div>
        </div>`;
      }).join('');
      card.innerHTML = `<div class="rq-num">Pregunta ${String(i+1).padStart(2,'0')}</div>
        <div class="rq-text">${q.text}</div>${bars}
        <div class="avg-badge"><span>${avg}</span><span>promedio de ${total} respuestas</span></div>`;

    } else {
      const open = rs.map(r => r[q.id]).filter(Boolean);
      const bubbles = open.length > 0
        ? open.map(t => `<div class="response-bubble">"${t}"</div>`).join('')
        : `<div class="no-responses">Sin respuestas aún</div>`;
      card.innerHTML = `<div class="rq-num">Pregunta ${String(i+1).padStart(2,'0')} — Abierta</div>
        <div class="rq-text">${q.text}</div>
        <div class="responses-list">${bubbles}</div>`;
    }

    body.appendChild(card);
    // Animate bars
    setTimeout(() => {
      card.querySelectorAll('.bar-fill').forEach(b => {
        const w = b.style.width;
        b.style.width = '0%';
        setTimeout(() => b.style.width = w, 50);
      });
    }, 100);
  });
}

// ── TABS ──────────────────────────────────────────────────────────
function showTab(tab) {
  document.querySelectorAll('.tab-btn').forEach((b,i) =>
    b.classList.toggle('active', (i===0 && tab==='survey') || (i===1 && tab==='results')));

  document.getElementById('surveyPanel').style.display = tab === 'survey' ? 'block' : 'none';
  document.getElementById('thankYou').style.display = 'none';
  document.getElementById('resultsPanel').style.display = tab === 'results' ? 'block' : 'none';

  if (tab === 'results') renderResults();
  window.scrollTo({ top: 0, behavior: 'smooth' });
}
</script>
</body>
</html>
