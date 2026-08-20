<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Farmacologia Veterinária — Banco de Estudo</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Zilla+Slab:wght@400;600;700&family=IBM+Plex+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@500;600&display=swap" rel="stylesheet">
<style>
  :root{
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
  *{box-sizing:border-box;}
  html{ scroll-behavior:smooth; }
  body{
    margin:0;
    background:
      radial-gradient(circle at 1px 1px, rgba(46,82,51,0.05) 1px, transparent 0) 0 0/14px 14px,
      var(--bg);
    color:var(--ink);
    font-family:'IBM Plex Sans', sans-serif;
    min-height:100vh;
    padding:0 16px 72px;
  }
  .wrap{max-width:900px; margin:0 auto;}
  ::selection{ background:var(--amber-light); color:var(--forest-dark); }
  button, input, select{ font:inherit; }
  button:focus-visible, input:focus-visible, select:focus-visible{
    outline:2px solid var(--amber-deep); outline-offset:2px;
  }
  @media (prefers-reduced-motion: reduce){
    *{ animation-duration:0.001ms !important; transition-duration:0.001ms !important; }
  }

  /* ---------- HEADER / RECEITUÁRIO ---------- */
  .letterhead{
    position:relative;
    background: linear-gradient(180deg, var(--paper-alt), var(--paper));
    border:1px solid var(--line);
    border-top:none;
    border-radius:0 0 10px 10px;
    padding:34px 34px 26px;
    margin:0 -1px 30px;
    box-shadow: 0 14px 30px -20px var(--shadow);
  }
  .letterhead::before{
    content:"";
    position:absolute; left:-1px; right:-1px; top:-9px; height:18px;
    background-image: radial-gradient(circle at 9px 9px, var(--bg) 9px, transparent 9.5px);
    background-size: 18px 18px;
    background-position: 0 0;
    border-left:1px solid var(--line); border-right:1px solid var(--line);
  }
  .letterhead-top{ display:flex; justify-content:space-between; align-items:flex-start; gap:18px; }
  .eyebrow{
    font-family:'IBM Plex Mono', monospace;
    font-size:10.5px; letter-spacing:0.16em; text-transform:uppercase;
    color:var(--amber-deep); display:flex; align-items:center; gap:7px; margin-bottom:10px;
  }
  .eyebrow::before{ content:""; width:16px; height:1px; background:var(--amber-deep); display:inline-block; }
  h1{
    font-family:'Zilla Slab', serif; font-weight:700; font-size:38px; margin:0 0 8px;
    line-height:1.06; letter-spacing:-0.01em; color:var(--forest-dark);
  }
  .sub{ color:var(--muted); font-size:14.5px; max-width:56ch; line-height:1.55; }

  .rx-stamp{
    flex-shrink:0; width:64px; height:64px; border-radius:50%;
    border:1.5px solid var(--forest); color:var(--forest);
    display:flex; align-items:center; justify-content:center;
    font-family:'Zilla Slab', serif; font-weight:700; font-size:22px;
    transform:rotate(-9deg); opacity:0.9;
    background: repeating-radial-gradient(circle, transparent 0 2px, rgba(46,82,51,0.05) 2px 3px);
  }

  .stats-row{
    display:flex; gap:10px; margin-top:20px; flex-wrap:wrap;
  }
  .stat-chip{
    display:flex; align-items:baseline; gap:6px;
    background:var(--paper); border:1px solid var(--line); border-radius:999px;
    padding:6px 13px 6px 11px;
  }
  .stat-chip .dot{ width:6px; height:6px; border-radius:50%; background:var(--amber); flex-shrink:0; }
  .stat-chip b{ font-family:'Zilla Slab', serif; font-size:15px; color:var(--forest-dark); }
  .stat-chip span.lbl{ font-family:'IBM Plex Mono', monospace; font-size:10.5px; color:var(--muted); }

  /* ---------- TABS: blister pack ---------- */
  nav.tabs{
    display:flex; gap:0; margin:0 0 22px; background:var(--paper-alt);
    border:1px solid var(--line); border-radius:12px; padding:5px; position:relative;
  }
  .tab{
    flex:1; font-family:'IBM Plex Mono', monospace; font-size:12px; letter-spacing:0.03em; text-transform:uppercase;
    background:none; border:none; padding:11px 4px; color:var(--muted); cursor:pointer;
    border-radius:8px; position:relative; transition:color 0.2s ease;
  }
  .tab + .tab::before{
    content:""; position:absolute; left:0; top:20%; bottom:20%; width:1px; background:var(--line);
  }
  .tab.active{ color:var(--paper); }
  .tab.active::before, .tab.active + .tab::before{ display:none; }
  .tab-highlight{
    position:absolute; top:5px; bottom:5px; border-radius:8px; background:var(--forest);
    box-shadow:0 4px 12px -4px var(--shadow); transition:transform 0.28s cubic-bezier(.4,.1,.2,1), width 0.28s cubic-bezier(.4,.1,.2,1);
    z-index:0; width:33.33%;
  }
  .tab{ z-index:1; }

  section.panel{ display:none; animation: rise 0.35s ease; } section.panel.active{ display:block; }
  @keyframes rise{ from{ opacity:0; transform:translateY(6px);} to{ opacity:1; transform:translateY(0);} }

  .toolbar{ display:flex; gap:10px; margin-bottom:14px; flex-wrap:wrap; align-items:center; }
  .toolbar input[type=text]{
    flex:1; min-width:160px; font-family:'IBM Plex Sans'; font-size:13.5px;
    background:var(--paper); border:1px solid var(--line); padding:10px 13px; border-radius:8px; color:var(--ink);
    transition:border-color 0.15s;
  }
  .toolbar input[type=text]:hover{ border-color:#c7c4ac; }
  select{
    font-family:'IBM Plex Mono', monospace; font-size:12px; background:var(--paper);
    border:1px solid var(--line); padding:9px 10px; color:var(--ink); border-radius:8px; cursor:pointer;
  }
  .chk-label{
    font-family:'IBM Plex Mono', monospace; font-size:11.5px; color:var(--muted);
    display:flex; align-items:center; gap:6px; white-space:nowrap; cursor:pointer;
  }
  .chk-label input{ accent-color:var(--forest); }

  .cat-pills{ display:flex; flex-wrap:wrap; gap:7px; margin-bottom:18px; }
  .pill{
    font-family:'IBM Plex Mono', monospace; font-size:10.5px; padding:6px 11px; border-radius:20px;
    border:1px solid var(--line); color:var(--muted); background:var(--paper); cursor:pointer;
    transition:all 0.15s;
  }
  .pill:hover{ border-color:var(--forest); color:var(--forest-dark); }
  .pill.active{ background:var(--forest); color:#F4EFDD; border-color:var(--forest); }

  .deck-meta{ display:flex; justify-content:space-between; align-items:center;
    font-family:'IBM Plex Mono', monospace; font-size:12px; color:var(--muted); margin-bottom:10px; }

  /* ---------- FLASHCARD ---------- */
  .card-stage{ perspective:1600px; height:270px; margin-bottom:18px; }
  .card{ position:relative; width:100%; height:100%; transform-style:preserve-3d;
    transition:transform 0.5s cubic-bezier(.34,1.1,.4,1); cursor:pointer; }
  .card.flipped{ transform:rotateY(180deg); }
  .card:hover{ transform:translateY(-2px); }
  .card.flipped:hover{ transform:rotateY(180deg) translateY(-2px); }
  .face{ position:absolute; inset:0; background:var(--paper); border:1px solid var(--line); border-radius:8px;
    backface-visibility:hidden; display:flex; flex-direction:column; padding:26px;
    box-shadow: 0 1px 0 var(--line), 0 16px 32px -18px var(--shadow); }
  .face::before{ content:""; position:absolute; left:0; top:20px; bottom:20px; width:3px; border-radius:2px;
    background: repeating-linear-gradient(180deg, var(--amber-light) 0 6px, transparent 6px 13px); }
  .face .tag{ font-family:'IBM Plex Mono', monospace; font-size:10px; text-transform:uppercase;
    letter-spacing:0.09em; color:var(--amber-deep); margin-bottom:12px; display:flex; justify-content:space-between;
    background:var(--amber-light); align-self:flex-start; padding:4px 10px; border-radius:20px; transform:rotate(-1deg); }
  .face .content{ font-family:'Zilla Slab', serif; font-size:21px; line-height:1.32; color:var(--ink); flex:1;
    display:flex; align-items:center; overflow-y:auto; }
  .face .hint{ font-family:'IBM Plex Mono', monospace; font-size:10px; color:#95a290; align-self:flex-end; }
  .back{ transform:rotateY(180deg); background:var(--forest-dark); border-color:var(--forest-dark);}
  .back .content{ color:#F4EFDD; font-size:17px; }
  .back .tag{ color:var(--amber-light); background:rgba(239,219,166,0.14); }
  .back .hint{ color:#7f9080; }

  .deck-controls{ display:flex; justify-content:space-between; align-items:center; gap:10px; flex-wrap:wrap; }
  .navbtn{ font-family:'IBM Plex Mono', monospace; font-size:12px; background:var(--forest); color:#F4EFDD;
    border:none; padding:10px 18px; border-radius:999px; cursor:pointer; transition:all 0.15s;
    box-shadow:0 6px 14px -8px var(--shadow); }
  .navbtn:hover{ background:var(--forest-dark); transform:translateY(-1px); }
  .navbtn.ghost{ background:none; color:var(--forest); border:1px solid var(--line); box-shadow:none; }
  .navbtn.ghost:hover{ border-color:var(--forest); background:var(--paper-alt); }
  .navbtn.small{ font-size:10.5px; padding:7px 12px; }
  .progress{ font-family:'IBM Plex Mono', monospace; font-size:11.5px; color:var(--muted); }
  .self-row{ display:flex; gap:8px; justify-content:center; margin:14px 0 6px; }
  .self-btn{ font-family:'IBM Plex Mono', monospace; font-size:11px; padding:8px 14px; border-radius:999px;
    border:1px solid var(--line); background:var(--paper); cursor:pointer; color:var(--muted); transition:all 0.15s; }
  .self-btn:hover{ border-color:var(--forest); }
  .self-btn.know.marked{ background:#E4EFE1; border-color:var(--ok); color:var(--forest-dark); }
  .self-btn.review.marked{ background:#F4E3DC; border-color:var(--red-flag); color:var(--red-flag); }

  /* ---------- QUIZ ---------- */
  .qmeta{ display:flex; justify-content:space-between; align-items:baseline;
    font-family:'IBM Plex Mono', monospace; font-size:12px; color:var(--muted); margin-bottom:10px; flex-wrap:wrap; gap:6px;}
  .qcard{ background:var(--paper); border:1px solid var(--line); border-radius:10px; padding:26px; margin-bottom:16px;
    box-shadow:0 16px 32px -20px var(--shadow); }
  .qtag{ font-family:'IBM Plex Mono', monospace; font-size:10px; text-transform:uppercase; letter-spacing:0.09em;
    color:var(--amber-deep); margin-bottom:12px; background:var(--amber-light); display:inline-block; padding:4px 10px;
    border-radius:20px; transform:rotate(-1deg); }
  .qtext{ font-family:'Zilla Slab', serif; font-size:19.5px; line-height:1.38; margin-bottom:18px; color:var(--forest-dark); }
  .options{ display:flex; flex-direction:column; gap:9px; }
  .opt{ text-align:left; font-family:'IBM Plex Sans'; font-size:14px; background:var(--paper-alt);
    border:1px solid var(--line); padding:12px 14px; border-radius:8px; cursor:pointer; display:flex; gap:11px; align-items:flex-start;
    transition:all 0.14s; }
  .opt:hover{ border-color:var(--forest); background:#F3F0E0; transform:translateX(2px); }
  .opt .letter{ font-family:'IBM Plex Mono', monospace; font-size:11.5px; color:var(--forest); border:1px solid var(--forest);
    width:20px; height:20px; border-radius:50%; display:flex; align-items:center; justify-content:center; flex-shrink:0; }
  .opt.correct{ background:#E4EFE1; border-color:var(--ok); }
  .opt.correct .letter{ background:var(--ok); border-color:var(--ok); color:#fff; }
  .opt.wrong{ background:#F4E3DC; border-color:var(--red-flag); }
  .opt.wrong .letter{ background:var(--red-flag); border-color:var(--red-flag); color:#fff; }
  .opt[disabled]{ cursor:default; }
  .opt[disabled]:hover{ transform:none; }
  .explain{ font-size:13.5px; color:#4a5a4a; border-top:1px dashed var(--line); margin-top:16px; padding-top:14px;
    line-height:1.55; display:none; } .explain.show{ display:block; animation:rise 0.25s ease; } .explain b{ color:var(--forest-dark); }

  .score-strip{ font-family:'IBM Plex Mono', monospace; font-size:11.5px; color:var(--muted); display:flex; gap:14px; }
  .reset-row{ text-align:right; margin-top:8px; }
  .reset-row button{ font-family:'IBM Plex Mono', monospace; font-size:11px; color:var(--amber-deep); background:none;
    border:none; cursor:pointer; text-decoration:underline; text-underline-offset:2px; }

  /* ---------- STATS ---------- */
  .stat-grid{ display:grid; grid-template-columns:1fr 1fr; gap:12px; margin-bottom:26px; }
  @media (min-width:600px){ .stat-grid{ grid-template-columns:repeat(4,1fr);} }
  .stat-box{ background:var(--paper); border:1px solid var(--line); border-radius:10px; padding:16px;
    border-top:3px solid var(--amber); box-shadow:0 10px 22px -18px var(--shadow); }
  .stat-box .num{ font-family:'Zilla Slab', serif; font-size:28px; color:var(--forest-dark); line-height:1; }
  .stat-box .lbl{ font-family:'IBM Plex Mono', monospace; font-size:10px; color:var(--muted); text-transform:uppercase; letter-spacing:0.06em; margin-top:6px; }
  .stats-heading{ font-family:'Zilla Slab',serif; font-size:16px; margin:6px 0 16px; color:var(--forest-dark); }
  .cat-bar-row{ display:flex; align-items:center; gap:10px; margin-bottom:10px; }
  .cat-bar-row .name{ font-family:'IBM Plex Mono', monospace; font-size:11px; width:190px; flex-shrink:0; color:var(--ink); }
  .cat-bar-track{ flex:1; height:9px; background:var(--line); border-radius:5px; overflow:hidden; }
  .cat-bar-fill{ height:100%; background:linear-gradient(90deg, var(--forest), var(--amber)); transition:width 0.4s ease; }
  .cat-bar-pct{ font-family:'IBM Plex Mono', monospace; font-size:10.5px; color:var(--muted); width:38px; text-align:right; }

  .empty{ font-family:'IBM Plex Mono', monospace; font-size:12.5px; color:var(--muted); padding:30px 0; text-align:center; }

  footer.stamp-row{
    display:flex; align-items:center; gap:10px; justify-content:center; margin-top:36px;
    font-family:'IBM Plex Mono', monospace; font-size:10.5px; color:var(--muted); letter-spacing:0.04em;
  }
  footer.stamp-row .seal{ width:9px; height:9px; border:1px solid var(--muted); border-radius:50%; flex-shrink:0; }

  @media (max-width:520px){
    .letterhead{ padding:24px 20px 20px; }
    h1{ font-size:28px; }
    .rx-stamp{ width:48px; height:48px; font-size:17px; }
    .card-stage{ height:320px; }
    .face .content{ font-size:17.5px; }
    .cat-bar-row .name{ width:120px; font-size:10px; }
    .tab{ font-size:10.5px; padding:10px 2px; }
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
{cat:"Corticoides", q:"O que é efeito mineralocorticoide de um glicocorticoide e por que importa clinicamente?", a:"Alguns corticoides também atuam em receptores mineralocorticoides, retendo sódio e água e promovendo excreção de potássio — relevante em pacientes cardiopatas ou com distúrbios eletrolíticos."},

// OPIOIDES E ANALGESIA
{cat:"Opioides", q:"Onde atuam principalmente os opioides para produzir analgesia?", a:"Nos receptores opioides (mu, kappa, delta) no sistema nervoso central e periférico, modulando a transmissão e percepção da dor."},
{cat:"Opioides", q:"Diferença entre um agonista total (ex: morfina, metadona) e um agonista parcial (ex: buprenorfina) em receptores mu.", a:"O agonista total produz efeito analgésico máximo dose-dependente; o agonista parcial tem um teto de efeito (efeito máximo menor), mesmo em doses altas."},
{cat:"Opioides", q:"Qual antagonista opioide é usado para reversão de emergência?", a:"Naloxona — antagonista competitivo dos receptores opioides, usado para reverter depressão respiratória e sedação excessiva."},
{cat:"Opioides", q:"Por que opioides podem causar disforia/excitação em gatos e cavalos em vez de sedação?", a:"A resposta aos opioides tem variação interespécie; em algumas espécies e doses, pode predominar estimulação do SNC em vez de sedação, exigindo associação com sedativos e ajuste de dose."},
{cat:"Opioides", q:"Principal efeito adverso respiratório dos opioides.", a:"Depressão respiratória dose-dependente por ação direta no centro respiratório do tronco encefálico."},
{cat:"Opioides", q:"Por que a morfina pode causar liberação de histamina quando administrada rapidamente por via IV?", a:"Pode estimular diretamente a degranulação de mastócitos, causando hipotensão, prurido e eritema — por isso a administração IV deve ser lenta."},
{cat:"Opioides", q:"O que caracteriza o tramadol em termos de mecanismo de ação?", a:"Tem ação dupla: agonista fraco em receptores opioides mu e inibição da recaptação de serotonina e noradrenalina, contribuindo para analgesia por vias adicionais."},
{cat:"Opioides", q:"Por que opioides costumam causar constipação com uso prolongado?", a:"Reduzem a motilidade gastrointestinal ao atuar em receptores opioides no plexo entérico, retardando o trânsito intestinal."},

// ANESTÉSICOS E SEDATIVOS
{cat:"Anestésicos", q:"Por que a acepromazina é usada com cautela em Boxers?", a:"A raça parece ter sensibilidade individual aumentada, podendo apresentar bradicardia, hipotensão e síncope mais acentuadas que outras raças."},
{cat:"Anestésicos", q:"Mecanismo de ação da acepromazina.", a:"Antagonista de receptores dopaminérgicos D2 no SNC, com efeito tranquilizante; também bloqueia receptores alfa-1 adrenérgicos, contribuindo para hipotensão."},
{cat:"Anestésicos", q:"Efeito da xilazina/detomidina (agonistas alfa-2) sobre o sistema cardiovascular.", a:"Causam vasoconstrição periférica inicial seguida de bradicardia reflexa e redução do débito cardíaco — usar com cautela em pacientes cardiopatas."},
{cat:"Anestésicos", q:"Qual antagonista reverte os efeitos dos agonistas alfa-2 (ex: xilazina, dexmedetomidina)?", a:"Atipamezol (antagonista alfa-2 adrenérgico específico); ioimbina também pode ser usada para reverter xilazina."},
{cat:"Anestésicos", q:"Mecanismo de ação geral dos anestésicos dissociativos (ex: cetamina).", a:"Antagonizam receptores NMDA de glutamato, produzindo um estado de dissociação entre o córtex e o sistema límbico, com analgesia somática e preservação relativa dos reflexos protetores."},
{cat:"Anestésicos", q:"Por que a cetamina costuma ser associada a um tranquilizante/sedativo antes do uso?", a:"Isolada, pode causar rigidez muscular, convulsões e recuperação anestésica agitada; a associação melhora o relaxamento muscular e suaviza a indução e recuperação."},
{cat:"Anestésicos", q:"Mecanismo de ação dos benzodiazepínicos (ex: diazepam, midazolam).", a:"Potencializam a ação do GABA nos receptores GABA-A, aumentando a frequência de abertura dos canais de cloreto e promovendo sedação, relaxamento muscular e efeito anticonvulsivante."},
{cat:"Anestésicos", q:"Qual antagonista reverte os efeitos dos benzodiazepínicos?", a:"Flumazenil, antagonista competitivo no sítio benzodiazepínico do receptor GABA-A."},
{cat:"Anestésicos", q:"Por que o propofol exige administração cuidadosa em gatos com uso repetido?", a:"Gatos metabolizam o propofol mais lentamente (relacionado à menor capacidade de glucuronidação hepática), podendo haver acúmulo e recuperação anestésica prolongada com doses repetidas."},
{cat:"Anestésicos", q:"Por que os anestésicos inalatórios voláteis (ex: isoflurano, sevoflurano) são preferidos em cirurgias longas?", a:"Permitem controle mais fino e rápido da profundidade anestésica através do ajuste da concentração inspirada, com eliminação predominantemente pulmonar (pouca dependência do metabolismo hepático/renal)."},

// CARDIOVASCULAR
{cat:"Cardiovascular", q:"Mecanismo de ação da furosemida.", a:"Diurético de alça: inibe o cotransportador Na⁺/K⁺/2Cl⁻ na alça de Henle, aumentando a excreção de água e eletrólitos — usado em insuficiência cardíaca congestiva."},
{cat:"Cardiovascular", q:"Para que serve o pimobendan em cardiopatas caninos?", a:"É um inodilatador: aumenta a contratilidade cardíaca (sensibilizador de cálcio, inibidor de fosfodiesterase-3) e promove vasodilatação, usado em insuficiência cardíaca congestiva e cardiomiopatia dilatada."},
{cat:"Cardiovascular", q:"Mecanismo de ação dos inibidores da ECA (ex: enalapril, benazepril).", a:"Bloqueiam a enzima conversora de angiotensina, reduzindo a formação de angiotensina II — diminuem a vasoconstrição e a retenção de sódio/água, reduzindo a pós-carga cardíaca."},
{cat:"Cardiovascular", q:"Por que a digoxina exige monitoramento cuidadoso da dose?", a:"Tem índice terapêutico estreito; níveis acima do adequado causam arritmias e sinais de toxicidade (anorexia, vômito, arritmias graves)."},
{cat:"Cardiovascular", q:"Mecanismo de ação básico dos bloqueadores dos canais de cálcio (ex: diltiazem).", a:"Bloqueiam a entrada de cálcio nas células musculares cardíacas e vasculares, reduzindo a contratilidade e promovendo vasodilatação — usados em algumas arritmias e cardiomiopatia hipertrófica felina."},
{cat:"Cardiovascular", q:"Por que betabloqueadores (ex: atenolol) devem ser retirados gradualmente e não de forma abrupta?", a:"A suspensão abrupta pode causar um efeito rebote com taquicardia e hipertensão, por up-regulation compensatória de receptores beta durante o uso prolongado."},
{cat:"Cardiovascular", q:"Qual é o principal uso clínico da lidocaína como antiarrítmico?", a:"Tratamento de arritmias ventriculares, por bloquear canais de sódio e reduzir a excitabilidade do tecido cardíaco ventricular."},
{cat:"Cardiovascular", q:"Por que a espironolactona é usada em associação com outros diuréticos em ICC?", a:"É um diurético poupador de potássio (antagonista da aldosterona), compensando a perda de potássio causada por diuréticos de alça e tiazídicos, além de ter efeito antifibrótico cardíaco."},
{cat:"Cardiovascular", q:"O que caracteriza a cardiomiopatia hipertrófica felina do ponto de vista farmacológico de manejo?", a:"O manejo frequentemente envolve bloqueadores de canais de cálcio ou betabloqueadores para reduzir a frequência cardíaca e melhorar o enchimento diastólico, além de diuréticos se houver congestão."},

// ENDÓCRINO
{cat:"Endócrino", q:"Diferença de manejo de insulina entre cães e gatos diabéticos.", a:"Gatos frequentemente entram em remissão diabética com bom controle glicêmico precoce (semelhante ao diabetes tipo 2); cães geralmente precisam de insulinoterapia vitalícia (semelhante ao diabetes tipo 1)."},
{cat:"Endócrino", q:"Mecanismo de ação do metimazol no tratamento de hipertireoidismo felino.", a:"Inibe a enzima tireoperoxidase, bloqueando a síntese de hormônios tireoidianos (T3 e T4) na glândula tireoide."},
{cat:"Endócrino", q:"Por que o levotiroxina é usada em cães hipotireoideos e não em gatos com a mesma frequência?", a:"O hipotireoidismo primário é uma condição comum em cães, enquanto em gatos o hipertireoidismo é muito mais frequente que o hipotireoidismo — os quadros e tratamentos endócrinos tireoidianos diferem bastante entre as espécies."},
{cat:"Endócrino", q:"Mecanismo de ação do trilostano no tratamento do hiperadrenocorticismo canino (Cushing).", a:"Inibe a enzima 3-beta-hidroxiesteroide desidrogenase, bloqueando a síntese de cortisol (e outros esteroides adrenais) nas glândulas adrenais."},
{cat:"Endócrino", q:"Por que pacientes com hipoadrenocorticismo (Addison) precisam de reposição de mineralocorticoide e glicocorticoide?", a:"Há destruição do córtex adrenal, incapaz de produzir aldosterona (regulação de sódio/potássio) e cortisol (resposta ao estresse, metabolismo) — a reposição hormonal é vitalícia."},
{cat:"Endócrino", q:"O que é o efeito Somogyi no manejo de diabetes com insulina?", a:"Hiperglicemia de rebote após um episódio de hipoglicemia induzida por dose excessiva de insulina, devido à liberação de hormônios contrarreguladores (como o glucagon) — pode ser confundida com dose insuficiente."},
{cat:"Endócrino", q:"Por que a administração de insulina exige cuidado especial com o tipo e a via de administração?", a:"Diferentes formulações de insulina (curta, intermediária, longa duração) têm perfis de ação distintos; erros de tipo, dose ou via podem causar hipoglicemia grave ou falta de controle glicêmico."},

// ANTIPARASITÁRIOS
{cat:"Antiparasitários", q:"Quais raças de cães têm risco de neurotoxicidade grave com ivermectina?", a:"Collies e raças relacionadas (Pastor de Shetland, Old English Sheepdog, Australian Shepherd) com mutação no gene MDR1/ABCB1, que compromete a função da glicoproteína-P na barreira hematoencefálica."},
{cat:"Antiparasitários", q:"Mecanismo de ação das lactonas macrocíclicas (ex: ivermectina).", a:"Aumentam a permeabilidade da membrana neuronal e muscular de invertebrados a íons cloreto (via canais de cloreto glutamato-dependentes), causando paralisia e morte do parasita."},
{cat:"Antiparasitários", q:"Por que produtos à base de permetrina são perigosos para gatos?", a:"Gatos têm deficiência de glucuroniltransferase e não conseguem metabolizar a permetrina com eficiência, resultando em intoxicação grave — tremores, convulsões e até morte, mesmo com exposição a produtos formulados apenas para cães."},
{cat:"Antiparasitários", q:"Mecanismo de ação geral dos piretroides (ex: permetrina) sobre os parasitas.", a:"Atuam nos canais de sódio dependentes de voltagem dos neurônios do parasita, prolongando sua abertura e causando hiperexcitação, paralisia e morte."},
{cat:"Antiparasitários", q:"Como agem os isoxazolinas (ex: fluralaner, afoxolaner) contra pulgas e carrapatos?", a:"Bloqueiam canais de cloreto dependentes de GABA e glutamato no sistema nervoso do parasita, causando hiperexcitação neuronal descontrolada e morte."},
{cat:"Antiparasitários", q:"Mecanismo de ação geral dos benzimidazólicos (ex: fenbendazol, albendazol) como anti-helmínticos.", a:"Ligam-se à beta-tubulina do parasita, impedindo a polimerização de microtúbulos — compromete funções celulares essenciais como transporte e absorção de nutrientes, levando à morte do parasita."},
{cat:"Antiparasitários", q:"Por que o praziquantel é eficaz contra cestódeos (tênias)?", a:"Aumenta a permeabilidade da membrana do parasita ao cálcio, causando contração espástica da musculatura e danos ao tegumento, o que facilita a digestão do parasita pelo hospedeiro ou sua expulsão."},
{cat:"Antiparasitários", q:"Por que protocolos de vermifugação em filhotes costumam ser mais frequentes que em adultos?", a:"Filhotes têm maior risco de infecção parasitária (inclusive transplacentária e via leite materno) e maior vulnerabilidade aos efeitos de parasitoses, exigindo esquemas mais frequentes nas primeiras semanas de vida."},
{cat:"Antiparasitários", q:"Por que antiparasitários tópicos devem ser aplicados sobre pele intacta e seca?", a:"A absorção adequada (para produtos sistêmicos) e a permanência do produto na pele/pelagem dependem dessas condições; pele lesionada ou úmida pode alterar a absorção e aumentar risco de irritação ou toxicidade sistêmica."},
{cat:"Antiparasitários", q:"Por que a resistência parasitária a anti-helmínticos é uma preocupação crescente no manejo veterinário?", a:"O uso repetido e inadequado (subdosagem, tratamentos desnecessários) seleciona populações de parasitas resistentes, reduzindo a eficácia dos fármacos disponíveis ao longo do tempo — por isso protocolos de rotação e diagnóstico correto são recomendados."},

// TOXICOLOGIA E ANTÍDOTOS
{cat:"Toxicologia", q:"Antídoto para intoxicação por organofosforados/carbamatos.", a:"Sulfato de atropina (controla os sinais muscarínicos) associado a pralidoxima nos casos de organofosforados (reativa a acetilcolinesterase inibida)."},
{cat:"Toxicologia", q:"Por que a intoxicação por anticoagulantes (raticidas tipo warfarina) é tratada com vitamina K1?", a:"Os raticidas inibem a enzima que recicla a vitamina K, necessária para ativar os fatores de coagulação II, VII, IX e X. A reposição de vitamina K1 restaura essa via de ativação."},
{cat:"Toxicologia", q:"Qual é o antídoto específico para intoxicação por paracetamol?", a:"N-acetilcisteína, que repõe glutationa hepática e ajuda a neutralizar o metabólito tóxico do paracetamol (NAPQI), reduzindo a lesão hepática e a metahemoglobinemia."},
{cat:"Toxicologia", q:"Por que o carvão ativado é usado em muitos casos de intoxicação oral recente?", a:"Adsorve toxinas ainda presentes no trato gastrointestinal, reduzindo sua absorção sistêmica — mais eficaz quando administrado logo após a ingestão."},
{cat:"Toxicologia", q:"Qual é o antídoto para intoxicação por opioides?", a:"Naloxona, antagonista competitivo dos receptores opioides que reverte rapidamente a depressão respiratória e do SNC."},
{cat:"Toxicologia", q:"Qual é o antídoto para intoxicação por benzodiazepínicos?", a:"Flumazenil, antagonista competitivo no receptor GABA-A no sítio benzodiazepínico."},
{cat:"Toxicologia", q:"Por que uva/passas são tóxicas para cães mesmo sem uma toxina totalmente elucidada?", a:"Estão associadas a lesão renal aguda idiossincrática em cães; como o composto exato ainda gera discussão científica, a recomendação clínica é tratar qualquer ingestão como potencialmente grave."},
{cat:"Toxicologia", q:"Por que o etilenoglicol (anticongelante) é tão perigoso mesmo em pequenas quantidades?", a:"É metabolizado no fígado em metabólitos altamente tóxicos (ácido glicólico e oxálico) que causam acidose metabólica grave e insuficiência renal aguda por precipitação de cristais de oxalato de cálcio nos túbulos renais."},
{cat:"Toxicologia", q:"Qual é o princípio geral de tratamento para a maioria das intoxicações sem antídoto específico?", a:"Suporte clínico (fluidoterapia, controle de sinais vitais), descontaminação quando aplicável (indução de êmese se recente e seguro, carvão ativado) e tratamento sintomático das complicações."},

// DERMATOLÓGICOS
{cat:"Dermatológicos", q:"Mecanismo de ação da oclacitinibe no tratamento de prurido alérgico canino.", a:"Inibe seletivamente a enzima Janus quinase 1 (JAK1), bloqueando a sinalização de citocinas envolvidas no prurido e na resposta inflamatória alérgica, incluindo a IL-31."},
{cat:"Dermatológicos", q:"Como age o lokivetmab no controle da dermatite atópica canina?", a:"É um anticorpo monoclonal caninizado que neutraliza especificamente a interleucina-31 (IL-31), citocina-chave na sinalização do prurido."},
{cat:"Dermatológicos", q:"Por que corticoides tópicos são preferidos em algumas dermatites localizadas em vez de sistêmicos?", a:"Permitem efeito anti-inflamatório local com menor absorção sistêmica, reduzindo o risco de efeitos adversos sistêmicos como supressão adrenal e imunossupressão generalizada."},
{cat:"Dermatológicos", q:"Mecanismo de ação geral dos xampus com clorexidina em piodermites.", a:"A clorexidina rompe a membrana celular bacteriana e fúngica por ação catiônica, tendo efeito antisséptico de amplo espectro na superfície da pele."},
{cat:"Dermatológicos", q:"Por que o tratamento de otite externa costuma exigir combinação de antibiótico, antifúngico e anti-inflamatório?", a:"Otites frequentemente envolvem infecção mista (bacteriana e fúngica) associada a inflamação significativa do canal auditivo; tratar apenas um componente costuma resultar em recidiva."},

// GASTROINTESTINAL
{cat:"Gastrointestinal", q:"Mecanismo de ação do omeprazol.", a:"Inibidor da bomba de prótons (H+/K+-ATPase) nas células parietais gástricas, reduzindo a secreção de ácido clorídrico de forma potente e prolongada."},
{cat:"Gastrointestinal", q:"Mecanismo de ação da ranitidina/famotidina (antagonistas H2).", a:"Bloqueiam os receptores H2 de histamina nas células parietais gástricas, reduzindo a secreção ácida — efeito geralmente menos potente e mais curto que os inibidores de bomba de prótons."},
{cat:"Gastrointestinal", q:"Mecanismo de ação do sucralfato como protetor de mucosa.", a:"Em ambiente ácido, forma uma pasta viscosa que adere a áreas ulceradas da mucosa gastrointestinal, criando uma barreira física de proteção contra ácido e enzimas digestivas."},
{cat:"Gastrointestinal", q:"Mecanismo de ação da metoclopramida.", a:"Antagonista de receptores dopaminérgicos D2 (e agonista 5-HT4 em maior dose) que aumenta a motilidade gastrointestinal e tem ação antiemética central ao bloquear receptores dopaminérgicos na zona de gatilho quimiorreceptora."},
{cat:"Gastrointestinal", q:"Mecanismo de ação do maropitant como antiemético.", a:"Antagonista dos receptores NK-1 de substância P no sistema nervoso central, bloqueando a via final comum do reflexo do vômito."},
{cat:"Gastrointestinal", q:"Por que o uso de loperamida deve ser cauteloso em algumas raças de cães?", a:"Assim como a ivermectina, é substrato da glicoproteína-P; cães com mutação MDR1 (ex: Collies) podem ter maior penetração no SNC e apresentar sedação ou depressão respiratória."},
{cat:"Gastrointestinal", q:"Como agem os probióticos no manejo de distúrbios gastrointestinais?", a:"Fornecem microrganismos benéficos que ajudam a restaurar o equilíbrio da microbiota intestinal, competindo com patógenos e podendo modular a resposta imune local."},

// REPRODUÇÃO E HORMÔNIOS
{cat:"Reprodução", q:"Mecanismo de ação da prostaglandina F2-alfa (ex: dinoprost) em protocolos reprodutivos.", a:"Promove a lise do corpo lúteo, reduzindo a produção de progesterona — usada para sincronização de cio, indução de parto ou tratamento de piometra em alguns protocolos."},
{cat:"Reprodução", q:"Por que a ocitocina é usada no manejo do parto e puerpério?", a:"Estimula a contração da musculatura uterina lisa, auxiliando na expulsão fetal e placentária, além de estimular a ejeção do leite durante a lactação."},
{cat:"Reprodução", q:"Mecanismo de ação geral dos progestágenos sintéticos no controle reprodutivo.", a:"Mimetizam a progesterona, suprimindo a liberação de gonadotrofinas (LH/FSH) e inibindo a ovulação — usados historicamente para supressão de cio, com riscos conhecidos como piometra e alterações mamárias."},
{cat:"Reprodução", q:"Por que o uso prolongado de progestágenos está associado a maior risco de piometra em cadelas?", a:"A progesterona (e seus análogos sintéticos) promove espessamento endometrial e reduz a defesa local contra infecção bacteriana no útero, favorecendo o desenvolvimento de piometra."},
{cat:"Reprodução", q:"Como age a cabergolina no tratamento de gestação indesejada ou pseudociese?", a:"É um agonista dopaminérgico que inibe a secreção de prolactina pela hipófise, reduzindo o suporte hormonal à manutenção da gestação ou aos sinais de pseudociese."},

// VACINAS E IMUNOBIOLÓGICOS
{cat:"Imunobiológicos", q:"Diferença entre vacina viva atenuada e vacina inativada.", a:"A vacina viva atenuada usa o agente enfraquecido, capaz de replicar minimamente e gerar resposta imune robusta e duradoura; a inativada usa o agente morto/inativado, geralmente exigindo adjuvantes e reforços mais frequentes."},
{cat:"Imunobiológicos", q:"Por que vacinas vivas atenuadas geralmente não são recomendadas em fêmeas gestantes?", a:"Há risco teórico ou comprovado (dependendo do agente) de o organismo vacinal atravessar a placenta e causar infecção fetal, mesmo estando atenuado para o adulto imunocompetente."},
{cat:"Imunobiológicos", q:"O que é um adjuvante vacinal e para que serve?", a:"Substância adicionada à vacina para potencializar e prolongar a resposta imune ao antígeno, comum em vacinas inativadas que sozinhas gerariam resposta imune mais fraca."},
{cat:"Imunobiológicos", q:"Por que filhotes recebem protocolos vacinais com múltiplas doses em vez de dose única?", a:"Anticorpos maternos residuais podem neutralizar o antígeno vacinal nas primeiras semanas de vida; doses repetidas em intervalos garantem que, assim que a imunidade materna declinar, o filhote seja efetivamente imunizado."},

// VIAS DE ADMINISTRAÇÃO
{cat:"Vias de administração", q:"Vantagem da via subcutânea sobre a intramuscular em pequenos animais.", a:"Menos dolorosa, mais fácil de aplicar e permite maior volume; porém tem absorção mais lenta e variável que a via IM, o que pode ser desvantajoso em emergências."},
{cat:"Vias de administração", q:"Por que a via intravenosa é preferida em situações de emergência?", a:"Proporciona início de ação praticamente imediato, já que o fármaco entra diretamente na circulação sistêmica, sem depender de absorção."},
{cat:"Vias de administração", q:"O que caracteriza a via transdérmica de administração?", a:"O fármaco é absorvido através da pele para a circulação sistêmica, geralmente com liberação lenta e prolongada — útil para manutenção de níveis plasmáticos estáveis, mas com absorção que pode variar conforme espessura da pele e presença de pelos."},
{cat:"Vias de administração", q:"Por que a via intramuscular pode não ser ideal para fármacos irritantes?", a:"Pode causar dor significativa e, em alguns casos, necrose tecidual local ou abscessos, dependendo do fármaco e do volume administrado."},
{cat:"Vias de administração", q:"O que é a via intratecal e quando é usada?", a:"Administração diretamente no espaço subaracnoide (líquido cefalorraquidiano), usada quando se deseja ação direta no sistema nervoso central, contornando a barreira hematoencefálica."},
{cat:"Vias de administração", q:"Por que a administração retal pode ser útil em situações de convulsão ativa?", a:"Permite absorção relativamente rápida (ex: diazepam retal) sem necessidade de acesso venoso, sendo prática em ambiente domiciliar antes de chegar ao atendimento veterinário."},

// INTERAÇÕES MEDICAMENTOSAS
{cat:"Interações", q:"O que é uma interação farmacocinética entre dois fármacos?", a:"Ocorre quando um fármaco altera a absorção, distribuição, metabolismo ou excreção de outro, mudando sua concentração plasmática efetiva (ex: inibição enzimática hepática)."},
{cat:"Interações", q:"O que é uma interação farmacodinâmica entre dois fármacos?", a:"Ocorre quando dois fármacos atuam no mesmo sistema fisiológico ou receptor, somando ou opondo seus efeitos, sem necessariamente alterar suas concentrações plasmáticas (ex: dois depressores do SNC usados juntos)."},
{cat:"Interações", q:"Por que associar dois fármacos altamente ligados a proteínas plasmáticas pode ser arriscado?", a:"Um pode deslocar o outro do sítio de ligação proteica, aumentando a fração livre (ativa) do fármaco deslocado e elevando o risco de toxicidade, mesmo sem mudança na dose administrada."},
{cat:"Interações", q:"Por que evitar associar aminoglicosídeos com outros fármacos nefrotóxicos (ex: alguns AINEs)?", a:"O efeito nefrotóxico pode ser aditivo ou sinérgico, aumentando significativamente o risco de lesão renal aguda."},
{cat:"Interações", q:"Por que inibidores da monoaminoxidase (ex: selegilina) exigem cautela com opioides e outros fármacos serotoninérgicos?", a:"O uso conjunto pode precipitar síndrome serotoninérgica, uma condição potencialmente grave por excesso de atividade serotoninérgica no SNC."},

// FARMACOLOGIA POR ESPÉCIE
{cat:"Por espécie", q:"Por que anti-inflamatórios em equinos exigem atenção especial ao trato gastrointestinal?", a:"Equinos são particularmente sensíveis a lesões da mucosa gástrica e do cólon direito induzidas por AINEs, podendo desenvolver úlceras graves mesmo com uso em doses terapêuticas prolongadas."},
{cat:"Por espécie", q:"Por que antibióticos orais de amplo espectro são especialmente arriscados em equinos?", a:"Podem alterar drasticamente a microbiota cecal fermentativa, predispondo a colite grave e potencialmente fatal (ex: relacionada a Clostridium difficile ou Salmonella)."},
{cat:"Por espécie", q:"Por que aves têm particularidades importantes na farmacocinética de muitos fármacos?", a:"Possuem metabolismo mais acelerado, sistema respiratório com sacos aéreos (relevante para anestesia inalatória) e diferenças significativas na função renal (presença de sistema porta-renal), exigindo doses e protocolos específicos por espécie/grupo taxonômico."},
{cat:"Por espécie", q:"Por que répteis exigem ajuste de dose e intervalo de fármacos conforme a temperatura ambiente?", a:"São ectotérmicos: seu metabolismo (incluindo metabolismo hepático de fármacos) depende diretamente da temperatura corporal, que por sua vez depende do ambiente — metabolismo mais lento em temperaturas baixas altera a farmacocinética."},
{cat:"Por espécie", q:"Por que ruminantes exigem atenção especial na escolha da via e do tipo de antimicrobiano?", a:"Fármacos administrados por via oral podem alterar a fermentação ruminal e a microbiota, além de sofrerem degradação pelos microrganismos do rúmen antes da absorção — a via parenteral costuma ser preferida para muitos antimicrobianos sistêmicos."},
{cat:"Por espécie", q:"Por que suínos podem apresentar hipertermia maligna com certos anestésicos?", a:"Alguns suínos (especialmente linhagens com mutação no gene do receptor de rianodina) têm predisposição genética a um distúrbio do metabolismo muscular do cálcio, desencadeado por anestésicos como halotano, levando a hipertermia maligna potencialmente fatal."},
{cat:"Por espécie", q:"Por que coelhos são particularmente sensíveis a antibióticos beta-lactâmicos orais?", a:"São herbívoros com fermentação intestinal importante (fermentadores pós-gástricos); antibióticos que afetam a flora Gram-positiva podem causar disbiose grave e enterotoxemia por Clostridium spp."},
{cat:"Por espécie", q:"Por que peixes ornamentais/de produção exigem cálculo de dose baseado no volume de água em vez de peso corporal isolado?", a:"Muitos tratamentos são administrados por imersão (banho), e a concentração do fármaco na água determina a exposição do animal — o cálculo depende do volume total do sistema aquático, não apenas do peso do peixe."},
{cat:"Por espécie", q:"Por que bovinos leiteiros exigem atenção ao período de carência de fármacos utilizados?", a:"Muitos fármacos são excretados no leite; o período de carência garante que resíduos do medicamento não ultrapassem limites seguros para consumo humano antes que o leite volte a ser comercializado."},

// ---- LOTE 2 DE FLASHCARDS ----
// Fluidoterapia
{cat:"Fluidoterapia", q:"Diferença entre fluido cristaloide e coloide.", a:"Cristaloides contêm pequenas moléculas que se distribuem entre os compartimentos vascular e intersticial; coloides têm moléculas maiores que permanecem mais tempo no espaço vascular, expandindo volume plasmático de forma mais sustentada."},
{cat:"Fluidoterapia", q:"Por que a reposição de potássio em fluidos IV exige controle rigoroso da taxa de infusão?", a:"Infusão rápida de potássio pode causar hipercalemia aguda, alterando perigosamente o potencial de membrana das células cardíacas e levando a arritmias graves ou parada cardíaca."},
{cat:"Fluidoterapia", q:"O que é solução Ringer com lactato e para que é usada?", a:"É um cristaloide isotônico balanceado, contendo sódio, potássio, cálcio e lactato (convertido em bicarbonato no fígado); usado para reposição volêmica e correção de desidratação/perdas eletrolíticas moderadas."},
{cat:"Fluidoterapia", q:"Por que pacientes cardiopatas ou com doença renal exigem cautela na taxa de fluidoterapia?", a:"Têm menor capacidade de lidar com sobrecarga de volume; infusão rápida ou excessiva pode precipitar edema pulmonar ou piora da função cardíaca/renal."},
{cat:"Fluidoterapia", q:"O que caracteriza uma solução hipertônica de NaCl e quando é usada?", a:"Tem concentração de sódio maior que o plasma; ao ser infundida, atrai água do interstício para o vaso rapidamente, sendo usada em situações de emergência como choque hipovolêmico, com efeito volêmico rápido mas transitório."},

// Anestesia local
{cat:"Anestesia local", q:"Mecanismo de ação geral dos anestésicos locais (ex: lidocaína, bupivacaína).", a:"Bloqueiam canais de sódio dependentes de voltagem nos neurônios, impedindo a propagação do potencial de ação e a transmissão do estímulo doloroso na região onde são aplicados."},
{cat:"Anestesia local", q:"Por que a associação de epinefrina a anestésicos locais prolonga o efeito anestésico?", a:"A epinefrina causa vasoconstrição local, retardando a absorção sistêmica do anestésico e prolongando seu tempo de contato com os nervos na região."},
{cat:"Anestesia local", q:"Por que a bupivacaína tem ação mais prolongada que a lidocaína?", a:"Tem maior lipossolubilidade e afinidade pelo canal de sódio, o que prolonga sua ligação ao receptor e, consequentemente, o tempo de bloqueio nervoso."},
{cat:"Anestesia local", q:"Por que a dose máxima de anestésicos locais deve ser respeitada rigorosamente?", a:"Doses excessivas podem ser absorvidas sistemicamente e causar toxicidade no sistema nervoso central (convulsões) e no sistema cardiovascular (arritmias, colapso), pelo mesmo mecanismo de bloqueio de canais de sódio em outros tecidos excitáveis."},

// Mais Farmacocinética
{cat:"Farmacocinética", q:"Por que a via de administração pode alterar a biodisponibilidade de um fármaco mesmo com a mesma dose numérica?", a:"Cada via tem barreiras de absorção diferentes (mucosa intestinal, pele, metabolismo de primeira passagem), alterando quanto do fármaco efetivamente chega intacto à circulação sistêmica."},
{cat:"Farmacocinética", q:"O que é clearance (depuração) de um fármaco?", a:"Medida do volume de plasma do qual o fármaco é completamente removido por unidade de tempo, refletindo a eficiência conjunta dos órgãos de eliminação (principalmente fígado e rins)."},

// Mais Farmacodinâmica
{cat:"Farmacodinâmica", q:"O que é um antagonista não competitivo?", a:"Liga-se a um sítio diferente do receptor do agonista (ou se liga irreversivelmente), reduzindo o efeito máximo (Emax) mesmo com aumento da dose do agonista — diferente do antagonista competitivo."},
{cat:"Farmacodinâmica", q:"O que caracteriza a janela terapêutica de um fármaco?", a:"É a faixa de concentração plasmática entre a dose mínima eficaz e a dose que começa a causar toxicidade; fármacos com janela estreita exigem monitoramento mais cuidadoso."},

// Mais Antibióticos
{cat:"Antibióticos", q:"Por que a cultura e o antibiograma são recomendados antes de tratamentos antimicrobianos prolongados ou refratários?", a:"Permitem identificar o agente causador e sua sensibilidade real, orientando uma escolha mais precisa e reduzindo o uso desnecessário de antimicrobianos de amplo espectro."},
{cat:"Antibióticos", q:"Por que a clindamicina é frequentemente escolhida para infecções ósseas e dentárias?", a:"Tem boa penetração no tecido ósseo e é eficaz contra diversos anaeróbios comumente envolvidos nesse tipo de infecção."},

// Mais AINEs
{cat:"AINEs", q:"Por que alguns AINEs administrados topicamente no olho podem causar efeitos sistêmicos?", a:"Parte do fármaco pode drenar pelo ducto nasolacrimal e ser absorvida pela mucosa nasal/gastrointestinal, sendo relevante em pacientes com contraindicações a AINEs sistêmicos."},

// Mais Corticoides
{cat:"Corticoides", q:"Por que corticoides podem mascarar sinais de infecção em um paciente?", a:"Ao suprimir a resposta inflamatória e imune, reduzem sinais clássicos de infecção (febre, edema) mesmo com o processo infeccioso ativo, dificultando o diagnóstico precoce."},

// Mais Opioides
{cat:"Opioides", q:"Por que a analgesia multimodal costuma ser preferida à monoterapia?", a:"Permite atuar em diferentes vias da dor simultaneamente, geralmente com menor dose de cada fármaco individual e menos efeitos colaterais associados."},

// Mais Anestésicos
{cat:"Anestésicos", q:"O que é CAM (concentração alveolar mínima) em anestesia inalatória?", a:"É a concentração do anestésico inalatório que impede movimento em 50% dos pacientes frente a um estímulo doloroso padronizado; quanto menor a CAM, mais potente é o agente."},

// Mais Cardiovascular
{cat:"Cardiovascular", q:"Por que o uso de IECA exige monitoramento da função renal e dos eletrólitos?", a:"Podem reduzir a taxa de filtração glomerular em alguns pacientes e favorecer retenção de potássio (hipercalemia), especialmente em quem já tem função renal comprometida."},

// Mais Endócrino
{cat:"Endócrino", q:"Por que o tratamento do hipertireoidismo felino costuma ser acompanhado de monitoramento da função renal?", a:"O hipertireoidismo aumenta a taxa de filtração glomerular, podendo mascarar uma doença renal crônica subjacente que se manifesta após o controle do hormônio tireoidiano."},

// Mais Antiparasitários
{cat:"Antiparasitários", q:"Por que combinar diferentes classes de antiparasitários pode ajudar a manejar a resistência parasitária?", a:"Reduz a chance de sobrevivência de parasitas resistentes a uma única classe, retardando a seleção de populações resistentes ao longo do tempo."},

// Mais Toxicologia
{cat:"Toxicologia", q:"Por que a indução de êmese não é recomendada em todos os casos de intoxicação oral?", a:"Substâncias cáusticas/corrosivas ou risco de aspiração (ex: paciente sedado ou com rebaixamento de consciência) contraindicam a indução de vômito, pelo risco de lesão adicional ou pneumonia aspirativa."},

// Mais Dermatológicos
{cat:"Dermatológicos", q:"Por que o tratamento da demodicose generalizada costuma ser mais prolongado que o de outras ectoparasitoses?", a:"O ácaro Demodex vive profundamente nos folículos pilosos, exigindo tratamento sustentado e monitoramento com raspados cutâneos seriados até a resolução completa."},

// Mais Gastrointestinal
{cat:"Gastrointestinal", q:"Por que a administração de sucralfato exige espaçamento em relação a outros fármacos orais?", a:"O sucralfato forma uma barreira física na mucosa que pode reduzir a absorção de outros fármacos administrados simultaneamente."},

// Mais Reprodução
{cat:"Reprodução", q:"Por que a prostaglandina F2-alfa pode induzir aborto quando administrada em fêmeas gestantes?", a:"Promove a lise do corpo lúteo, reduzindo a progesterona necessária para manter a gestação — por isso é usada deliberadamente em protocolos de indução de parto ou interrupção de gestação."},

// Mais Imunobiológicos
{cat:"Imunobiológicos", q:"Por que animais imunocomprometidos exigem avaliação cuidadosa antes de vacinas vivas atenuadas?", a:"Mesmo atenuado, o agente vacinal pode causar doença clínica em um sistema imune incapaz de controlar sua replicação mínima."},

// Mais Vias de administração
{cat:"Vias de administração", q:"Por que a via intraóssea é uma alternativa válida em emergências com acesso venoso difícil?", a:"Permite infusão de fluidos e fármacos diretamente na medula óssea, com absorção sistêmica rápida, útil em pacientes pediátricos, muito pequenos ou em colapso vascular."},

// Mais Interações
{cat:"Interações", q:"Por que fármacos indutores de enzimas hepáticas (ex: fenobarbital) podem reduzir a eficácia de outros fármacos usados junto?", a:"Aceleram o metabolismo de outros fármacos que dependem das mesmas vias enzimáticas, reduzindo sua concentração plasmática e efeito terapêutico se as doses não forem ajustadas."},

// Mais Por espécie
{cat:"Por espécie", q:"Por que filhotes muito jovens exigem cautela especial com fármacos metabolizados por glucuronidação?", a:"As vias de biotransformação hepática, incluindo a glucuronidação, ainda estão em desenvolvimento nos primeiros meses de vida, prolongando o efeito de certos fármacos nesses animais."},
{cat:"Por espécie", q:"Por que cavalos apresentam risco elevado de cólica associada ao uso de certos antimicrobianos orais?", a:"A microbiota cecal fermentativa dos equinos é sensível a alterações; antimicrobianos de amplo espectro por via oral podem desencadear disbiose e colite, manifestando-se clinicamente como cólica."},

// ---- LOTE 3 DE FLASHCARDS ----
// Neurologia / Anticonvulsivantes (categoria nova)
{cat:"Neurologia", q:"Mecanismo de ação do fenobarbital como anticonvulsivante.", a:"Potencializa a ação do GABA nos receptores GABA-A, aumentando a duração de abertura dos canais de cloreto e elevando o limiar convulsivo neuronal."},
{cat:"Neurologia", q:"Por que o fenobarbital exige monitoramento periódico da função hepática?", a:"É um indutor enzimático hepático e, com uso prolongado, pode causar hepatotoxicidade; a indução também acelera seu próprio metabolismo e o de outros fármacos ao longo do tempo."},
{cat:"Neurologia", q:"Mecanismo de ação do levetiracetam.", a:"Liga-se à proteína SV2A das vesículas sinápticas, modulando a liberação de neurotransmissores e reduzindo a excitabilidade neuronal excessiva, por um mecanismo distinto dos anticonvulsivantes clássicos."},
{cat:"Neurologia", q:"Por que a suspensão abrupta de anticonvulsivantes é perigosa em pacientes epilépticos?", a:"Pode desencadear convulsões de rebote ou mesmo estado de mal epiléptico (status epilepticus), já que o sistema nervoso estava adaptado à presença contínua do fármaco."},
{cat:"Neurologia", q:"Mecanismo de ação do brometo de potássio como anticonvulsivante.", a:"O íon brometo compete com o cloreto e hiperpolariza a membrana neuronal através dos canais de cloreto, elevando o limiar para disparo de potenciais de ação excitatórios."},
{cat:"Neurologia", q:"Por que o diazepam é a primeira escolha em protocolos de emergência para status epilepticus?", a:"Tem início de ação muito rápido ao potencializar o GABA nos receptores GABA-A, interrompendo a atividade convulsiva de forma imediata, embora seu efeito seja relativamente curto."},
{cat:"Neurologia", q:"Por que trocas de anticonvulsivante ou ajustes de dose devem ser feitos gradualmente, com sobreposição entre fármacos?", a:"Mudanças abruptas podem deixar o paciente com controle inadequado das convulsões durante a transição, já que os níveis plasmáticos do fármaco anterior caem antes do novo atingir concentração terapêutica estável."},

// Oncologia / Quimioterapia (categoria nova)
{cat:"Oncologia", q:"Mecanismo de ação geral dos agentes alquilantes (ex: ciclofosfamida) na quimioterapia.", a:"Formam ligações cruzadas (cross-links) covalentes no DNA, impedindo a replicação e transcrição corretas e levando à morte da célula, principalmente das que se dividem rapidamente."},
{cat:"Oncologia", q:"Por que a quimioterapia costuma causar mielossupressão, sinais gastrointestinais e perda de pelos?", a:"Esses agentes atuam preferencialmente sobre células de divisão rápida; medula óssea, mucosa gastrointestinal e folículos pilosos têm alto turnover celular, tornando-os mais vulneráveis aos efeitos citotóxicos."},
{cat:"Oncologia", q:"Mecanismo de ação da vincristina.", a:"Inibe a polimerização de microtúbulos, impedindo a formação do fuso mitótico e interrompendo a divisão celular na metáfase — um alcaloide da vinca com ação antineoplásica."},
{cat:"Oncologia", q:"Por que a doxorrubicina exige monitoramento cardíaco durante o tratamento?", a:"Está associada a cardiotoxicidade cumulativa dose-dependente, podendo levar a cardiomiopatia e insuficiência cardíaca, especialmente com doses totais acumuladas altas ao longo do tratamento."},
{cat:"Oncologia", q:"Por que a ciclofosfamida pode causar cistite hemorrágica estéril?", a:"Um metabólito da ciclofosfamida (acroleína) é irritante para a mucosa vesical, podendo causar inflamação e sangramento da bexiga na ausência de infecção."},
{cat:"Oncologia", q:"Por que o extravasamento de certos agentes quimioterápicos vesicantes durante a aplicação IV é uma emergência?", a:"Esses agentes podem causar necrose tecidual grave e progressiva no local de extravasamento, exigindo manejo imediato e cuidadoso para minimizar o dano local."},
{cat:"Oncologia", q:"Por que protocolos quimioterápicos costumam combinar fármacos com mecanismos de ação diferentes?", a:"A combinação ataca as células neoplásicas por vias distintas simultaneamente, podendo aumentar a eficácia e reduzir a chance de desenvolvimento de resistência a um único mecanismo."},

// Mais Farmacocinética
{cat:"Farmacocinética", q:"O que é o estado de equilíbrio (steady state) na farmacocinética de doses repetidas?", a:"Ponto em que a quantidade de fármaco administrada em cada intervalo se iguala à quantidade eliminada, mantendo a concentração plasmática relativamente estável entre doses — geralmente atingido após cerca de 4-5 meias-vidas de administração repetida."},

// Mais Farmacodinâmica
{cat:"Farmacodinâmica", q:"O que é regulação para cima (up-regulation) de receptores?", a:"Aumento do número de receptores disponíveis na membrana celular, geralmente em resposta a bloqueio prolongado (por um antagonista) ou redução crônica do estímulo endógeno — relevante, por exemplo, na suspensão abrupta de betabloqueadores."},

// Mais Antibióticos
{cat:"Antibióticos", q:"Por que a doxiciclina é frequentemente preferida a outras tetraciclinas em pacientes com função renal comprometida?", a:"Tem eliminação predominantemente biliar/fecal, ao contrário de outras tetraciclinas mais dependentes de excreção renal, tornando-a uma opção mais segura nesses pacientes."},

// Mais Antifúngicos
{cat:"Antifúngicos", q:"Por que a terbinafina é considerada relativamente seletiva para fungos em comparação a alguns azólicos?", a:"Inibe a enzima esqualeno epoxidase fúngica com maior seletividade que muitos azólicos pelas enzimas do citocromo P450 de mamíferos, resultando geralmente em menos interações medicamentosas."},

// Mais Cardiovascular
{cat:"Cardiovascular", q:"Por que a sildenafila é usada no tratamento de hipertensão pulmonar em cães?", a:"Como inibidor da fosfodiesterase-5, aumenta os níveis de GMPc no músculo liso vascular pulmonar, promovendo vasodilatação seletiva da circulação pulmonar."},

// Mais Endócrino
{cat:"Endócrino", q:"Por que o uso de glicocorticoides em altas doses pode precipitar ou agravar diabetes mellitus latente?", a:"Corticoides aumentam a resistência periférica à insulina e estimulam a gliconeogênese hepática, podendo desmascarar uma predisposição diabética préexistente."},

// Mais Antiparasitários
{cat:"Antiparasitários", q:"Por que a seleção do antiparasitário em gestantes/lactantes exige atenção especial?", a:"Alguns princípios ativos podem atravessar a placenta ou ser excretados no leite, exigindo escolha de produtos com segurança estabelecida para essas fases fisiológicas."},

// Mais Toxicologia
{cat:"Toxicologia", q:"Por que a intoxicação por xilitol é particularmente perigosa em cães?", a:"O xilitol estimula liberação intensa de insulina em cães (diferente de outras espécies), causando hipoglicemia grave e, em doses maiores, também pode causar hepatotoxicidade aguda."},

// Mais Vias de administração
{cat:"Vias de administração", q:"Por que a via epidural é usada em alguns protocolos analgésicos/anestésicos?", a:"Permite depositar o fármaco próximo às raízes nervosas espinhais, produzindo analgesia/anestesia regional eficaz com menor necessidade de fármacos sistêmicos e seus efeitos colaterais associados."}
];

/* ================= DADOS: QUIZ ================= */
const quiz = [
// FARMACOCINÉTICA
{cat:"Farmacocinética", q:"O que significa dizer que um fármaco administrado por via IV tem biodisponibilidade de 100%?", opts:["Que o fármaco não sofre metabolismo hepático","Que toda a dose administrada atinge a circulação sistêmica diretamente, sem perdas de absorção","Que o fármaco tem meia-vida curta","Que o fármaco é altamente ligado a proteínas plasmáticas"], correct:1, exp:"A via IV entrega o fármaco diretamente na corrente sanguínea, sem etapa de absorção — por isso é a referência (100%) para calcular a biodisponibilidade de outras vias."},
{cat:"Farmacocinética", q:"O que é meia-vida de eliminação de um fármaco?", opts:["O tempo até o início do efeito terapêutico","O tempo necessário para a concentração plasmática cair pela metade","A duração total do efeito clínico","O tempo de absorção pela via oral"], correct:1, exp:"É usada para calcular o intervalo entre doses; após cerca de 4-5 meias-vidas, o fármaco é considerado praticamente eliminado do organismo."},
{cat:"Farmacocinética", q:"Por que a insuficiência renal exige ajuste de dose de muitos fármacos?", opts:["Porque altera o pH gástrico","Porque reduz a excreção de fármacos e metabólitos ativos, favorecendo acúmulo e toxicidade","Porque aumenta a absorção intestinal","Porque acelera o metabolismo hepático"], correct:1, exp:"Rins comprometidos eliminam fármacos com menor eficiência; sem ajuste, há risco de acúmulo e efeitos tóxicos."},
{cat:"Farmacocinética", q:"O que é o efeito de primeira passagem hepática?", opts:["Efeito tóxico exclusivo de fármacos IV","Metabolismo parcial de um fármaco oral no fígado antes de atingir a circulação sistêmica","Acúmulo do fármaco nos rins","Ligação do fármaco a proteínas plasmáticas"], correct:1, exp:"Reduz a biodisponibilidade oral de diversos fármacos, já que uma parte é metabolizada no fígado antes de alcançar a circulação geral."},

// FARMACODINÂMICA
{cat:"Farmacodinâmica", q:"O que é índice terapêutico de um fármaco?", opts:["A dose mínima para ter qualquer efeito","A razão entre a dose tóxica e a dose eficaz — quanto maior, mais seguro o fármaco","O tempo até o pico de concentração plasmática","A fração do fármaco ligada a proteínas"], correct:1, exp:"Um índice terapêutico alto indica boa margem de segurança entre a dose eficaz e a dose tóxica."},
{cat:"Farmacodinâmica", q:"O que caracteriza um agonista parcial, como a buprenorfina em receptores opioides mu?", opts:["Bloqueia totalmente o receptor sem produzir efeito","Produz efeito máximo menor que um agonista total, mesmo ocupando todos os receptores","Só age em concentrações tóxicas","Tem efeito idêntico a um antagonista competitivo"], correct:1, exp:"Agonistas parciais têm um teto de efeito — mesmo aumentando a dose, o efeito máximo alcançável é menor que o de um agonista total."},
{cat:"Farmacodinâmica", q:"O que é tolerância farmacológica?", opts:["Alergia medicamentosa grave","Redução da resposta a um fármaco após exposição repetida, exigindo doses maiores para o mesmo efeito","Efeito colateral imediato após a primeira dose","Interação entre dois fármacos distintos"], correct:1, exp:"É comum com opioides e benzodiazepínicos, relacionada a mecanismos como down-regulation de receptores."},

// ANTIBIÓTICOS
{cat:"Antibióticos", q:"Qual é o mecanismo de ação geral das penicilinas e cefalosporinas?", opts:["Inibem a síntese proteica ribossomal","Inibem a síntese da parede celular bacteriana ao bloquear transpeptidases (PBPs)","Inibem a topoisomerase bacteriana","Danificam a membrana celular por ação detergente"], correct:1, exp:"Beta-lactâmicos se ligam às PBPs, impedindo a formação correta da parede celular, o que leva à lise osmótica da bactéria."},
{cat:"Antibióticos", q:"Por que evitar enrofloxacina em cães filhotes de raças grandes em fase de crescimento?", opts:["Risco de manchamento dentário","Risco de artropatia por lesão de cartilagem articular","Risco de hepatotoxicidade imediata","Não há contraindicação nessa faixa etária"], correct:1, exp:"Fluoroquinolonas podem lesar a cartilagem em desenvolvimento — o risco é maior em raças grandes durante o pico de crescimento ósseo."},
{cat:"Antibióticos", q:"Por que tetraciclinas são evitadas em filhotes e fêmeas prenhes?", opts:["Causam sedação profunda","Podem se depositar em ossos e dentes em formação, causando manchamento e alterações de crescimento","Aumentam o risco de convulsões","Não têm nenhuma contraindicação especial"], correct:1, exp:"Tetraciclinas quelam cálcio e se depositam em tecidos calcificados em formação, causando manchamento dentário permanente."},
{cat:"Antibióticos", q:"Como agem os aminoglicosídeos (ex: gentamicina)?", opts:["Inibem a parede celular bacteriana","Ligam-se à subunidade ribossomal 30S, causando leitura incorreta do mRNA e inibindo a síntese proteica","Bloqueiam a DNA-girase bacteriana","Inibem a síntese de ácido fólico bacteriano"], correct:1, exp:"São bactericidas, principalmente contra Gram-negativos, mas exigem monitoramento por risco de nefro e ototoxicidade."},
{cat:"Antibióticos", q:"Por que antibióticos orais de amplo espectro são especialmente arriscados em coelhos?", opts:["Coelhos são alérgicos à maioria dos antibióticos","Podem causar disbiose grave da flora fermentativa intestinal, levando a enterotoxemia","Não têm nenhum risco especial","Reduzem apenas o apetite temporariamente"], correct:1, exp:"Coelhos dependem de fermentação intestinal por microbiota específica; antibióticos de amplo espectro podem destruir essa flora e causar quadros graves, às vezes fatais."},

// AINES
{cat:"AINEs", q:"Uma tutora administra paracetamol ao seu gato por conta própria para dor. Qual é o principal risco?", opts:["Sedação leve e passageira","Metahemoglobinemia e necrose hepática, podendo ser fatal","Diarreia autolimitada","Nenhum risco relevante em dose única"], correct:1, exp:"Gatos têm deficiência de glucuroniltransferase e não conjugam bem o paracetamol, que se acumula e gera metabólitos tóxicos, mesmo em doses consideradas seguras para cães."},
{cat:"AINEs", q:"Por que a associação de AINE com corticoide é considerada perigosa?", opts:["Os efeitos se anulam, tornando o tratamento inútil","Aumenta drasticamente o risco de úlceras e perfuração gastrointestinal","Causa apenas sonolência excessiva","Não há interação relevante entre essas classes"], correct:1, exp:"Ambas as classes comprometem a proteção da mucosa gástrica por mecanismos diferentes e complementares, somando o risco de lesão."},
{cat:"AINEs", q:"Qual é a diferença funcional entre COX-1 e COX-2 relevante para o uso clínico de AINEs?", opts:["COX-1 só existe em felinos","COX-1 é constitutiva e protetora (mucosa, rim); COX-2 é induzida principalmente na inflamação","Não há diferença funcional relevante","COX-2 é exclusiva do sistema nervoso"], correct:1, exp:"AINEs mais seletivos para COX-2 tendem a poupar mais as funções fisiológicas protetoras dependentes de COX-1, embora não eliminem o risco de efeitos adversos."},

// CORTICOIDES
{cat:"Corticoides", q:"Por que a suspensão abrupta de corticoterapia prolongada é perigosa?", opts:["Causa apenas leve desconforto gástrico","Pode causar insuficiência adrenal aguda por supressão do eixo hipotálamo-hipófise-adrenal","Não há nenhum risco associado","Provoca hipertireoidismo imediato"], correct:1, exp:"O uso prolongado suprime a produção endógena de cortisol; a suspensão abrupta pode deixar o paciente sem resposta adrenal adequada ao estresse."},
{cat:"Corticoides", q:"Por que corticoides são usados com extrema cautela em pacientes diabéticos?", opts:["Não têm nenhuma relação com o metabolismo da glicose","Antagonizam a ação da insulina e aumentam a gliconeogênese hepática, elevando a glicemia","Reduzem drasticamente a glicemia","Causam apenas alterações renais"], correct:1, exp:"Corticoides são hiperglicemiantes por natureza, dificultando o controle glicêmico em pacientes diabéticos."},

// OPIOIDES
{cat:"Opioides", q:"Qual antagonista opioide é usado para reversão de emergência de depressão respiratória?", opts:["Flumazenil","Naloxona","Atipamezol","Ioimbina"], correct:1, exp:"Naloxona é antagonista competitivo dos receptores opioides, revertendo rapidamente sedação e depressão respiratória excessivas."},
{cat:"Opioides", q:"Por que a administração IV rápida de morfina pode causar hipotensão e prurido?", opts:["Por hipersensibilidade alérgica exclusiva","Por estimulação direta da liberação de histamina por mastócitos","Por bloqueio dos receptores beta-adrenérgicos","Não há relação conhecida"], correct:1, exp:"A morfina pode causar degranulação direta de mastócitos quando administrada rapidamente por via IV, por isso a infusão deve ser lenta."},

// ANESTÉSICOS
{cat:"Anestésicos", q:"Qual fármaco é usado para reverter os efeitos de agonistas alfa-2 como a xilazina?", opts:["Flumazenil","Atipamezol","Naloxona","Neostigmina"], correct:1, exp:"Atipamezol é um antagonista alfa-2 adrenérgico específico, usado para reverter sedação e efeitos cardiovasculares de xilazina e dexmedetomidina."},
{cat:"Anestésicos", q:"Qual é o mecanismo de ação geral dos anestésicos dissociativos como a cetamina?", opts:["Potencializam o GABA","Antagonizam receptores NMDA de glutamato","Bloqueiam canais de sódio neuronais","Inibem a acetilcolinesterase"], correct:1, exp:"O antagonismo NMDA produz um estado de dissociação entre córtex e sistema límbico, com analgesia somática e preservação relativa de reflexos protetores."},
{cat:"Anestésicos", q:"Por que gatos exigem cautela especial com doses repetidas de propofol?", opts:["Gatos são alérgicos ao propofol","Metabolizam mais lentamente (menor capacidade de glucuronidação), podendo haver acúmulo e recuperação prolongada","O propofol não tem nenhum efeito em felinos","Gatos metabolizam o propofol mais rápido que cães"], correct:1, exp:"A menor capacidade de glucuronidação hepática felina pode levar a acúmulo do fármaco com doses repetidas ou infusão contínua prolongada."},

// CARDIOVASCULAR
{cat:"Cardiovascular", q:"Qual é o mecanismo de ação da furosemida?", opts:["Bloqueia receptores beta-adrenérgicos","Inibe o cotransportador Na⁺/K⁺/2Cl⁻ na alça de Henle","Inibe a enzima conversora de angiotensina","Bloqueia canais de cálcio no músculo liso vascular"], correct:1, exp:"É um diurético de alça que aumenta a excreção de sódio, potássio e água, reduzindo a congestão em pacientes com ICC."},
{cat:"Cardiovascular", q:"Para que serve o pimobendan no tratamento de cardiopatas caninos?", opts:["É um diurético puro","É um inodilatador: aumenta contratilidade cardíaca e promove vasodilatação","É um antiarrítmico de classe I","Serve apenas para controle da pressão arterial sistêmica"], correct:1, exp:"Atua como sensibilizador de cálcio (contratilidade) e inibidor da fosfodiesterase-3 (vasodilatação), muito usado em ICC e cardiomiopatia dilatada."},
{cat:"Cardiovascular", q:"Por que a digoxina exige monitoramento rigoroso da dose administrada?", opts:["Não tem nenhum risco de toxicidade","Tem índice terapêutico estreito, com risco de arritmias graves em doses excessivas","É completamente eliminada sem necessidade de ajuste","Só é usada topicamente"], correct:1, exp:"A margem entre dose terapêutica e tóxica da digoxina é pequena, exigindo monitoramento cuidadoso, especialmente em pacientes com função renal alterada."},

// ENDÓCRINO
{cat:"Endócrino", q:"Qual é uma diferença importante no manejo de diabetes entre cães e gatos?", opts:["Gatos nunca respondem à insulinoterapia","Gatos podem entrar em remissão diabética com bom controle glicêmico precoce; cães geralmente não","Cães não desenvolvem diabetes","Não há diferenças relevantes"], correct:1, exp:"O diabetes felino se assemelha mais ao tipo 2, com possibilidade de remissão; o canino se assemelha mais ao tipo 1, exigindo insulina vitalícia."},
{cat:"Endócrino", q:"Qual é o mecanismo de ação do metimazol no hipertireoidismo felino?", opts:["Destrói diretamente o tecido tireoidiano","Inibe a tireoperoxidase, bloqueando a síntese de T3 e T4","Aumenta a liberação de TSH hipofisário","Substitui os hormônios tireoidianos endógenos"], correct:1, exp:"O metimazol bloqueia a enzima responsável pela síntese dos hormônios tireoidianos, controlando o excesso hormonal sem destruir a glândula."},

// ANTIPARASITÁRIOS
{cat:"Antiparasitários", q:"Um Collie precisa de tratamento antiparasitário. Por que a ivermectina exige cautela nessa raça?", opts:["Collies têm fígado menor que a média","Mutação no gene MDR1 compromete a barreira hematoencefálica, permitindo acúmulo neurotóxico","A raça é alérgica a princípios ativos macrocíclicos","Não há nenhum cuidado especial necessário"], correct:1, exp:"A mutação MDR1 reduz a função da glicoproteína-P, que normalmente expulsa a ivermectina do SNC, levando a acúmulo e neurotoxicidade grave."},
{cat:"Antiparasitários", q:"Por que produtos com permetrina não devem ser usados em gatos?", opts:["Gatos são naturalmente resistentes a pulgas","Deficiência de glucuroniltransferase impede metabolização eficiente, causando intoxicação grave","Permetrina não tem efeito em felinos","Causa apenas irritação leve na pele"], correct:1, exp:"A mesma deficiência enzimática que afeta o paracetamol em gatos compromete a metabolização da permetrina, podendo causar tremores, convulsões e morte."},
{cat:"Antiparasitários", q:"Como agem os isoxazolinas (ex: fluralaner) contra pulgas e carrapatos?", opts:["Paralisam o parasita por hipoglicemia induzida","Bloqueiam canais de cloreto GABA/glutamato-dependentes, causando hiperexcitação neuronal e morte","Impedem apenas a reprodução do parasita","Atuam exclusivamente por repelência"], correct:1, exp:"O bloqueio desses canais de cloreto causa hiperexcitação descontrolada do sistema nervoso do parasita, levando à sua morte."},

// TOXICOLOGIA
{cat:"Toxicologia", q:"Um cão ingeriu raticida anticoagulante (tipo warfarina). Qual é o tratamento específico?", opts:["Atropina em altas doses","Reposição de vitamina K1","Bicarbonato de sódio IV","Naloxona"], correct:1, exp:"Os raticidas anticoagulantes bloqueiam a reciclagem da vitamina K; repor vitamina K1 restaura a ativação dos fatores de coagulação II, VII, IX e X."},
{cat:"Toxicologia", q:"Qual é o antídoto específico para intoxicação por paracetamol?", opts:["Vitamina K1","N-acetilcisteína","Atropina","Flumazenil"], correct:1, exp:"A N-acetilcisteína repõe glutationa hepática, ajudando a neutralizar o metabólito tóxico (NAPQI) responsável pela lesão hepática."},
{cat:"Toxicologia", q:"Por que o etilenoglicol (anticongelante) é extremamente perigoso mesmo em pequenas quantidades?", opts:["Causa apenas irritação gástrica leve","É metabolizado em compostos que causam acidose metabólica grave e insuficiência renal aguda","Não é absorvido pelo trato digestivo","Afeta exclusivamente o sistema respiratório"], correct:1, exp:"Seus metabólitos (ácido glicólico e oxálico) causam acidose grave e precipitação de cristais de oxalato de cálcio nos túbulos renais."},

// DERMATOLÓGICOS
{cat:"Dermatológicos", q:"Qual é o mecanismo de ação da oclacitinibe no prurido alérgico canino?", opts:["Bloqueia receptores de histamina H1","Inibe seletivamente a enzima JAK1, bloqueando sinalização de citocinas pruriginosas","Age como corticoide sistêmico","Neutraliza diretamente a IL-31 circulante"], correct:1, exp:"A inibição da JAK1 bloqueia a sinalização intracelular de diversas citocinas envolvidas no prurido, incluindo a via da IL-31."},

// GASTROINTESTINAL
{cat:"Gastrointestinal", q:"Qual é o mecanismo de ação do omeprazol?", opts:["Antagonista de receptores H2","Inibidor da bomba de prótons (H+/K+-ATPase) nas células parietais gástricas","Antiemético central por bloqueio de NK-1","Protetor físico da mucosa gástrica"], correct:1, exp:"O omeprazol reduz a secreção ácida gástrica de forma potente e prolongada ao inibir diretamente a bomba de prótons."},
{cat:"Gastrointestinal", q:"Como age o maropitant como antiemético?", opts:["Bloqueia receptores dopaminérgicos D2","Antagoniza os receptores NK-1 de substância P no SNC","Inibe a bomba de prótons gástrica","Estimula a motilidade intestinal"], correct:1, exp:"O bloqueio dos receptores NK-1 interrompe a via final comum do reflexo do vômito no sistema nervoso central."},

// REPRODUÇÃO
{cat:"Reprodução", q:"Por que o uso prolongado de progestágenos sintéticos está associado a maior risco de piometra em cadelas?", opts:["Reduzem a produção de estrógeno","Promovem espessamento endometrial e reduzem a defesa local contra infecção uterina","Aumentam a motilidade uterina","Não há relação conhecida"], correct:1, exp:"A ação semelhante à progesterona favorece um ambiente endometrial propício à proliferação bacteriana, aumentando o risco de piometra."},

// IMUNOBIOLÓGICOS
{cat:"Imunobiológicos", q:"Por que filhotes recebem protocolos vacinais com múltiplas doses em vez de uma dose única?", opts:["Porque vacinas para filhotes são sempre menos potentes","Porque anticorpos maternos residuais podem neutralizar o antígeno vacinal nas primeiras semanas de vida","Porque filhotes têm sistema imune hiperativo","Não há razão farmacológica, é apenas tradição"], correct:1, exp:"Doses repetidas garantem que, assim que a imunidade materna declinar, o filhote seja efetivamente imunizado pela vacina."},

// VIAS DE ADMINISTRAÇÃO
{cat:"Vias de administração", q:"Por que antibióticos orais podem ser perigosos em coelhos e ruminantes?", opts:["Porque nunca são absorvidos no intestino desses animais","Porque podem causar disbiose grave ao alterar a flora fermentativa do trato digestivo","Porque esses animais não têm fígado funcional","Não há nenhum risco especial"], correct:1, exp:"Coelhos e ruminantes dependem de uma flora microbiana complexa para a fermentação digestiva; antibióticos orais de amplo espectro podem causar disbiose potencialmente fatal."},
{cat:"Vias de administração", q:"Por que a via intravenosa é a preferida em situações de emergência?", opts:["Porque é a via mais barata","Porque proporciona início de ação praticamente imediato, sem depender de absorção","Porque nunca causa efeitos colaterais","Porque é a única via compatível com todos os fármacos"], correct:1, exp:"O fármaco entra diretamente na circulação sistêmica, eliminando a etapa de absorção e permitindo ação rápida — essencial em emergências."},

// INTERAÇÕES
{cat:"Interações", q:"O que caracteriza uma interação farmacocinética entre dois fármacos?", opts:["Os dois fármacos competem pelo mesmo receptor","Um fármaco altera a absorção, distribuição, metabolismo ou excreção do outro","Os dois fármacos têm o mesmo mecanismo de ação","Não existe influência mútua entre concentrações plasmáticas"], correct:1, exp:"Interações farmacocinéticas mudam a concentração plasmática efetiva do fármaco afetado, diferente das interações farmacodinâmicas (que envolvem efeitos no mesmo sistema/receptor)."},

// POR ESPÉCIE
{cat:"Por espécie", q:"Por que equinos exigem atenção especial ao uso prolongado de AINEs?", opts:["Equinos são resistentes a efeitos gastrointestinais de AINEs","São particularmente sensíveis a lesões da mucosa gástrica e do cólon direito","AINEs não têm efeito analgésico em equinos","Não há nenhuma particularidade relevante"], correct:1, exp:"Equinos podem desenvolver úlceras gástricas e de cólon direito mesmo com AINEs em doses terapêuticas, exigindo monitoramento no uso prolongado."},
{cat:"Por espécie", q:"Por que suínos de certas linhagens podem desenvolver hipertermia maligna com alguns anestésicos?", opts:["Por alergia alimentar cruzada","Por mutação genética no receptor de rianodina, afetando o metabolismo muscular do cálcio","Por deficiência de vitamina D","Por hipersensibilidade cutânea"], correct:1, exp:"A mutação no gene do receptor de rianodina predispõe a um distúrbio grave do metabolismo do cálcio muscular, desencadeado por certos anestésicos."},
{cat:"Por espécie", q:"Por que répteis exigem ajuste de dose conforme a temperatura ambiente?", opts:["Répteis não metabolizam fármacos","São ectotérmicos, e seu metabolismo (incluindo hepático) depende diretamente da temperatura corporal/ambiental","A temperatura não influencia a farmacocinética em répteis","Répteis eliminam fármacos apenas pela pele"], correct:1, exp:"Como o metabolismo réptil depende da temperatura ambiente, a velocidade de metabolização de fármacos varia conforme essa temperatura, exigindo ajustes de dose e intervalo."},

// ---- LOTE 2: mais questões por categoria ----
// Farmacocinética
{cat:"Farmacocinética", q:"O que é volume de distribuição (Vd) de um fármaco?", opts:["A quantidade de fármaco excretada por hora","Parâmetro que relaciona a quantidade de fármaco no corpo com sua concentração plasmática","O tempo até o pico plasmático","A fração metabolizada no fígado"], correct:1, exp:"Um Vd alto sugere ampla distribuição tecidual (fármaco 'sai' do plasma para os tecidos); um Vd baixo sugere fármaco mais restrito ao compartimento plasmático."},
{cat:"Farmacocinética", q:"Por que apenas a fração livre (não ligada a proteínas) de um fármaco é farmacologicamente ativa?", opts:["Porque a fração ligada é imediatamente destruída","Porque só a fração livre pode se difundir para os tecidos e interagir com receptores","Porque a ligação proteica ativa o fármaco","Não há diferença de atividade entre as frações"], correct:1, exp:"A fração ligada a proteínas plasmáticas funciona como um reservatório inativo; apenas o fármaco livre consegue atravessar membranas e agir nos tecidos-alvo."},
{cat:"Farmacocinética", q:"O que caracteriza a cinética de eliminação de ordem zero?", opts:["A eliminação depende exponencialmente da concentração plasmática","Uma quantidade constante do fármaco é eliminada por unidade de tempo, independente da concentração","O fármaco nunca é eliminado","A meia-vida é sempre a mesma que a de ordem um"], correct:1, exp:"É típica de vias metabólicas saturáveis; ocorre, por exemplo, com etanol ou fenitoína em doses altas, quando o sistema enzimático responsável pela eliminação satura."},
{cat:"Farmacocinética", q:"Por que pacientes com insuficiência hepática exigem cautela no uso de fármacos metabolizados no fígado?", opts:["O fígado não influencia a farmacocinética de nenhum fármaco","A capacidade reduzida de biotransformação pode levar ao acúmulo do fármaco ativo, aumentando o risco de toxicidade","O fígado só afeta fármacos administrados por via tópica","A insuficiência hepática acelera sempre o metabolismo"], correct:1, exp:"Fígados comprometidos metabolizam fármacos mais lentamente, podendo prolongar sua ação e aumentar o risco de efeitos tóxicos com as doses habituais."},

// Farmacodinâmica
{cat:"Farmacodinâmica", q:"O que é down-regulation de receptores?", opts:["Aumento do número de receptores após uso agudo de um fármaco","Redução do número de receptores disponíveis após exposição prolongada a um agonista","Mudança na forma do receptor sem alteração de número","Processo exclusivo de receptores hormonais"], correct:1, exp:"A redução do número de receptores na membrana após estímulo repetido contribui para o fenômeno de tolerância farmacológica."},
{cat:"Farmacodinâmica", q:"Diferença entre potência e eficácia de um fármaco.", opts:["São sinônimos e podem ser usados indistintamente","Potência é a dose necessária para o efeito; eficácia é o efeito máximo alcançável","Potência refere-se apenas a fármacos tópicos","Eficácia é sempre proporcional ao preço do fármaco"], correct:1, exp:"Um fármaco pode ser muito potente (efeito com dose baixa) mas ter eficácia máxima menor que outro fármaco menos potente."},
{cat:"Farmacodinâmica", q:"O que caracteriza o antagonismo fisiológico entre dois fármacos?", opts:["Os dois competem pelo mesmo sítio de ligação no mesmo receptor","Atuam em receptores ou sistemas diferentes, mas produzem efeitos opostos no organismo","Um fármaco inativa quimicamente o outro no frasco","Não existe esse tipo de antagonismo em farmacologia"], correct:1, exp:"No antagonismo fisiológico, os efeitos opostos resultam de vias farmacológicas distintas atuando sobre a mesma função fisiológica, e não de competição direta pelo receptor."},

// Antibióticos
{cat:"Antibióticos", q:"O que faz o ácido clavulânico quando associado à amoxicilina?", opts:["Aumenta a absorção intestinal da amoxicilina","Inibe a enzima beta-lactamase, protegendo a amoxicilina da degradação por bactérias resistentes","Reduz os efeitos colaterais gastrointestinais","Substitui a necessidade de diagnóstico bacteriológico"], correct:1, exp:"O ácido clavulânico não tem ação antimicrobiana relevante por si só, mas protege a amoxicilina da inativação por beta-lactamases bacterianas, ampliando seu espectro efetivo."},
{cat:"Antibióticos", q:"Como agem as sulfonamidas potencializadas (associação sulfa + trimetoprima)?", opts:["Bloqueiam a parede celular bacteriana em duas etapas","Bloqueiam sequencialmente duas etapas da síntese de ácido fólico bacteriano, com efeito sinérgico","Inibem apenas a replicação viral","Atuam somente contra fungos"], correct:1, exp:"A sulfa inibe a di-hidropteroato sintetase e a trimetoprima a di-hidrofolato redutase; juntas bloqueiam duas etapas sequenciais da via, com efeito bactericida sinérgico."},
{cat:"Antibióticos", q:"Por que é importante respeitar o tempo total de um tratamento antimicrobiano mesmo com melhora clínica precoce?", opts:["Para aumentar o custo do tratamento","Interromper cedo pode deixar bactérias parcialmente resistentes sobreviventes, favorecendo recidiva e seleção de resistência","Não há nenhuma razão farmacológica para isso","Antibióticos só fazem efeito após o término do tratamento"], correct:1, exp:"A suspensão precoce favorece a sobrevivência de subpopulações bacterianas menos sensíveis, aumentando o risco de recidiva e de desenvolvimento de resistência antimicrobiana."},

// Antifúngicos (categoria nova no quiz)
{cat:"Antifúngicos", q:"Qual é o mecanismo de ação geral dos antifúngicos azólicos (ex: cetoconazol, itraconazol)?", opts:["Rompem diretamente a parede celular fúngica por ação osmótica","Inibem a enzima fúngica lanosterol 14-alfa-desmetilase, bloqueando a síntese de ergosterol","Inibem a síntese proteica ribossomal do fungo","Atuam exclusivamente por via tópica sem absorção sistêmica"], correct:1, exp:"Ao bloquear a síntese de ergosterol, componente essencial da membrana celular fúngica, os azólicos comprometem a integridade e função dessa membrana."},
{cat:"Antifúngicos", q:"Por que o cetoconazol pode causar efeitos colaterais endócrinos em cães?", opts:["Não tem nenhuma ação fora do fungo-alvo","Também inibe enzimas do citocromo P450 envolvidas na esteroidogênese, podendo reduzir cortisol e testosterona","Estimula diretamente a hipófise","Só afeta a tireoide"], correct:1, exp:"A falta de seletividade do cetoconazol por enzimas fúngicas faz com que ele também iniba enzimas P450 de mamíferos envolvidas na síntese de hormônios esteroides."},
{cat:"Antifúngicos", q:"Por que a griseofulvina é contraindicada em fêmeas gestantes?", opts:["Causa apenas desconforto gástrico leve","Tem potencial teratogênico comprovado, podendo causar malformações fetais graves","Reduz a fertilidade permanentemente","Não tem nenhuma contraindicação na gestação"], correct:1, exp:"A griseofulvina interfere na divisão celular (inclusive de células fetais em rápida multiplicação), com risco teratogênico bem documentado."},

// AINEs
{cat:"AINEs", q:"Por que gatos exigem maior cautela com AINEs em geral, não apenas com paracetamol?", opts:["Gatos são completamente resistentes a efeitos adversos de AINEs","Têm capacidade reduzida de glucuronidação hepática, prolongando a meia-vida de muitos AINEs","AINEs não têm nenhum efeito analgésico em felinos","Gatos eliminam AINEs mais rápido que cães"], correct:1, exp:"A menor capacidade de glucuronidação felina pode levar a acúmulo de AINEs com doses repetidas, aumentando o risco de toxicidade em comparação com cães."},
{cat:"AINEs", q:"Por que é recomendado suspender alguns AINEs antes de cirurgias com risco de sangramento?", opts:["Porque aumentam a pressão arterial de forma perigosa","Porque alguns inibem a agregação plaquetária dependente de tromboxano A2, prolongando o tempo de sangramento","Porque interferem na anestesia geral diretamente","Não há nenhuma recomendação nesse sentido"], correct:1, exp:"A inibição da COX reduz a produção de tromboxano A2, importante para a agregação plaquetária, o que pode prolongar o tempo de sangramento cirúrgico."},
{cat:"AINEs", q:"O que caracteriza clinicamente um AINE COX-2 preferencial (ex: meloxicam, carprofeno)?", opts:["Elimina totalmente o risco de efeitos adversos gastrointestinais","Tende a preservar mais as funções fisiológicas dependentes de COX-1, mas não elimina o risco de efeitos adversos GI e renais","Só pode ser usado por via injetável","Não tem nenhum efeito anti-inflamatório"], correct:1, exp:"A seletividade por COX-2 reduz, mas não elimina, o risco de efeitos adversos gastrointestinais e renais, especialmente em uso crônico ou doses altas."},

// Corticoides
{cat:"Corticoides", q:"Quais são efeitos colaterais comuns do uso crônico de corticoides em cães?", opts:["Perda de peso e hipoglicemia","Poliúria/polidipsia/polifagia, atrofia muscular, imunossupressão e predisposição a diabetes iatrogênico","Apenas sonolência leve e passageira","Aumento da massa muscular e da densidade óssea"], correct:1, exp:"O uso crônico de corticoides produz um quadro semelhante ao hiperadrenocorticismo (Cushing iatrogênico), com esses sinais clássicos."},
{cat:"Corticoides", q:"O que é o efeito mineralocorticoide de um glicocorticoide, e por que importa clinicamente?", opts:["É um efeito exclusivo em répteis","Alguns corticoides também atuam em receptores mineralocorticoides, retendo sódio e água e excretando potássio", "Refere-se ao efeito anti-inflamatório propriamente dito","Não tem nenhuma relevância clínica"], correct:1, exp:"Esse efeito é especialmente relevante em pacientes cardiopatas ou com distúrbios eletrolíticos, já que a retenção de sódio/água pode agravar quadros de congestão."},
{cat:"Corticoides", q:"Por que a diferença de potência entre dexametasona e prednisolona é clinicamente relevante?", opts:["Não há diferença de potência entre elas","A dexametasona é bem mais potente e de ação mais longa, exigindo doses proporcionalmente menores","A prednisolona é sempre mais potente que a dexametasona","Ambas têm exatamente a mesma potência e duração"], correct:1, exp:"Usar a mesma dose numérica das duas sem ajuste levaria a super ou subdosagem, dada a diferença significativa de potência entre elas."},

// Opioides
{cat:"Opioides", q:"Por que opioides podem causar constipação com uso prolongado?", opts:["Por desidratação induzida diretamente","Reduzem a motilidade gastrointestinal ao atuar em receptores opioides no plexo entérico","Por efeito exclusivamente central sem relação com o intestino","Não há relação entre opioides e função intestinal"], correct:1, exp:"A ativação de receptores opioides no trato gastrointestinal retarda o trânsito intestinal, sendo um efeito colateral comum do uso prolongado."},
{cat:"Opioides", q:"O que caracteriza o mecanismo de ação do tramadol além da ação opioide?", opts:["Atua apenas como anti-inflamatório","Tem ação dupla: agonista fraco em receptores mu e inibição da recaptação de serotonina e noradrenalina","É um antagonista opioide puro","Age exclusivamente em receptores GABA"], correct:1, exp:"Essa ação dupla contribui para o efeito analgésico do tramadol por vias adicionais à simples ativação de receptores opioides."},
{cat:"Opioides", q:"Por que a resposta a opioides pode variar tanto entre espécies como gatos e cavalos em comparação a cães?", opts:["Opioides não têm efeito em nenhuma dessas espécies","Pode predominar estimulação do SNC (excitação/disforia) em vez de sedação, dependendo da espécie e da dose","Gatos e cavalos não possuem receptores opioides","A resposta é sempre idêntica entre todas as espécies"], correct:1, exp:"Há variação interespécie na resposta aos opioides; por isso, em algumas espécies e doses, a associação com sedativos é importante para evitar excitação paradoxal."},

// Anestésicos
{cat:"Anestésicos", q:"Qual é o mecanismo de ação dos benzodiazepínicos (ex: diazepam, midazolam)?", opts:["Bloqueiam receptores NMDA de glutamato","Potencializam a ação do GABA nos receptores GABA-A, aumentando a frequência de abertura dos canais de cloreto","Inibem diretamente a acetilcolinesterase","Bloqueiam canais de sódio neuronais"], correct:1, exp:"Essa potencialização do GABA produz sedação, relaxamento muscular e efeito anticonvulsivante."},
{cat:"Anestésicos", q:"Por que a cetamina costuma ser associada a um tranquilizante antes do uso isolado?", opts:["Porque sozinha não tem nenhum efeito anestésico","Isolada pode causar rigidez muscular, convulsões e recuperação anestésica agitada","Porque reduz o custo do protocolo anestésico","Não há necessidade de associação em nenhuma espécie"], correct:1, exp:"A associação com sedativos/tranquilizantes melhora o relaxamento muscular e suaviza a indução e a recuperação anestésica com cetamina."},
{cat:"Anestésicos", q:"Por que os anestésicos inalatórios voláteis (ex: isoflurano, sevoflurano) são preferidos em cirurgias longas?", opts:["Porque não exigem monitoramento durante o procedimento","Permitem ajuste rápido e fino da profundidade anestésica, com eliminação predominantemente pulmonar","Porque são sempre mais baratos que anestésicos injetáveis","Porque eliminam a necessidade de intubação"], correct:1, exp:"A eliminação pulmonar (pouco dependente do metabolismo hepático/renal) permite ajustes rápidos na profundidade anestésica ao longo de procedimentos prolongados."},

// Cardiovascular
{cat:"Cardiovascular", q:"Qual é o mecanismo de ação dos inibidores da ECA (ex: enalapril, benazepril)?", opts:["Bloqueiam diretamente os receptores beta-adrenérgicos","Bloqueiam a enzima conversora de angiotensina, reduzindo a formação de angiotensina II","Aumentam a excreção de sódio pela alça de Henle","Bloqueiam canais de cálcio no miocárdio"], correct:1, exp:"Ao reduzir a angiotensina II, diminuem a vasoconstrição e a retenção de sódio/água, reduzindo a pós-carga cardíaca."},
{cat:"Cardiovascular", q:"Por que betabloqueadores devem ser retirados gradualmente e não de forma abrupta?", opts:["Não há nenhum risco na suspensão abrupta","A suspensão abrupta pode causar efeito rebote, com taquicardia e hipertensão por up-regulation compensatória de receptores beta","Causam apenas sonolência ao serem retirados","Betabloqueadores nunca podem ser suspensos"], correct:1, exp:"O uso prolongado leva a uma compensação com aumento do número de receptores beta; a retirada abrupta desmascara esse efeito, causando taquicardia e hipertensão de rebote."},
{cat:"Cardiovascular", q:"Por que a espironolactona costuma ser associada a outros diuréticos no manejo de ICC?", opts:["Porque não tem nenhum efeito diurético próprio","É poupadora de potássio (antagonista da aldosterona), compensando a perda de potássio causada por outros diuréticos, além de ter efeito antifibrótico cardíaco","Porque potencializa a toxicidade dos demais diuréticos sem benefício","Porque substitui totalmente a necessidade de outros diuréticos"], correct:1, exp:"A espironolactona ajuda a equilibrar o potássio perdido com diuréticos de alça/tiazídicos e contribui com efeitos protetores adicionais sobre o miocárdio."},

// Endócrino
{cat:"Endócrino", q:"Qual é o mecanismo de ação do trilostano no tratamento do hiperadrenocorticismo canino (Cushing)?", opts:["Destrói o córtex adrenal de forma irreversível","Inibe a enzima 3-beta-hidroxiesteroide desidrogenase, bloqueando a síntese de cortisol", "Substitui diretamente o cortisol endógeno","Estimula a produção hipofisária de ACTH"], correct:1, exp:"O trilostano bloqueia uma etapa enzimática da esteroidogênese adrenal, reduzindo a produção de cortisol sem destruir permanentemente a glândula."},
{cat:"Endócrino", q:"Por que pacientes com hipoadrenocorticismo (Addison) precisam de reposição tanto de mineralocorticoide quanto de glicocorticoide?", opts:["Porque têm excesso de produção desses hormônios","Há destruição do córtex adrenal, incapaz de produzir aldosterona e cortisol endogenamente","Porque a hipófise para de funcionar completamente","Não é necessária reposição hormonal nesses pacientes"], correct:1, exp:"A destruição do córtex adrenal compromete a produção tanto de aldosterona (regulação eletrolítica) quanto de cortisol, exigindo reposição vitalícia de ambos."},
{cat:"Endócrino", q:"O que é o efeito Somogyi no manejo de diabetes com insulinoterapia?", opts:["Hiperglicemia de rebote após hipoglicemia induzida por dose excessiva de insulina","Resposta alérgica grave à insulina","Ausência completa de resposta à insulina","Aumento permanente da necessidade de insulina sem causa aparente"], correct:1, exp:"A hiperglicemia de rebote ocorre pela liberação de hormônios contrarreguladores após um episódio de hipoglicemia, podendo ser confundida com dose insuficiente de insulina."},

// Antiparasitários
{cat:"Antiparasitários", q:"Qual é o mecanismo de ação geral das lactonas macrocíclicas (ex: ivermectina)?", opts:["Bloqueiam a síntese de quitina do parasita","Aumentam a permeabilidade da membrana neuronal/muscular do parasita a íons cloreto, causando paralisia","Rompem diretamente o tegumento do parasita","Inibem a fotossíntese do parasita"], correct:1, exp:"Ao atuar em canais de cloreto glutamato-dependentes de invertebrados, essas lactonas causam paralisia e morte do parasita."},
{cat:"Antiparasitários", q:"Qual é o mecanismo de ação geral dos benzimidazólicos (ex: fenbendazol) como anti-helmínticos?", opts:["Bloqueiam receptores de acetilcolina do parasita","Ligam-se à beta-tubulina do parasita, impedindo a polimerização de microtúbulos", "Aumentam a permeabilidade da cutícula do parasita à água","Atuam apenas por repelência mecânica"], correct:1, exp:"Ao impedir a formação de microtúbulos, comprometem funções celulares essenciais do parasita, como transporte e absorção de nutrientes, levando à sua morte."},
{cat:"Antiparasitários", q:"Por que o praziquantel é eficaz contra cestódeos (tênias)?", opts:["Bloqueia a digestão do hospedeiro","Aumenta a permeabilidade da membrana do parasita ao cálcio, causando contração espástica e danos ao tegumento","Inibe exclusivamente a reprodução do parasita sem afetar adultos","Atua apenas em ovos do parasita"], correct:1, exp:"O influxo de cálcio induzido pelo praziquantel causa contração espástica da musculatura do parasita e lesão do tegumento, facilitando sua eliminação."},

// Toxicologia
{cat:"Toxicologia", q:"Por que o carvão ativado é usado em muitos casos de intoxicação oral recente?", opts:["Neutraliza quimicamente qualquer toxina no sangue","Adsorve toxinas ainda presentes no trato gastrointestinal, reduzindo sua absorção sistêmica","Induz vômito imediato em todos os casos","Substitui a necessidade de qualquer outro tratamento"], correct:1, exp:"O carvão ativado é mais eficaz quando administrado logo após a ingestão, antes que a toxina seja absorvida pela mucosa intestinal."},
{cat:"Toxicologia", q:"Qual é o antídoto para intoxicação por benzodiazepínicos?", opts:["Naloxona","Flumazenil","Atropina","Vitamina K1"], correct:1, exp:"Flumazenil é um antagonista competitivo no sítio benzodiazepínico do receptor GABA-A, revertendo os efeitos sedativos dos benzodiazepínicos."},
{cat:"Toxicologia", q:"Qual é o princípio geral de tratamento para intoxicações sem antídoto específico disponível?", opts:["Aguardar a evolução espontânea sem intervenção","Suporte clínico, descontaminação quando aplicável e tratamento sintomático das complicações","Administrar antibióticos de amplo espectro em todos os casos","Induzir hipotermia terapêutica sistematicamente"], correct:1, exp:"Na ausência de antídoto específico, o manejo se baseia em suporte (fluidoterapia, monitoramento), descontaminação quando indicada e tratamento dos sinais clínicos apresentados."},

// Dermatológicos
{cat:"Dermatológicos", q:"Como age o lokivetmab no controle da dermatite atópica canina?", opts:["É um corticoide de depósito de longa duração","É um anticorpo monoclonal caninizado que neutraliza especificamente a interleucina-31 (IL-31)","Atua bloqueando receptores histamínicos H1","É um antifúngico tópico de amplo espectro"], correct:1, exp:"Ao neutralizar a IL-31, citocina-chave na sinalização do prurido, o lokivetmab reduz a coceira associada à dermatite atópica sem os efeitos sistêmicos amplos de um corticoide."},
{cat:"Dermatológicos", q:"Por que corticoides tópicos são preferidos em algumas dermatites localizadas em vez de sistêmicos?", opts:["Porque nunca funcionam para dermatites localizadas","Permitem efeito anti-inflamatório local com menor absorção sistêmica, reduzindo risco de efeitos adversos generalizados","Porque são sempre mais baratos","Porque não têm nenhum efeito colateral, nem local"], correct:1, exp:"A aplicação tópica concentra o efeito no local afetado, reduzindo (mas não eliminando totalmente) o risco de efeitos sistêmicos como supressão adrenal."},
{cat:"Dermatológicos", q:"Por que o tratamento de otite externa costuma exigir combinação de antibiótico, antifúngico e anti-inflamatório?", opts:["Porque otites nunca têm componente infeccioso","Porque frequentemente envolvem infecção mista (bacteriana e fúngica) associada a inflamação significativa","Porque essa combinação é exigida por lei em todos os casos","Porque reduz o custo total do tratamento"], correct:1, exp:"Tratar apenas um componente (por exemplo, só o fungo ou só a bactéria) costuma resultar em recidiva, já que a otite geralmente tem múltiplos fatores envolvidos."},

// Gastrointestinal
{cat:"Gastrointestinal", q:"Qual é o mecanismo de ação da metoclopramida?", opts:["Inibidor da bomba de prótons","Antagonista de receptores dopaminérgicos D2, com ação procinética e antiemética central","Protetor físico da mucosa gástrica","Agonista de receptores opioides mu"], correct:1, exp:"Ao bloquear receptores D2 na zona de gatilho quimiorreceptora e aumentar a motilidade GI, a metoclopramida atua tanto como antiemético quanto como procinético."},
{cat:"Gastrointestinal", q:"Por que o uso de loperamida deve ser cauteloso em Collies e raças com mutação MDR1?", opts:["Não há nenhum cuidado especial necessário nessas raças","É substrato da glicoproteína-P; a mutação pode permitir maior penetração no SNC, causando sedação ou depressão respiratória","Loperamida é sempre contraindicada em cães, independente da raça","Essas raças metabolizam a loperamida mais rápido que as demais"], correct:1, exp:"Assim como a ivermectina, a loperamida normalmente é mantida fora do SNC pela glicoproteína-P; a mutação MDR1 compromete esse mecanismo de proteção."},
{cat:"Gastrointestinal", q:"Como agem os probióticos no manejo de distúrbios gastrointestinais?", opts:["Eliminam diretamente toda a microbiota intestinal","Fornecem microrganismos benéficos que ajudam a restaurar o equilíbrio da microbiota, competindo com patógenos","Atuam exclusivamente como antiácidos","Substituem a necessidade de qualquer outro tratamento em diarreias graves"], correct:1, exp:"Os probióticos ajudam a restabelecer o equilíbrio microbiano intestinal e podem modular a resposta imune local, sendo um coadjuvante e não substituto de tratamentos específicos."},

// Reprodução
{cat:"Reprodução", q:"Por que a ocitocina é usada no manejo do parto e do puerpério?", opts:["Porque inibe as contrações uterinas indesejadas","Estimula a contração da musculatura uterina lisa, auxiliando na expulsão fetal/placentária e na ejeção do leite", "Porque bloqueia a produção de prolactina","Porque tem ação exclusivamente analgésica"], correct:1, exp:"A ocitocina promove contração uterina (auxiliando o parto) e também participa do reflexo de ejeção do leite durante a lactação."},
{cat:"Reprodução", q:"Como age a cabergolina no tratamento de gestação indesejada ou pseudociese?", opts:["É um análogo sintético de progesterona","É um agonista dopaminérgico que inibe a secreção de prolactina pela hipófise","Estimula diretamente a liberação de ocitocina","Bloqueia receptores de estrógeno no útero"], correct:1, exp:"Ao inibir a prolactina, a cabergolina reduz o suporte hormonal necessário para a manutenção da gestação ou para os sinais associados à pseudociese."},

// Imunobiológicos
{cat:"Imunobiológicos", q:"Qual é a diferença entre vacina viva atenuada e vacina inativada?", opts:["Não há diferença relevante entre os dois tipos","A viva atenuada usa o agente enfraquecido e gera resposta imune geralmente mais robusta; a inativada usa o agente morto e costuma exigir reforços mais frequentes","A inativada sempre confere imunidade mais duradoura que a viva atenuada","Vacinas vivas atenuadas nunca são usadas em medicina veterinária"], correct:1, exp:"A capacidade de replicação mínima da vacina viva atenuada tende a estimular uma resposta imune mais completa e duradoura, mas exige mais cuidado em pacientes imunocomprometidos ou gestantes."},
{cat:"Imunobiológicos", q:"O que é um adjuvante vacinal e para que serve?", opts:["É o próprio antígeno da vacina","Substância adicionada para potencializar e prolongar a resposta imune ao antígeno vacinal","É um conservante que não tem efeito imunológico","É usado apenas em vacinas vivas atenuadas"], correct:1, exp:"Adjuvantes são comuns em vacinas inativadas, que sozinhas gerariam uma resposta imune mais fraca sem esse reforço."},

// Vias de administração
{cat:"Vias de administração", q:"O que caracteriza a via transdérmica de administração de fármacos?", opts:["Injeção direta no tecido subcutâneo","Absorção do fármaco através da pele para a circulação sistêmica, geralmente com liberação lenta e prolongada","Administração exclusiva em mucosas","Via usada apenas para vacinas"], correct:1, exp:"A via transdérmica é útil para manter níveis plasmáticos estáveis ao longo do tempo, embora a absorção possa variar conforme espessura da pele e presença de pelos."},
{cat:"Vias de administração", q:"Por que a administração retal pode ser útil em situações de convulsão ativa?", opts:["Porque é sempre a via de escolha em qualquer emergência","Permite absorção relativamente rápida (ex: diazepam retal) sem necessidade de acesso venoso imediato","Porque tem início de ação mais rápido que a via intravenosa","Porque é a única via segura para anticonvulsivantes"], correct:1, exp:"A via retal é prática em ambiente domiciliar, permitindo início do controle da crise antes mesmo de se conseguir um acesso venoso ou chegar ao atendimento veterinário."},
{cat:"Vias de administração", q:"Qual é a principal vantagem da via intravenosa sobre as demais em situações de emergência?", opts:["Menor custo do tratamento","Início de ação praticamente imediato, pois o fármaco entra diretamente na circulação sistêmica","Menor risco de efeitos adversos em geral","É a única via que permite uso de fármacos irritantes"], correct:1, exp:"Ao eliminar a etapa de absorção, a via IV proporciona início de ação muito mais rápido que vias como oral, subcutânea ou intramuscular."},

// Interações
{cat:"Interações", q:"O que caracteriza uma interação farmacodinâmica entre dois fármacos?", opts:["Um fármaco altera a absorção intestinal do outro","Os dois fármacos atuam no mesmo sistema fisiológico ou receptor, somando ou opondo efeitos, sem necessariamente mudar suas concentrações plasmáticas","Um fármaco altera o metabolismo hepático do outro","Não existe esse tipo de interação em farmacologia veterinária"], correct:1, exp:"Diferente da interação farmacocinética (que altera concentrações), a farmacodinâmica envolve efeitos somados ou opostos no mesmo sistema, mesmo com concentrações inalteradas."},
{cat:"Interações", q:"Por que associar dois fármacos nefrotóxicos (ex: alguns AINEs com aminoglicosídeos) é especialmente arriscado?", opts:["Os efeitos nefrotóxicos se anulam mutuamente","O efeito nefrotóxico pode ser aditivo ou sinérgico, aumentando significativamente o risco de lesão renal aguda","Não há nenhuma interação relevante entre essas classes","Um fármaco sempre neutraliza a toxicidade renal do outro"], correct:1, exp:"Quando dois fármacos compartilham um mesmo órgão-alvo de toxicidade, o risco de dano costuma se somar, exigindo cautela redobrada na associação."},

// Por espécie
{cat:"Por espécie", q:"Por que antibióticos orais de amplo espectro são especialmente arriscados em equinos?", opts:["Equinos são resistentes a qualquer disbiose intestinal","Podem alterar drasticamente a microbiota cecal fermentativa, predispondo a colite grave e potencialmente fatal","Não têm nenhum risco especial em relação a outras espécies","Equinos não absorvem antibióticos orais"], correct:1, exp:"A fermentação cecal equina depende de uma microbiota equilibrada; sua alteração por antibióticos de amplo espectro pode causar colite grave, às vezes fatal."},
{cat:"Por espécie", q:"Por que aves têm particularidades importantes na farmacocinética de muitos fármacos?", opts:["Não existem diferenças farmacocinéticas relevantes em aves","Possuem metabolismo mais acelerado e um sistema porta-renal, além de sacos aéreos relevantes para anestesia inalatória", "Aves não metabolizam fármacos no fígado","Aves eliminam todos os fármacos exclusivamente pelas penas"], correct:1, exp:"Essas particularidades anatômicas e metabólicas exigem doses e protocolos específicos por espécie/grupo taxonômico de ave, diferentes dos usados em mamíferos."},
{cat:"Por espécie", q:"Por que bovinos leiteiros exigem atenção ao período de carência de fármacos utilizados?", opts:["Porque fármacos nunca afetam a produção de leite","Muitos fármacos são excretados no leite, e a carência garante que resíduos não ultrapassem limites seguros para consumo humano","Porque a carência é apenas uma formalidade sem base farmacológica","Porque bovinos leiteiros não metabolizam fármacos"], correct:1, exp:"O período de carência é calculado com base na farmacocinética do fármaco no leite, protegendo o consumidor final de resíduos medicamentosos."},

// ---- LOTE 3 ----
// Farmacocinética
{cat:"Farmacocinética", q:"Por que a via de administração de um fármaco pode alterar sua biodisponibilidade mesmo mantendo a mesma dose?", opts:["A dose numérica é o único fator relevante, a via não importa","Vias diferentes têm etapas distintas de absorção (ou nenhuma, como a IV), afetando quanto do fármaco chega intacto à circulação","Isso só ocorre com fármacos veterinários, nunca em humanos","A biodisponibilidade é sempre 100% independente da via"], correct:1, exp:"Cada via tem barreiras de absorção diferentes (mucosa intestinal, pele, metabolismo de primeira passagem), o que altera a fração do fármaco que efetivamente atinge a circulação sistêmica."},
{cat:"Farmacocinética", q:"O que significa dizer que um fármaco tem alta ligação a proteínas plasmáticas em uma espécie mas não em outra?", opts:["Isso nunca varia entre espécies","A afinidade de ligação pode diferir por variações estruturais nas proteínas plasmáticas entre espécies, alterando a fração livre e ativa do fármaco","Significa que o fármaco é tóxico apenas nessa espécie","A ligação proteica não tem relação com a espécie"], correct:1, exp:"Diferenças na concentração e estrutura de proteínas plasmáticas (como a albumina) entre espécies podem alterar significativamente a farmacocinética de um mesmo fármaco."},

// Farmacodinâmica
{cat:"Farmacodinâmica", q:"O que é um antagonista não competitivo?", opts:["Liga-se ao mesmo sítio do agonista e pode ser deslocado por doses maiores dele","Liga-se a um sítio diferente do receptor (ou se liga irreversivelmente), reduzindo o efeito máximo mesmo com aumento da dose do agonista","É sinônimo de agonista parcial","Não tem nenhum efeito sobre a curva dose-resposta"], correct:1, exp:"Diferente do antagonismo competitivo, o não competitivo reduz o efeito máximo (Emax) da curva dose-resposta, já que não pode ser simplesmente superado por mais agonista."},
{cat:"Farmacodinâmica", q:"O que caracteriza a janela terapêutica de um fármaco na prática clínica?", opts:["É o mesmo que a dose máxima permitida por lei","É a faixa de concentração plasmática entre a dose mínima eficaz e a dose que começa a causar toxicidade","É o tempo de validade do medicamento","Refere-se apenas ao horário de administração do fármaco"], correct:1, exp:"Fármacos com janela terapêutica estreita (como a digoxina) exigem monitoramento mais cuidadoso da dose, já que a margem entre efeito e toxicidade é pequena."},

// Antibióticos
{cat:"Antibióticos", q:"Por que a associação de dois antibióticos bacteriostáticos com mecanismos antagônicos pode reduzir a eficácia do tratamento?", opts:["Bacteriostáticos nunca podem ser associados a nada","Um fármaco que depende de bactérias em replicação ativa pode ter sua ação prejudicada se outro fármaco já interrompeu essa replicação","Essa associação sempre aumenta a eficácia do tratamento","Não existe interação relevante entre antibióticos bacteriostáticos"], correct:1, exp:"Alguns antagonismos ocorrem quando um antibiótico bacteriostático interrompe processos (como síntese proteica ou replicação) dos quais outro antibiótico depende para agir — por isso a escolha de associações deve considerar o mecanismo de cada fármaco."},
{cat:"Antibióticos", q:"Por que a cultura e o antibiograma são recomendados antes de tratamentos antimicrobianos prolongados ou em casos refratários?", opts:["Porque são exigência apenas burocrática","Permitem identificar o agente causador e sua sensibilidade real aos antimicrobianos, orientando uma escolha mais precisa e reduzindo uso desnecessário de amplo espectro","Porque todo antibiótico funciona igualmente bem sem esse exame","Porque substituem a necessidade de exame clínico"], correct:1, exp:"O uso empírico prolongado sem cultura pode selecionar resistência e atrasar o tratamento eficaz; o antibiograma orienta a escolha do antimicrobiano mais adequado ao patógeno identificado."},
{cat:"Antibióticos", q:"Por que a clindamicina é frequentemente escolhida para infecções ósseas e dentárias?", opts:["Porque não penetra tecido ósseo","Porque tem boa penetração óssea e é eficaz contra diversos anaeróbios comumente envolvidos nessas infecções","Porque atua exclusivamente contra vírus","Porque é sempre a primeira escolha para qualquer infecção bacteriana"], correct:1, exp:"A boa penetração tecidual (incluindo osso) e o espectro que cobre anaeróbios tornam a clindamicina uma opção frequente em infecções odontológicas e osteomielites."},

// AINEs
{cat:"AINEs", q:"Por que alguns AINEs administrados topicamente no olho ainda podem causar efeitos sistêmicos?", opts:["Colírios nunca são absorvidos além do olho","Parte do fármaco pode drenar pelo ducto nasolacrimal e ser absorvida pela mucosa nasal/gastrointestinal","AINEs oftálmicos não têm nenhuma ação farmacológica","O olho é completamente isolado da circulação sistêmica"], correct:1, exp:"A drenagem nasolacrimal permite que uma parte do fármaco aplicado no olho seja absorvida sistemicamente, o que é relevante em pacientes com contraindicações a AINEs sistêmicos."},

// Corticoides
{cat:"Corticoides", q:"Por que corticoides podem mascarar sinais de infecção em um paciente?", opts:["Corticoides eliminam diretamente os patógenos","Suprimem a resposta inflamatória e imune, reduzindo sinais clássicos de infecção (febre, edema) mesmo com o processo infeccioso ativo","Corticoides sempre pioram os sinais visíveis de infecção","Não há relação entre corticoides e sinais infecciosos"], correct:1, exp:"Por suprimirem a resposta inflamatória, corticoides podem atenuar sinais que normalmente alertariam para uma infecção em curso, dificultando o diagnóstico precoce."},

// Opioides
{cat:"Opioides", q:"Por que a analgesia multimodal (combinar opioide + AINE + outras classes) é frequentemente preferida à monoterapia?", opts:["Porque reduz custos exclusivamente","Permite atuar em diferentes vias da dor simultaneamente, geralmente com menor dose de cada fármaco e menos efeitos colaterais individuais","Porque um único fármaco nunca tem efeito analgésico suficiente","Não há vantagem comprovada na analgesia multimodal"], correct:1, exp:"Ao combinar mecanismos de ação diferentes, a analgesia multimodal pode proporcionar controle mais eficaz da dor com doses menores de cada agente, reduzindo efeitos adversos."},

// Anestésicos
{cat:"Anestésicos", q:"O que caracteriza o conceito de CAM (concentração alveolar mínima) em anestesia inalatória?", opts:["É a dose máxima segura de um anestésico injetável","É a concentração do anestésico inalatório que impede movimento em 50% dos pacientes frente a um estímulo doloroso padronizado, usada como medida de potência","É o tempo de indução anestésica","Refere-se à concentração de oxigênio no circuito anestésico"], correct:1, exp:"A CAM é um parâmetro comparativo de potência entre anestésicos inalatórios: quanto menor a CAM, mais potente é o agente."},

// Cardiovascular
{cat:"Cardiovascular", q:"Por que o uso de IECA (inibidores da ECA) exige monitoramento da função renal e dos eletrólitos?", opts:["Porque não têm nenhuma relação com a função renal","Podem reduzir a taxa de filtração glomerular em alguns pacientes e favorecer retenção de potássio (hipercalemia)","Porque sempre causam insuficiência renal aguda","Porque eliminam completamente o potássio do organismo"], correct:1, exp:"A redução da angiotensina II pode alterar a hemodinâmica renal e a excreção de potássio, exigindo acompanhamento em pacientes com função renal já comprometida."},

// Endócrino
{cat:"Endócrino", q:"Por que o diagnóstico e tratamento do hipertireoidismo felino frequentemente evoluem em paralelo ao monitoramento da função renal?", opts:["Não há nenhuma relação entre as duas condições","O hipertireoidismo aumenta a taxa de filtração glomerular, podendo mascarar uma doença renal crônica subjacente que se manifesta após o controle do hormônio tireoidiano","O hipertireoidismo sempre cura a doença renal","A função renal não é avaliada nesses pacientes"], correct:1, exp:"Ao normalizar a função tireoidiana, a taxa de filtração glomerular tende a cair, podendo revelar uma doença renal crônica que estava sendo mascarada pelo estado hipertireoideo."},

// Antiparasitários
{cat:"Antiparasitários", q:"Por que a associação de diferentes classes de antiparasitários em um mesmo protocolo pode ser uma estratégia de manejo de resistência?", opts:["Porque aumenta apenas o custo do tratamento sem benefício","Reduz a chance de sobrevivência de parasitas resistentes a uma única classe, retardando a seleção de resistência","Antiparasitários de classes diferentes nunca podem ser combinados","A resistência parasitária não é influenciada pela escolha de classes"], correct:1, exp:"Rotacionar ou combinar classes com mecanismos de ação distintos reduz a pressão seletiva sobre uma única via, ajudando a preservar a eficácia dos antiparasitários a longo prazo."},

// Toxicologia
{cat:"Toxicologia", q:"Por que a indução de êmese não é recomendada em todos os casos de intoxicação oral?", opts:["A êmese é sempre segura e recomendada em qualquer intoxicação","Substâncias cáusticas/corrosivas ou risco de aspiração (ex: paciente sedado) contraindicam a indução de vômito, pelo risco de lesão adicional","Vomitar nunca remove toxinas do estômago","Não há nenhuma contraindicação para indução de êmese"], correct:1, exp:"Em casos de ingestão de cáusticos ou quando há risco de aspiração pulmonar, induzir o vômito pode causar mais dano do que benefício — a decisão depende da substância e do estado clínico do paciente."},

// Dermatológicos
{cat:"Dermatológicos", q:"Por que o tratamento da demodicose generalizada costuma exigir protocolos mais prolongados que o de outras ectoparasitoses?", opts:["Porque o ácaro Demodex vive profundamente nos folículos pilosos, exigindo tratamento sustentado para eliminação completa","Porque a demodicose nunca responde a tratamento farmacológico","Porque o Demodex é resistente a todas as classes de antiparasitários conhecidas","Porque a demodicose é sempre autolimitada sem necessidade de tratamento"], correct:0, exp:"Por se alojar profundamente nos folículos pilosos, o Demodex exige tratamento mais prolongado e monitoramento com raspados cutâneos seriados até a resolução completa."},

// Gastrointestinal
{cat:"Gastrointestinal", q:"Por que a associação de sucralfato com outros fármacos orais exige atenção ao horário de administração?", opts:["Não há nenhuma interação relevante com o horário","O sucralfato pode reduzir a absorção de outros fármacos administrados simultaneamente, por isso costuma-se espaçar a administração entre eles","O sucralfato deve ser administrado exclusivamente por via injetável","O horário de administração nunca influencia a eficácia de fármacos orais"], correct:1, exp:"Como o sucralfato forma uma barreira física na mucosa, ele pode interferir na absorção de outros fármacos administrados ao mesmo tempo, por isso recomenda-se espaçar as doses."},

// Reprodução
{cat:"Reprodução", q:"Por que o uso de prostaglandina F2-alfa em fêmeas gestantes pode induzir aborto ou parto prematuro?", opts:["Não tem nenhum efeito sobre a gestação","Promove a lise do corpo lúteo, reduzindo a progesterona necessária para manter a gestação em várias espécies","Estimula diretamente a implantação do embrião","Aumenta a produção de progesterona"], correct:1, exp:"A queda de progesterona causada pela lise do corpo lúteo pode desencadear a expulsão do conteúdo uterino, por isso esse fármaco é usado deliberadamente para indução de parto ou interrupção da gestação em protocolos específicos."},

// Imunobiológicos
{cat:"Imunobiológicos", q:"Por que animais imunocomprometidos exigem avaliação cuidadosa antes de receberem vacinas vivas atenuadas?", opts:["Porque vacinas vivas atenuadas nunca podem ser aplicadas em nenhum animal","Mesmo atenuado, o agente vacinal pode causar doença clínica em um sistema imune incapaz de controlar sua replicação mínima","Porque vacinas vivas atenuadas não geram nenhuma resposta imune","Não há nenhum cuidado especial necessário nesses pacientes"], correct:1, exp:"Em pacientes imunocomprometidos, mesmo um agente atenuado pode replicar de forma descontrolada e causar doença, por isso a decisão de vacinar exige avaliação individual de risco-benefício."},

// Vias de administração
{cat:"Vias de administração", q:"Por que a via intraóssea é considerada uma alternativa válida em emergências quando o acesso venoso é difícil?", opts:["Porque é sempre a primeira escolha em qualquer situação","Permite infusão de fluidos e fármacos diretamente na medula óssea, com absorção sistêmica rápida, quando veias periféricas não são acessíveis","Porque tem absorção mais lenta que a via oral","Porque substitui permanentemente a necessidade de acesso venoso"], correct:1, exp:"Em pacientes pediátricos, muito pequenos ou em choque com colapso venoso, a via intraóssea oferece uma rota rápida e eficaz para fluidos e fármacos de emergência."},

// Interações
{cat:"Interações", q:"Por que fármacos que induzem enzimas hepáticas (ex: fenobarbital) podem reduzir a eficácia de outros fármacos administrados concomitantemente?", opts:["A indução enzimática não afeta outros fármacos","Aceleram o metabolismo de outros fármacos metabolizados pelas mesmas vias, reduzindo sua concentração plasmática e efeito terapêutico","Sempre aumentam a toxicidade de outros fármacos","Só afetam fármacos administrados por via tópica"], correct:1, exp:"A indução enzimática hepática acelera a biotransformação de outros fármacos que dependem das mesmas enzimas, podendo reduzir sua eficácia se as doses não forem ajustadas."},

// Por espécie
{cat:"Por espécie", q:"Por que gatos filhotes muito jovens exigem cautela especial com fármacos metabolizados por glucuronidação?", opts:["Filhotes têm capacidade de glucuronidação já totalmente madura ao nascer","Vias de biotransformação hepática, incluindo a glucuronidação, ainda estão em desenvolvimento nos primeiros meses de vida, prolongando o efeito de certos fármacos","Não há nenhuma diferença metabólica entre filhotes e adultos","Filhotes eliminam fármacos mais rápido que gatos adultos"], correct:1, exp:"Assim como em outras espécies, vias metabólicas hepáticas amadurecem gradualmente após o nascimento, exigindo cautela e ajuste de dose em neonatos e filhotes muito jovens."},

// Fluidoterapia (categoria nova)
{cat:"Fluidoterapia", q:"Qual é a principal diferença entre um fluido cristaloide isotônico (ex: Ringer lactato) e um coloide?", opts:["Coloides são sempre mais baratos que cristaloides","Cristaloides contêm pequenas moléculas que se distribuem entre compartimentos vascular e intersticial; coloides têm moléculas maiores que permanecem mais tempo no espaço vascular","Não há diferença relevante entre eles","Cristaloides nunca podem ser usados por via intravenosa"], correct:1, exp:"Essa diferença de tamanho molecular explica por que os coloides expandem o volume plasmático de forma mais sustentada, enquanto cristaloides se redistribuem mais rapidamente para o interstício."},
{cat:"Fluidoterapia", q:"Por que a reposição de potássio em fluidos IV deve ser feita com taxa de infusão controlada?", opts:["Porque o potássio não tem nenhum efeito cardíaco","Infusão rápida de potássio pode causar arritmias graves e parada cardíaca por alteração aguda do potencial de membrana das células cardíacas","Porque o potássio é sempre inofensivo em qualquer velocidade","Não há necessidade de controle da taxa de infusão de potássio"], correct:1, exp:"A hipercalemia aguda por infusão rápida de potássio altera perigosamente a excitabilidade cardíaca, por isso a taxa máxima de infusão é rigorosamente respeitada na prática clínica."},

// Anestesia local (categoria nova)
{cat:"Anestesia local", q:"Qual é o mecanismo de ação geral dos anestésicos locais (ex: lidocaína, bupivacaína)?", opts:["Potencializam receptores GABA no SNC","Bloqueiam canais de sódio dependentes de voltagem nos neurônios, impedindo a propagação do potencial de ação e a transmissão do estímulo doloroso","Inibem a ciclo-oxigenase local","Antagonizam receptores opioides periféricos"], correct:1, exp:"Ao bloquear os canais de sódio, os anestésicos locais impedem a despolarização e a condução do impulso nervoso na região onde são aplicados, produzindo anestesia localizada."},
{cat:"Anestesia local", q:"Por que a associação de epinefrina a alguns anestésicos locais prolonga seu efeito?", opts:["A epinefrina acelera a absorção sistêmica do anestésico","A epinefrina causa vasoconstrição local, retardando a absorção do anestésico e prolongando seu tempo de ação no local","A epinefrina neutraliza quimicamente o anestésico","Não há nenhum efeito da epinefrina sobre a duração do bloqueio"], correct:1, exp:"A vasoconstrição local reduz o clearance do anestésico do sítio de aplicação, prolongando o contato com os nervos e, consequentemente, o efeito anestésico."},
{cat:"Anestesia local", q:"Por que a bupivacaína tem duração de ação mais longa que a lidocaína?", opts:["Porque é sempre administrada em doses maiores","Tem maior lipossolubilidade e afinidade pelo canal de sódio, prolongando sua ligação ao receptor","Porque causa vasodilatação intensa no local","Não há diferença real de duração entre elas"], correct:1, exp:"A maior afinidade pelo canal de sódio e lipossolubilidade da bupivacaína prolongam seu tempo de ligação ao alvo, resultando em bloqueio nervoso mais duradouro que o da lidocaína."},

// ---- LOTE 4 ----
// Fluidoterapia
{cat:"Fluidoterapia", q:"O que caracteriza uma solução hipertônica de NaCl e em que situação é usada?", opts:["Tem concentração de sódio menor que o plasma e é usada para manutenção diária","Tem concentração de sódio maior que o plasma, atraindo água do interstício rapidamente — usada em emergências como choque hipovolêmico","É idêntica ao soro fisiológico 0,9%","Não tem nenhuma aplicação clínica em medicina veterinária"], correct:1, exp:"O efeito volêmico rápido, porém transitório, da solução hipertônica a torna útil em protocolos de ressuscitação inicial em choque, geralmente seguida de cristaloides isotônicos."},
{cat:"Fluidoterapia", q:"Por que pacientes cardiopatas exigem cautela especial na taxa de fluidoterapia intravenosa?", opts:["Porque não conseguem absorver fluidos IV","Têm menor capacidade de lidar com sobrecarga de volume, com risco de precipitar edema pulmonar", "Porque fluidos IV são sempre contraindicados em cardiopatas","Não há nenhuma relação entre fluidoterapia e função cardíaca"], correct:1, exp:"A infusão rápida ou excessiva de fluidos pode sobrecarregar um coração já comprometido, favorecendo congestão e edema pulmonar."},

// Farmacocinética
{cat:"Farmacocinética", q:"O que é clearance (depuração) de um fármaco?", opts:["O tempo necessário para o fármaco fazer efeito","O volume de plasma do qual o fármaco é completamente removido por unidade de tempo","A quantidade total de fármaco administrada","A fração do fármaco ligada a proteínas plasmáticas"], correct:1, exp:"O clearance reflete a eficiência conjunta dos órgãos de eliminação (principalmente fígado e rins) em remover o fármaco da circulação."},

// Antibióticos
{cat:"Antibióticos", q:"Por que a associação de dois antibióticos bacteriostáticos com mecanismos antagônicos pode reduzir a eficácia do tratamento?", opts:["Bacteriostáticos nunca podem ser associados entre si","Um fármaco que depende de bactérias em replicação ativa pode ter sua ação prejudicada se outro já interrompeu essa replicação","Essa associação sempre potencializa o efeito de ambos","Não existe interação relevante entre bacteriostáticos"], correct:1, exp:"A escolha de associações antimicrobianas deve considerar o mecanismo de ação de cada fármaco, já que alguns antagonismos farmacodinâmicos podem reduzir a eficácia geral do tratamento."},

// AINEs
{cat:"AINEs", q:"Por que a monitorização da função renal é recomendada durante o uso prolongado de AINEs, especialmente em pacientes idosos ou desidratados?", opts:["AINEs nunca afetam a função renal","A síntese de certas prostaglandinas renais protetoras é reduzida pelos AINEs, podendo comprometer a perfusão renal em situações de baixo fluxo sanguíneo","AINEs sempre melhoram a função renal","A função renal não tem relação com prostaglandinas"], correct:1, exp:"Prostaglandinas mantêm a vasodilatação das arteríolas renais em situações de baixa perfusão; ao serem inibidas pelos AINEs, esse mecanismo compensatório fica comprometido, aumentando o risco de lesão renal."},

// Corticoides
{cat:"Corticoides", q:"Por que a administração de corticoides em pacientes com infecção fúngica sistêmica não diagnosticada é particularmente perigosa?", opts:["Corticoides tratam infecções fúngicas diretamente","A imunossupressão causada pelos corticoides pode permitir a disseminação e agravamento da infecção fúngica", "Não há nenhuma interação entre corticoides e infecções fúngicas","Corticoides eliminam fungos por ação direta"], correct:1, exp:"Por suprimirem a resposta imune, os corticoides podem favorecer a progressão de infecções fúngicas sistêmicas não controladas, por isso o diagnóstico diferencial é importante antes de iniciar a corticoterapia."},

// Opioides
{cat:"Opioides", q:"Por que a metadona é frequentemente preferida à morfina em alguns protocolos de analgesia perioperatória?", opts:["Porque não tem nenhuma ação opioide","Combina ação agonista opioide mu com antagonismo de receptores NMDA, contribuindo para analgesia adicional e menor risco de liberação de histamina","Porque é sempre mais barata que a morfina","Porque não causa nenhuma sedação"], correct:1, exp:"A ação dupla da metadona (agonista mu + antagonista NMDA) pode contribuir para um perfil analgésico mais completo, além de apresentar menor risco de liberação histamínica que a morfina."},

// Anestésicos
{cat:"Anestésicos", q:"Por que o monitoramento da temperatura corporal é essencial durante procedimentos anestésicos prolongados?", opts:["A temperatura não tem nenhuma relação com a anestesia","A maioria dos anestésicos compromete a termorregulação, e a hipotermia pode prolongar a recuperação anestésica e alterar o metabolismo dos fármacos","A hipotermia acelera sempre a recuperação anestésica","Só é relevante em anestesia odontológica"], correct:1, exp:"A hipotermia intraoperatória é comum sob anestesia geral e pode retardar o metabolismo e a eliminação dos fármacos anestésicos, prolongando a recuperação e aumentando riscos perioperatórios."},

// Cardiovascular
{cat:"Cardiovascular", q:"Por que o diltiazem é utilizado no manejo da cardiomiopatia hipertrófica felina?", opts:["Porque aumenta drasticamente a frequência cardíaca","Como bloqueador de canais de cálcio, reduz a frequência cardíaca e pode melhorar o relaxamento e enchimento diastólico do ventrículo hipertrofiado","Porque tem ação diurética potente","Porque substitui a necessidade de qualquer outro tratamento cardíaco"], correct:1, exp:"Ao reduzir a frequência cardíaca e a contratilidade excessiva, o diltiazem pode melhorar o enchimento diastólico em corações com hipertrofia ventricular, comum na cardiomiopatia hipertrófica felina."},

// Endócrino
{cat:"Endócrino", q:"Por que o desmopressina é utilizado no diagnóstico e manejo do diabetes insípido central?", opts:["Porque estimula a produção pancreática de insulina","É um análogo sintético do hormônio antidiurético (ADH), substituindo sua deficiência e reduzindo a produção excessiva de urina diluída","Porque bloqueia receptores de ADH","Não tem nenhuma relação com o diabetes insípido"], correct:1, exp:"No diabetes insípido central, há deficiência de ADH endógeno; a desmopressina repõe essa função hormonal, controlando a poliúria característica da doença."},

// Antiparasitários
{cat:"Antiparasitários", q:"Por que testes de sensibilidade e monitoramento de eficácia (como contagem de ovos fecais) são importantes em programas de controle parasitário?", opts:["Porque não têm nenhuma utilidade prática","Ajudam a identificar precocemente sinais de resistência parasitária a determinada classe de anti-helmíntico, orientando ajustes no protocolo","Porque substituem a necessidade de qualquer tratamento","Porque são exigência apenas legal, sem valor clínico"], correct:1, exp:"O monitoramento da redução na contagem de ovos após tratamento é uma ferramenta prática para detectar precocemente resistência parasitária emergente."},

// Toxicologia
{cat:"Toxicologia", q:"Por que a exposição a chumbo (ex: tintas antigas, baterias) pode causar sinais neurológicos e gastrointestinais em animais?", opts:["O chumbo não tem nenhuma toxicidade em animais","O chumbo interfere na síntese do heme e tem efeito neurotóxico direto, causando sinais como dor abdominal, vômito e alterações neurológicas/comportamentais","O chumbo afeta exclusivamente a pele","Só causa sinais respiratórios"], correct:1, exp:"A intoxicação por chumbo é um diagnóstico diferencial importante em quadros neurológicos e gastrointestinais inexplicados, especialmente em animais com acesso a materiais antigos contendo o metal."},

// Dermatológicos
{cat:"Dermatológicos", q:"Por que xampus com ácido salicílico são usados em dermatoses com hiperqueratose?", opts:["Porque têm ação exclusivamente antibiótica","Têm efeito queratolítico, ajudando a remover o excesso de células córneas e escamas da pele","Porque bloqueiam receptores de histamina na pele","Porque substituem a necessidade de diagnóstico dermatológico"], correct:1, exp:"O efeito queratolítico ajuda a normalizar a descamação cutânea em condições com produção excessiva de queratina, sendo um coadjuvante no manejo de certas dermatoses."},

// Gastrointestinal
{cat:"Gastrointestinal", q:"Por que a cisaprida (procinético) tem uso restrito em algumas situações apesar de sua eficácia?", opts:["Porque nunca teve nenhum efeito adverso relatado","Está associada a risco de arritmias cardíacas graves em humanos, o que levou à restrição de sua disponibilidade comercial em várias regiões","Porque não tem nenhum efeito procinético real","Porque é extremamente barata e por isso pouco utilizada"], correct:1, exp:"Apesar de eficaz como procinético, a cisaprida foi retirada do mercado humano em vários países por risco cardíaco, o que também restringiu seu uso veterinário e disponibilidade."},

// Reprodução
{cat:"Reprodução", q:"Por que o uso de progestágenos sintéticos para supressão de cio é hoje menos recomendado que no passado?", opts:["Porque nunca funcionaram para essa finalidade","Estão associados a riscos conhecidos como piometra, alterações mamárias (incluindo tumores) e outros efeitos endócrinos com uso prolongado","Porque não existe alternativa mais segura disponível","Porque progestágenos não têm nenhum efeito hormonal"], correct:1, exp:"Os riscos reprodutivos e neoplásicos associados ao uso prolongado de progestágenos sintéticos levaram a uma preferência por métodos alternativos de controle reprodutivo, como a ovariohisterectomia eletiva."},

// Imunobiológicos
{cat:"Imunobiológicos", q:"Por que a titulação de anticorpos é usada por alguns veterinários para avaliar a necessidade de reforço vacinal?", opts:["Porque é a única forma de avaliar imunidade em qualquer situação","Pode indicar se o animal ainda possui níveis protetores de anticorpos contra determinado agente, ajudando a individualizar o protocolo vacinal","Porque substitui completamente a necessidade de vacinação","Porque não tem nenhuma relação com proteção imunológica"], correct:1, exp:"A titulação sorológica é uma ferramenta complementar para avaliar a resposta imune prévia, especialmente para agentes com testes validados, embora não substitua o julgamento clínico geral do protocolo vacinal."},

// Vias de administração
{cat:"Vias de administração", q:"Por que a via inalatória é preferida para muitos broncodilatadores no tratamento de doenças respiratórias?", opts:["Porque tem absorção sistêmica muito mais lenta que a via oral","Permite ação direta e rápida no tecido pulmonar-alvo, com menor exposição sistêmica e menos efeitos colaterais gerais","Porque é sempre a via mais barata disponível","Porque substitui a necessidade de diagnóstico respiratório"], correct:1, exp:"A entrega direta ao pulmão concentra o efeito terapêutico no local de ação, reduzindo a exposição sistêmica em comparação a vias como a oral."},

// Interações
{cat:"Interações", q:"Por que a associação de IECA com AINEs exige cautela especial em pacientes com função renal comprometida?", opts:["Não há nenhuma interação relevante entre essas classes","Ambos podem reduzir a perfusão renal por mecanismos distintos, e a combinação pode aumentar significativamente o risco de lesão renal aguda","AINEs sempre potencializam o efeito anti-hipertensivo dos IECA de forma benéfica","IECA sempre neutralizam os efeitos adversos dos AINEs"], correct:1, exp:"AINEs reduzem prostaglandinas vasodilatadoras renais e IECA reduzem angiotensina II (que mantém a pressão de filtração); a combinação pode comprometer duplamente a hemodinâmica renal."},

// Por espécie
{cat:"Por espécie", q:"Por que cavalos apresentam risco elevado de cólica associada ao uso de certos antimicrobianos orais?", opts:["Cavalos não possuem microbiota intestinal relevante","A microbiota cecal fermentativa dos equinos é sensível a alterações; antimicrobianos de amplo espectro por via oral podem desencadear disbiose e colite","Antimicrobianos orais nunca são absorvidos em equinos","Não há nenhuma relação entre antimicrobianos e cólica equina"], correct:1, exp:"A disbiose induzida por antimicrobianos de amplo espectro pode se manifestar clinicamente como cólica e colite em equinos, exigindo cautela na escolha da via e do espectro do antimicrobiano."},
{cat:"Por espécie", q:"Por que a administração de fármacos por via intramuscular é geralmente evitada em coelhos sempre que possível?", opts:["Coelhos não têm massa muscular suficiente para qualquer injeção","Coelhos têm massa muscular relativamente pequena e podem apresentar maior desconforto e risco de lesão muscular com injeções IM repetidas, sendo a via SC frequentemente preferida","A via IM é sempre proibida por lei em coelhos","Coelhos não absorvem fármacos por via muscular"], correct:1, exp:"A preferência pela via subcutânea em coelhos considera o conforto do animal e a menor massa muscular disponível para injeções repetidas, quando essa alternativa é clinicamente adequada."},

// ---- LOTE 5 ----
// Neurologia / Anticonvulsivantes (categoria nova)
{cat:"Neurologia", q:"Qual é o mecanismo de ação do fenobarbital como anticonvulsivante?", opts:["Bloqueia canais de sódio dependentes de voltagem","Potencializa a ação do GABA nos receptores GABA-A, elevando o limiar convulsivo","Antagoniza receptores NMDA de glutamato","Inibe a acetilcolinesterase"], correct:1, exp:"Ao aumentar a duração de abertura dos canais de cloreto GABA-dependentes, o fenobarbital reduz a excitabilidade neuronal, elevando o limiar para disparo de convulsões."},
{cat:"Neurologia", q:"Por que o fenobarbital exige monitoramento periódico da função hepática em uso crônico?", opts:["Não tem nenhuma relação com o fígado","É um indutor enzimático hepático e, com uso prolongado, pode causar hepatotoxicidade","Só afeta a função renal, nunca a hepática","O fenobarbital é eliminado exclusivamente pelos pulmões"], correct:1, exp:"O uso crônico de fenobarbital pode induzir enzimas hepáticas e, em alguns casos, levar a hepatotoxicidade, justificando o acompanhamento laboratorial periódico."},
{cat:"Neurologia", q:"Por que a suspensão abrupta de anticonvulsivantes é perigosa em pacientes epilépticos?", opts:["Não há nenhum risco associado à suspensão abrupta","Pode desencadear convulsões de rebote ou status epilepticus, pela adaptação do SNC à presença contínua do fármaco","A suspensão abrupta sempre cura a epilepsia definitivamente","Anticonvulsivantes podem ser suspensos a qualquer momento sem cuidado"], correct:1, exp:"A retirada de anticonvulsivantes deve ser sempre gradual, já que o sistema nervoso se adapta à presença do fármaco, e a suspensão brusca pode precipitar crises graves."},
{cat:"Neurologia", q:"Qual é o mecanismo de ação do levetiracetam como anticonvulsivante?", opts:["Bloqueia diretamente receptores GABA","Liga-se à proteína SV2A das vesículas sinápticas, modulando a liberação de neurotransmissores","Inibe a bomba de prótons neuronal","Antagoniza receptores dopaminérgicos"], correct:1, exp:"Esse mecanismo, distinto dos anticonvulsivantes clássicos, modula a liberação de neurotransmissores e reduz a excitabilidade neuronal excessiva associada às crises convulsivas."},

// Oncologia / Quimioterapia (categoria nova)
{cat:"Oncologia", q:"Qual é o mecanismo de ação geral dos agentes alquilantes (ex: ciclofosfamida)?", opts:["Inibem a formação do fuso mitótico","Formam ligações cruzadas covalentes no DNA, impedindo replicação e transcrição corretas","Bloqueiam receptores hormonais na célula tumoral","Atuam exclusivamente inibindo a angiogênese"], correct:1, exp:"Ao formar cross-links no DNA, os agentes alquilantes impedem a célula (especialmente as de divisão rápida) de replicar seu material genético corretamente, levando à morte celular."},
{cat:"Oncologia", q:"Por que a quimioterapia costuma causar mielossupressão, sinais gastrointestinais e perda de pelos?", opts:["Esses efeitos não têm relação com o mecanismo de ação dos quimioterápicos","Esses agentes atuam preferencialmente sobre células de divisão rápida, e medula óssea, mucosa GI e folículos pilosos têm alto turnover celular","Só ocorrem por reação alérgica ao veículo do medicamento","Esses efeitos são exclusivos de quimioterápicos administrados por via oral"], correct:1, exp:"A falta de seletividade entre células tumorais e células normais de rápida divisão explica os efeitos colaterais clássicos da quimioterapia citotóxica convencional."},
{cat:"Oncologia", q:"Qual é o mecanismo de ação da vincristina?", opts:["Forma ligações cruzadas no DNA","Inibe a polimerização de microtúbulos, impedindo a formação do fuso mitótico","Inibe a topoisomerase bacteriana","Bloqueia receptores de andrógeno"], correct:1, exp:"Como alcaloide da vinca, a vincristina impede a formação correta do fuso mitótico, interrompendo a divisão celular na metáfase."},
{cat:"Oncologia", q:"Por que a doxorrubicina exige monitoramento cardíaco durante o tratamento oncológico?", opts:["Não tem nenhum efeito sobre o coração","Está associada a cardiotoxicidade cumulativa dose-dependente, podendo levar a cardiomiopatia e insuficiência cardíaca","Causa apenas arritmias transitórias sem relevância clínica","Só afeta o coração em doses únicas muito baixas"], correct:1, exp:"O risco cumulativo de cardiotoxicidade da doxorrubicina exige avaliação cardíaca periódica e atenção à dose total acumulada ao longo do tratamento."},

// Fluidoterapia
{cat:"Fluidoterapia", q:"O que caracteriza um fluido cristaloide isotônico balanceado como o Ringer lactato?", opts:["Contém apenas água destilada sem eletrólitos","Contém eletrólitos como sódio, potássio e cálcio, além de lactato, em concentração próxima à do plasma","É sempre hipertônico em relação ao plasma","Não pode ser administrado por via intravenosa"], correct:1, exp:"O Ringer lactato é formulado para se aproximar da composição eletrolítica plasmática, sendo amplamente usado para reposição volêmica e correção de desidratação."},

// Farmacocinética
{cat:"Farmacocinética", q:"O que caracteriza o estado de equilíbrio (steady state) durante a administração repetida de um fármaco?", opts:["É o momento em que o fármaco para de fazer efeito","Ponto em que a quantidade administrada em cada intervalo se iguala à eliminada, mantendo a concentração plasmática relativamente estável","Ocorre apenas com fármacos administrados uma única vez","É sinônimo de meia-vida de eliminação"], correct:1, exp:"O steady state é geralmente atingido após cerca de 4-5 meias-vidas de administração repetida em intervalos regulares, sendo importante para prever a eficácia terapêutica sustentada."},

// Cardiovascular
{cat:"Cardiovascular", q:"Por que a sildenafila é utilizada no tratamento de hipertensão pulmonar em cães?", opts:["Porque bloqueia receptores beta-adrenérgicos pulmonares","Como inibidor da fosfodiesterase-5, aumenta o GMPc no músculo liso vascular pulmonar, promovendo vasodilatação seletiva dessa circulação","Porque tem ação diurética direta nos pulmões","Porque estimula a produção de eritropoetina"], correct:1, exp:"O aumento seletivo de GMPc no leito vascular pulmonar promove vasodilatação nessa região, reduzindo a pressão pulmonar sem efeito sistêmico tão pronunciado."},

// Toxicologia
{cat:"Toxicologia", q:"Por que a intoxicação por xilitol é particularmente perigosa em cães, diferente de outras espécies?", opts:["O xilitol não tem nenhum efeito metabólico em cães","Estimula liberação intensa de insulina em cães, causando hipoglicemia grave e podendo causar hepatotoxicidade aguda","Causa apenas irritação gástrica leve e autolimitada","O xilitol é inofensivo para cães em qualquer quantidade"], correct:1, exp:"Diferente de humanos, em cães o xilitol provoca liberação abrupta de insulina pancreática, levando a hipoglicemia potencialmente grave, além de risco de dano hepático agudo."},

// Antifúngicos
{cat:"Antifúngicos", q:"Por que a terbinafina costuma ter menos interações medicamentosas que muitos antifúngicos azólicos?", opts:["Porque não tem nenhuma ação antifúngica real","Inibe a esqualeno epoxidase fúngica com maior seletividade, interferindo menos nas enzimas do citocromo P450 de mamíferos","Porque é administrada apenas por via tópica","Porque não é metabolizada no fígado"], correct:1, exp:"A maior seletividade da terbinafina pela via fúngica (em comparação à inibição ampla do citocromo P450 pelos azólicos) reduz o potencial de interações medicamentosas clinicamente relevantes."},

// Vias de administração
{cat:"Vias de administração", q:"Por que a via epidural é utilizada em alguns protocolos analgésicos/anestésicos?", opts:["Porque é sempre mais barata que outras vias","Permite depositar o fármaco próximo às raízes nervosas espinhais, produzindo analgesia regional eficaz com menor necessidade de fármacos sistêmicos","Porque tem absorção sistêmica muito mais rápida que a via IV","Porque substitui a necessidade de qualquer monitoramento anestésico"], correct:1, exp:"A ação regional da via epidural permite boa analgesia em procedimentos de membros posteriores e abdômen caudal, com menor exposição sistêmica a opioides/anestésicos."},

// ---- LOTE 6 ----
{cat:"Neurologia", q:"Qual é o mecanismo de ação do brometo de potássio como anticonvulsivante?", opts:["Bloqueia canais de sódio dependentes de voltagem","O íon brometo compete com o cloreto e hiperpolariza a membrana neuronal, elevando o limiar convulsivo","Inibe diretamente a enzima acetilcolinesterase","Antagoniza receptores dopaminérgicos D2"], correct:1, exp:"Ao competir com o cloreto nos canais iônicos neuronais, o brometo promove hiperpolarização da membrana, tornando o neurônio menos excitável e elevando o limiar para convulsões."},
{cat:"Neurologia", q:"Por que trocas de anticonvulsivante devem ser feitas gradualmente, com sobreposição entre os fármacos?", opts:["Porque anticonvulsivantes nunca podem ser trocados","Mudanças abruptas podem deixar o paciente com controle inadequado das crises durante a transição, já que os níveis do fármaco anterior caem antes do novo atingir concentração estável","Porque a sobreposição é exigida apenas por questões de custo","Não há nenhum risco em trocas abruptas de anticonvulsivante"], correct:1, exp:"A sobreposição gradual evita um período de desproteção contra crises convulsivas enquanto o novo fármaco ainda não atingiu níveis terapêuticos estáveis."},
{cat:"Oncologia", q:"Por que a ciclofosfamida pode causar cistite hemorrágica estéril?", opts:["Por infecção bacteriana direta da bexiga","Um metabólito da ciclofosfamida (acroleína) é irritante para a mucosa vesical, causando inflamação e sangramento sem infecção","Porque é sempre administrada diretamente na bexiga","Não há nenhuma relação entre ciclofosfamida e o trato urinário"], correct:1, exp:"A acroleína, metabólito da ciclofosfamida, tem efeito irritante direto sobre o urotélio, podendo causar cistite hemorrágica mesmo na ausência de infecção bacteriana."},
{cat:"Oncologia", q:"Por que o extravasamento de agentes quimioterápicos vesicantes durante aplicação IV é considerado uma emergência?", opts:["Porque encarece o tratamento sem outro risco relevante","Pode causar necrose tecidual grave e progressiva no local, exigindo manejo imediato","Porque reduz a eficácia do tratamento sistêmico","Não há nenhum risco associado ao extravasamento desses agentes"], correct:1, exp:"Agentes vesicantes que escapam da veia para o tecido subcutâneo podem causar lesão tecidual severa e progressiva, exigindo intervenção rápida para minimizar o dano."},
{cat:"Antibióticos", q:"Por que a doxiciclina costuma ser preferida a outras tetraciclinas em pacientes com função renal comprometida?", opts:["Porque não tem nenhuma atividade antimicrobiana","Tem eliminação predominantemente biliar/fecal, ao invés de depender muito da excreção renal","Porque é sempre administrada por via tópica","Porque não é uma tetraciclina verdadeira"], correct:1, exp:"Ao contrário de outras tetraciclinas mais dependentes da excreção renal, a via biliar/fecal predominante da doxiciclina a torna mais segura em pacientes com comprometimento renal."},
{cat:"Farmacodinâmica", q:"O que é regulação para cima (up-regulation) de receptores?", opts:["Redução do número de receptores após uso agudo de agonista","Aumento do número de receptores disponíveis, geralmente em resposta a bloqueio prolongado por um antagonista ou redução crônica do estímulo endógeno","Processo exclusivo de receptores olfativos","Fenômeno que não ocorre em farmacologia"], correct:1, exp:"É relevante, por exemplo, na suspensão abrupta de betabloqueadores: o aumento compensatório de receptores beta durante o bloqueio crônico se manifesta como taquicardia de rebote quando o fármaco é retirado."},
{cat:"Endócrino", q:"Por que o uso de glicocorticoides em altas doses pode precipitar diabetes mellitus latente?", opts:["Corticoides não têm nenhuma relação com o metabolismo da glicose","Aumentam a resistência periférica à insulina e estimulam a gliconeogênese hepática, podendo desmascarar predisposição diabética", "Corticoides sempre reduzem a glicemia de forma perigosa","Não existe associação conhecida entre corticoterapia e diabetes"], correct:1, exp:"O efeito hiperglicemiante direto dos corticoides pode revelar uma tendência diabética subclínica que ainda não havia se manifestado clinicamente."},
{cat:"Toxicologia", q:"Por que a exposição a chumbo pode causar sinais neurológicos e gastrointestinais simultâneos em animais?", opts:["O chumbo é completamente inerte no organismo","Interfere na síntese do heme e tem efeito neurotóxico direto, causando sinais digestivos e neurológicos/comportamentais","Só afeta a pele e não tem ação sistêmica","O chumbo é rapidamente eliminado sem causar nenhum efeito"], correct:1, exp:"A intoxicação por chumbo deve ser um diagnóstico diferencial em quadros neurológicos e gastrointestinais inexplicados, especialmente com histórico de exposição a materiais antigos contendo o metal."},
{cat:"Reprodução", q:"Por que o uso prolongado de progestágenos sintéticos para supressão de cio é hoje menos recomendado?", opts:["Porque nunca tiveram nenhum efeito prático","Estão associados a riscos como piometra e alterações mamárias (incluindo tumores) com uso prolongado","Porque não existe alternativa disponível","Progestágenos não têm nenhuma ação hormonal real"], correct:1, exp:"Os riscos reprodutivos e neoplásicos conhecidos levaram a uma preferência por alternativas mais seguras de controle reprodutivo a longo prazo."},
{cat:"Antiparasitários", q:"Por que a seleção de antiparasitários em fêmeas gestantes ou lactantes exige atenção especial?", opts:["Porque nenhum antiparasitário pode ser usado nessas fases","Alguns princípios ativos podem atravessar a placenta ou ser excretados no leite, exigindo produtos com segurança estabelecida para essas fases","Porque a gestação elimina a necessidade de controle parasitário","Não há nenhuma diferença de manejo nessas fases fisiológicas"], correct:1, exp:"A escolha do antiparasitário nessas fases deve considerar dados de segurança específicos, já que a exposição fetal ou pelo leite pode ter consequências diferentes da exposição em animais adultos não gestantes."},
{cat:"Gastrointestinal", q:"Por que a cisaprida teve seu uso restrito apesar de ser um procinético eficaz?", opts:["Porque nunca teve eficácia comprovada","Está associada a risco de arritmias cardíacas graves, levando à restrição de sua disponibilidade comercial em várias regiões","Porque é extremamente cara em comparação a outros procinéticos","Porque não tem nenhum efeito sobre a motilidade intestinal"], correct:1, exp:"O risco cardíaco identificado em humanos levou à retirada da cisaprida do mercado em várias regiões, restringindo também seu uso e disponibilidade em medicina veterinária."},
{cat:"Dermatológicos", q:"Por que xampus com ácido salicílico são indicados em dermatoses com hiperqueratose?", opts:["Porque têm ação antibiótica potente","Têm efeito queratolítico, ajudando a remover o excesso de células córneas e escamas da pele","Porque bloqueiam receptores de histamina cutâneos","Porque eliminam a necessidade de diagnóstico dermatológico prévio"], correct:1, exp:"O efeito queratolítico ajuda a normalizar a descamação cutânea excessiva, atuando como coadjuvante no manejo de dermatoses hiperqueratósicas."},
{cat:"Imunobiológicos", q:"Por que a titulação de anticorpos pode ser usada para individualizar protocolos de reforço vacinal?", opts:["Porque substitui totalmente a necessidade de vacinação em qualquer situação","Pode indicar se o animal ainda possui níveis protetores de anticorpos contra determinado agente, ajudando a decidir sobre a necessidade de reforço","Porque não tem nenhuma relação com proteção imunológica","Porque é exigida por lei em todos os protocolos vacinais"], correct:1, exp:"A titulação sorológica complementa (sem substituir totalmente) o julgamento clínico sobre a necessidade de reforços vacinais para agentes com testes validados disponíveis."},
{cat:"Interações", q:"Por que associar IECA com AINEs exige cautela redobrada em pacientes com função renal já comprometida?", opts:["Não há nenhuma interação relevante entre essas classes","Ambos podem reduzir a perfusão renal por mecanismos distintos, e a combinação aumenta o risco de lesão renal aguda","AINEs sempre potencializam de forma benéfica o efeito dos IECA","IECA sempre neutralizam completamente os efeitos adversos dos AINEs"], correct:1, exp:"AINEs reduzem prostaglandinas vasodilatadoras renais, e IECA reduzem angiotensina II (que ajuda a manter a pressão de filtração); juntos, podem comprometer duplamente a hemodinâmica renal."},
{cat:"Cardiovascular", q:"Por que a lidocaína é usada como antiarrítmico especificamente em arritmias ventriculares?", opts:["Porque bloqueia receptores beta-adrenérgicos cardíacos","Bloqueia canais de sódio, reduzindo a excitabilidade do tecido cardíaco ventricular sem grande efeito sobre o tecido atrial","Porque estimula diretamente o nó sinusal","Porque é um diurético de ação cardíaca"], correct:1, exp:"A seletividade relativa da lidocaína pelo tecido ventricular despolarizado a torna útil especificamente para o controle de arritmias ventriculares, com menor efeito sobre o tecido atrial normal."},
{cat:"Antiparasitários", q:"Qual é o mecanismo de ação dos piretroides (ex: permetrina) sobre os parasitas?", opts:["Bloqueiam a síntese de proteínas do parasita","Atuam em canais de sódio dependentes de voltagem dos neurônios do parasita, prolongando sua abertura e causando hiperexcitação e paralisia","Rompem diretamente a cutícula do parasita por ação osmótica","Inibem a fotossíntese do parasita"], correct:1, exp:"A prolongação da abertura dos canais de sódio causa despolarização contínua dos neurônios do parasita, levando a hiperexcitação, paralisia e morte."},
{cat:"AINEs", q:"Por que a associação de dois AINEs diferentes ao mesmo tempo é contraindicada?", opts:["Porque neutralizam completamente um ao outro sem risco","Aumenta significativamente o risco de efeitos adversos gastrointestinais e renais, sem benefício analgésico adicional comprovado","Porque um AINE sempre potencializa a segurança do outro","Não há nenhum risco em combinar AINEs diferentes"], correct:1, exp:"Como atuam por mecanismos semelhantes (inibição da COX), associar dois AINEs simplesmente soma os riscos de toxicidade gastrointestinal e renal, sem ganho terapêutico proporcional."},
{cat:"Corticoides", q:"Por que a troca entre diferentes corticoides exige conversão cuidadosa de dose equivalente?", opts:["Porque todos os corticoides têm exatamente a mesma potência","Diferentes corticoides têm potências anti-inflamatórias e durações de ação distintas, exigindo ajuste de dose para manter o efeito clínico equivalente","Porque a troca de corticoide nunca é necessária na prática clínica","Porque apenas a via de administração importa, não a potência"], correct:1, exp:"Sem o ajuste de dose equivalente, a troca entre corticoides de potências diferentes (ex: prednisolona para dexametasona) pode resultar em sub ou superdosagem clínica."}
];

/* Embaralha as alternativas de cada questão para a resposta certa não ficar sempre na mesma letra */
quiz.forEach(item => {
  const correctText = item.opts[item.correct];
  for(let i = item.opts.length - 1; i > 0; i--){
    const j = Math.floor(Math.random() * (i+1));
    [item.opts[i], item.opts[j]] = [item.opts[j], item.opts[i]];
  }
  item.correct = item.opts.indexOf(correctText);
});
let fState = flashcards.map(() => ({status:null})); // null | 'know' | 'review'
let fIndex = 0;
let currentCat = "Todas";
let searchTerm = "";
let onlyReview = false;
let fOrder = flashcards.map((_,i)=>i);

let qIndex = 0;
let answers = new Array(quiz.length).fill(null);
let quizCatFilter = "Todas";
let qOrder = quiz.map((_,i)=>i);

/* ================= HEADER STATS ================= */
function renderHeaderStats(){
  const knownCount = fState.filter(s=>s.status==='know').length;
  const reviewCount = fState.filter(s=>s.status==='review').length;
  const answeredCount = answers.filter(a=>a!==null).length;
  const correctCount = answers.filter((a,i)=>a===quiz[i].correct).length;
  document.getElementById('headerStats').innerHTML = `
    <div class="stat-chip"><span class="dot"></span><b>${flashcards.length}</b><span class="lbl">flashcards</span></div>
    <div class="stat-chip"><span class="dot"></span><b>${quiz.length}</b><span class="lbl">questões</span></div>
    <div class="stat-chip"><span class="dot"></span><b>${knownCount}</b><span class="lbl">já sei</span></div>
    <div class="stat-chip"><span class="dot"></span><b>${reviewCount}</b><span class="lbl">p/ revisar</span></div>
    <div class="stat-chip"><span class="dot"></span><b>${answeredCount ? Math.round(100*correctCount/answeredCount)+'%' : '—'}</b><span class="lbl">acerto no quiz</span></div>
  `;
}

/* ================= FLASHCARDS ================= */
const catList = [...new Set(flashcards.map(c => c.cat))];

function renderCatPills(){
  const wrap = document.getElementById('catPills');
  wrap.innerHTML = '';
  const all = document.createElement('button');
  all.className = 'pill' + (currentCat === 'Todas' ? ' active' : '');
  all.textContent = `Todas (${flashcards.length})`;
  all.onclick = () => { currentCat = 'Todas'; fIndex = 0; buildOrder(); renderCard(); renderCatPills(); };
  wrap.appendChild(all);
  catList.forEach(cat => {
    const count = flashcards.filter(c => c.cat === cat).length;
    const btn = document.createElement('button');
    btn.className = 'pill' + (currentCat === cat ? ' active' : '');
    btn.textContent = `${cat} (${count})`;
    btn.onclick = () => { currentCat = cat; fIndex = 0; buildOrder(); renderCard(); renderCatPills(); };
    wrap.appendChild(btn);
  });
}

function buildOrder(){
  let idxs = flashcards.map((_,i)=>i);
  if(currentCat !== 'Todas') idxs = idxs.filter(i => flashcards[i].cat === currentCat);
  if(searchTerm.trim()){
    const t = searchTerm.trim().toLowerCase();
    idxs = idxs.filter(i => flashcards[i].q.toLowerCase().includes(t) || flashcards[i].a.toLowerCase().includes(t) || flashcards[i].cat.toLowerCase().includes(t));
  }
  if(onlyReview){
    idxs = idxs.filter(i => fState[i].status === 'review');
  }
  fOrder = idxs;
  fIndex = 0;
}

function shuffleOrder(){
  for(let i = fOrder.length - 1; i > 0; i--){
    const j = Math.floor(Math.random() * (i+1));
    [fOrder[i], fOrder[j]] = [fOrder[j], fOrder[i]];
  }
  fIndex = 0;
  renderCard();
}

function renderCard(){
  const wrap = document.getElementById('card');
  if(fOrder.length === 0){
    document.getElementById('deckCount').textContent = 'Nenhuma carta encontrada';
    document.getElementById('progressText').textContent = '';
    document.getElementById('frontText').textContent = 'Ajuste os filtros ou a busca.';
    document.getElementById('backText').textContent = '';
    return;
  }
  fIndex = ((fIndex % fOrder.length) + fOrder.length) % fOrder.length;
  const realIdx = fOrder[fIndex];
  const c = flashcards[realIdx];
  document.getElementById('frontText').textContent = c.q;
  document.getElementById('backText').textContent = c.a;
  document.getElementById('frontTag').textContent = c.cat + " — Pergunta";
  document.getElementById('backTag').textContent = c.cat + " — Resposta";
  document.getElementById('deckCount').textContent = `Carta ${fIndex+1} de ${fOrder.length}`;
  document.getElementById('progressText').textContent = `${fIndex+1} / ${fOrder.length}`;
  wrap.classList.remove('flipped');

  const status = fState[realIdx].status;
  document.getElementById('btnKnow').classList.toggle('marked', status === 'know');
  document.getElementById('btnReview').classList.toggle('marked', status === 'review');
  renderHeaderStats();
}

document.getElementById('card').addEventListener('click', () => {
  document.getElementById('card').classList.toggle('flipped');
});
document.getElementById('nextBtn').addEventListener('click', () => { fIndex++; renderCard(); });
document.getElementById('prevBtn').addEventListener('click', () => { fIndex--; renderCard(); });
document.getElementById('shuffleBtn').addEventListener('click', shuffleOrder);
document.getElementById('searchBox').addEventListener('input', (e) => { searchTerm = e.target.value; buildOrder(); renderCard(); });
document.getElementById('onlyReview').addEventListener('change', (e) => { onlyReview = e.target.checked; buildOrder(); renderCard(); });

document.getElementById('btnKnow').addEventListener('click', () => {
  const realIdx = fOrder[fIndex];
  fState[realIdx].status = fState[realIdx].status === 'know' ? null : 'know';
  renderCard();
});
document.getElementById('btnReview').addEventListener('click', () => {
  const realIdx = fOrder[fIndex];
  fState[realIdx].status = fState[realIdx].status === 'review' ? null : 'review';
  renderCard();
});

renderCatPills();
buildOrder();
renderCard();

/* ================= QUIZ ================= */
const quizCats = ["Todas", ...new Set(quiz.map(q => q.cat))];
const quizCatSelect = document.getElementById('quizCat');
quizCats.forEach(c => {
  const opt = document.createElement('option');
  opt.value = c;
  const count = c === 'Todas' ? quiz.length : quiz.filter(q=>q.cat===c).length;
  opt.textContent = `${c} (${count})`;
  quizCatSelect.appendChild(opt);
});

function buildQuizOrder(){
  let idxs = quiz.map((_,i)=>i);
  if(quizCatFilter !== 'Todas') idxs = idxs.filter(i => quiz[i].cat === quizCatFilter);
  qOrder = idxs;
  qIndex = 0;
}

function renderQuiz(){
  if(qOrder.length === 0){
    document.getElementById('quizText').textContent = 'Nenhuma questão nessa categoria.';
    document.getElementById('quizOptions').innerHTML = '';
    document.getElementById('quizExplain').classList.remove('show');
    return;
  }
  qIndex = ((qIndex % qOrder.length) + qOrder.length) % qOrder.length;
  const realIdx = qOrder[qIndex];
  const item = quiz[realIdx];
  document.getElementById('quizTag').textContent = item.cat;
  document.getElementById('quizText').textContent = item.q;
  document.getElementById('quizProgress').textContent = `Questão ${qIndex+1} de ${qOrder.length}`;

  const optsWrap = document.getElementById('quizOptions');
  optsWrap.innerHTML = '';
  const letters = ['A','B','C','D'];

  item.opts.forEach((optText, i) => {
    const btn = document.createElement('button');
    btn.className = 'opt';
    btn.innerHTML = `<span class="letter">${letters[i]}</span><span>${optText}</span>`;
    const chosen = answers[realIdx];
    if(chosen !== null && chosen !== undefined){
      btn.disabled = true;
      if(i === item.correct) btn.classList.add('correct');
      else if(i === chosen) btn.classList.add('wrong');
    }
    btn.addEventListener('click', () => {
      if(answers[realIdx] !== null && answers[realIdx] !== undefined) return;
      answers[realIdx] = i;
      renderQuiz();
      renderHeaderStats();
    });
    optsWrap.appendChild(btn);
  });

  const explainBox = document.getElementById('quizExplain');
  const chosen = answers[realIdx];
  if(chosen !== null && chosen !== undefined){
    explainBox.classList.add('show');
    const correctLabel = letters[item.correct];
    explainBox.innerHTML = `<b>Resposta correta: ${correctLabel}.</b> ${item.exp}`;
  } else {
    explainBox.classList.remove('show');
    explainBox.innerHTML = '';
  }

  const subset = qOrder;
  const acertos = subset.filter(i => answers[i] === quiz[i].correct).length;
  const respondidas = subset.filter(i => answers[i] !== null && answers[i] !== undefined).length;
  document.getElementById('quizScore').textContent = `Acertos: ${acertos} / ${respondidas}`;
}

document.getElementById('quizNext').addEventListener('click', () => { qIndex++; renderQuiz(); });
document.getElementById('quizPrev').addEventListener('click', () => { qIndex--; renderQuiz(); });
document.getElementById('quizShuffle').addEventListener('click', () => {
  for(let i = qOrder.length - 1; i > 0; i--){
    const j = Math.floor(Math.random() * (i+1));
    [qOrder[i], qOrder[j]] = [qOrder[j], qOrder[i]];
  }
  qIndex = 0; renderQuiz();
});
quizCatSelect.addEventListener('change', (e) => { quizCatFilter = e.target.value; buildQuizOrder(); renderQuiz(); });
document.getElementById('quizReset').addEventListener('click', () => {
  answers = new Array(quiz.length).fill(null);
  qIndex = 0; renderQuiz(); renderHeaderStats(); renderStats();
});

buildQuizOrder();
renderQuiz();

/* ================= STATS PANEL ================= */
function renderStats(){
  const totalCards = flashcards.length;
  const known = fState.filter(s=>s.status==='know').length;
  const review = fState.filter(s=>s.status==='review').length;
  const answered = answers.filter(a=>a!==null && a!==undefined).length;
  const correct = answers.filter((a,i)=> a === quiz[i].correct).length;

  document.getElementById('statGrid').innerHTML = `
    <div class="stat-box"><div class="num">${totalCards}</div><div class="lbl">Total de flashcards</div></div>
    <div class="stat-box"><div class="num">${known}</div><div class="lbl">Marcadas "já sei"</div></div>
    <div class="stat-box"><div class="num">${review}</div><div class="lbl">Marcadas p/ revisar</div></div>
    <div class="stat-box"><div class="num">${answered ? Math.round(100*correct/answered)+'%' : '—'}</div><div class="lbl">Acerto no quiz (${correct}/${answered})</div></div>
  `;

  const cats = [...new Set(quiz.map(q=>q.cat))];
  const barsWrap = document.getElementById('catBars');
  barsWrap.innerHTML = '';
  cats.forEach(cat => {
    const idxs = quiz.map((q,i)=>i).filter(i => quiz[i].cat === cat);
    const ans = idxs.filter(i => answers[i] !== null && answers[i] !== undefined);
    const correctN = idxs.filter(i => answers[i] === quiz[i].correct).length;
    const pct = ans.length ? Math.round(100*correctN/ans.length) : 0;
    const row = document.createElement('div');
    row.className = 'cat-bar-row';
    row.innerHTML = `
      <span class="name">${cat}</span>
      <div class="cat-bar-track"><div class="cat-bar-fill" style="width:${ans.length ? pct : 0}%"></div></div>
      <span class="cat-bar-pct">${ans.length ? pct+'%' : '—'}</span>
    `;
    barsWrap.appendChild(row);
  });
}

/* ================= TABS ================= */
function moveHighlight(tab){
  const highlight = document.getElementById('tabHighlight');
  const nav = document.getElementById('tabsNav');
  const navRect = nav.getBoundingClientRect();
  const tabRect = tab.getBoundingClientRect();
  highlight.style.width = tabRect.width + 'px';
  highlight.style.transform = `translateX(${tabRect.left - navRect.left - 5}px)`;
}

document.querySelectorAll('.tab').forEach(tab => {
  tab.addEventListener('click', () => {
    document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
    document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
    tab.classList.add('active');
    document.getElementById(tab.dataset.panel).classList.add('active');
    moveHighlight(tab);
    if(tab.dataset.panel === 'stats') renderStats();
  });
});

window.addEventListener('resize', () => {
  const active = document.querySelector('.tab.active');
  if(active) moveHighlight(active);
});

renderHeaderStats();
requestAnimationFrame(() => moveHighlight(document.querySelector('.tab.active')));
</script>
</body>
</html>
