<!doctype html>
<html lang="fr">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Slot Ultimate v42 — Deluxe</title>
<style>
:root{
  --bg:#071026; --card:#0d1730; --accent:#ffce00; --muted:#9aa7c0;
  --reel-bg:linear-gradient(180deg,#081827,#03101a);
  --symbol-bg:linear-gradient(180deg,rgba(255,255,255,.02),rgba(255,255,255,.01));
  --glow: rgba(255,206,0,0.08);
  --win-glow: rgba(31,208,122,0.22);
}
body.theme-classic{--bg:#071026;--card:#0d1730;--accent:#ffce00;--muted:#9aa7c0;--reel-bg:linear-gradient(180deg,#081827,#03101a);--symbol-bg:linear-gradient(180deg,rgba(255,255,255,.02),rgba(255,255,255,.01));--glow: rgba(255,206,0,0.08);--win-glow: rgba(31,208,122,0.22);}
body.theme-neon{--bg:#02040f;--card:#041025;--accent:#39ff14;--muted:#a0fffc;--reel-bg:linear-gradient(180deg,#040c2a,#01111b);--symbol-bg:linear-gradient(180deg,rgba(57,255,20,.05),rgba(57,255,20,.02));--glow: rgba(57,255,20,0.12);--win-glow: rgba(57,255,20,0.3);}
body.theme-gold{--bg:#1b1000;--card:#3d2205;--accent:#ffd700;--muted:#f8d28c;--reel-bg:linear-gradient(180deg,#3d2205,#1b1000);--symbol-bg:linear-gradient(180deg,rgba(255,215,0,.05),rgba(255,215,0,.02));--glow: rgba(255,215,0,0.12);--win-glow: rgba(255,215,0,0.3);}
*{box-sizing:border-box;font-family:Inter,Segoe UI,Roboto,Arial,sans-serif}
html,body{height:100%;margin:0;background:var(--bg);color:#eaf2ff}
.container{width:100%;max-width:1100px;margin:20px auto;border-radius:14px;padding:18px;background:linear-gradient(180deg,#08142a,#041025);box-shadow:0 28px 80px rgba(2,6,23,.75);position:relative}
.header-row{display:flex;justify-content:space-between;align-items:center;gap:12px}
h1{font-size:18px;margin:0}
.top-controls{display:flex;gap:8px;align-items:center}
.balance{font-weight:800;color:var(--accent)}
.btn{background:transparent;border:1px solid rgba(255,255,255,.06);padding:8px;border-radius:8px;color:var(--muted);cursor:pointer}
.btn.primary{background:linear-gradient(180deg,var(--accent),#f8b400);border:none;color:#061018;font-weight:800;transition:transform .12s}
.btn.primary:active{transform:scale(.96)}
.status-row{display:flex;gap:12px;align-items:center}
.bank-display{display:flex;gap:10px;align-items:center;font-weight:900}
.machine{background:linear-gradient(180deg,#071a32,#041224);padding:18px;border-radius:12px;margin-top:12px;position:relative;overflow:hidden}
.reels{display:flex;gap:12px;justify-content:center;padding:6px;align-items:center}
.reel-wrap{width:120px;height:220px;background:var(--reel-bg);border-radius:12px;padding:6px;display:flex;align-items:center;justify-content:center;position:relative;overflow:hidden;border:2px solid rgba(255,255,255,.02)}
.reel{width:100%;height:100%;position:relative;overflow:hidden}
.tape{position:absolute;left:0;right:0;top:0;display:flex;flex-direction:column;align-items:center;gap:10px;transition:transform 900ms cubic-bezier(.2,.9,.2,1)}
.symbol{width:92px;height:64px;border-radius:10px;background:var(--symbol-bg);display:flex;align-items:center;justify-content:center;font-size:36px;font-weight:900;color:#fff;user-select:none;box-shadow:none;transition:box-shadow .18s, transform .18s}
.symbol.win{box-shadow:0 18px 50px var(--win-glow); transform:scale(1.08)}
.controls{display:flex;justify-content:space-between;align-items:center;margin-top:12px}
.left-controls{display:flex;gap:8px;align-items:center}
.spin-btn{padding:12px 18px;border-radius:12px;min-width:160px;cursor:pointer;display:inline-flex;align-items:center;gap:10px;justify-content:center;transition:transform .12s}
.spin-btn.push{transform:translateY(3px) scale(.98)}
.info{margin-top:10px;color:var(--muted);font-size:13px;display:flex;justify-content:space-between}
.jackpot{color:var(--accent);font-weight:900;text-align:center;margin-top:8px}
#center-win{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);font-size:36px;font-weight:900;color:var(--accent);pointer-events:none;opacity:0;transition:opacity 0.25s, transform .25s;}
.center-pop{transform:translate(-50%,-60%) scale(1.08)}
.progress-wrap{margin-top:12px}
.progress-bar{height:14px;background:rgba(255,255,255,.06);border-radius:8px;overflow:hidden;position:relative}
.progress-fill{height:100%;width:0;background:linear-gradient(90deg,var(--accent),#fff4aa);transition:width .3s}
.progress-text{font-size:13px;color:var(--muted);margin-top:6px;display:flex;justify-content:space-between}
.modal{position:fixed;left:0;top:0;right:0;bottom:0;display:none;align-items:center;justify-content:center;background:rgba(2,6,23,.6);z-index:999}
.modal-card{width:92%;max-width:760px;background:linear-gradient(180deg,#0b1220,#07101a);padding:18px;border-radius:12px;border:1px solid rgba(255,255,255,.04)}
.shop-grid{display:flex;gap:12px;flex-wrap:wrap}
.shop-card{width:calc(50% - 12px);background:#071426;padding:10px;border-radius:10px;color:#fff;display:flex;justify-content:space-between;align-items:center;cursor:pointer;border:1px solid transparent}
.shop-card.selected{border-color:var(--accent)}
.check-sq{width:28px;height:28px;border-radius:6px;border:2px solid rgba(255,255,255,.08);display:flex;align-items:center;justify-content:center}
#coins-canvas{position:fixed;left:0;top:0;width:100%;height:100%;pointer-events:none;z-index:500}
.gains-table{width:100%;border-collapse:collapse;margin-top:8px;color:var(--muted)}
.gains-table th,.gains-table td{padding:8px;border-bottom:1px solid rgba(255,255,255,.03);text-align:left}
.header-bank-actions{display:flex;gap:12px;align-items:center;margin-left:8px}
.badge{background:rgba(255,255,255,0.03);padding:6px 10px;border-radius:8px;font-weight:700}
.gameover-modal{display:flex;flex-direction:column;gap:12px;align-items:center;justify-content:center;text-align:center}
.small{font-size:13px;color:var(--muted)}
</style>
</head>
<body class="theme-classic">
  <div class="container">
    <div class="header-row">
      <div style="display:flex;align-items:center;gap:12px">
        <h1>🎰 Slot Ultimate v42</h1>
        <div class="top-controls">
          <div class="balance">💎 <span id="session-gems">1000</span></div>
          <div class="header-bank-actions">
            <button id="transfer-btn" class="btn">Transférer vers la banque</button>
            <div class="bank-display">💰 <span id="bank-amount">0</span></div>
          </div>
        </div>
      </div>

      <div style="display:flex;align-items:center;gap:8px">
        <div class="status-row small">
          <div>Niveau: <strong id="level">1</strong></div>
          <div>Tours restants: <strong id="turns-left">5</strong></div>
        </div>
        <div class="top-controls">
          <button id="options-btn" class="btn">⚙️</button>
          <button id="open-shop" class="btn">🏷️ Shop</button>
          <button id="gains-btn" class="btn">ℹ️ Gains</button>
          <button id="watch-ad" class="btn">📺 Regarder une pub +300</button>
        </div>
      </div>
    </div>

    <div class="machine" id="machine">
      <div class="reels" id="reels">
        <div class="reel-wrap"><div class="reel" data-index="0"><div class="tape"></div></div></div>
        <div class="reel-wrap"><div class="reel" data-index="1"><div class="tape"></div></div></div>
        <div class="reel-wrap"><div class="reel" data-index="2"><div class="tape"></div></div></div>
        <div class="reel-wrap"><div class="reel" data-index="3"><div class="tape"></div></div></div>
        <div class="reel-wrap"><div class="reel" data-index="4"><div class="tape"></div></div></div>
      </div>

      <div id="center-win"></div>

      <div class="controls">
        <div class="left-controls">
          <button id="spin" class="spin-btn primary">SPIN</button>
        </div>
        <div style="text-align:right">
          <div style="font-size:13px;color:var(--muted)">Dernier gain</div>
          <div id="last-win" style="font-weight:900">0</div>
        </div>
      </div>

      <div class="info">
        <div id="message">Bonne chance ! 🍀</div>
      </div>

      <div id="jackpot-msg" class="jackpot"></div>

      <div class="progress-wrap">
        <div class="progress-bar">
          <div id="progress-fill" class="progress-fill"></div>
        </div>
        <div class="progress-text">
          <div>Objectif: <strong id="objective">400</strong></div>
          <div>Progress: <strong id="progress-text">0</strong></div>
        </div>
      </div>

    </div>
  </div>

  <canvas id="coins-canvas" aria-hidden="true"></canvas>

  <!-- Options modal -->
  <div id="options-modal" class="modal"><div class="modal-card">
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px">
      <h2 style="margin:0">⚙️ Options</h2>
      <button id="close-options" class="btn">Fermer</button>
    </div>
    <div style="display:flex;gap:8px;align-items:center;margin-bottom:8px">
      <button id="toggle-sound" class="btn">🔊 Sons ON</button>
      <button id="reset-session" class="btn">Reset session (💎 → 0, cycle reset)</button>
      <button id="reset-all" class="btn">Reset everything (bank too)</button>
    </div>
    <div class="small">Reset session: resets the session gems & cycle.</div>
    <div class="small">Reset everything: resets session, bank, level/objective.</div>
  </div></div>

  <!-- Shop modal -->
  <div id="shop-modal" class="modal"><div class="modal-card">
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px">
      <h2 style="margin:0">🎨 Shop</h2>
      <button id="close-shop" class="btn">Fermer</button>
    </div>
    <div style="margin-bottom:12px;color:var(--muted)">Choisis un thème et un pack de symboles.</div>

    <div style="margin-bottom:12px"><strong>Thèmes</strong></div>
    <div class="shop-grid" id="theme-grid">
      <div class="shop-card" data-theme="classic"><div>Classique</div><div class="check-sq"></div></div>
      <div class="shop-card" data-theme="neon"><div>Neon</div><div class="check-sq"></div></div>
      <div class="shop-card" data-theme="gold"><div>Gold</div><div class="check-sq"></div></div>
    </div>

    <div style="margin-top:14px;margin-bottom:8px"><strong>Symbol Packs</strong></div>
    <div class="shop-grid" id="pack-grid">
      <div class="shop-card" data-pack="emoji"><div>Emoji Classic</div><div class="check-sq"></div></div>
      <div class="shop-card" data-pack="minimal"><div>Minimal SVG</div><div class="check-sq"></div></div>
    </div>
  </div></div>

  <!-- Gains modal -->
  <div id="gains-modal" class="modal"><div class="modal-card">
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px">
      <h2 style="margin:0">ℹ️ Tableau des gains</h2>
      <button id="close-gains" class="btn">Fermer</button>
    </div>

    <table class="gains-table" id="gains-table">
      <thead>
        <tr>
          <th>Symbole</th>
          <th>Nom</th>
          <th>3</th>
          <th>4</th>
          <th>5</th>
          <th>% Chance</th>
        </tr>
      </thead>
      <tbody id="gains-body"></tbody>
    </table>
  </div></div>

  <!-- Game Over modal -->
  <div id="gameover-modal" class="modal"><div class="modal-card gameover-modal" id="gameover-card">
    <h2 style="margin:0">💀 Game Over</h2>
    <div class="small" id="gameover-msg">You didn't reach the objective in time.</div>
    <div style="display:flex;gap:8px;margin-top:6px">
      <button id="replay-btn" class="btn primary">Rejouer</button>
      <button id="go-bank-btn" class="btn">Transférer vers la banque</button>
    </div>
  </div></div>

<script>
/* ============================
   Game state & persistent storage
   ============================ */
const REELS=5, ROWS=3, SPIN_COST=100;
let sessionGems = Number(localStorage.getItem('slot_v30_session')) || 1000; // 💎 (session)
let bank = Number(localStorage.getItem('slot_v30_bank')) || 0;            // 💰 (bank)
let selectedPack = localStorage.getItem('slot_v30_pack') || 'emoji';
let selectedTheme = localStorage.getItem('slot_v30_theme') || 'classic';
let soundOn = (localStorage.getItem('slot_v30_sound') !== '0');
let spinning = false;

// cycle / objective
let level = Number(localStorage.getItem('slot_v30_level')) || 1;
let objective = Number(localStorage.getItem('slot_v30_objective')) || 400;
let turnsLeft = Number(localStorage.getItem('slot_v30_turnsLeft')) || 5;
let cycleProgress = Number(localStorage.getItem('slot_v30_cycleProgress')) || 0;

/* ============================
   Symbols with weights
   ============================ */
const SYMBOLS = [
  {id:'cherry', icon:'🍒', name:'Cerise', base:0.5, color:'#ff3b30', weight:28},
  {id:'lemon',  icon:'🍋', name:'Citron', base:0.7, color:'#ffd60a', weight:22},
  {id:'orange', icon:'🍊', name:'Orange', base:0.6, color:'#ff9a00', weight:18},
  {id:'bell',   icon:'🔔', name:'Cloche', base:1,   color:'#ffd27a', weight:12},
  {id:'star',   icon:'⭐',  name:'Étoile', base:2,   color:'#ffd700', weight:8},
  {id:'diamond',icon:'💎', name:'Diamant', base:5,   color:'#00bfff', weight:6},
  {id:'seven',  icon:'7️⃣', name:'Seven',  base:10,  color:'#ff2d95', weight:6}
];

// Minimal SVG mapping: a solid color square per symbol (fixed mapping)
const MINIMAL_MAP = {
  cherry:  '#ff3b30', // rouge
  lemon:   '#ffd60a', // jaune
  orange:  '#ff9a00', // orange
  bell:    '#ffd27a', // doré clair
  star:    '#ffd700', // or
  diamond: '#00bfff', // bleu
  seven:   '#ff2d95'  // rose
};

const SYMBOL_PACKS = {
  emoji: SYMBOLS,
  minimal: SYMBOLS.map(s => ({...s, icon:'■'})) // icon placeholder; we paint with color instead
};

/* DOM references */
const sessionGemsEl = document.getElementById('session-gems');
const bankEl = document.getElementById('bank-amount');
const spinBtn = document.getElementById('spin');
const messageEl = document.getElementById('message');
const lastWinEl = document.getElementById('last-win');
const reelsEl = document.getElementById('reels');
const centerWinEl = document.getElementById('center-win');
const jackpotMsg = document.getElementById('jackpot-msg');
const optionsBtn = document.getElementById('options-btn');
const optionsModal = document.getElementById('options-modal');
const closeOptions = document.getElementById('close-options');
const toggleSoundBtn = document.getElementById('toggle-sound');
const resetSessionBtn = document.getElementById('reset-session');
const resetAllBtn = document.getElementById('reset-all');
const shopBtn = document.getElementById('open-shop');
const shopModal = document.getElementById('shop-modal');
const closeShop = document.getElementById('close-shop');
const themeGrid = document.getElementById('theme-grid');
const packGrid = document.getElementById('pack-grid');
const gainsBtn = document.getElementById('gains-btn');
const gainsModal = document.getElementById('gains-modal');
const closeGains = document.getElementById('close-gains');
const gainsBody = document.getElementById('gains-body');
const watchAdBtn = document.getElementById('watch-ad');
const coinsCanvas = document.getElementById('coins-canvas');
const transferBtn = document.getElementById('transfer-btn');
const levelEl = document.getElementById('level');
const turnsLeftEl = document.getElementById('turns-left');
const progressFill = document.getElementById('progress-fill');
const progressText = document.getElementById('progress-text');
const objectiveEl = document.getElementById('objective');
const gameoverModal = document.getElementById('gameover-modal');
const replayBtn = document.getElementById('replay-btn');
const goBankBtn = document.getElementById('go-bank-btn');

/* -------------------------
   Audio engine
   ------------------------- */
class AudioEngine {
  constructor(){
    try{
      this.ctx = new (window.AudioContext||window.webkitAudioContext)();
      this.master = this.ctx.createGain();
      this.master.gain.value = 0.9;
      this.master.connect(this.ctx.destination);
    }catch(e){ this.ctx = null; }
    this.tickInterval = null;
  }
  resume(){ if(this.ctx && this.ctx.state==='suspended') this.ctx.resume(); }
  playSpinStart(){ if(!this.ctx||!soundOn) return; const now=this.ctx.currentTime; const o=this.ctx.createOscillator(); o.type='sawtooth'; o.frequency.setValueAtTime(160,now); o.frequency.exponentialRampToValueAtTime(700,now+0.25); const g=this.ctx.createGain(); g.gain.setValueAtTime(0.02,now); o.connect(g); g.connect(this.master); o.start(now); o.stop(now+0.28); }
  startTicks(rateMs=120){ if(!this.ctx||!soundOn) return; this.stopTicks(); this.tickInterval=setInterval(()=>this._playTick(), rateMs); }
  _playTick(){ if(!this.ctx||!soundOn) return; const now=this.ctx.currentTime; const o=this.ctx.createOscillator(); o.type='square'; o.frequency.setValueAtTime(900,now); const g=this.ctx.createGain(); g.gain.setValueAtTime(0.02,now); o.connect(g); g.connect(this.master); o.start(now); o.stop(now+0.06); }
  stopTicks(){ if(this.tickInterval){ clearInterval(this.tickInterval); this.tickInterval=null; } }
  playWin(){ if(!this.ctx||!soundOn) return; const now=this.ctx.currentTime; [720,880,1040].forEach((f,i)=>{ const o=this.ctx.createOscillator(); o.type=(i%2)?'sine':'triangle'; o.frequency.setValueAtTime(f,now+i*0.06); const g=this.ctx.createGain(); g.gain.setValueAtTime(0.02,now+i*0.06); o.connect(g); g.connect(this.master); o.start(now+i*0.06); o.stop(now+i*0.06+0.36); }); }
  playJackpot(){ if(!this.ctx||!soundOn) return; const now=this.ctx.currentTime; [320,380,520,760,1100].forEach((f,i)=>{ const o=this.ctx.createOscillator(); o.type='sawtooth'; o.frequency.setValueAtTime(f,now+i*0.08); const g=this.ctx.createGain(); g.gain.setValueAtTime(0.02,now+i*0.08); o.connect(g); g.connect(this.master); o.start(now+i*0.08); o.stop(now+i*0.08+0.46); }); }
  muteAll(){ if(this.ctx) this.master.gain.value = 0; }
  unmuteAll(){ if(this.ctx) this.master.gain.value = 0.9; }
}
const audio = new AudioEngine(); audio.resume();

/* -------------------------
   Persistence helpers
   ------------------------- */
function saveState(){
  localStorage.setItem('slot_v30_session', String(sessionGems));
  localStorage.setItem('slot_v30_bank', String(bank));
  localStorage.setItem('slot_v30_pack', selectedPack);
  localStorage.setItem('slot_v30_theme', selectedTheme);
  localStorage.setItem('slot_v30_sound', soundOn?'1':'0');
  localStorage.setItem('slot_v30_level', String(level));
  localStorage.setItem('slot_v30_objective', String(objective));
  localStorage.setItem('slot_v30_turnsLeft', String(turnsLeft));
  localStorage.setItem('slot_v30_cycleProgress', String(cycleProgress));
}

/* -------------------------
   Weighted random symbol
   ------------------------- */
function randSymbol(){
  const list = SYMBOL_PACKS[selectedPack];
  const totalWeight = list.reduce((s,x)=>s+(x.weight||1),0);
  let r = Math.random()*totalWeight;
  for(const s of list){
    const w = s.weight||1;
    if(r < w) return s;
    r -= w;
  }
  return list[0];
}

/* -------------------------
   UI update
   ------------------------- */
function updateUI(){
  sessionGemsEl.textContent = Math.floor(sessionGems);
  bankEl.textContent = Math.floor(bank);
  levelEl.textContent = level;
  turnsLeftEl.textContent = turnsLeft;
  objectiveEl.textContent = objective;
  progressText.textContent = `${cycleProgress}/${objective}`;
  const pct = Math.min(100, Math.round((cycleProgress/objective)*100));
  progressFill.style.width = pct + '%';
  // sound button text
  toggleSoundBtn.textContent = soundOn ? '🔊 Sons ON' : '🔇 Sons OFF';
}
updateUI();

/* -------------------------
   Helper: build a symbol div according to current pack
   ------------------------- */
function buildSymbolDiv(sym){
  const div = document.createElement('div');
  div.className = 'symbol';
  div.dataset.id = sym.id;
  if(selectedPack === 'minimal'){
    // Colored square – map color by symbol id
    const col = MINIMAL_MAP[sym.id] || '#888';
    div.textContent = ''; // no glyph
    div.style.background = col;
    div.style.color = '#061018';
    div.setAttribute('aria-label', sym.name);
  }else{
    div.textContent = sym.icon;
    div.style.background = '';
    div.style.color = '';
  }
  return div;
}

/* -------------------------
   Reels init
   ------------------------- */
function initReels(){
  document.querySelectorAll('.reel').forEach(r=>{
    const tape = r.querySelector('.tape');
    tape.style.transition = '';
    tape.innerHTML = '';
    for(let i=0;i<40;i++){
      const sym = randSymbol();
      const div = buildSymbolDiv(sym);
      tape.appendChild(div);
    }
  });
}

/* -------------------------
   Animate single reel
   ------------------------- */
function animateReel(reelEl, steps, duration){
  return new Promise(resolve=>{
    const tape = reelEl.querySelector('.tape');
    const symEl = tape.querySelector('.symbol');
    const symbolHeight = symEl ? (symEl.offsetHeight + parseFloat(getComputedStyle(tape).gap || 0)) : 74;
    tape.style.transition = `transform ${duration}ms cubic-bezier(.2,.9,.2,1)`;
    const shift = steps * symbolHeight;
    requestAnimationFrame(()=>{ tape.style.transform = `translateY(-${shift}px)`; });
    const onEnd = ()=>{
      tape.removeEventListener('transitionend', onEnd);
      for(let i=0;i<steps;i++){
        const first = tape.firstElementChild;
        if(first) tape.removeChild(first);
        const ns = randSymbol();
        const div = buildSymbolDiv(ns);
        tape.appendChild(div);
      }
      tape.style.transition = 'none';
      tape.style.transform = 'translateY(0)';
      void tape.offsetWidth;
      setTimeout(()=>{ tape.style.transition = ''; resolve(); }, 10);
    };
    tape.addEventListener('transitionend', onEnd);
  });
}

/* -------------------------
   Visible grid extraction
   ------------------------- */
function getVisibleGrid(){
  const grid=[];
  const reels = document.querySelectorAll('.reel');
  for(let r=0;r<ROWS;r++){
    const row=[];
    reels.forEach(reel=>{
      const sym = reel.querySelectorAll('.symbol')[r];
      row.push({id: sym.dataset.id, el: sym});
    });
    grid.push(row);
  }
  return grid;
}

/* -------------------------
   Compute winning lines
   ------------------------- */
function computeWinningLines(grid, bet){
  const lines = [];
  function addLine(coords){
    if(coords.length < 3) return;
    const symId = grid[coords[0].r][coords[0].c].id;
    const symData = SYMBOLS.find(s=>s.id===symId);
    let mult = coords.length===3 ? 1 : coords.length===4 ? 2 : 5;
    const win = Math.round(bet * symData.base * mult);
    lines.push({coords, win, symId});
  }

  // horizontal
  for(let r=0;r<ROWS;r++){
    let start = 0;
    for(let c=1;c<=REELS;c++){
      if(c < REELS && grid[r][c].id === grid[r][start].id) continue;
      const len = c - start;
      if(len >= 3){
        const seq = [];
        for(let k=start;k<c;k++) seq.push({r, c:k});
        addLine(seq);
      }
      start = c;
    }
  }

  // vertical
  for(let c=0;c<REELS;c++){
    let start = 0;
    for(let r=1;r<=ROWS;r++){
      if(r < ROWS && grid[r][c].id === grid[start][c].id) continue;
      const len = r - start;
      if(len >= 3){
        const seq = [];
        for(let k=start;k<r;k++) seq.push({r:k, c});
        addLine(seq);
      }
      start = r;
    }
  }

  // diag TL->BR
  for(let r=0;r<=ROWS-3;r++){
    for(let c=0;c<=REELS-3;c++){
      const a = grid[r][c].id;
      let seq = [{r,c}];
      let k=1;
      while(r+k<ROWS && c+k<REELS && grid[r+k][c+k].id===a){ seq.push({r:r+k, c:c+k}); k++; }
      if(seq.length>=3) addLine(seq);
    }
  }

  // diag TR->BL
  for(let r=0;r<=ROWS-3;r++){
    for(let c=2;c<REELS;c++){
      const a = grid[r][c].id;
      let seq = [{r,c}];
      let k=1;
      while(r+k<ROWS && c-k>=0 && grid[r+k][c-k].id===a){ seq.push({r:r+k, c:c-k}); k++; }
      if(seq.length>=3) addLine(seq);
    }
  }

  // jackpot check
  const firstId = grid[0][0].id;
  const jackpot = grid.flat().every(s => s.id === firstId);

  const totalWin = lines.reduce((s,l)=>s+l.win, 0);
  return { totalWin, lines, jackpot };
}

/* -------------------------
   Center gain & highlight
   ------------------------- */
function showCenterAccum(newAccum){
  centerWinEl.textContent = `+${newAccum}`;
  centerWinEl.style.opacity = 1;
  centerWinEl.classList.add('center-pop');
  clearTimeout(centerWinEl._hideTimeout);
  centerWinEl._hideTimeout = setTimeout(()=>{
    centerWinEl.classList.remove('center-pop');
    centerWinEl.style.opacity = 0;
  }, 700);
}

function highlightLine(line){
  return new Promise(resolve=>{
    line.coords.forEach(p=>{
      const sym = document.querySelectorAll('.reel')[p.c].querySelectorAll('.symbol')[p.r];
      if(sym) sym.classList.add('win');
    });
    spawnCoins(line.win);
    setTimeout(()=>{
      line.coords.forEach(p=>{
        const sym = document.querySelectorAll('.reel')[p.c].querySelectorAll('.symbol')[p.r];
        if(sym) sym.classList.remove('win');
      });
      resolve();
    }, 600);
  });
}

/* -------------------------
   Confetti / coins
   ------------------------- */
function spawnCoins(amount){
  const canvas = coinsCanvas;
  const ctx = canvas.getContext('2d');
  canvas.width = innerWidth;
  canvas.height = innerHeight;
  const count = Math.min(120, Math.round(Math.max(12, amount/2)));
  const pieces = [];
  for(let i=0;i<count;i++){
    pieces.push({
      x: Math.random()*canvas.width,
      y: -20 - Math.random()*200,
      vy: 2 + Math.random()*6,
      r: 4 + Math.random()*8,
      color: `hsl(${Math.random()*360},70%,60%)`,
      rot: Math.random()*360,
      vr: (Math.random()-0.5)*6
    });
  }
  let frames = 0;
  function frame(){
    ctx.clearRect(0,0,canvas.width,canvas.height);
    pieces.forEach(p=>{
      ctx.save();
      ctx.translate(p.x,p.y);
      ctx.rotate(p.rot*Math.PI/180);
      ctx.fillStyle = p.color;
      ctx.beginPath();
      ctx.ellipse(0,0,p.r,p.r*0.7,0,0,Math.PI*2);
      ctx.fill();
      ctx.restore();
      p.y += p.vy;
      p.rot += p.vr;
    });
    frames++;
    if(frames < 120) requestAnimationFrame(frame);
    else ctx.clearRect(0,0,canvas.width,canvas.height);
  }
  frame();
}

/* -------------------------
   Spin logic
   ------------------------- */
async function spinAll(){
  if(spinning) return;
  if(sessionGems < SPIN_COST){ messageEl.textContent = 'Solde de partie insuffisant pour SPIN (💎).'; return; }
  if(gameoverModal.style.display === 'flex') return;

  spinning = true;
  spinBtn.disabled = true;

  sessionGems -= SPIN_COST;
  updateUI();
  lastWinEl.textContent = '0';
  jackpotMsg.textContent = '';
  messageEl.textContent = 'Spinning...';
  centerWinEl.style.opacity = 0;
  centerWinEl.dataset.accum = 0;

  spinBtn.classList.add('push');
  setTimeout(()=>spinBtn.classList.remove('push'), 140);

  audio.playSpinStart();
  audio.startTicks(110);

  const final = Array.from({length:REELS}, ()=> Array(ROWS).fill(null));
  for(let c=0;c<REELS;c++){
    for(let r=0;r<ROWS;r++){
      final[c][r] = randSymbol();
    }
  }

  const reelEls = Array.from(document.querySelectorAll('.reel'));
  const promises = reelEls.map((reelEl, idx)=>{
    const tape = reelEl.querySelector('.tape');
    for(let i=final[idx].length-1;i>=0;i--){
      const ns = final[idx][i];
      const div = buildSymbolDiv(ns);
      tape.insertBefore(div, tape.firstChild);
    }
    const steps = 8 + Math.floor(Math.random()*14) + idx*4;
    const baseDuration = 700 + idx*190 + Math.floor(Math.random()*220);
    return animateReel(reelEl, steps, baseDuration);
  });

  await Promise.all(promises);
  audio.stopTicks();

  const grid = getVisibleGrid();
  const { totalWin, lines, jackpot } = computeWinningLines(grid, SPIN_COST);

  let cumulativeThisSpin = 0;
  for(const line of lines){
    sessionGems += line.win;
    cycleProgress += line.win;
    cumulativeThisSpin += line.win;
    showCenterAccum(Number(centerWinEl.dataset.accum || 0) + line.win);
    centerWinEl.dataset.accum = Number(centerWinEl.dataset.accum || 0) + line.win;
    updateUI();
    audio.playWin();
    await highlightLine(line);
    await new Promise(res => setTimeout(res, 180));
  }

  if(lines.length === 0){
    await new Promise(res => setTimeout(res, 120));
  }

  if(jackpot) {
    audio.playJackpot();
    jackpotMsg.textContent = '🎉 JACKPOT ! 🎉';
  } else {
    jackpotMsg.textContent = '';
  }

  lastWinEl.textContent = cumulativeThisSpin;
  messageEl.textContent = cumulativeThisSpin > 0 ? `Tu gagnes ${cumulativeThisSpin} crédits 🎉` : 'Aucun gain.';

  turnsLeft = Math.max(0, turnsLeft - 1);

  if(cycleProgress >= objective){
    level += 1;
    objective = objective * 2;
    cycleProgress = 0;
    turnsLeft = 5;
    messageEl.textContent = `Objectif atteint ! Niveau ${level} 🔥 Objectif suivant : ${objective}`;
    audio.playJackpot();
  } else if(turnsLeft <= 0 && cycleProgress < objective){
    onGameOver();
  }

  updateUI();
  saveState();
  spinning = false;
  spinBtn.disabled = false;
}

/* -------------------------
   Game Over handling
   ------------------------- */
function onGameOver(){
  audio.stopTicks();
  audio.muteAll();
  // reset level & cycle immediately on game over (as requested)
  level = 1;
  objective = 400;
  turnsLeft = 5;
  cycleProgress = 0;
  saveState();
  updateUI();
  gameoverModal.style.display = 'flex';
  spinBtn.disabled = true;
  messageEl.textContent = 'Game Over — you failed to reach the objective';
}

/* -------------------------
   Rejouer (cycle already reset at game over)
   ------------------------- */
function replayGame(){
  audio.unmuteAll();
  gameoverModal.style.display = 'none';
  spinBtn.disabled = false;
  updateUI();
  saveState();
}

/* -------------------------
   Transfer session gems to bank
   ------------------------- */
function transferToBank(){
  if(sessionGems <= 0) { messageEl.textContent = 'Aucun gain à transférer.'; return; }
  bank += sessionGems;
  sessionGems = 0;
  messageEl.textContent = 'Transféré vers la banque.';
  updateUI();
  saveState();
}

/* -------------------------
   Populate gains table
   ------------------------- */
function populateGains(){
  gainsBody.innerHTML = '';
  const list = SYMBOL_PACKS[selectedPack];
  const totalW = list.reduce((s,x)=>s+(x.weight||1),0);
  SYMBOLS.forEach(s=>{
    const v3 = Math.floor(s.base * SPIN_COST * 1);
    const v4 = Math.floor(s.base * SPIN_COST * 2);
    const v5 = Math.floor(s.base * SPIN_COST * 5);
    const symObj = list.find(x=>x.id===s.id);
    const weight = symObj ? (symObj.weight || 1) : 1;
    const chancePct = ((weight / totalW) * 100).toFixed(1);
    const tr = document.createElement('tr');
    tr.innerHTML = `<td style="font-size:20px">${s.icon}</td><td>${s.name}</td><td>${v3}</td><td>${v4}</td><td>${v5}</td><td>${chancePct}%</td>`;
    gainsBody.appendChild(tr);
  });
}

/* ============================
   UI wiring & event handlers
   ============================ */

spinBtn.addEventListener('click', spinAll);

// options modal
optionsBtn.addEventListener('click', ()=> optionsModal.style.display = 'flex');
closeOptions.addEventListener('click', ()=> optionsModal.style.display = 'none');

toggleSoundBtn.addEventListener('click', ()=>{
  soundOn = !soundOn;
  toggleSoundBtn.textContent = soundOn ? '🔊 Sons ON' : '🔇 Sons OFF';
  if(!soundOn) audio.muteAll(); else audio.unmuteAll();
  localStorage.setItem('slot_v30_sound', soundOn ? '1' : '0');
});

resetSessionBtn.addEventListener('click', ()=>{
  sessionGems = 0;
  cycleProgress = 0;
  turnsLeft = 5;
  level = 1;
  objective = 400;
  messageEl.textContent = 'Session reset.';
  updateUI(); saveState();
});

resetAllBtn.addEventListener('click', ()=>{
  sessionGems = 0;
  bank = 0;
  cycleProgress = 0;
  turnsLeft = 5;
  level = 1;
  objective = 400;
  messageEl.textContent = 'Everything reset.';
  updateUI(); saveState();
});

// shop
shopBtn.addEventListener('click', ()=> shopModal.style.display='flex');
closeShop.addEventListener('click', ()=> shopModal.style.display='none');

// select theme cards visually & persist
themeGrid.querySelectorAll('.shop-card').forEach(card=>{
  card.addEventListener('click', ()=>{
    themeGrid.querySelectorAll('.shop-card').forEach(c => c.classList.remove('selected'));
    card.classList.add('selected');
    selectedTheme = card.dataset.theme;
    document.body.className = 'theme-' + selectedTheme;
    localStorage.setItem('slot_v30_theme', selectedTheme);
  });
  if(card.dataset.theme === selectedTheme) card.classList.add('selected');
});

// select packs
packGrid.querySelectorAll('.shop-card').forEach(card=>{
  card.addEventListener('click', ()=>{
    packGrid.querySelectorAll('.shop-card').forEach(c => c.classList.remove('selected'));
    card.classList.add('selected');
    selectedPack = card.dataset.pack;
    localStorage.setItem('slot_v30_pack', selectedPack);
    initReels();
    populateGains();
  });
  if(card.dataset.pack === selectedPack) card.classList.add('selected');
});

// gains modal
gainsBtn.addEventListener('click', ()=> { populateGains(); gainsModal.style.display='flex'; });
closeGains.addEventListener('click', ()=> gainsModal.style.display='none');

// watch ad button (exact label preserved)
watchAdBtn.addEventListener('click', ()=>{
  sessionGems += 300;
  messageEl.textContent = '+300 crédits reçus ! 🎁';
  updateUI();
  saveState();
});

// transfer button
transferBtn.addEventListener('click', transferToBank);

// game over modal handlers
replayBtn.addEventListener('click', ()=>{
  replayGame();
  saveState();
});
goBankBtn.addEventListener('click', ()=>{
  transferToBank();
  gameoverModal.style.display='none';
  audio.unmuteAll();
  spinBtn.disabled = false;
  updateUI();
  saveState();
});

// initial setup
document.body.className = 'theme-' + selectedTheme;
updateUI();
populateGains();
initReels();
</script>
</body>
</html>
