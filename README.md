[tradex_with_auth.html](https://github.com/user-attachments/files/27308864/tradex_with_auth.html)

<style>
@import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=DM+Sans:wght@300;400;500;600&display=swap');
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg:#0a0c10;--bg2:#111318;--bg3:#181b22;--bg4:#1e2229;
  --border:#2a2f3a;--border2:#333844;
  --text:#e8eaf0;--text2:#8b92a5;--text3:#555e72;
  --green:#00d68f;--green2:#00a86b;--green-bg:rgba(0,214,143,.08);
  --red:#ff4d6d;--red2:#cc3355;--red-bg:rgba(255,77,109,.08);
  --blue:#4d9fff;--blue-bg:rgba(77,159,255,.08);
  --gold:#f5a623;--gold-bg:rgba(245,166,35,.08);
  --font-mono:'Space Mono',monospace;--font:'DM Sans',sans-serif;
}
body{background:var(--bg);color:var(--text);font-family:var(--font);font-size:14px;min-height:100vh}
.screen{min-height:100vh;display:flex;align-items:center;justify-content:center}
.login-box{background:var(--bg2);border:1px solid var(--border2);border-radius:12px;padding:40px;width:380px}
.logo-big{font-family:var(--font-mono);font-size:22px;font-weight:700;letter-spacing:3px;margin-bottom:4px}
.logo-sub{font-size:11px;color:var(--text3);letter-spacing:3px;text-transform:uppercase;margin-bottom:32px}
.form-group{margin-bottom:16px}
.form-label{font-size:11px;letter-spacing:1.5px;text-transform:uppercase;color:var(--text3);font-family:var(--font-mono);display:block;margin-bottom:6px}
.form-input{background:var(--bg3);border:1px solid var(--border2);border-radius:6px;padding:10px 14px;color:var(--text);font-size:14px;font-family:var(--font);outline:none;transition:border .15s;width:100%}
.form-input:focus{border-color:#4d9fff55}
.btn{display:inline-flex;align-items:center;justify-content:center;gap:6px;padding:10px 18px;border-radius:6px;font-size:13px;font-weight:600;cursor:pointer;border:none;transition:all .15s;font-family:var(--font);width:100%}
.btn-primary{background:var(--green);color:#000}
.btn-primary:hover{background:var(--green2)}
.btn-ghost{background:transparent;color:var(--text2);border:1px solid var(--border2)}
.btn-ghost:hover{color:var(--text);background:var(--bg3)}
.btn-red{background:var(--red-bg);color:var(--red);border:1px solid var(--red);width:auto;padding:6px 12px;font-size:11px}
.btn-sm{padding:6px 12px;font-size:11px;width:auto;border-radius:4px}
.error-msg{background:var(--red-bg);border:1px solid var(--red);color:var(--red);padding:10px 14px;border-radius:6px;font-size:12px;margin-bottom:16px}
.success-msg{background:var(--green-bg);border:1px solid var(--green);color:var(--green);padding:10px 14px;border-radius:6px;font-size:12px;margin-bottom:16px}
.app{display:flex;min-height:100vh}
.sidebar{width:220px;background:var(--bg2);border-right:1px solid var(--border);display:flex;flex-direction:column;flex-shrink:0}
.logo{padding:24px 20px 20px;border-bottom:1px solid var(--border)}
.logo-text{font-family:var(--font-mono);font-size:15px;font-weight:700;letter-spacing:2px}
.logo-sub2{font-size:10px;color:var(--text3);letter-spacing:3px;text-transform:uppercase;margin-top:2px}
.nav{padding:16px 0;flex:1}
.nav-item{display:flex;align-items:center;gap:10px;padding:10px 20px;cursor:pointer;color:var(--text2);font-size:13px;border-left:2px solid transparent;transition:all .15s}
.nav-item:hover{color:var(--text);background:var(--bg3)}
.nav-item.active{color:var(--text);background:var(--bg3);border-left-color:var(--green)}
.nav-icon{width:16px;height:16px;opacity:.7;flex-shrink:0}
.nav-item.active .nav-icon{opacity:1}
.sidebar-footer{padding:16px 20px;border-top:1px solid var(--border)}
.user-info{font-size:12px;color:var(--text2);margin-bottom:8px}
.expiry-badge{font-size:10px;font-family:var(--font-mono);padding:3px 8px;border-radius:3px;display:inline-block;margin-bottom:10px}
.exp-ok{background:var(--green-bg);color:var(--green)}
.exp-warn{background:var(--gold-bg);color:var(--gold)}
.exp-bad{background:var(--red-bg);color:var(--red)}
.main{flex:1;overflow:hidden;display:flex;flex-direction:column}
.topbar{background:var(--bg2);border-bottom:1px solid var(--border);padding:0 28px;height:56px;display:flex;align-items:center;justify-content:space-between;flex-shrink:0}
.topbar-title{font-size:16px;font-weight:500}
.content{flex:1;overflow-y:auto;padding:28px}
.grid4{display:grid;grid-template-columns:repeat(4,1fr);gap:16px;margin-bottom:16px}
.grid2{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:16px}
.grid3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:16px;margin-bottom:16px}
.card{background:var(--bg2);border:1px solid var(--border);border-radius:8px;padding:20px}
.card-sm{background:var(--bg3);border:1px solid var(--border);border-radius:6px;padding:16px}
.metric-label{font-size:11px;color:var(--text3);letter-spacing:1.5px;text-transform:uppercase;margin-bottom:8px}
.metric-val{font-family:var(--font-mono);font-size:24px;font-weight:700}
.metric-val.up{color:var(--green)}
.metric-val.dn{color:var(--red)}
.metric-sub{font-size:11px;color:var(--text3);margin-top:4px}
.section-title{font-size:12px;letter-spacing:2px;text-transform:uppercase;color:var(--text3);margin-bottom:16px;font-family:var(--font-mono)}
table{width:100%;border-collapse:collapse}
thead th{font-size:10px;letter-spacing:1.5px;text-transform:uppercase;color:var(--text3);padding:0 12px 12px;text-align:left;font-family:var(--font-mono);font-weight:400;border-bottom:1px solid var(--border)}
thead th.r{text-align:right}
tbody tr{border-bottom:1px solid var(--border)}
tbody tr:hover{background:var(--bg3)}
tbody td{padding:10px 12px;font-size:13px;color:var(--text2)}
tbody td.mono{font-family:var(--font-mono);font-size:12px}
.pill{display:inline-flex;align-items:center;padding:2px 8px;border-radius:3px;font-size:10px;font-family:var(--font-mono);font-weight:700}
.pill-green{background:var(--green-bg);color:var(--green)}
.pill-red{background:var(--red-bg);color:var(--red)}
.pill-blue{background:var(--blue-bg);color:var(--blue)}
.pill-gold{background:var(--gold-bg);color:var(--gold)}
.pill-gray{background:rgba(139,146,165,.1);color:var(--text2)}
.filter-row{display:flex;align-items:center;gap:10px;margin-bottom:20px;flex-wrap:wrap}
.filter-select{background:var(--bg3);border:1px solid var(--border2);border-radius:5px;padding:7px 12px;color:var(--text2);font-size:12px;font-family:var(--font);outline:none;cursor:pointer}
.chart-wrap{position:relative;width:100%;height:220px}
.blocked-screen{min-height:100vh;display:flex;align-items:center;justify-content:center;flex-direction:column;gap:16px;text-align:center;padding:24px}
.blocked-icon{font-size:48px;margin-bottom:8px}
.blocked-title{font-family:var(--font-mono);font-size:20px;font-weight:700;color:var(--red)}
.blocked-sub{color:var(--text2);font-size:14px;max-width:340px;line-height:1.6}
.admin-card{background:var(--bg2);border:1px solid var(--border2);border-radius:8px;padding:20px;margin-bottom:12px}
.admin-row{display:flex;align-items:center;gap:12px;padding:10px 0;border-bottom:1px solid var(--border)}
.admin-row:last-child{border-bottom:none}
.form-overlay{position:fixed;inset:0;background:rgba(0,0,0,.75);z-index:100;display:flex;align-items:center;justify-content:center}
.form-box{background:var(--bg2);border:1px solid var(--border2);border-radius:10px;width:440px;padding:28px}
.form-title{font-size:16px;font-weight:600;margin-bottom:20px;display:flex;justify-content:space-between;align-items:center}
.close-btn{background:none;border:none;color:var(--text3);cursor:pointer;font-size:20px}
.toggle-row{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:12px}
.toggle-btn{padding:8px;border-radius:5px;border:1px solid var(--border2);background:transparent;color:var(--text2);cursor:pointer;font-size:12px;font-weight:500;transition:all .15s;font-family:var(--font)}
.toggle-btn.sel-type{border-color:var(--blue);background:var(--blue-bg);color:var(--blue)}
.toggle-btn.sel-long{border-color:var(--green);background:var(--green-bg);color:var(--green)}
.toggle-btn.sel-short{border-color:var(--red);background:var(--red-bg);color:var(--red)}
.form-row{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px}
.form-select{background:var(--bg3);border:1px solid var(--border2);border-radius:5px;padding:9px 12px;color:var(--text);font-size:13px;font-family:var(--font);outline:none;width:100%;cursor:pointer}
.result-preview{background:var(--bg4);border-radius:5px;padding:10px 16px;margin-top:8px;font-family:var(--font-mono);font-size:16px;font-weight:700;text-align:center}
.pnl-bar-wrap{height:5px;background:var(--bg4);border-radius:3px;overflow:hidden;margin-top:4px}
.pnl-bar{height:100%;border-radius:3px}
.dot{width:6px;height:6px;border-radius:50%;flex-shrink:0;display:inline-block}
</style>

<div id="root"></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
<script>
const CRYPTO=["BTC","ETH","BNB","SOL","XRP","ADA","DOGE","AVAX","DOT","MATIC"];
const B3=["WIN","WDO"];
const ALL_ASSETS=[...B3,...CRYPTO];
const ASSET_COLORS={BTC:"#f7931a",ETH:"#627eea",BNB:"#f3ba2f",SOL:"#9945ff",XRP:"#00aae4",ADA:"#0033ad",DOGE:"#c2a633",AVAX:"#e84142",DOT:"#e6007a",MATIC:"#8247e5",WIN:"#4d9fff",WDO:"#00d68f"};

// ── USERS DB (em produção substituir por backend/Supabase) ──
const USERS_KEY='tradex_users';
const DEFAULT_USERS=[
  {id:1,username:'admin',password:'admin123',role:'admin',name:'Administrador',expiry:'2099-12-31',active:true},
  {id:2,username:'cliente1',password:'senha123',role:'user',name:'João Silva',expiry:'2025-03-01',active:true},
  {id:3,username:'cliente2',password:'abc456',role:'user',name:'Maria Souza',expiry:'2025-07-01',active:true},
];
function getUsers(){return JSON.parse(localStorage.getItem(USERS_KEY)||'null')||DEFAULT_USERS;}
function saveUsers(u){localStorage.setItem(USERS_KEY,JSON.stringify(u));}

// ── SESSION ──
let session=JSON.parse(sessionStorage.getItem('tradex_session')||'null');
function login(username,password){
  const users=getUsers();
  const u=users.find(u=>u.username===username&&u.password===password&&u.active);
  if(!u)return{ok:false,msg:'Usuário ou senha incorretos.'};
  const today=new Date().toISOString().slice(0,10);
  if(u.role!=='admin'&&u.expiry<today)return{ok:false,msg:'Acesso expirado. Entre em contato com o administrador.'};
  session={...u};
  sessionStorage.setItem('tradex_session',JSON.stringify(session));
  return{ok:true};
}
function logout(){session=null;sessionStorage.removeItem('tradex_session');renderApp();}

// ── TRADES DB por usuário ──
function tradesKey(uid){return'tradex_trades_'+uid;}
const SEEDS=[
  {id:1,asset:"BTC",dir:"long",qty:0.05,entry:198000,exit:205000,result:350,date:"2025-01-03",notes:"Rompimento de resistência"},
  {id:2,asset:"WIN",dir:"short",qty:5,entry:134200,exit:133800,result:200,date:"2025-01-05",notes:"Pullback no topo"},
  {id:3,asset:"ETH",dir:"long",qty:0.5,entry:11800,exit:11400,result:-200,date:"2025-01-08",notes:"Stop na LTA"},
  {id:4,asset:"WDO",dir:"long",qty:3,entry:6.152,exit:6.174,result:330,date:"2025-01-10",notes:""},
  {id:5,asset:"SOL",dir:"long",qty:2,entry:980,exit:1120,result:280,date:"2025-01-12",notes:"Tendência de alta"},
  {id:6,asset:"BTC",dir:"short",qty:0.05,entry:208000,exit:210500,result:-125,date:"2025-01-15",notes:"Contra-tendência"},
  {id:7,asset:"WIN",dir:"long",qty:10,entry:133500,exit:134100,result:600,date:"2025-01-17",notes:"Abertura forte"},
  {id:8,asset:"ETH",dir:"long",qty:0.8,entry:11200,exit:12100,result:720,date:"2025-01-20",notes:"Acumulação"},
  {id:9,asset:"BTC",dir:"long",qty:0.1,entry:202000,exit:218000,result:1600,date:"2025-01-28",notes:"Breakout mensal"},
  {id:10,asset:"WIN",dir:"long",qty:8,entry:134800,exit:135400,result:480,date:"2025-02-04",notes:""},
];
function getTrades(){
  const uid=session?session.id:0;
  return JSON.parse(localStorage.getItem(tradesKey(uid))||'null')||SEEDS.map(t=>({...t}));
}
function setTrades(t){localStorage.setItem(tradesKey(session.id),JSON.stringify(t));}

// ── HELPERS ──
function fmtBRL(v){const a=Math.abs(v);const s=a>=1000?'R$'+(a/1000).toFixed(1)+'k':'R$'+a.toFixed(0);return v<0?'-'+s:s;}
function fmtFull(v){return'R$ '+v.toLocaleString('pt-BR',{minimumFractionDigits:2,maximumFractionDigits:2});}
function isCrypto(a){return CRYPTO.includes(a);}
function assetColor(a){return ASSET_COLORS[a]||'#8b92a5';}
function daysLeft(expiry){const d=Math.ceil((new Date(expiry)-new Date())/86400000);return d;}

let currentPage='dashboard';
let tradeFormState=null;
let charts={};

function destroyCharts(){Object.values(charts).forEach(c=>{try{c.destroy();}catch(e){}});charts={};}

// ── STATS ──
function stats(trades){
  const total=trades.reduce((s,t)=>s+(t.result||0),0);
  const wins=trades.filter(t=>t.result>0);
  const losses=trades.filter(t=>t.result<0);
  const wr=trades.length?wins.length/trades.length:0;
  const avgW=wins.length?wins.reduce((s,t)=>s+t.result,0)/wins.length:0;
  const avgL=losses.length?Math.abs(losses.reduce((s,t)=>s+t.result,0)/losses.length):0;
  const rr=avgL?avgW/avgL:0;
  return{total,wins:wins.length,losses:losses.length,wr,avgW,avgL,rr,count:trades.length};
}
function equityCurve(trades){
  const sorted=[...trades].sort((a,b)=>new Date(a.date)-new Date(b.date));
  let acc=0;return sorted.map(t=>{acc+=t.result||0;return{date:t.date,val:acc};});
}
function byAsset(trades){
  const map={};
  trades.forEach(t=>{
    if(!map[t.asset])map[t.asset]={asset:t.asset,count:0,total:0,wins:0};
    map[t.asset].count++;map[t.asset].total+=t.result||0;
    if(t.result>0)map[t.asset].wins++;
  });
  return Object.values(map).sort((a,b)=>b.total-a.total);
}
function byMonth(trades){
  const map={};
  trades.forEach(t=>{const m=t.date.slice(0,7);if(!map[m])map[m]={month:m,total:0,count:0};map[m].total+=t.result||0;map[m].count++;});
  return Object.values(map).sort((a,b)=>a.month.localeCompare(b.month));
}

// ── RENDER ROOT ──
function renderApp(){
  const root=document.getElementById('root');
  destroyCharts();
  if(!session){root.innerHTML=loginHTML();return;}
  const today=new Date().toISOString().slice(0,10);
  if(session.role!=='admin'&&session.expiry<today){root.innerHTML=blockedHTML();return;}
  if(session.role==='admin'&&currentPage==='admin'){root.innerHTML=appShell(adminHTML());return;}
  root.innerHTML=appShell(pageContent());
  afterRender();
}

// ── LOGIN ──
function loginHTML(){return`
<div class="screen">
  <div class="login-box">
    <div class="logo-big">TRADEX</div>
    <div class="logo-sub">Pro Journal — Acesso</div>
    <div id="login-err"></div>
    <div class="form-group">
      <label class="form-label">Usuário</label>
      <input class="form-input" id="l-user" placeholder="seu_usuario" onkeydown="if(event.key==='Enter')doLogin()">
    </div>
    <div class="form-group">
      <label class="form-label">Senha</label>
      <input class="form-input" id="l-pass" type="password" placeholder="••••••••" onkeydown="if(event.key==='Enter')doLogin()">
    </div>
    <button class="btn btn-primary" onclick="doLogin()">Entrar</button>
    <div style="margin-top:16px;font-size:11px;color:var(--text3);text-align:center">
      Demo: admin/admin123 · cliente1/senha123 · cliente2/abc456
    </div>
  </div>
</div>`;}

function doLogin(){
  const u=document.getElementById('l-user').value.trim();
  const p=document.getElementById('l-pass').value;
  const r=login(u,p);
  if(!r.ok){document.getElementById('login-err').innerHTML=`<div class="error-msg">${r.msg}</div>`;}
  else{currentPage='dashboard';renderApp();}
}

// ── BLOCKED ──
function blockedHTML(){return`
<div class="blocked-screen">
  <div class="blocked-icon">🔒</div>
  <div class="blocked-title">Acesso Bloqueado</div>
  <div class="blocked-sub">Seu plano expirou em <strong>${session.expiry}</strong>.<br>Entre em contato com o administrador para renovar.</div>
  <button class="btn btn-ghost" style="width:auto;margin-top:8px" onclick="logout()">Voltar ao Login</button>
</div>`;}

// ── APP SHELL ──
function appShell(inner){
  const today=new Date().toISOString().slice(0,10);
  const dl=daysLeft(session.expiry);
  const expClass=dl>30?'exp-ok':dl>7?'exp-warn':'exp-bad';
  const expLabel=session.role==='admin'?'Admin':dl>0?`Expira em ${dl}d`:'Expirado';
  const pages=[
    {id:'dashboard',icon:`<rect x="1" y="1" width="6" height="6" rx="1" fill="currentColor" opacity=".8"/><rect x="9" y="1" width="6" height="6" rx="1" fill="currentColor" opacity=".4"/><rect x="1" y="9" width="6" height="6" rx="1" fill="currentColor" opacity=".4"/><rect x="9" y="9" width="6" height="6" rx="1" fill="currentColor" opacity=".6"/>`,label:'Dashboard'},
    {id:'journal',icon:`<rect x="2" y="1" width="12" height="14" rx="1.5" stroke="currentColor" stroke-width="1.2"/><line x1="5" y1="5" x2="11" y2="5" stroke="currentColor" stroke-width="1.2"/><line x1="5" y1="8" x2="11" y2="8" stroke="currentColor" stroke-width="1.2"/><line x1="5" y1="11" x2="9" y2="11" stroke="currentColor" stroke-width="1.2"/>`,label:'Diário'},
    {id:'analytics',icon:`<polyline points="1,12 5,7 9,9 15,3" stroke="currentColor" stroke-width="1.4" fill="none"/><circle cx="5" cy="7" r="1.5" fill="currentColor"/><circle cx="9" cy="9" r="1.5" fill="currentColor"/><circle cx="15" cy="3" r="1.5" fill="currentColor"/>`,label:'Análise'},
    ...(session.role==='admin'?[{id:'admin',icon:`<circle cx="8" cy="5" r="3" stroke="currentColor" stroke-width="1.2" fill="none"/><path d="M2 14c0-3.3 2.7-6 6-6s6 2.7 6 6" stroke="currentColor" stroke-width="1.2" fill="none"/>`,label:'Clientes'}]:[]),
  ];
  return`
  <div class="app">
    <div class="sidebar">
      <div class="logo"><div class="logo-text">TRADEX</div><div class="logo-sub2">Pro Journal</div></div>
      <nav class="nav" id="nav">
        ${pages.map(p=>`<div class="nav-item ${currentPage===p.id?'active':''}" data-page="${p.id}">
          <svg class="nav-icon" viewBox="0 0 16 16" fill="none">${p.icon}</svg>${p.label}
        </div>`).join('')}
      </nav>
      <div class="sidebar-footer">
        <div class="user-info">${session.name}</div>
        <span class="expiry-badge ${expClass}">${expLabel}</span>
        <button class="btn btn-ghost" style="padding:6px;font-size:11px" onclick="logout()">Sair</button>
      </div>
    </div>
    <div class="main">
      <div class="topbar">
        <div style="font-size:16px;font-weight:500">${{dashboard:'Dashboard',journal:'Diário de Trades',analytics:'Análise',admin:'Gestão de Clientes'}[currentPage]||''}</div>
        ${currentPage!=='admin'?`<button class="btn btn-primary" style="width:auto;padding:8px 16px" onclick="openTradeForm()">+ Novo Trade</button>`:''}
      </div>
      <div class="content" id="content">${inner}</div>
    </div>
  </div>`;
}

// ── PAGES ──
function pageContent(){
  const trades=getTrades();
  if(currentPage==='dashboard')return dashHTML(trades);
  if(currentPage==='journal')return journalHTML(trades);
  if(currentPage==='analytics')return analyticsHTML(trades);
  return'';
}

function dashHTML(trades){
  const s=stats(trades);
  const recent=[...trades].sort((a,b)=>new Date(b.date)-new Date(a.date)).slice(0,8);
  return`
  <div class="grid4">
    <div class="card-sm"><div class="metric-label">Resultado Total</div><div class="metric-val ${s.total>=0?'up':'dn'}">${fmtBRL(s.total)}</div><div class="metric-sub">${s.count} operações</div></div>
    <div class="card-sm"><div class="metric-label">Win Rate</div><div class="metric-val ${s.wr>=0.5?'up':'dn'}">${(s.wr*100).toFixed(1)}%</div><div class="metric-sub">${s.wins}W / ${s.losses}L</div></div>
    <div class="card-sm"><div class="metric-label">Risk/Reward</div><div class="metric-val ${s.rr>=1?'up':'dn'}">${s.rr.toFixed(2)}</div><div class="metric-sub">Avg win/loss</div></div>
    <div class="card-sm"><div class="metric-label">Profit Factor</div><div class="metric-val ${(s.wins*s.avgW/(s.losses*s.avgL||1))>=1?'up':'dn'}">${(s.wins*s.avgW/(s.losses*s.avgL||1)).toFixed(2)}</div><div class="metric-sub">fator de lucro</div></div>
  </div>
  <div class="grid2">
    <div class="card"><div class="section-title">Curva de Equity</div><div class="chart-wrap"><canvas id="eqChart" role="img" aria-label="Curva de equity"></canvas></div></div>
    <div class="card"><div class="section-title">P&L por Ativo</div><div class="chart-wrap"><canvas id="assetChart" role="img" aria-label="PnL por ativo"></canvas></div></div>
  </div>
  <div class="card">
    <div class="section-title">Últimas Operações</div>
    <table><thead><tr><th>Data</th><th>Ativo</th><th>Dir.</th><th>Qtd</th><th class="r">Resultado</th><th>Notas</th></tr></thead>
    <tbody>${recent.map(t=>`<tr>
      <td class="mono">${t.date}</td>
      <td><span style="display:inline-flex;align-items:center;gap:4px"><span class="dot" style="background:${assetColor(t.asset)}"></span>${t.asset}</span>${isCrypto(t.asset)?'<span class="pill pill-gold" style="margin-left:4px;font-size:9px">₿</span>':''}</td>
      <td><span class="pill ${t.dir==='long'?'pill-green':'pill-red'}">${t.dir.toUpperCase()}</span></td>
      <td class="mono">${t.qty||'—'}</td>
      <td class="mono" style="text-align:right;color:${(t.result||0)>=0?'var(--green)':'var(--red)'};font-weight:700">${fmtBRL(t.result||0)}</td>
      <td style="font-size:12px;color:var(--text3);max-width:140px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap">${t.notes||'—'}</td>
    </tr>`).join('')}</tbody></table>
  </div>`;
}

function journalHTML(trades){
  return`
  <div class="filter-row">
    <select class="filter-select" id="f-type" onchange="applyFilters()"><option value="all">Todos os tipos</option><option value="b3">B3</option><option value="crypto">Cripto</option></select>
    <select class="filter-select" id="f-asset" onchange="applyFilters()"><option value="all">Todos os ativos</option>${ALL_ASSETS.map(a=>`<option value="${a}">${a}</option>`).join('')}</select>
    <select class="filter-select" id="f-dir" onchange="applyFilters()"><option value="all">Long & Short</option><option value="long">Long</option><option value="short">Short</option></select>
    <select class="filter-select" id="f-result" onchange="applyFilters()"><option value="all">Todos</option><option value="gain">Gains</option><option value="loss">Losses</option></select>
    <div id="j-summary" style="margin-left:auto;display:flex;gap:12px;align-items:center"></div>
  </div>
  <div class="card" style="padding:0;overflow-x:auto">
    <table><thead><tr><th>Data</th><th>Ativo</th><th>Tipo</th><th>Dir.</th><th class="r">Qtd</th><th class="r">Entrada</th><th class="r">Saída</th><th class="r">Resultado</th><th>Notas</th><th></th></tr></thead>
    <tbody id="j-body"></tbody></table>
  </div>`;
}

function applyFilters(){
  const trades=getTrades();
  const ft=document.getElementById('f-type')?.value||'all';
  const fa=document.getElementById('f-asset')?.value||'all';
  const fd=document.getElementById('f-dir')?.value||'all';
  const fr=document.getElementById('f-result')?.value||'all';
  let f=[...trades].sort((a,b)=>new Date(b.date)-new Date(a.date));
  if(ft==='b3')f=f.filter(t=>B3.includes(t.asset));
  if(ft==='crypto')f=f.filter(t=>CRYPTO.includes(t.asset));
  if(fa!=='all')f=f.filter(t=>t.asset===fa);
  if(fd!=='all')f=f.filter(t=>t.dir===fd);
  if(fr==='gain')f=f.filter(t=>(t.result||0)>0);
  if(fr==='loss')f=f.filter(t=>(t.result||0)<0);
  const total=f.reduce((s,t)=>s+(t.result||0),0);
  const body=document.getElementById('j-body');
  const summ=document.getElementById('j-summary');
  if(body)body.innerHTML=f.length?f.map(t=>`<tr>
    <td class="mono">${t.date}</td>
    <td><span style="display:inline-flex;align-items:center;gap:4px"><span class="dot" style="background:${assetColor(t.asset)}"></span>${t.asset}</span></td>
    <td><span class="pill ${isCrypto(t.asset)?'pill-gold':'pill-blue'}">${isCrypto(t.asset)?'CRIPTO':'B3'}</span></td>
    <td><span class="pill ${t.dir==='long'?'pill-green':'pill-red'}">${t.dir.toUpperCase()}</span></td>
    <td class="mono" style="text-align:right">${t.qty||'—'}</td>
    <td class="mono" style="text-align:right">${t.entry||'—'}</td>
    <td class="mono" style="text-align:right">${t.exit||'—'}</td>
    <td class="mono" style="text-align:right;color:${(t.result||0)>=0?'var(--green)':'var(--red)'};font-weight:700">${fmtFull(t.result||0)}</td>
    <td style="font-size:12px;color:var(--text3);max-width:120px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap">${t.notes||'—'}</td>
    <td><button style="background:none;border:none;color:var(--text3);cursor:pointer;font-size:13px;padding:2px 6px" onclick="deleteTrade(${t.id})">✕</button></td>
  </tr>`).join(''):`<tr><td colspan="10" style="text-align:center;padding:40px;color:var(--text3)">Nenhum trade encontrado</td></tr>`;
  if(summ)summ.innerHTML=`<span style="font-size:12px;color:var(--text3)">${f.length} trades</span><span style="font-family:var(--font-mono);font-size:13px;font-weight:700;color:${total>=0?'var(--green)':'var(--red)'}">${fmtFull(total)}</span>`;
}

function deleteTrade(id){
  if(!confirm('Remover este trade?'))return;
  const t=getTrades().filter(t=>t.id!==id);
  setTrades(t);renderApp();
}

function analyticsHTML(trades){
  const s=stats(trades);
  const ab=byAsset(trades);
  const months=byMonth(trades);
  return`
  <div class="grid4" style="margin-bottom:20px">
    <div class="card-sm"><div class="metric-label">Avg. Win</div><div class="metric-val up">${fmtBRL(s.avgW)}</div></div>
    <div class="card-sm"><div class="metric-label">Avg. Loss</div><div class="metric-val dn">${fmtBRL(-s.avgL)}</div></div>
    <div class="card-sm"><div class="metric-label">Profit Factor</div><div class="metric-val ${(s.wins*s.avgW/(s.losses*s.avgL||1))>=1?'up':'dn'}">${(s.wins*s.avgW/(s.losses*s.avgL||1)).toFixed(2)}</div></div>
    <div class="card-sm"><div class="metric-label">Expectativa/Trade</div><div class="metric-val ${(s.wr*s.avgW-(1-s.wr)*s.avgL)>=0?'up':'dn'}">${fmtBRL(s.wr*s.avgW-(1-s.wr)*s.avgL)}</div></div>
  </div>
  <div class="grid2">
    <div class="card"><div class="section-title">P&L Mensal</div><div class="chart-wrap"><canvas id="monthChart" role="img" aria-label="PnL mensal"></canvas></div></div>
    <div class="card"><div class="section-title">Distribuição por Ativo</div><div class="chart-wrap"><canvas id="distChart" role="img" aria-label="Distribuição por ativo"></canvas></div></div>
  </div>
  <div class="card">
    <div class="section-title">Performance por Ativo</div>
    <table><thead><tr><th>Ativo</th><th>Tipo</th><th>Trades</th><th>Win Rate</th><th class="r">P&L</th><th>Barra</th></tr></thead>
    <tbody>${ab.map(a=>{
      const mx=Math.max(...ab.map(x=>Math.abs(x.total)));
      return`<tr>
        <td><span style="display:inline-flex;align-items:center;gap:4px"><span class="dot" style="background:${assetColor(a.asset)}"></span>${a.asset}</span></td>
        <td><span class="pill ${isCrypto(a.asset)?'pill-gold':'pill-blue'}">${isCrypto(a.asset)?'CRIPTO':'B3'}</span></td>
        <td class="mono">${a.count}</td>
        <td class="mono">${a.count?((a.wins/a.count)*100).toFixed(0)+'%':'—'}</td>
        <td class="mono" style="text-align:right;color:${a.total>=0?'var(--green)':'var(--red)'};font-weight:700">${fmtBRL(a.total)}</td>
        <td style="min-width:80px"><div class="pnl-bar-wrap"><div class="pnl-bar" style="width:${mx?(Math.abs(a.total)/mx*100).toFixed(0):0}%;background:${a.total>=0?'var(--green)':'var(--red)'}"></div></div></td>
      </tr>`}).join('')}</tbody></table>
  </div>`;
}

// ── ADMIN PANEL ──
function adminHTML(){
  const users=getUsers().filter(u=>u.role!=='admin');
  const today=new Date().toISOString().slice(0,10);
  return`
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:20px">
    <div style="font-size:13px;color:var(--text2)">${users.length} clientes cadastrados</div>
    <button class="btn btn-primary" style="width:auto;padding:8px 16px" onclick="openNewClient()">+ Novo Cliente</button>
  </div>
  <div class="card" style="padding:0;overflow-x:auto">
    <table><thead><tr><th>Cliente</th><th>Usuário</th><th>Status</th><th>Vencimento</th><th>Trades</th><th>P&L</th><th style="text-align:right">Ações</th></tr></thead>
    <tbody>${users.map(u=>{
      const dl=daysLeft(u.expiry);
      const expired=u.expiry<today;
      const warn=dl<=7&&!expired;
      const trades=JSON.parse(localStorage.getItem(tradesKey(u.id))||'[]');
      const total=trades.reduce((s,t)=>s+(t.result||0),0);
      return`<tr>
        <td style="font-weight:500;color:var(--text)">${u.name}</td>
        <td class="mono">${u.username}</td>
        <td><span class="pill ${!u.active?'pill-gray':expired?'pill-red':warn?'pill-gold':'pill-green'}">${!u.active?'INATIVO':expired?'EXPIRADO':warn?'EXPIRA EM BREVE':'ATIVO'}</span></td>
        <td class="mono">${u.expiry} ${warn?`<span style="color:var(--gold);font-size:11px">(${dl}d)</span>`:''}</td>
        <td class="mono">${trades.length||'—'}</td>
        <td class="mono" style="color:${total>=0?'var(--green)':'var(--red)'}">${trades.length?fmtBRL(total):'—'}</td>
        <td style="text-align:right">
          <button class="btn btn-ghost btn-sm" style="margin-right:6px" onclick="openEditClient(${u.id})">Editar</button>
          <button class="btn ${u.active?'btn-red':'btn-ghost'} btn-sm" onclick="toggleClient(${u.id})">${u.active?'Bloquear':'Liberar'}</button>
        </td>
      </tr>`;}).join('')}
    </tbody></table>
  </div>
  <div id="admin-form-area"></div>`;
}

function openNewClient(){
  document.getElementById('admin-form-area').innerHTML=clientFormHTML(null);
}
function openEditClient(id){
  const u=getUsers().find(u=>u.id===id);
  document.getElementById('admin-form-area').innerHTML=clientFormHTML(u);
}

function clientFormHTML(u){
  return`
  <div class="form-overlay" id="client-form-overlay">
    <div class="form-box">
      <div class="form-title">
        <span>${u?'Editar Cliente':'Novo Cliente'}</span>
        <button class="close-btn" onclick="document.getElementById('client-form-overlay').remove()">×</button>
      </div>
      <div class="form-group"><label class="form-label">Nome completo</label><input class="form-input" id="c-name" value="${u?u.name:''}"></div>
      <div class="form-row">
        <div class="form-group"><label class="form-label">Usuário</label><input class="form-input" id="c-user" value="${u?u.username:''}" ${u?'readonly':''}></div>
        <div class="form-group"><label class="form-label">Senha</label><input class="form-input" id="c-pass" type="password" placeholder="${u?'deixe em branco para manter':'nova senha'}"></div>
      </div>
      <div class="form-group"><label class="form-label">Vencimento do Plano</label><input class="form-input" id="c-expiry" type="date" value="${u?u.expiry:''}"></div>
      ${u?`<div style="background:var(--green-bg);border:1px solid var(--green);border-radius:6px;padding:10px 14px;font-size:12px;color:var(--green);margin-bottom:12px">Acesso válido até <strong>${u.expiry}</strong> · ${daysLeft(u.expiry)} dias restantes</div>`:''}
      <div style="display:flex;gap:10px;margin-top:8px">
        <button class="btn btn-ghost" onclick="document.getElementById('client-form-overlay').remove()">Cancelar</button>
        <button class="btn btn-primary" onclick="saveClient(${u?u.id:'null'})">${u?'Salvar Alterações':'Criar Cliente'}</button>
      </div>
    </div>
  </div>`;
}

function saveClient(id){
  const name=document.getElementById('c-name').value.trim();
  const username=document.getElementById('c-user').value.trim();
  const pass=document.getElementById('c-pass').value;
  const expiry=document.getElementById('c-expiry').value;
  if(!name||!username||!expiry){alert('Preencha todos os campos.');return;}
  const users=getUsers();
  if(id==='null'||id===null){
    if(!pass){alert('Informe a senha.');return;}
    if(users.find(u=>u.username===username)){alert('Usuário já existe.');return;}
    users.push({id:Date.now(),username,password:pass,role:'user',name,expiry,active:true});
  } else {
    const idx=users.findIndex(u=>u.id===id);
    if(idx>=0){
      users[idx].name=name;
      users[idx].expiry=expiry;
      if(pass)users[idx].password=pass;
    }
  }
  saveUsers(users);
  document.getElementById('client-form-overlay').remove();
  currentPage='admin';renderApp();
}

function toggleClient(id){
  const users=getUsers();
  const u=users.find(u=>u.id===id);
  if(!u)return;
  const msg=u.active?`Bloquear acesso de ${u.name}?`:`Liberar acesso de ${u.name}?`;
  if(!confirm(msg))return;
  u.active=!u.active;
  saveUsers(users);
  renderApp();
}

// ── TRADE FORM ──
let fs={asset_type:'b3',asset:'',dir:'long',date:new Date().toISOString().slice(0,10),qty:'',entry:'',exit:'',result:'',notes:''};
let nextId=getTrades().reduce((m,t)=>Math.max(m,t.id),0)+1;

function openTradeForm(){
  fs={asset_type:'b3',asset:'',dir:'long',date:new Date().toISOString().slice(0,10),qty:'',entry:'',exit:'',result:'',notes:''};
  renderTradeForm();
}

function renderTradeForm(){
  const old=document.getElementById('trade-overlay');if(old)old.remove();
  const list=fs.asset_type==='crypto'?CRYPTO:B3;
  const auto=fs.entry&&fs.exit&&fs.qty?
    ((fs.dir==='long'?(parseFloat(fs.exit)-parseFloat(fs.entry)):(parseFloat(fs.entry)-parseFloat(fs.exit)))*parseFloat(fs.qty)).toFixed(2):'';
  const res=fs.result||auto||'';
  const o=document.createElement('div');
  o.className='form-overlay';o.id='trade-overlay';
  o.innerHTML=`<div class="form-box">
    <div class="form-title"><span>Registrar Trade</span><button class="close-btn" onclick="document.getElementById('trade-overlay').remove()">×</button></div>
    <div class="toggle-row">
      <button class="toggle-btn ${fs.asset_type==='b3'?'sel-type':''}" onclick="setFS('asset_type','b3');setFS('asset','');renderTradeForm()">📈 B3 / Futuros</button>
      <button class="toggle-btn ${fs.asset_type==='crypto'?'sel-type':''}" onclick="setFS('asset_type','crypto');setFS('asset','');renderTradeForm()">🪙 Cripto</button>
    </div>
    <div class="form-row">
      <div class="form-group" style="margin-bottom:0"><label class="form-label">Ativo</label>
        <select class="form-select" onchange="setFS('asset',this.value)"><option value="">Selecione...</option>${list.map(a=>`<option value="${a}" ${fs.asset===a?'selected':''}>${a}</option>`).join('')}</select>
      </div>
      <div class="form-group" style="margin-bottom:0"><label class="form-label">Data</label><input type="date" class="form-input" value="${fs.date}" onchange="setFS('date',this.value)"></div>
    </div>
    <div class="toggle-row" style="margin-top:12px">
      <button class="toggle-btn ${fs.dir==='long'?'sel-long':''}" onclick="setFS('dir','long');setFS('result','');renderTradeForm()">▲ Long</button>
      <button class="toggle-btn ${fs.dir==='short'?'sel-short':''}" onclick="setFS('dir','short');setFS('result','');renderTradeForm()">▼ Short</button>
    </div>
    <div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;margin-bottom:12px">
      <div class="form-group" style="margin-bottom:0"><label class="form-label">Entrada</label><input type="number" class="form-input" value="${fs.entry}" placeholder="0.00" oninput="setFS('entry',this.value);setFS('result','');renderTradeForm()"></div>
      <div class="form-group" style="margin-bottom:0"><label class="form-label">Saída</label><input type="number" class="form-input" value="${fs.exit}" placeholder="0.00" oninput="setFS('exit',this.value);setFS('result','');renderTradeForm()"></div>
      <div class="form-group" style="margin-bottom:0"><label class="form-label">Qtd</label><input type="number" class="form-input" value="${fs.qty}" placeholder="0" oninput="setFS('qty',this.value);setFS('result','');renderTradeForm()"></div>
    </div>
    <div class="form-group">
      <label class="form-label">Resultado (R$)</label>
      <input type="number" class="form-input" value="${res}" placeholder="${auto?'Auto: '+auto:'ex: 350'}" oninput="setFS('result',this.value)">
      ${auto?`<div style="font-size:11px;color:var(--text3);margin-top:3px">Calculado automaticamente</div>`:''}
    </div>
    ${res?`<div class="result-preview" style="color:${parseFloat(res)>=0?'var(--green)':'var(--red)'}">${fmtFull(parseFloat(res)||0)}</div>`:''}
    <div class="form-group" style="margin-top:10px"><label class="form-label">Notas</label><input type="text" class="form-input" value="${fs.notes}" placeholder="Setup, racional..." oninput="setFS('notes',this.value)"></div>
    <div style="display:flex;gap:10px;margin-top:16px">
      <button class="btn btn-ghost" onclick="document.getElementById('trade-overlay').remove()">Cancelar</button>
      <button class="btn btn-primary" onclick="submitTrade()">Salvar Trade</button>
    </div>
  </div>`;
  document.body.appendChild(o);
  o.addEventListener('click',e=>{if(e.target===o)o.remove();});
}

function setFS(k,v){fs[k]=v;}

function submitTrade(){
  const auto=fs.entry&&fs.exit&&fs.qty?
    ((fs.dir==='long'?(parseFloat(fs.exit)-parseFloat(fs.entry)):(parseFloat(fs.entry)-parseFloat(fs.exit)))*parseFloat(fs.qty)):null;
  const result=parseFloat(fs.result)||auto||null;
  if(!fs.asset){alert('Selecione um ativo.');return;}
  if(!fs.date){alert('Informe a data.');return;}
  if(result===null||isNaN(result)){alert('Informe o resultado.');return;}
  const trades=getTrades();
  nextId=trades.reduce((m,t)=>Math.max(m,t.id),0)+1;
  trades.unshift({id:nextId,asset:fs.asset,dir:fs.dir,qty:parseFloat(fs.qty)||null,entry:parseFloat(fs.entry)||null,exit:parseFloat(fs.exit)||null,result,date:fs.date,notes:fs.notes});
  setTrades(trades);
  const o=document.getElementById('trade-overlay');if(o)o.remove();
  renderApp();
}

// ── CHARTS ──
function afterRender(){
  if(currentPage==='journal'){applyFilters();return;}
  const trades=getTrades();
  if(currentPage==='dashboard'){
    const eq=equityCurve(trades);
    const ab=byAsset(trades);
    const eqCtx=document.getElementById('eqChart');
    if(eqCtx)charts.eq=new Chart(eqCtx,{type:'line',data:{labels:eq.map(p=>p.date.slice(5)),datasets:[{data:eq.map(p=>p.val),borderColor:'#00d68f',backgroundColor:'rgba(0,214,143,.08)',borderWidth:2,pointRadius:0,fill:true,tension:.4}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false}},scales:{x:{ticks:{color:'#555e72',font:{size:10}},grid:{color:'rgba(255,255,255,.04)'}},y:{ticks:{color:'#555e72',font:{size:10},callback:v=>fmtBRL(v)},grid:{color:'rgba(255,255,255,.04)'}}}}});
    const aCtx=document.getElementById('assetChart');
    if(aCtx)charts.asset=new Chart(aCtx,{type:'bar',data:{labels:ab.slice(0,7).map(a=>a.asset),datasets:[{data:ab.slice(0,7).map(a=>a.total),backgroundColor:ab.slice(0,7).map(a=>a.total>=0?'rgba(0,214,143,.7)':'rgba(255,77,109,.7)'),borderRadius:4}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false}},scales:{x:{ticks:{color:'#555e72',font:{size:11}},grid:{display:false}},y:{ticks:{color:'#555e72',font:{size:10},callback:v=>fmtBRL(v)},grid:{color:'rgba(255,255,255,.04)'}}}}});
  }
  if(currentPage==='analytics'){
    const months=byMonth(trades);const ab=byAsset(trades);
    const mCtx=document.getElementById('monthChart');
    if(mCtx)charts.month=new Chart(mCtx,{type:'bar',data:{labels:months.map(m=>m.month.slice(5)+'/'+m.month.slice(2,4)),datasets:[{data:months.map(m=>m.total),backgroundColor:months.map(m=>m.total>=0?'rgba(0,214,143,.7)':'rgba(255,77,109,.7)'),borderRadius:4}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false}},scales:{x:{ticks:{color:'#555e72',font:{size:11}},grid:{display:false}},y:{ticks:{color:'#555e72',font:{size:10},callback:v=>fmtBRL(v)},grid:{color:'rgba(255,255,255,.04)'}}}}});
    const top=ab.slice(0,6);const dCtx=document.getElementById('distChart');
    if(dCtx)charts.dist=new Chart(dCtx,{type:'doughnut',data:{labels:top.map(a=>a.asset),datasets:[{data:top.map(a=>Math.abs(a.total)),backgroundColor:top.map(a=>assetColor(a.asset)+'cc'),borderColor:'#0a0c10',borderWidth:2}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{position:'right',labels:{color:'#8b92a5',font:{size:11},padding:12}}},cutout:'65%'}});
  }
}

// ── NAV ──
document.addEventListener('click',e=>{
  const ni=e.target.closest('.nav-item');
  if(ni&&ni.dataset.page){currentPage=ni.dataset.page;destroyCharts();renderApp();}
});

renderApp();
</script>
