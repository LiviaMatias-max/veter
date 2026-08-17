<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Farmacologia Veterinária — Caderno de Estudo</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Zilla+Slab:wght@400;600;700&family=IBM+Plex+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #E5E8D6;
    --bg-deep: #DCE0CB;
    --paper: #FFFCF4;
    --paper-alt: #FBF6E8;
    --ink: #202B1E;
    --forest: #2E5233;
    --forest-dark: #142418;
    --amber: #B8863A;
    --amber-deep: #8C5F1E;
    --amber-light: #EFDBA6;
    --line: #D8D5C0;
    --red-flag: #9C4030;
    --ok: #2E5233;
    --muted: #64735E;
    --shadow: rgba(20,36,24,0.16);
  }
  * { box-sizing: border-box; }
  html { scroll-behavior: smooth; }
  body {
    margin: 0;
    background:
      radial-gradient(circle at 1px 1px, rgba(46,82,51,0.05) 1px, transparent 0) 0 0/14px 14px,
      var(--bg);
    color: var(--ink);
    font-family: 'IBM Plex Sans', sans-serif;
    min-height: 100vh;
    padding: 0 16px 72px;
  }
  .wrap { max-width: 900px; margin: 0 auto; }
  ::selection { background: var(--amber-light); color: var(--forest-dark); }
  button, input, select { font: inherit; }
  button:focus-visible, input:focus-visible, select:focus-visible {
    outline: 2px solid var(--amber-deep); outline-offset: 2px;
  }
  @media (prefers-reduced-motion: reduce) {
    * { animation-duration: 0.001ms !important; transition-duration: 0.001ms !important; }
  }

  /* ---------- HEADER ---------- */
  .letterhead {
    position: relative;
    background: linear-gradient(180deg, var(--paper-alt), var(--paper));
    border: 1px solid var(--line);
    border-top: none;
    border-radius: 0 0 10px 10px;
    padding: 34px 34px 26px;
    margin: 0 -1px 30px;
    box-shadow: 0 14px 30px -20px var(--shadow);
  }
  .letterhead::before {
    content: "";
    position: absolute; left: -1px; right: -1px; top: -9px; height: 18px;
    background-image: radial-gradient(circle at 9px 9px, var(--bg) 9px, transparent 9.5px);
    background-size: 18px 18px;
    background-position: 0 0;
    border-left: 1px solid var(--line); border-right: 1px solid var(--line);
  }
  .letterhead-top { display: flex; justify-content: space-between; align-items: flex-start; gap: 18px; }
  .eyebrow {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 10.5px; letter-spacing: 0.16em; text-transform: uppercase;
    color: var(--amber-deep); display: flex; align-items: center; gap: 7px; margin-bottom: 10px;
  }
  .eyebrow::before { content: ""; width: 16px; height: 1px; background: var(--amber-deep); display: inline-block; }
  h1 {
    font-family: 'Zilla Slab', serif; font-weight: 700; font-size: 38px; margin: 0 0 8px;
    line-height: 1.06; letter-spacing: -0.01em; color: var(--forest-dark);
  }
  .sub { color: var(--muted); font-size: 14.5px; max-width: 56ch; line-height: 1.55; }

  .rx-stamp {
    flex-shrink: 0; width: 64px; height: 64px; border-radius: 50%;
    border: 1.5px solid var(--forest); color: var(--forest);
    display: flex; align-items: center; justify-content: center;
    font-family: 'Zilla Slab', serif; font-weight: 700; font-size: 22px;
    transform: rotate(-9deg); opacity: 0.9;
    background: repeating-radial-gradient(circle, transparent 0 2px, rgba(46,82,51,0.05) 2px 3px);
  }

  .stats-row { display: flex; gap: 10px; margin-top: 20px; flex-wrap: wrap; }
  .stat-chip {
    display: flex; align-items: baseline; gap: 6px;
    background: var(--paper); border: 1px solid var(--line); border-radius: 999px;
    padding: 6px 13px 6px 11px;
  }
  .stat-chip .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--amber); flex-shrink: 0; }
  .stat-chip b { font-family: 'Zilla Slab', serif; font-size: 15px; color: var(--forest-dark); }
  .stat-chip span.lbl { font-family: 'IBM Plex Mono', monospace; font-size: 10.5px; color: var(--muted); }

  /* ---------- TABS ---------- */
  nav.tabs {
    display: flex; gap: 0; margin: 0 0 22px; background: var(--paper-alt);
    border: 1px solid var(--line); border-radius: 12px; padding: 5px; position: relative;
  }
  .tab {
    flex: 1; font-family: 'IBM Plex Mono', monospace; font-size: 12px; letter-spacing: 0.03em; text-transform: uppercase;
    background: none; border: none; padding: 11px 4px; color: var(--muted); cursor: pointer;
    border-radius: 8px; position: relative; transition: color 0.2s ease;
  }
  .tab + .tab::before {
    content: ""; position: absolute; left: 0; top: 20%; bottom: 20%; width: 1px; background: var(--line);
  }
  .tab.active { color: var(--paper); }
  .tab.active::before, .tab.active + .tab::before { display: none; }
  .tab-highlight {
    position: absolute; top: 5px; bottom: 5px; border-radius: 8px; background: var(--forest);
    box-shadow: 0 4px 12px -4px var(--shadow); transition: transform 0.28s cubic-bezier(.4,.1,.2,1), width 0.28s cubic-bezier(.4,.1,.2,1);
    z-index: 0; width: 33.33%;
  }
  .tab { z-index: 1; }

  section.panel { display: none; animation: rise 0.35s ease; } 
  section.panel.active { display: block; }
  @keyframes rise { from { opacity: 0; transform: translateY(6px); } to { opacity: 1; transform: translateY(0); } }

  .toolbar { display: flex; gap: 10px; margin-bottom: 14px; flex-wrap: wrap; align-items: center; }
  .toolbar input[type=text] {
    flex: 1; min-width: 160px; font-family: 'IBM Plex Sans'; font-size: 13.5px;
    background: var(--paper); border: 1px solid var(--line); padding: 10px 13px; border-radius: 8px; color: var(--ink);
    transition: border-color 0.15s;
  }
  .toolbar input[type=text]:hover { border-color: #c7c4ac; }
  select {
    font-family: 'IBM Plex Mono', monospace; font-size: 12px; background: var(--paper);
    border: 1px solid var(--line); padding: 9px 10px; color: var(--ink); border-radius: 8px; cursor: pointer;
  }
  .chk-label {
    font-family: 'IBM Plex Mono', monospace; font-size: 11.5px; color: var(--muted);
    display: flex; align-items: center; gap: 6px; white-space: nowrap; cursor: pointer;
  }
  .chk-label input { accent-color: var(--forest); }

  .cat-pills { display: flex; flex-wrap: wrap; gap: 7px; margin-bottom: 18px; }
  .pill {
    font-family: 'IBM Plex Mono', monospace; font-size: 10.5px; padding: 6px 11px; border-radius: 20px;
    border: 1px solid var(--line); color: var(--muted); background: var(--paper); cursor: pointer;
    transition: all 0.15s;
  }
  .pill:hover { border-color: var(--forest); color: var(--forest-dark); }
  .pill.active { background: var(--forest); color: #F4EFDD; border-color: var(--forest); }

  .deck-meta { display: flex; justify-content: space-between; align-items: center;
    font-family: 'IBM Plex Mono', monospace; font-size: 12px; color: var(--muted); margin-bottom: 10px; }

  /* ---------- FLASHCARD ---------- */
  .card-stage { perspective: 1600px; height: 270px; margin-bottom: 18px; }
  .card { position: relative; width: 100%; height: 100%; transform-style: preserve-3d;
    transition: transform 0.5s cubic-bezier(.34,1.1,.4,1); cursor: pointer; }
  .card.flipped { transform: rotateY(180deg); }
  .card:hover { transform: translateY(-2px); }
  .card.flipped:hover { transform: rotateY(180deg) translateY(-2px); }
  .face { position: absolute; inset: 0; background: var(--paper); border: 1px solid var(--line); border-radius: 8px;
    backface-visibility: hidden; display: flex; flex-direction: column; padding: 26px;
    box-shadow: 0 1px 0 var(--line), 0 16px 32px -18px var(--shadow); }
  .face::before { content: ""; position: absolute; left: 0; top: 20px; bottom: 20px; width: 3px; border-radius: 2px;
    background: repeating-linear-gradient(180deg, var(--amber-light) 0 6px, transparent 6px 13px); }
  .face .tag { font-family: 'IBM Plex Mono', monospace; font-size: 10px; text-transform: uppercase;
    letter-spacing: 0.09em; color: var(--amber-deep); margin-bottom: 12px; display: flex; justify-content: space-between;
    background: var(--amber-light); align-self: flex-start; padding: 4px 10px; border-radius: 20px; transform: rotate(-1deg); }
  .face .content { font-family: 'Zilla Slab', serif; font-size: 21px; line-height: 1.32; color: var(--ink); flex: 1;
    display: flex; align-items: center; overflow-y: auto; }
  .face .hint { font-family: 'IBM Plex Mono', monospace; font-size: 10px; color: #95a290; align-self: flex-end; }
  .back { transform: rotateY(180deg); background: var(--forest-dark); border-color: var(--forest-dark); }
  .back .content { color: #F4EFDD; font-size: 17px; }
  .back .tag { color: var(--amber-light); background: rgba(239,219,166,0.14); }
  .back .hint { color: #7f9080; }

  .deck-controls { display: flex; justify-content: space-between; align-items: center; gap: 10px; flex-wrap: wrap; }
  .navbtn { font-family: 'IBM Plex Mono', monospace; font-size: 12px; background: var(--forest); color: #F4EFDD;
    border: none; padding: 10px 18px; border-radius: 999px; cursor: pointer; transition: all 0.15s;
    box-shadow: 0 6px 14px -8px var(--shadow); }
  .navbtn:hover { background: var(--forest-dark); transform: translateY(-1px); }
  .navbtn.ghost { background: none; color: var(--forest); border: 1px solid var(--line); box-shadow: none; }
  .navbtn.ghost:hover { border-color: var(--forest); background: var(--paper-alt); }
  .navbtn.small { font-size: 10.5px; padding: 7px 12px; }
  .progress { font-family: 'IBM Plex Mono', monospace; font-size: 11.5px; color: var(--muted); }
  .self-row { display: flex; gap: 8px; justify-content: center; margin: 14px 0 6px; }
  .self-btn { font-family: 'IBM Plex Mono', monospace; font-size: 11px; padding: 8px 14px; border-radius: 999px;
    border: 1px solid var(--line); background: var(--paper); cursor: pointer; color: var(--muted); transition: all 0.15s; }
  .self-btn:hover { border-color: var(--forest); }
  .self-btn.know.marked { background: #E4EFE1; border-color: var(--ok); color: var(--forest-dark); }
  .self-btn.review.marked { background: #F4E3DC; border-color: var(--red-flag); color: var(--red-flag); }

  /* ---------- QUIZ ---------- */
  .qmeta { display: flex; justify-content: space-between; align-items: baseline;
    font-family: 'IBM Plex Mono', monospace; font-size: 12px; color: var(--muted); margin-bottom: 10px; flex-wrap: wrap; gap: 6px; }
  .qcard { background: var(--paper); border: 1px solid var(--line); border-radius: 10px; padding: 26px; margin-bottom: 16px;
    box-shadow: 0 16px 32px -20px var(--shadow); }
  .qtag { font-family: 'IBM Plex Mono', monospace; font-size: 10px; text-transform: uppercase; letter-spacing: 0.09em;
    color: var(--amber-deep); margin-bottom: 12px; background: var(--amber-light); display: inline-block; padding: 4px 10px;
    border-radius: 20px; transform: rotate(-1deg); }
  .qtext { font-family: 'Zilla Slab', serif; font-size: 19.5px; line-height: 1.38; margin-bottom: 18px; color: var(--forest-dark); }
  .options { display: flex; flex-direction: column; gap: 9px; }
  .opt { text-align: left; font-family: 'IBM Plex Sans'; font-size: 14px; background: var(--paper-alt);
    border: 1px solid var(--line); padding: 12px 14px; border-radius: 8px; cursor: pointer; display: flex; gap: 11px; align-items: flex-start;
    transition: all 0.14s; }
  .opt:hover { border-color: var(--forest); background: #F3F0E0; transform: translateX(2px); }
  .opt .letter { font-family: 'IBM Plex Mono', monospace; font-size: 11.5px; color: var(--forest); border: 1px solid var(--forest);
    width: 20px; height: 20px; border-radius: 50%; display: flex; align-items: center; justify-content: center; flex-shrink: 0; }
  .opt.correct { background: #E4EFE1; border-color: var(--ok); }
  .opt.correct .letter { background: var(--ok); border-color: var(--ok); color: #fff; }
  .opt.wrong { background: #F4E3DC; border-color: var(--red-flag); }
  .opt.wrong .letter { background: var(--red-flag); border-color: var(--red-flag); color: #fff; }
  .opt[disabled] { cursor: default; }
  .opt[disabled]:hover { transform: none; }
  .explain { font-size: 13.5px; color: #4a5a4a; border-top: 1px dashed var(--line); margin-top: 16px; padding-top: 14px;
    line-height: 1.55; display: none; } 
  .explain.show { display: block; animation: rise 0.25s ease; } 
  .explain b { color: var(--forest-dark); }

  .score-strip { font-family: 'IBM Plex Mono', monospace; font-size: 11.5px; color: var(--muted); display: flex; gap: 14px; }
  .reset-row { text-align: right; margin-top: 8px; }
  .reset-row button { font-family: 'IBM Plex Mono', monospace; font-size: 11px; color: var(--amber-deep); background: none;
    border: none; cursor: pointer; text-decoration: underline; text-underline-offset: 2px; }

  /* ---------- STATS ---------- */
  .stat-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-bottom: 26px; }
  @media (min-width: 600px) { .stat-grid { grid-template-columns: repeat(4, 1fr); } }
  .stat-box { background: var(--paper); border: 1px solid var(--line); border-radius: 10px; padding: 16px;
    border-top: 3px solid var(--amber); box-shadow: 0 10px 22px -18px var(--shadow); }
  .stat-box .num { font-family: 'Zilla Slab', serif; font-size: 28px; color: var(--forest-dark); line-height: 1; }
  .stat-box .lbl { font-family: 'IBM Plex Mono', monospace; font-size: 10px; color: var(--muted); text-transform: uppercase; letter-spacing: 0.06em; margin-top: 6px; }
  .stats-heading { font-family: 'Zilla Slab', serif; font-size: 16px; margin: 6px 0 16px; color: var(--forest-dark); }
  .cat-bar-row { display: flex; align-items: center; gap: 10px; margin-bottom: 10px; }
  .cat-bar-row .name { font-family: 'IBM Plex Mono', monospace; font-size: 11px; width: 190px; flex-shrink: 0; color: var(--ink); }
  .cat-bar-track { flex: 1; height: 9px; background: var(--line); border-radius: 5px; overflow: hidden; }
  .cat-bar-fill { height: 100%; background: linear-gradient(90deg, var(--forest), var(--amber)); transition: width 0.4s ease; }
  .cat-bar-pct { font-family: 'IBM Plex Mono', monospace; font-size: 10.5px; color: var(--muted); width: 38px; text-align: right; }

  .empty { font-family: 'IBM Plex Mono', monospace; font-size: 12.5px; color: var(--muted); padding: 30px 0; text-align: center; }

  footer.stamp-row {
    display: flex; align-items: center; gap: 10px; justify-content: center; margin-top: 36px;
    font-family: 'IBM Plex Mono', monospace; font-size: 10.5px; color: var(--muted); letter-spacing: 0.04em;
  }
  footer.stamp-row .seal { width: 9px; height: 9px; border: 1px solid var(--muted); border-radius: 50%; flex-shrink: 0; }

  @media (max-width: 520px) {
    .letterhead { padding: 24px 20px 20px; }
    h1 { font-size: 28px; }
    .rx-stamp { width: 48px; height: 48px; font-size: 17px; }
    .card-stage { height: 320px; }
    .face .content { font-size: 17.5px; }
    .cat-bar-row .name { width: 120px; font-size: 10px; }
    .tab { font-size: 10.5px; padding: 10px 2px; }
  }
</style>
</head>
<body>
<div class="wrap">

  <header class="letterhead">
    <div class="letterhead-top">
      <div>
        <div class="eyebrow">Caderno de revisão</div>
        <h1>Farmacologia<br>Veterinária</h1>
        <p class="sub">Flashcards e questões para revisão, com busca, filtros por categoria e estatísticas de desempenho. Roda inteiro no navegador.</p>
      </div>
      <div class="rx-stamp" aria-hidden="true">℞</div>
    </div>
    <div class="stats-row" id="headerStats"></div>
  </header>

  <nav class="tabs" id="tabsNav">
    <div class="tab-highlight" id="tabHighlight"></div>
    <button class="tab active" data-panel="flash">Flashcards</button>
    <button class="tab" data-panel="quiz">Questões</button>
    <button class="tab" data-panel="stats">Estatísticas</button>
  </nav>

  <!-- FLASHCARDS -->
  <section class="panel active" id="flash">
    <div class="toolbar">
      <input type="text" id="searchBox" placeholder="Buscar por palavra-chave...">
      <label class="chk-label"><input type="checkbox" id="onlyReview"> só marcadas p/ revisar</label>
      <button class="navbtn ghost small" id="shuffleBtn">embaralhar</button>
    </div>
    <div class="cat-pills" id="catPills"></div>

    <div class="deck-meta">
      <span id="deckCount">Carta 1 de 1</span>
      <span id="deckCatLabel"></span>
    </div>

    <div class="card-stage">
      <div class="card" id="card">
        <div class="face front">
          <div class="tag"><span id="frontTag">Pergunta</span></div>
          <div class="content" id="frontText"></div>
          <div class="hint">toque para virar</div>
        </div>
        <div class="face back">
          <div class="tag"><span id="backTag">Resposta</span></div>
          <div class="content" id="backText"></div>
          <div class="hint">toque para voltar</div>
        </div>
      </div>
    </div>

    <div class="self-row">
      <button class="self-btn know" id="btnKnow">✓ já sei</button>
      <button class="self-btn review" id="btnReview">↻ revisar depois</button>
    </div>

    <div class="deck-controls">
      <button class="navbtn ghost" id="prevBtn">← Anterior</button>
      <span class="progress" id="progressText"></span>
      <button class="navbtn" id="nextBtn">Próxima →</button>
    </div>
  </section>

  <!-- QUIZ -->
  <section class="panel" id="quiz">
    <div class="toolbar">
      <select id="quizCat"></select>
      <button class="navbtn ghost small" id="quizShuffle">embaralhar</button>
    </div>
    <div class="qmeta">
      <span id="quizProgress">Questão 1 de 1</span>
      <span id="quizScore">Acertos: 0</span>
    </div>

    <div class="qcard">
      <div class="qtag" id="quizTag">Categoria</div>
      <div class="qtext" id="quizText"></div>
      <div class="options" id="quizOptions"></div>
      <div class="explain" id="quizExplain"></div>
    </div>

    <div class="deck-controls">
      <button class="navbtn ghost" id="quizPrev">← Anterior</button>
      <span class="score-strip" id="scoreStrip"></span>
      <button class="navbtn" id="quizNext">Próxima →</button>
    </div>
    <div class="reset-row"><button id="quizReset">reiniciar respostas</button></div>
  </section>

  <!-- STATS -->
  <section class="panel" id="stats">
    <div class="stat-grid" id="statGrid"></div>
    <h3 class="stats-heading">Desempenho por categoria (questões)</h3>
    <div id="catBars"></div>
  </section>

  <footer class="stamp-row"><span class="seal"></span> Material de apoio para revisão — uso educacional</footer>

</div>

<script>
/* ================= DADOS: FLASHCARDS ================= */
const flashcards = [
  // FARMACOCINÉTICA
  {cat:"Farmacocinética", q:"O que é biodisponibilidade?", a:"Fração da dose administrada que atinge a circulação sistêmica de forma inalterada. Via IV = 100% por definição, sendo a referência para as demais vias."},
  {cat:"Farmacocinética", q:"Diferença entre farmacocinética e farmacodinâmica.", a:"Farmacocinética é o que o corpo faz com o fármaco (absorção, distribuição, metabolismo, excreção — ADME). Farmacodinâmica é o que o fármaco faz com o corpo (mecanismo de ação, efeito)."},
  {cat:"Farmacocinética", q:"O que é meia-vida de eliminação (t½)?", a:"Tempo necessário para a concentração plasmática do fármaco cair pela metade. Usada para calcular o intervalo entre doses; após ~4-5 meias-vidas o fármaco é considerado praticamente eliminado."},
  {cat:"Farmacocinética", q:"Por que gatos metabolizam certos fármacos mais lentamente que cães?", a:"Gatos têm deficiência relativa de glicuroniltransferase hepática, reduzindo a glucuronidação de fármacos como paracetamol e alguns AINEs, exigindo maior cautela e ajuste de doses/intervalos."},
  {cat:"Farmacocinética", q:"O que é o efeito de primeira passagem hepática?", a:"Metabolismo de parte da dose de um fármaco administrado por via oral antes de atingir a circulação sistêmica, ao passar pelo fígado — reduz a biodisponibilidade oral de vários fármacos."},
  {cat:"Farmacocinética", q:"O que é volume de distribuição (Vd)?", a:"Parâmetro teórico que relaciona a quantidade de fármaco no corpo com sua concentração plasmática; Vd alto sugere ampla distribuição tecidual, Vd baixo sugere fármaco mais restrito ao plasma."},
  {cat:"Farmacocinética", q:"Como a ligação a proteínas plasmáticas afeta a ação de um fármaco?", a:"Apenas a fração livre (não ligada) do fármaco é farmacologicamente ativa e pode se difundir para os tecidos; alta ligação proteica prolonga a permanência no plasma."},
  {cat:"Farmacocinética", q:"Por que a função renal comprometida altera a farmacocinética de muitos fármacos?", a:"Reduz a excreção de fármacos e metabólitos ativos eliminados pelos rins, podendo causar acúmulo e toxicidade — exigindo ajuste de dose ou intervalo em pacientes renais."},
  {cat:"Farmacocinética", q:"O que caracteriza a cinética de ordem zero?", a:"Uma quantidade constante (não uma fração constante) do fármaco é eliminada por unidade de tempo, independente da concentração plasmática — típico de vias saturáveis (ex: etanol, altas doses de fenitoína)."},
  {cat:"Farmacocinética", q:"Por que suínos e aves são mais sensíveis a certos anestésicos inalatórios que outras espécies?", a:"Diferenças metabólicas e na farmacocinética respiratória entre espécies alteram a captação e eliminação dos agentes voláteis, exigindo monitoramento e ajuste de concentração específicos por espécie."},

  // FARMACODINÂMICA
  {cat:"Farmacodinâmica", q:"O que é índice terapêutico?", a:"Razão entre a dose tóxica e a dose eficaz de um fármaco. Quanto maior o índice, maior a margem de segurança entre efeito desejado e toxicidade."},
  {cat:"Farmacodinâmica", q:"O que caracteriza um antagonista competitivo?", a:"Liga-se de forma reversível ao mesmo sítio do agonista no receptor e pode ser deslocado por doses maiores do agonista — desloca a curva dose-resposta para a direita sem reduzir o efeito máximo."},
  {cat:"Farmacodinâmica", q:"O que é um agonista parcial?", a:"Fármaco que se liga ao receptor mas produz efeito máximo menor que um agonista total, mesmo ocupando todos os receptores disponíveis (ex: buprenorfina em receptores opioides mu)."},
  {cat:"Farmacodinâmica", q:"Diferença entre potência e eficácia de um fármaco.", a:"Potência é a quantidade necessária para produzir um efeito (dose); eficácia é o efeito máximo que o fármaco consegue produzir, independente da dose."},
  {cat:"Farmacodinâmica", q:"O que é tolerância farmacológica?", a:"Redução da resposta a um fármaco após exposição repetida, exigindo doses maiores para obter o mesmo efeito — comum com opioides e benzodiazepínicos."},
  {cat:"Farmacodinâmica", q:"O que é down-regulation de receptores?", a:"Redução do número de receptores disponíveis na membrana celular após exposição prolongada a um agonista, contribuindo para tolerância farmacológica."},
  {cat:"Farmacodinâmica", q:"O que é sinergismo farmacológico?", a:"Quando o efeito combinado de dois fármacos é maior que a soma dos efeitos individuais — pode ser terapeuticamente útil ou perigoso, dependendo da combinação."},
  {cat:"Farmacodinâmica", q:"O que é antagonismo fisiológico?", a:"Dois fármacos atuam em receptores ou sistemas diferentes, mas produzem efeitos opostos no organismo (ex: um broncodilatador e um broncoconstritor atuando por vias distintas)."},

  // ANTIBIÓTICOS BETA-LACTÂMICOS
  {cat:"Antibióticos", q:"Mecanismo de ação geral dos beta-lactâmicos (penicilinas, cefalosporinas).", a:"Inibem a síntese da parede celular bacteriana ao bloquear as transpeptidases (PBPs — proteínas ligadoras de penicilina), levando à lise osmótica da bactéria."},
  {cat:"Antibióticos", q:"Por que os beta-lactâmicos são mais eficazes contra bactérias em crescimento ativo?", a:"Seu mecanismo depende da síntese ativa da parede celular; bactérias em fase estacionária (não se dividindo) são menos afetadas."},
  {cat:"Antibióticos", q:"O que faz o ácido clavulânico associado à amoxicilina?", a:"Inibe a enzima beta-lactamase produzida por algumas bactérias resistentes, protegendo a amoxicilina da degradação e ampliando seu espectro de ação."},
  {cat:"Antibióticos", q:"Por que cefalosporinas de 1ª geração têm menor ação contra Gram-negativos que as de 3ª geração?", a:"As gerações mais recentes foram desenvolvidas com maior afinidade e penetração pela membrana externa de bactérias Gram-negativas, ampliando o espectro nessa direção."},
  {cat:"Antibióticos", q:"Qual é a principal via de excreção da maioria das penicilinas?", a:"Excreção renal, principalmente por secreção tubular — por isso doses devem ser ajustadas em pacientes com insuficiência renal."},

  // ANTIBIÓTICOS - OUTRAS CLASSES
  {cat:"Antibióticos", q:"Mecanismo de ação dos aminoglicosídeos (ex: gentamicina).", a:"Ligam-se à subunidade ribossomal 30S, causando leitura incorreta do RNA mensageiro e inibição da síntese proteica bacteriana — bactericidas, principalmente contra Gram-negativos."},
  {cat:"Antibióticos", q:"Principal toxicidade a monitorar no uso de aminoglicosídeos.", a:"Nefrotoxicidade e ototoxicidade (vestibular e coclear), mais prováveis com uso prolongado ou em pacientes desidratados/com função renal comprometida."},
  {cat:"Antibióticos", q:"Por que as fluoroquinolonas (ex: enrofloxacina) são evitadas em animais jovens em crescimento?", a:"Podem causar artropatia (lesão de cartilagem articular) em animais em fase de crescimento, especialmente em raças grandes durante o pico de desenvolvimento ósseo."},
  {cat:"Antibióticos", q:"Mecanismo de ação das fluoroquinolonas.", a:"Inibem a DNA-girase e a topoisomerase IV bacterianas, enzimas essenciais para a replicação do DNA bacteriano — bactericidas de amplo espectro."},
  {cat:"Antibióticos", q:"Por que tetraciclinas são evitadas em filhotes e fêmeas prenhes?", a:"Podem se depositar em ossos e dentes em formação (quelação com cálcio), causando manchamento dentário permanente e alterações no crescimento ósseo do feto/filhote."},
  {cat:"Antibióticos", q:"Mecanismo de ação dos macrolídeos (ex: eritromicina, azitromicina).", a:"Ligam-se à subunidade ribossomal 50S, inibindo a translocação durante a síntese proteica bacteriana — geralmente bacteriostáticos."},
  {cat:"Antibióticos", q:"Como agem as sulfonamidas potencializadas (ex: sulfa + trimetoprima)?", a:"Bloqueiam sequencialmente duas etapas da síntese de ácido fólico bacteriano (a sulfa inibe a di-hidropteroato sintetase e a trimetoprima a di-hidrofolato redutase), com efeito sinérgico bactericida."},
  {cat:"Antibióticos", q:"Por que o metronidazol é eficaz contra anaeróbios e protozoários?", a:"É reduzido dentro de células anaeróbicas/protozoários, gerando metabólitos que danificam o DNA microbiano — esse mecanismo depende de um ambiente com baixo potencial redox, ausente em aeróbios."},
  {cat:"Antibióticos", q:"Por que antibióticos orais de amplo espectro podem ser perigosos em coelhos e ruminantes?", a:"Podem alterar drasticamente a flora fermentativa do trato digestivo, causando disbiose grave e potencialmente fatal (ex: enterotoxemia por Clostridium)."},
  {cat:"Antibióticos", q:"O que significa um antibiótico ser bactericida versus bacteriostático?", a:"Bactericida mata diretamente as bactérias; bacteriostático inibe seu crescimento e reprodução, dependendo do sistema imune do hospedeiro para eliminar a infecção."},
  {cat:"Antibióticos", q:"Por que é importante respeitar o tempo total de um tratamento antimicrobiano mesmo com melhora clínica precoce?", a:"Interromper cedo pode deixar bactérias parcialmente resistentes sobreviventes, favorecendo recidiva da infecção e seleção de cepas resistentes."},

  // ANTIFÚNGICOS
  {cat:"Antifúngicos", q:"Mecanismo de ação geral dos azólicos (ex: cetoconazol, itraconazol).", a:"Inibem a enzima fúngica lanosterol 14-alfa-desmetilase, bloqueando a síntese de ergosterol — componente essencial da membrana celular fúngica."},
  {cat:"Antifúngicos", q:"Por que o cetoconazol pode causar efeitos colaterais endócrinos?", a:"Também inibe enzimas do citocromo P450 envolvidas na esteroidogênese de mamíferos, podendo reduzir a síntese de cortisol e testosterona."},
  {cat:"Antifúngicos", q:"Mecanismo de ação da griseofulvina.", a:"Interfere na formação do fuso mitótico fúngico, inibindo a divisão celular; é usada principalmente contra dermatófitos."},
  {cat:"Antifúngicos", q:"Por que a griseofulvina é contraindicada em gatas e cadelas prenhes?", a:"Tem potencial teratogênico comprovado, podendo causar malformações fetais graves."},
  {cat:"Antifúngicos", q:"Mecanismo de ação da anfotericina B.", a:"Liga-se ao ergosterol da membrana fúngica, formando poros que alteram a permeabilidade celular e levam à morte do fungo; apresenta risco significativo de nefrotoxicidade."},

  // AINES
  {cat:"AINEs", q:"Mecanismo de ação geral dos AINEs.", a:"Inibem as enzimas ciclo-oxigenase (COX-1 e/ou COX-2), reduzindo a síntese de prostaglandinas responsáveis por dor, inflamação e febre."},
  {cat:"AINEs", q:"Diferença funcional entre COX-1 e COX-2.", a:"COX-1 é constitutiva, associada a funções fisiológicas protetoras (mucosa gástrica, fluxo renal); COX-2 é induzida principalmente em processos inflamatórios. AINEs seletivos para COX-2 tendem a poupar mais o trato GI."},
  {cat:"AINEs", q:"Por que o paracetamol é contraindicado em gatos?", a:"Gatos não conseguem glucuronizar eficientemente o paracetamol devido à deficiência de glicuroniltransferase; ele se acumula e forma metabólitos que causam metahemoglobinemia e necrose hepática — pode ser fatal mesmo em doses baixas."},
  {cat:"AINEs", q:"Principal risco do uso prolongado de AINEs em cães.", a:"Úlceras gastrointestinais e nefrotoxicidade, especialmente se associados a corticoides, desidratação ou hipotensão (redução do fluxo sanguíneo renal dependente de prostaglandinas)."},
  {cat:"AINEs", q:"Por que nunca associar AINE com corticoide?", a:"O uso concomitante aumenta drasticamente o risco de úlceras e perfuração gastrointestinal, pois os dois mecanismos de lesão da mucosa se somam."},
  {cat:"AINEs", q:"Por que gatos exigem maior cautela com AINEs em geral, não só paracetamol?", a:"Têm capacidade reduzida de glucuronidação hepática, prolongando a meia-vida de muitos AINEs e aumentando o risco de acúmulo e toxicidade com doses repetidas."},
  {cat:"AINEs", q:"Por que é recomendado suspender AINEs antes de procedimentos cirúrgicos com risco de sangramento?", a:"Alguns AINEs inibem a agregação plaquetária dependente de tromboxano A2, podendo prolongar o tempo de sangramento."},
  {cat:"AINEs", q:"O que caracteriza um AINE COX-2 preferencial (ex: meloxicam, carprofeno) do ponto de vista clínico?", a:"Tende a preservar mais as funções fisiológicas dependentes de COX-1 (proteção gástrica, perfusão renal), mas não elimina o risco de efeitos adversos GI e renais, especialmente em doses altas ou uso crônico."},

  // CORTICOIDES
  {cat:"Corticoides", q:"Mecanismo de ação anti-inflamatório dos glicocorticoides.", a:"Ligam-se a receptores intracelulares que regulam a transcrição gênica, reduzindo a produção de mediadores inflamatórios (incluindo inibição da fosfolipase A2, reduzindo a formação de prostaglandinas e leucotrienos)."},
  {cat:"Corticoides", q:"Por que a suspensão abrupta de corticoterapia prolongada é perigosa?", a:"O uso prolongado suprime o eixo hipotálamo-hipófise-adrenal (HHA); a suspensão abrupta pode causar insuficiência adrenal aguda, já que as glândulas adrenais ficam temporariamente incapazes de produzir cortisol suficiente."},
  {cat:"Corticoides", q:"Quais são efeitos colaterais comuns do uso crônico de corticoides em cães?", a:"Poliúria/polidipsia/polifagia, atrofia muscular, adelgaçamento de pele, imunossupressão, risco aumentado de infecções e predisposição a diabetes mellitus iatrogênico."},
  {cat:"Corticoides", q:"Por que corticoides são usados com extrema cautela em pacientes diabéticos?", a:"Antagonizam a ação da insulina e aumentam a gliconeogênese hepática, elevando a glicemia e dificultando o controle glicêmico."},
  {cat:"Corticoides", q:"Diferença de potência anti-inflamatória entre dexametasona e prednisolona.", a:"A dexametasona é significativamente mais potente e tem meia-vida biológica mais longa que a prednisolona, exigindo doses proporcionalmente menores e ajuste de intervalo."},
  {cat:"Corticoides", q:"Por que corticoides não devem ser associados a AINEs?", a:"O uso concomitante aumenta muito o risco de úlceras e perfuração gastrointestinal, somando os mecanismos de lesão da mucosa das duas classes."},
  {cat:"Corticoides", q:"O que é efeito mineralocorticoide de um glicocorticoide e por que importa clinicamente?", a:"É a capacidade de reter sódio e água e excretar potássio (ex: hidrocortisona, fludrocortisona). Em excesso, pode levar a edema e hipertensão; fármacos sintéticos como dexametasona têm efeito mineralocorticoide quase nulo."}
];

/* ================= DADOS: QUESTÕES / QUIZ ================= */
const quizData = [
  {
    cat: "Farmacocinética",
    q: "Um cão recebe um fármaco por via IV e o mesmo fármaco por via oral em ocasiões distintas. Sabendo que a AUC (área sob a curva) oral é metade da AUC IV, qual é a biodisponibilidade oral desse fármaco?",
    opts: ["100%", "50%", "25%", "10%"],
    ans: 1,
    exp: "A biodisponibilidade (F) por via extravascular é calculada dividindo a AUC da via testada pela AUC da via IV. Se a AUC oral é metade (50%) da IV, F = 50%."
  },
  {
    cat: "Farmacocinética",
    q: "A deficiência de glucuronidação em felinos é um fator crítico na prescrição veterinária. Qual fármaco é classicamente TÓXICO em gatos por este motivo?",
    opts: ["Dipirona", "Paracetamol", "Amoxicilina", "Ranitidina"],
    ans: 1,
    exp: "O paracetamol exige glucuronidação para sua metabolização segura. Em gatos, ele segue para oxidação via P450, gerando NAPQI em quantidades tóxicas, resultando em metahemoglobinemia e necrose hepática grave."
  },
  {
    cat: "Farmacodinâmica",
    q: "Ao administrar um antagonista competitivo junto a um agonista total, o que se espera observar na curva dose-resposta do agonista?",
    opts: [
      "Deslocamento para a esquerda sem alterar o efeito máximo",
      "Deslocamento para a direita sem alterar o efeito máximo",
      "Redução drástica do efeito máximo sem mudar a DE50",
      "Inibição irreversível do receptor"
    ],
    ans: 1,
    exp: "O antagonismo competitivo é reversível. Ele reduz a afinidade aparente do agonista (aumenta a DE50), exigindo maior dose para produzir o mesmo efeito (desloca a curva para a direita), mantendo contudo a eficácia máxima."
  },
  {
    cat: "Antibióticos",
    q: "Qual das alternativas apresenta o mecanismo de ação correto dos antibióticos fluoroquinolônicos (ex: enrofloxacina)?",
    opts: [
      "Inibição da síntese da parede celular via PBPs",
      "Inibição da subunidade ribossomal 50S",
      "Inibição da DNA-girase e Topoisomerase IV bacterianas",
      "Inibição da síntese de ácido fólico por bloqueio enzimático"
    ],
    ans: 2,
    exp: "Fluoroquinolonas são bactericidas que atuam bloqueando as enzimas DNA-girase e topoisomerase IV, essenciais no superenrolamento e replicação do DNA bacteriano."
  },
  {
    cat: "Antibióticos",
    q: "Por que o uso de gentamicina requer especial atenção à hidratação e função renal do paciente?",
    opts: [
      "Porque gera cristalúria e obstrução ureteral",
      "Porque é um aminoglicosídeo com risco potencial de nefrotoxicidade",
      "Porque causa necrose hepática imediata por acúmulo",
      "Porque induz hipotensão reativa súbita"
    ],
    ans: 1,
    exp: "Aminoglicosídeos acumulam-se nas células do túbulo proximal renal e no ouvido interno, podendo levar à necrose tubular aguda (nefrotoxicidade) e ototoxicidade, riscos agravados pela desidratação."
  },
  {
    cat: "AINEs",
    q: "Qual o principal motivo de se evitar a administração simultânea de dois AINEs distintos ou de um AINE associado a um Corticoide?",
    opts: [
      "Risco severo de ulceração e perfuração gastrointestinal",
      "Inativação química mútua no plasma sanguíneo",
      "Indução rápida de tolerância medicamentosa",
      "Inibição da absorção intestinal por quelação"
    ],
    ans: 0,
    exp: "Ambas as classes reduzem a síntese de prostaglandinas protetoras da mucosa gástrica e do fluxo renal. A associação potencializa drasticamente a lesão mucosal, levando a úlceras e perfurações."
  },
  {
    cat: "Corticoides",
    q: "A interrupção abrupta de um tratamento prolongado com glicocorticoides (ex: prednisolona) pode resultar em qual complicação grave?",
    opts: [
      "Crise de hipertireoidismo iatrogênico",
      "Insuficiência adrenal aguda (síndrome de retirada)",
      "Síndrome de Cushing imediata",
      "Insuficiência renal aguda por desidratação"
    ],
    ans: 1,
    exp: "A corticoterapia prolongada suprime o eixo HHA (hipotálamo-hipófise-adrenal). Retirar o fármaco bruscamente não dá tempo para as adrenais atróficas retomarem a produção fisiológica de cortisol, gerando crise adrenal."
  },
  {
    cat: "Antifúngicos",
    q: "O mecanismo de ação dos antifúngicos azólicos (ex: itraconazol) baseia-se na inibição de qual componente essencial fúngico?",
    opts: [
      "Síntese de quitina na parede celular",
      "Síntese de ergosterol na membrana celular",
      "Montagem dos microtúbulos no fuso mitótico",
      "Transcrição de RNA mensageiro"
    ],
    ans: 1,
    exp: "Azólicos inibem a enzima lanosterol 14-alfa-desmetilase (dependente do CYP), bloqueando a conversão de lanosterol em ergosterol, desestabilizando a membrana fúngica."
  }
];

/* ================= ESTADO E LÓGICA DA APLICAÇÃO ================= */

// Estados do app armazenados localmente
let state = {
  activeTab: 'flash',
  flash: {
    cards: [...flashcards],
    filtered: [],
    idx: 0,
    flipped: false,
    cat: 'Todas',
    search: '',
    onlyReview: false,
    markedKnow: new Set(),
    markedReview: new Set()
  },
  quiz: {
    data: [...quizData],
    filtered: [],
    idx: 0,
    cat: 'Todas',
    userAnswers: {} // index -> optionIndex
  }
};

// Inicialização de Elementos DOM
const DOM = {
  tabs: document.querySelectorAll('.tab'),
  panels: document.querySelectorAll('.panel'),
  tabHighlight: document.getElementById('tabHighlight'),
  headerStats: document.getElementById('headerStats'),
  
  // Flashcards
  searchBox: document.getElementById('searchBox'),
  onlyReview: document.getElementById('onlyReview'),
  shuffleBtn: document.getElementById('shuffleBtn'),
  catPills: document.getElementById('catPills'),
  deckCount: document.getElementById('deckCount'),
  deckCatLabel: document.getElementById('deckCatLabel'),
  card: document.getElementById('card'),
  frontTag: document.getElementById('frontTag'),
  frontText: document.getElementById('frontText'),
  backTag: document.getElementById('backTag'),
  backText: document.getElementById('backText'),
  btnKnow: document.getElementById('btnKnow'),
  btnReview: document.getElementById('btnReview'),
  prevBtn: document.getElementById('prevBtn'),
  nextBtn: document.getElementById('nextBtn'),
  progressText: document.getElementById('progressText'),

  // Quiz
  quizCat: document.getElementById('quizCat'),
  quizShuffle: document.getElementById('quizShuffle'),
  quizProgress: document.getElementById('quizProgress'),
  quizScore: document.getElementById('quizScore'),
  quizTag: document.getElementById('quizTag'),
  quizText: document.getElementById('quizText'),
  quizOptions: document.getElementById('quizOptions'),
  quizExplain: document.getElementById('quizExplain'),
  quizPrev: document.getElementById('quizPrev'),
  quizNext: document.getElementById('quizNext'),
  scoreStrip: document.getElementById('scoreStrip'),
  quizReset: document.getElementById('quizReset'),

  // Stats
  statGrid: document.getElementById('statGrid'),
  catBars: document.getElementById('catBars')
};

/* --- NAVEGAÇÃO POR ABAS --- */
function initTabs() {
  DOM.tabs.forEach((tab, index) => {
    tab.addEventListener('click', () => {
      DOM.tabs.forEach(t => t.classList.remove('active'));
      DOM.panels.forEach(p => p.classList.remove('active'));

      tab.classList.add('active');
      const panelId = tab.dataset.panel;
      document.getElementById(panelId).classList.add('active');
      
      // Ajusta o destaque deslizante (tab highlight)
      DOM.tabHighlight.style.width = `${100 / DOM.tabs.length}%`;
      DOM.tabHighlight.style.transform = `translateX(${index * 100}%)`;

      state.activeTab = panelId;
      if(panelId === 'stats') renderStats();
    });
  });
}

/* --- LÓGICA DE FLASHCARDS --- */
function getCategories() {
  const cats = ['Todas', ...new Set(flashcards.map(c => c.cat))];
  return cats;
}

function filterFlashcards() {
  const f = state.flash;
  f.filtered = f.cards.filter(card => {
    const matchCat = (f.cat === 'Todas' || card.cat === f.cat);
    const qLower = card.q.toLowerCase();
    const aLower = card.a.toLowerCase();
    const sLower = f.search.toLowerCase();
    const matchSearch = !f.search || qLower.includes(sLower) || aLower.includes(sLower);
    const matchReview = !f.onlyReview || f.markedReview.has(card.q);
    return matchCat && matchSearch && matchReview;
  });

  if (f.idx >= f.filtered.length) {
    f.idx = Math.max(0, f.filtered.length - 1);
  }
  renderFlashcard();
}

function renderFlashcard() {
  const f = state.flash;
  const cardStage = document.querySelector('.card-stage');
  
  if (f.filtered.length === 0) {
    cardStage.style.display = 'none';
    DOM.deckCount.textContent = '0 cartas';
    DOM.deckCatLabel.textContent = f.cat;
    DOM.progressText.textContent = '-';
    DOM.btnKnow.style.display = 'none';
    DOM.btnReview.style.display = 'none';
    return;
  }

  cardStage.style.display = 'block';
  DOM.btnKnow.style.display = 'inline-block';
  DOM.btnReview.style.display = 'inline-block';

  const current = f.filtered[f.idx];
  
  // Desvira a carta antes de atualizar texto
  DOM.card.classList.remove('flipped');
  f.flipped = false;

  setTimeout(() => {
    DOM.frontTag.textContent = current.cat;
    DOM.frontText.textContent = current.q;
    DOM.backTag.textContent = `${current.cat} — Resposta`;
    DOM.backText.textContent = current.a;
  }, 150);

  DOM.deckCount.textContent = `Carta ${f.idx + 1} de ${f.filtered.length}`;
  DOM.deckCatLabel.textContent = current.cat;
  DOM.progressText.textContent = `${Math.round(((f.idx + 1) / f.filtered.length) * 100)}% concluído`;

  // Atualiza marcas
  DOM.btnKnow.classList.toggle('marked', f.markedKnow.has(current.q));
  DOM.btnReview.classList.toggle('marked', f.markedReview.has(current.q));

  updateHeaderStats();
}

function initFlashcards() {
  // Renderiza pills de categorias
  const cats = getCategories();
  DOM.catPills.innerHTML = '';
  cats.forEach(c => {
    const btn = document.createElement('button');
    btn.className = `pill ${c === 'Todas' ? 'active' : ''}`;
    btn.textContent = c;
    btn.addEventListener('click', () => {
      document.querySelectorAll('.cat-pills .pill').forEach(p => p.classList.remove('active'));
      btn.classList.add('active');
      state.flash.cat = c;
      filterFlashcards();
    });
    DOM.catPills.appendChild(btn);
  });

  // Flip na carta
  DOM.card.addEventListener('click', () => {
    state.flash.flipped = !state.flash.flipped;
    DOM.card.classList.toggle('flipped', state.flash.flipped);
  });

  // Botões de Navegação
  DOM.nextBtn.addEventListener('click', () => {
    if (state.flash.filtered.length === 0) return;
    state.flash.idx = (state.flash.idx + 1) % state.flash.filtered.length;
    renderFlashcard();
  });

  DOM.prevBtn.addEventListener('click', () => {
    if (state.flash.filtered.length === 0) return;
    state.flash.idx = (state.flash.idx - 1 + state.flash.filtered.length) % state.flash.filtered.length;
    renderFlashcard();
  });

  // Marcar estado de conhecimento
  DOM.btnKnow.addEventListener('click', (e) => {
    e.stopPropagation();
    const cur = state.flash.filtered[state.flash.idx];
    if (!cur) return;
    if (state.flash.markedKnow.has(cur.q)) {
      state.flash.markedKnow.delete(cur.q);
    } else {
      state.flash.markedKnow.add(cur.q);
      state.flash.markedReview.delete(cur.q);
    }
    renderFlashcard();
  });

  DOM.btnReview.addEventListener('click', (e) => {
    e.stopPropagation();
    const cur = state.flash.filtered[state.flash.idx];
    if (!cur) return;
    if (state.flash.markedReview.has(cur.q)) {
      state.flash.markedReview.delete(cur.q);
    } else {
      state.flash.markedReview.add(cur.q);
      state.flash.markedKnow.delete(cur.q);
    }
    renderFlashcard();
  });

  // Filtros
  DOM.searchBox.addEventListener('input', (e) => {
    state.flash.search = e.target.value;
    filterFlashcards();
  });

  DOM.onlyReview.addEventListener('change', (e) => {
    state.flash.onlyReview = e.target.checked;
    filterFlashcards();
  });

  DOM.shuffleBtn.addEventListener('click', () => {
    state.flash.filtered.sort(() => Math.random() - 0.5);
    state.flash.idx = 0;
    renderFlashcard();
  });

  filterFlashcards();
}

/* --- LÓGICA DE QUIZ / QUESTÕES --- */
function filterQuiz() {
  const q = state.quiz;
  q.filtered = q.data.filter(item => q.cat === 'Todas' || item.cat === q.cat);
  if (q.idx >= q.filtered.length) q.idx = 0;
  renderQuiz();
}

function renderQuiz() {
  const q = state.quiz;
  const container = document.querySelector('.qcard');

  if (q.filtered.length === 0) {
    container.innerHTML = '<div class="empty">Nenhuma questão encontrada nesta categoria.</div>';
    DOM.quizProgress.textContent = '0 questões';
    return;
  }

  const current = q.filtered[q.idx];
  const origIndex = q.data.indexOf(current);
  const savedAns = q.userAnswers[origIndex];

  DOM.quizProgress.textContent = `Questão ${q.idx + 1} de ${q.filtered.length}`;
  DOM.quizTag.textContent = current.cat;
  DOM.quizText.textContent = current.q;

  // Renderiza opções
  DOM.quizOptions.innerHTML = '';
  DOM.quizExplain.classList.remove('show');
  DOM.quizExplain.innerHTML = '';

  const letters = ['A', 'B', 'C', 'D'];
  current.opts.forEach((optText, index) => {
    const btn = document.createElement('button');
    btn.className = 'opt';
    btn.innerHTML = `<span class="letter">${letters[index]}</span> <span>${optText}</span>`;

    if (savedAns !== undefined) {
      btn.disabled = true;
      if (index === current.ans) {
        btn.classList.add('correct');
      }
      if (savedAns === index && savedAns !== current.ans) {
        btn.classList.add('wrong');
      }
    } else {
      btn.addEventListener('click', () => handleAnswer(origIndex, index));
    }

    DOM.quizOptions.appendChild(btn);
  });

  // Mostra explicação se respondida
  if (savedAns !== undefined) {
    DOM.quizExplain.innerHTML = `<b>Explicação:</b> ${current.exp}`;
    DOM.quizExplain.classList.add('show');
  }

  // Atualiza placar
  let correctCount = 0;
  let totalAnswered = Object.keys(q.userAnswers).length;
  Object.keys(q.userAnswers).forEach(k => {
    if (q.userAnswers[k] === q.data[k].ans) correctCount++;
  });

  DOM.quizScore.textContent = `Acertos: ${correctCount}/${totalAnswered}`;
  DOM.scoreStrip.textContent = `Aproveitamento: ${totalAnswered ? Math.round((correctCount / totalAnswered) * 100) : 0}%`;

  updateHeaderStats();
}

function handleAnswer(questionIndex, chosenOption) {
  state.quiz.userAnswers[questionIndex] = chosenOption;
  renderQuiz();
}

function initQuiz() {
  // Preenche select de categorias
  const cats = ['Todas', ...new Set(quizData.map(q => q.cat))];
  DOM.quizCat.innerHTML = '';
  cats.forEach(c => {
    const opt = document.createElement('option');
    opt.value = c;
    opt.textContent = c;
    DOM.quizCat.appendChild(opt);
  });

  DOM.quizCat.addEventListener('change', (e) => {
    state.quiz.cat = e.target.value;
    filterQuiz();
  });

  DOM.quizNext.addEventListener('click', () => {
    if (!state.quiz.filtered.length) return;
    state.quiz.idx = (state.quiz.idx + 1) % state.quiz.filtered.length;
    renderQuiz();
  });

  DOM.quizPrev.addEventListener('click', () => {
    if (!state.quiz.filtered.length) return;
    state.quiz.idx = (state.quiz.idx - 1 + state.quiz.filtered.length) % state.quiz.filtered.length;
    renderQuiz();
  });

  DOM.quizShuffle.addEventListener('click', () => {
    state.quiz.filtered.sort(() => Math.random() - 0.5);
    state.quiz.idx = 0;
    renderQuiz();
  });

  DOM.quizReset.addEventListener('click', () => {
    if (confirm("Deseja zerar todas as respostas do quiz?")) {
      state.quiz.userAnswers = {};
      renderQuiz();
    }
  });

  filterQuiz();
}

/* --- ESTATÍSTICAS E RENDIMENTO --- */
function updateHeaderStats() {
  const totalCards = flashcards.length;
  const know = state.flash.markedKnow.size;
  const review = state.flash.markedReview.size;

  DOM.headerStats.innerHTML = `
    <div class="stat-chip"><span class="dot"></span><b>${totalCards}</b><span class="lbl">cartas</span></div>
    <div class="stat-chip"><span class="dot" style="background:var(--ok)"></span><b>${know}</b><span class="lbl">dominadas</span></div>
    <div class="stat-chip"><span class="dot" style="background:var(--red-flag)"></span><b>${review}</b><span class="lbl">p/ revisar</span></div>
  `;
}

function renderStats() {
  const qData = state.quiz.data;
  const answers = state.quiz.userAnswers;
  const answeredKeys = Object.keys(answers);
  const totalAnswered = answeredKeys.length;

  let totalCorrect = 0;
  answeredKeys.forEach(k => {
    if (answers[k] === qData[k].ans) totalCorrect++;
  });

  const accuracy = totalAnswered ? Math.round((totalCorrect / totalAnswered) * 100) : 0;

  DOM.statGrid.innerHTML = `
    <div class="stat-box">
      <div class="num">${flashcards.length}</div>
      <div class="lbl">Total de Flashcards</div>
    </div>
    <div class="stat-box">
      <div class="num">${state.flash.markedKnow.size}</div>
      <div class="lbl">Cartas Dominadas</div>
    </div>
    <div class="stat-box">
      <div class="num">${totalAnswered}/${qData.length}</div>
      <div class="lbl">Questões Respondidas</div>
    </div>
    <div class="stat-box">
      <div class="num">${accuracy}%</div>
      <div class="lbl">Taxa de Acerto</div>
    </div>
  `;

  // Barras de progresso por categoria
  const cats = [...new Set(qData.map(item => item.cat))];
  DOM.catBars.innerHTML = '';

  cats.forEach(cat => {
    const catQuestions = qData.filter(q => q.cat === cat);
    let catAnswered = 0;
    let catCorrect = 0;

    catQuestions.forEach(q => {
      const idx = qData.indexOf(q);
      if (answers[idx] !== undefined) {
        catAnswered++;
        if (answers[idx] === q.ans) catCorrect++;
      }
    });

    const pct = catAnswered ? Math.round((catCorrect / catAnswered) * 100) : 0;

    const row = document.createElement('div');
    row.className = 'cat-bar-row';
    row.innerHTML = `
      <div class="name">${cat}</div>
      <div class="cat-bar-track">
        <div class="cat-bar-fill" style="width: ${pct}%"></div>
      </div>
      <div class="cat-bar-pct">${pct}%</div>
    `;
    DOM.catBars.appendChild(row);
  });
}

/* --- DISPARO INICIAL --- */
document.addEventListener('DOMContentLoaded', () => {
  initTabs();
  initFlashcards();
  initQuiz();
  updateHeaderStats();
});
</script>
</body>
</html>
