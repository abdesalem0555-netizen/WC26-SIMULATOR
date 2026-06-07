# WC26-SIMULATOR
Assimilator fort worth cab 2026 with a good taste in games simulators
هذه هي لعبة محاكي كأس العالم 2026 الكاملة والمطورة. يمكنك مشاركة الرابط مع أصدقائك، وسيحتفظ بتوقعاتهم ونتائجهم.

```html
<!DOCTYPE html>
<html lang="en" dir="ltr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
<title>🏆 World Cup 2026 Simulator – Play & Predict the Champion</title>
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;900&family=Bebas+Neue&family=Barlow+Condensed:wght@400;600;700;900&display=swap" rel="stylesheet">
<style>
:root {
  --gold: #FFD700;
  --gold2: #FFA500;
  --dark: #060912;
  --dark2: #0d1020;
  --panel: #111827;
  --panel2: #1a2340;
  --panel3: #0f1e38;
  --accent: #e94560;
  --green: #00e676;
  --blue: #2979ff;
  --text: #e8eaf6;
  --muted: #8892b0;
}
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
html {
  scroll-behavior: smooth;
}
body {
  font-family: 'Cairo', sans-serif;
  background: var(--dark);
  color: var(--text);
  min-height: 100vh;
  overflow-x: hidden;
}
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background: radial-gradient(ellipse at 20% 20%, rgba(255,215,0,.05) 0%, transparent 60%),
              radial-gradient(ellipse at 80% 80%, rgba(41,121,255,.05) 0%, transparent 60%);
  pointer-events: none;
  z-index: 0;
}
/* layout */
.lang-toggle {
  position: fixed;
  top: 15px;
  right: 15px;
  z-index: 2000;
  display: flex;
  background: var(--panel);
  border-radius: 40px;
  border: 1px solid rgba(255,215,0,.3);
  overflow: hidden;
  backdrop-filter: blur(4px);
}
.lang-btn {
  padding: 8px 18px;
  border: none;
  background: transparent;
  color: var(--muted);
  font-weight: 700;
  cursor: pointer;
  transition: all .3s;
  font-size: .85rem;
}
.lang-btn.active {
  background: var(--gold);
  color: #000;
}
header {
  text-align: center;
  padding: 60px 20px 30px;
  position: relative;
  z-index: 1;
}
.trophy-wrap {
  width: 90px;
  height: 90px;
  background: radial-gradient(circle, rgba(255,215,0,.15), transparent);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 15px;
  animation: trophy-pulse 2s infinite;
}
@keyframes trophy-pulse { 0%,100% { box-shadow: 0 0 0 0 rgba(255,215,0,.3); } 50% { box-shadow: 0 0 0 25px rgba(255,215,0,0); } }
.trophy-icon { font-size: 4rem; filter: drop-shadow(0 0 12px var(--gold)); }
h1 {
  font-family: 'Bebas Neue', sans-serif;
  font-size: clamp(2rem,6vw,4rem);
  letter-spacing: 3px;
  background: linear-gradient(135deg, var(--gold), var(--gold2), #fff8a0);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}
.sub {
  color: var(--muted);
  font-size: .9rem;
}
/* tabs */
.tabs {
  display: flex;
  justify-content: center;
  gap: 10px;
  position: sticky;
  top: 0;
  z-index: 100;
  background: rgba(6,9,18,.96);
  backdrop-filter: blur(12px);
  padding: 12px 15px;
  border-bottom: 1px solid rgba(255,215,0,.1);
}
.tab-btn {
  background: var(--panel);
  border: 1px solid rgba(255,215,0,.25);
  padding: 10px 26px;
  border-radius: 40px;
  font-weight: 700;
  cursor: pointer;
  transition: 0.2s;
  color: var(--muted);
}
.tab-btn.active {
  background: linear-gradient(135deg, var(--gold), var(--gold2));
  color: #000;
  border-color: transparent;
  box-shadow: 0 4px 14px rgba(255,215,0,.3);
}
.content {
  max-width: 1300px;
  margin: 0 auto;
  padding: 25px 16px 130px;
}
/* groups */
.groups-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(330px, 1fr));
  gap: 20px;
}
.group-card {
  background: var(--panel);
  border-radius: 20px;
  border: 1px solid rgba(255,255,255,.07);
  overflow: hidden;
  transition: 0.2s;
  box-shadow: 0 10px 25px rgba(0,0,0,.3);
}
.group-header {
  background: linear-gradient(135deg, var(--panel2), var(--panel3));
  padding: 14px;
  font-weight: 900;
  color: var(--gold);
  text-align: center;
  font-size: 1.1rem;
  letter-spacing: 1px;
}
.standings-mini {
  width: 100%;
  font-size: 0.8rem;
  border-collapse: collapse;
  text-align: center;
}
.standings-mini th {
  padding: 10px 5px;
  color: var(--muted);
  font-size: 0.7rem;
}
.standings-mini td {
  padding: 8px 4px;
  border-bottom: 1px solid rgba(255,255,255,.05);
}
.pts-cell {
  background: rgba(255,215,0,.15);
  border-radius: 20px;
  font-weight: 800;
  color: var(--gold);
  display: inline-block;
  min-width: 32px;
}
.matches-list {
  padding: 6px 8px 12px;
}
.match-item {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 8px 6px;
  border-bottom: 1px solid rgba(255,255,255,.04);
}
.match-team {
  flex: 1;
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 0.8rem;
  font-weight: 600;
  white-space: nowrap;
}
.match-team.right {
  justify-content: flex-end;
}
.score-input {
  width: 44px;
  height: 38px;
  background: rgba(0,0,0,.6);
  border: 1px solid rgba(255,215,0,.4);
  color: var(--gold);
  text-align: center;
  font-size: 1rem;
  font-weight: 800;
  border-radius: 10px;
  transition: 0.2s;
}
.score-input:focus {
  outline: none;
  border-color: var(--gold);
  background: #000;
}
.vs-sep {
  color: var(--muted);
  font-weight: 800;
  min-width: 18px;
  text-align: center;
}
.best3-panel {
  background: var(--panel);
  border-radius: 20px;
  border: 1px solid rgba(165,214,167,.3);
  padding: 18px;
  margin-bottom: 25px;
}
.best3-title {
  color: #a5d6a7;
  font-weight: 900;
  margin-bottom: 12px;
  text-align: center;
}
.best3-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(170px,1fr));
  gap: 8px;
}
.best3-item {
  background: rgba(165,214,167,.08);
  border: 1px solid rgba(165,214,167,.2);
  border-radius: 40px;
  padding: 8px 14px;
  display: flex;
  justify-content: space-between;
  font-size: 0.8rem;
  font-weight: 500;
}
.best3-item.qualified {
  border-color: #a5d6a7;
  background: rgba(165,214,167,.2);
  color: #c8e6c9;
}
/* knockout */
.bracket-round {
  margin-bottom: 35px;
}
.round-title {
  text-align: center;
  margin: 15px 0 18px;
  font-family: 'Bebas Neue', sans-serif;
  font-size: 2rem;
  letter-spacing: 2px;
  color: var(--gold);
}
.ko-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 14px;
}
.ko-card {
  background: var(--panel);
  border-radius: 18px;
  padding: 10px;
  border: 1px solid rgba(255,215,0,.2);
  transition: 0.1s;
}
.ko-card-label {
  text-align: center;
  font-size: 0.7rem;
  color: var(--gold);
  margin-bottom: 8px;
  font-weight: 700;
}
.ko-team {
  padding: 10px 14px;
  margin: 6px 0;
  border-radius: 40px;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  background: rgba(0,0,0,.4);
  border: 1px solid transparent;
  font-weight: 600;
  font-size: 0.85rem;
  transition: 0.2s;
}
.ko-team:hover {
  background: rgba(255,215,0,.15);
  border-color: var(--gold);
  transform: scale(1.01);
}
.ko-team.winner {
  background: linear-gradient(135deg, rgba(0,230,118,.25), rgba(0,230,118,.1));
  border-color: var(--green);
  color: #b9f6ca;
  font-weight: 800;
}
.ko-team.tbd {
  color: var(--muted);
  font-style: italic;
  cursor: default;
  justify-content: center;
}
#champion-display {
  text-align: center;
  padding: 35px 20px;
  margin-top: 35px;
  background: linear-gradient(135deg, rgba(255,215,0,.1), rgba(255,165,0,.05));
  border: 2px solid rgba(255,215,0,.5);
  border-radius: 50px;
  display: none;
  animation: glow 0.8s ease;
}
@keyframes glow {
  from { opacity: 0; transform: scale(0.9); }
  to { opacity: 1; transform: scale(1); }
}
#winner-name {
  font-family: 'Bebas Neue', sans-serif;
  font-size: clamp(2.2rem, 7vw, 4.8rem);
  background: linear-gradient(135deg, var(--gold), #fff2b5);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}
/* progress */
.progress-bar-wrap {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 20px;
  background: rgba(0,0,0,.3);
  padding: 8px 16px;
  border-radius: 60px;
}
.progress-bar {
  flex: 1;
  height: 6px;
  background: #2a2f45;
  border-radius: 10px;
  overflow: hidden;
}
.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, var(--gold), var(--gold2));
  width: 0%;
}
.reset-btn {
  background: rgba(255,80,80,0.2);
  border: 1px solid #ff5555;
  color: #ffaaaa;
  border-radius: 40px;
  padding: 6px 15px;
  font-weight: bold;
  cursor: pointer;
  transition: 0.2s;
}
.reset-btn:hover {
  background: #ff5555;
  color: white;
}
/* share */
.share-bar {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(6,9,18,.98);
  backdrop-filter: blur(16px);
  padding: 12px 16px;
  border-top: 1px solid rgba(255,215,0,.2);
  z-index: 1000;
}
.share-inner {
  display: flex;
  justify-content: center;
  gap: 8px;
  flex-wrap: wrap;
  max-width: 700px;
  margin: auto;
}
.btn-share, .btn-copy, .btn-twitter, .btn-facebook {
  border: none;
  padding: 8px 16px;
  border-radius: 40px;
  font-weight: 700;
  cursor: pointer;
  display: inline-flex;
  gap: 6px;
  align-items: center;
  font-size: 0.8rem;
}
.btn-share { background: #25d366; color: #fff; }
.btn-twitter { background: #1d9bf0; color: #fff; }
.btn-facebook { background: #1877f2; color: #fff; }
.btn-copy { background: var(--panel2); color: var(--text); border: 1px solid var(--gold);}
.toast {
  position: fixed;
  top: 80px;
  left: 50%;
  transform: translateX(-50%) translateY(-20px);
  background: var(--green);
  color: #000;
  padding: 12px 28px;
  border-radius: 60px;
  font-weight: 800;
  z-index: 9999;
  opacity: 0;
  transition: 0.2s;
  pointer-events: none;
}
.toast.show { opacity: 1; transform: translateX(-50%) translateY(0); }
@media (max-width: 600px) {
  .share-inner button { padding: 6px 12px; font-size: 0.7rem; }
  .score-input { width: 40px; }
}
</style>
</head>
<body>

<div class="lang-toggle">
  <button class="lang-btn" id="btn-ar" onclick="setLang('ar')">عربي</button>
  <button class="lang-btn active" id="btn-en" onclick="setLang('en')">EN</button>
</div>
<div class="toast" id="toast"></div>

<header>
  <div class="trophy-wrap"><span class="trophy-icon">🏆</span></div>
  <h1 id="h-title">WORLD CUP 2026</h1>
  <p id="h-sub" class="sub">⚡ Predict scores, knockouts & become the champion maker ⚡</p>
</header>

<div class="tabs">
  <button class="tab-btn active" id="tab1" onclick="showTab('groups')">⚽ <span id="t-groups">Group Stage</span></button>
  <button class="tab-btn" id="tab2" onclick="showTab('ko')">🏆 <span id="t-ko">Knockout</span></button>
</div>

<div class="content">
  <div id="groups-view">
    <div class="progress-bar-wrap">
      <span id="progress-label" style="font-size:0.8rem;">Matches: 0/72</span>
      <div class="progress-bar"><div class="progress-fill" id="progress-fill"></div></div>
      <button class="reset-btn" onclick="resetAllScores()">⟳ Reset</button>
    </div>
    <div class="best3-panel">
      <div class="best3-title" id="best3-title">🏅 Best 3rd-placed teams (Top 8 qualify)</div>
      <div class="best3-grid" id="best3-grid"></div>
    </div>
    <div class="groups-grid" id="groups-grid"></div>
  </div>
  <div id="ko-view" style="display:none;">
    <div id="bracket-container"></div>
    <div id="champion-display">
      <div style="font-size:2rem;">🏆🎉🏆</div>
      <h2 id="champ-label">🏆 PREDICTED CHAMPION 🏆</h2>
      <div id="winner-name"></div>
    </div>
  </div>
</div>

<div class="share-bar">
  <div class="share-inner">
    <span id="share-label">Share:</span>
    <button class="btn-share" onclick="shareWhatsApp()">📱 <span id="btn-wa">WhatsApp</span></button>
    <button class="btn-twitter" onclick="shareTwitter()">🐦 <span id="btn-tw">Twitter/X</span></button>
    <button class="btn-facebook" onclick="shareFacebook()">📘 <span id="btn-fb">Facebook</span></button>
    <button class="btn-copy" onclick="copyLink()">🔗 <span id="btn-cp">Copy Link</span></button>
  </div>
</div>

<script>
// ==================== TRANSLATIONS ====================
const LANG = {
  en:{
    title:'WORLD CUP 2026', sub:'⚡ Predict scores, knockouts & become the champion maker ⚡',
    groups:'Group Stage', ko:'Knockout', group:'Group', pts:'Pts', gd:'GD', gf:'GF',
    round32:'Round of 32', round16:'Round of 16', qf:'Quarterfinals', sf:'Semifinals', final:'Final',
    champion:'🏆 PREDICTED CHAMPION 🏆', share:'Share:', wa:'WhatsApp', tw:'Twitter', fb:'Facebook', cp:'Copy Link',
    copied:'Link copied! 🎉', waText:'🏆 My World Cup 2026 simulation! Predict yours: ', twText:'🏆 My #WorldCup2026 champion prediction! ',
    progress:'Matches', of:'of', best3Title:'🏅 Best 3rd-placed teams (Top 8 qualify)', tbd:'TBD',
    resetConfirm:'Reset all scores & knockout picks?'
  },
  ar:{
    title:'محاكي كأس العالم 2026', sub:'⚡ توقع النتائج، اختر البطل وتحدى أصدقاءك ⚡',
    groups:'دور المجموعات', ko:'خروج المغلوب', group:'المجموعة', pts:'نقاط', gd:'فارق', gf:'أهداف',
    round32:'دور الـ32', round16:'دور الـ16', qf:'ربع النهائي', sf:'نصف النهائي', final:'النهائي',
    champion:'🏆 البطل المتوقع 🏆', share:'مشاركة:', wa:'واتساب', tw:'تويتر', fb:'فيسبوك', cp:'نسخ الرابط',
    copied:'✅ تم نسخ الرابط!', waText:'🏆 توقعاتي لكأس العالم 2026! جرب توقعاتك: ', twText:'🏆 توقعاتي #كأس_العالم_2026 هل تتفوق علي؟ ',
    progress:'المباريات', of:'من', best3Title:'🏅 أفضل الثوالث (أفضل 8 يتأهلون)', tbd:'قادم',
    resetConfirm:'هل تريد مسح كل النتائج والتوقعات؟'
  }
};
let currentLang='en';
const T=(k)=>LANG[currentLang][k]||LANG.en[k]||k;
const TN=(code)=> (LANG[currentLang].teams?.[code] || LANG.en.teams?.[code] || code);
const TEAMS_TR = {
  MEX:'Mexico',RSA:'South Africa',KOR:'South Korea',CZE:'Czechia',CAN:'Canada',BIH:'Bosnia',QAT:'Qatar',SUI:'Switzerland',
  BRA:'Brazil',MAR:'Morocco',HAI:'Haiti',SCO:'Scotland',USA:'USA',PAR:'Paraguay',AUS:'Australia',TUR:'Turkey',
  GER:'Germany',CUW:'Curaçao',CIV:'Ivory Coast',ECU:'Ecuador',NED:'Netherlands',JPN:'Japan',SWE:'Sweden',TUN:'Tunisia',
  BEL:'Belgium',EGY:'Egypt',IRN:'Iran',NZL:'New Zealand',ESP:'Spain',CPV:'Cape Verde',KSA:'Saudi Arabia',URU:'Uruguay',
  FRA:'France',SEN:'Senegal',NOR:'Norway',IRQ:'Iraq',ARG:'Argentina',ALG:'Algeria',AUT:'Austria',JOR:'Jordan',
  POR:'Portugal',COD:'DR Congo',UZB:'Uzbekistan',COL:'Colombia',ENG:'England',CRO:'Croatia',GHA:'Ghana',PAN:'Panama'
};
LANG.en.teams = TEAMS_TR;
LANG.ar.teams = {
  MEX:'المكسيك',RSA:'جنوب أفريقيا',KOR:'كوريا الجنوبية',CZE:'تشيكيا',CAN:'كندا',BIH:'البوسنة',QAT:'قطر',SUI:'سويسرا',
  BRA:'البرازيل',MAR:'المغرب',HAI:'هايتي',SCO:'اسكتلندا',USA:'أمريكا',PAR:'باراغواي',AUS:'أستراليا',TUR:'تركيا',
  GER:'ألمانيا',CUW:'كوراساو',CIV:'ساحل العاج',ECU:'الإكوادور',NED:'هولندا',JPN:'اليابان',SWE:'السويد',TUN:'تونس',
  BEL:'بلجيكا',EGY:'مصر',IRN:'إيران',NZL:'نيوزيلندا',ESP:'إسبانيا',CPV:'الرأس الأخضر',KSA:'السعودية',URU:'أوروغواي',
  FRA:'فرنسا',SEN:'السنغال',NOR:'النرويج',IRQ:'العراق',ARG:'الأرجنتين',ALG:'الجزائر',AUT:'النمسا',JOR:'الأردن',
  POR:'البرتغال',COD:'الكونغو',UZB:'أوزبكستان',COL:'كولومبيا',ENG:'إنجلترا',CRO:'كرواتيا',GHA:'غانا',PAN:'بنما'
};

// ==================== WORLD CUP DATA (12 GROUPS) ====================
const GROUPS_DATA = {
  A:{teams:[{c:'MEX',f:'🇲🇽'},{c:'RSA',f:'🇿🇦'},{c:'KOR',f:'🇰🇷'},{c:'CZE',f:'🇨🇿'}]},
  B:{teams:[{c:'CAN',f:'🇨🇦'},{c:'BIH',f:'🇧🇦'},{c:'QAT',f:'🇶🇦'},{c:'SUI',f:'🇨🇭'}]},
  C:{teams:[{c:'BRA',f:'🇧🇷'},{c:'MAR',f:'🇲🇦'},{c:'HAI',f:'🇭🇹'},{c:'SCO',f:'🏴󠁧󠁢󠁳󠁣󠁴󠁿'}]},
  D:{teams:[{c:'USA',f:'🇺🇸'},{c:'PAR',f:'🇵🇾'},{c:'AUS',f:'🇦🇺'},{c:'TUR',f:'🇹🇷'}]},
  E:{teams:[{c:'GER',f:'🇩🇪'},{c:'CUW',f:'🇨🇼'},{c:'CIV',f:'🇨🇮'},{c:'ECU',f:'🇪🇨'}]},
  F:{teams:[{c:'NED',f:'🇳🇱'},{c:'JPN',f:'🇯🇵'},{c:'SWE',f:'🇸🇪'},{c:'TUN',f:'🇹🇳'}]},
  G:{teams:[{c:'BEL',f:'🇧🇪'},{c:'EGY',f:'🇪🇬'},{c:'IRN',f:'🇮🇷'},{c:'NZL',f:'🇳🇿'}]},
  H:{teams:[{c:'ESP',f:'🇪🇸'},{c:'CPV',f:'🇨🇻'},{c:'KSA',f:'🇸🇦'},{c:'URU',f:'🇺🇾'}]},
  I:{teams:[{c:'FRA',f:'🇫🇷'},{c:'SEN',f:'🇸🇳'},{c:'NOR',f:'🇳🇴'},{c:'IRQ',f:'🇮🇶'}]},
  J:{teams:[{c:'ARG',f:'🇦🇷'},{c:'ALG',f:'🇩🇿'},{c:'AUT',f:'🇦🇹'},{c:'JOR',f:'🇯🇴'}]},
  K:{teams:[{c:'POR',f:'🇵🇹'},{c:'COD',f:'🇨🇩'},{c:'UZB',f:'🇺🇿'},{c:'COL',f:'🇨🇴'}]},
  L:{teams:[{c:'ENG',f:'🏴󠁧󠁢󠁥󠁮󠁧󠁿'},{c:'CRO',f:'🇭🇷'},{c:'GHA',f:'🇬🇭'},{c:'PAN',f:'🇵🇦'}]}
};

let gameData = { scores: {}, koWinners: {}, standings: {} };
let best3rds = [];

// ==================== UTILITIES ====================
function saveToLocalStorage() { localStorage.setItem('wc2026_data', JSON.stringify({ scores: gameData.scores, koWinners: gameData.koWinners })); }
function loadFromLocalStorage() {
  const raw = localStorage.getItem('wc2026_data');
  if (raw) { try { const d = JSON.parse(raw); gameData.scores = d.scores || {}; gameData.koWinners = d.koWinners || {}; } catch(e){} }
}
function resetAllScores() {
  if(confirm(T('resetConfirm'))) { gameData.scores = {}; gameData.koWinners = {}; for(let k in GROUPS_DATA) calculateStandings(k); computeBest3rds(); renderGroupsFull(); renderBest3Panel(); updateBracket(); updateProgress(); saveToLocalStorage(); showToast("✓ Reset done"); }
}
function showToast(msg){ const t=document.getElementById('toast'); t.textContent=msg; t.classList.add('show'); setTimeout(()=>t.classList.remove('show'),2500); }
function setLang(lang) { currentLang=lang; document.documentElement.lang=lang; document.documentElement.dir=lang==='ar'?'rtl':'ltr'; document.getElementById('btn-ar').classList.toggle('active',lang==='ar'); document.getElementById('btn-en').classList.toggle('active',lang==='en'); applyTranslations(); renderGroupsFull(); renderBest3Panel(); updateBracket(); updateProgress(); }
function applyTranslations() { document.getElementById('h-title').innerText=T('title'); document.getElementById('h-sub').innerText=T('sub'); document.getElementById('t-groups').innerText=T('groups'); document.getElementById('t-ko').innerText=T('ko'); document.getElementById('share-label').innerText=T('share'); document.getElementById('btn-wa').innerText=T('wa'); document.getElementById('btn-tw').innerText=T('tw'); document.getElementById('btn-fb').innerText=T('fb'); document.getElementById('btn-cp').innerText=T('cp'); document.getElementById('champ-label').innerHTML=T('champion'); document.getElementById('best3-title').innerHTML=T('best3Title'); }

// ==================== STANDINGS ====================
function calculateStandings(gKey) {
  const base = GROUPS_DATA[gKey].teams;
  let teams = base.map(t => ({ ...t, pts:0, gd:0, gf:0, ga:0 }));
  for(let mId in gameData.scores) {
    if(!mId.startsWith(gKey+'_')) continue;
    let parts=mId.split('_'), c1=parts[1], c2=parts[2];
    let s=gameData.scores[mId];
    if(s.s1===undefined || s.s2===undefined) continue;
    let t1=teams.find(t=>t.c===c1), t2=teams.find(t=>t.c===c2);
    if(!t1||!t2) continue;
    t1.gf+=s.s1; t1.ga+=s.s2; t1.gd+=(s.s1-s.s2);
    t2.gf+=s.s2; t2.ga+=s.s1; t2.gd+=(s.s2-s.s1);
    if(s.s1>s.s2) t1.pts+=3; else if(s.s2>s.s1) t2.pts+=3; else { t1.pts+=1; t2.pts+=1; }
  }
  teams.sort((a,b)=>b.pts-a.pts || b.gd-a.gd || b.gf-a.gf);
  gameData.standings[gKey] = teams;
}
function computeBest3rds() {
  let thirds=[];
  for(let k in GROUPS_DATA) { let st=gameData.standings[k]; if(st && st[2]) thirds.push({...st[2], group:k}); }
  thirds.sort((a,b)=>b.pts-a.pts || b.gd-a.gd || b.gf-a.gf || a.group.localeCompare(b.group));
  best3rds = thirds;
}
function renderBest3Panel() {
  computeBest3rds();
  const grid=document.getElementById('best3-grid');
  if(!grid) return;
  let all=Object.keys(GROUPS_DATA);
  grid.innerHTML = all.map(k=>{
    let st=gameData.standings[k];
    let t3 = (st && st[2]) ? st[2] : null;
    let rank = t3 ? best3rds.findIndex(x=>x.c===t3.c && x.group===k)+1 : 99;
    let qualified = (rank>=1 && rank<=8);
    return `<div class="best3-item ${qualified?'qualified':''}"><span>${t3?t3.f+' '+TN(t3.c):'—'} (${T('group')} ${k})</span><span>${t3?t3.pts+' pts':''}${qualified?' ✓':''}</span></div>`;
  }).join('');
}

// ==================== RENDER GROUPS ====================
function renderGroupsFull() {
  const grid=document.getElementById('groups-grid');
  grid.innerHTML='';
  for(let k in GROUPS_DATA) {
    let g=GROUPS_DATA[k];
    let dir=currentLang==='ar'?'right':'left';
    let card=document.createElement('div'); card.className='group-card';
    card.innerHTML=`<div class="group-header">${T('group')} ${k}</div>
      <table class="standings-mini" id="table-${k}"><thead><tr><th>#</th><th style="text-align:${dir}">${T('team')}</th><th>${T('pts')}</th><th>${T('gd')}</th><th>${T('gf')}</th></tr></thead><tbody>${g.teams.map((t,i)=>`<tr><td>${i+1}</td><td style="text-align:${dir}">${t.f} ${TN(t.c)}</td><td><span class="pts-cell">0</span></td><td>0</td><td>0</td></tr>`).join('')}</tbody></table>
      <div class="matches-list">${genMatchesHTML(k,g.teams)}</div>`;
    grid.appendChild(card);
    calculateStandings(k);
    updateGroupTableUI(k);
  }
}
function genMatchesHTML(gKey,teams){
  let html='';
  for(let i=0;i<teams.length;i++) for(let j=i+1;j<teams.length;j++){
    let mId=`${gKey}_${teams[i].c}_${teams[j].c}`;
    let s=gameData.scores[mId]||{};
    html+=`<div class="match-item"><div class="match-team">${teams[i].f} ${TN(teams[i].c)}</div>
    <input type="number" min="0" max="20" class="score-input" data-mid="${mId}" data-side="s1" oninput="onScore('${gKey}',this)" value="${s.s1!==undefined?s.s1:''}">
    <span class="vs-sep">-</span>
    <input type="number" min="0" max="20" class="score-input" data-mid="${mId}" data-side="s2" oninput="onScore('${gKey}',this)" value="${s.s2!==undefined?s.s2:''}">
    <div class="match-team right">${TN(teams[j].c)} ${teams[j].f}</div></div>`;
  }
  return html;
}
function updateGroupTableUI(gKey) {
  let st=gameData.standings[gKey]; if(!st) return;
  let tbl=document.querySelector(`#table-${gKey} tbody`);
  if(!tbl) return;
  let dir=currentLang==='ar'?'right':'left';
  tbl.innerHTML=st.map((t,i)=>{
    let gdStr=(t.gd>0?'+':'')+t.gd;
    let gdColor=t.gd>0?'#a5d6a7':t.gd<0?'#ef9a9a':'#ccc';
    return `<tr><td class="${i===0?'rank-1':i===1?'rank-2':''}">${i+1}</td><td style="text-align:${dir}">${t.f} ${TN(t.c)}</td><td><span class="pts-cell">${t.pts}</span></td><td style="color:${gdColor}">${gdStr}</td><td>${t.gf}</td></tr>`;
  }).join('');
}
function onScore(gKey,el){
  let mId=el.dataset.mid, side=el.dataset.side, v=parseInt(el.value);
  if(!gameData.scores[mId]) gameData.scores[mId]={};
  if(!isNaN(v) && v>=0) gameData.scores[mId][side]=v;
  else delete gameData.scores[mId][side];
  calculateStandings(gKey);
  updateGroupTableUI(gKey);
  computeBest3rds();
  renderBest3Panel();
  updateBracket();
  updateProgress();
  saveToLocalStorage();
}
function updateProgress(){
  let filled=0,total=0;
  for(let k in GROUPS_DATA){
    let t=GROUPS_DATA[k].teams;
    for(let i=0;i<t.length;i++) for(let j=i+1;j<t.length;j++){
      total++;
      let mId=`${k}_${t[i].c}_${t[j].c}`;
      let s=gameData.scores[mId];
      if(s && s.s1!==undefined && s.s2!==undefined) filled++;
    }
  }
  let pct=Math.round(filled/total*100);
  document.getElementById('progress-fill').style.width=pct+'%';
  document.getElementById('progress-label').innerHTML=`${T('progress')}: ${filled} ${T('of')} ${total}`;
}

// ==================== KNOCKOUT (REALISTIC R32) ====================
function getQualifiedTeams(){
  let winners=[], runners=[];
  for(let k in GROUPS_DATA){
    let st=gameData.standings[k];
    if(st && st[0]) winners.push({...st[0], group:k, type:'W'});
    if(st && st[1]) runners.push({...st[1], group:k, type:'R'});
  }
  let thirds=best3rds.slice(0,8).map((t,idx)=>({...t, type:'T', rank3:idx+1}));
  return { winners, runners, thirds };
}
function buildR32Matches(){
  let {winners, runners, thirds}=getQualifiedTeams();
  if(winners.length<12 || runners.length<12 || thirds.length<8) return [];
  // pairing based on realistic rules: 1st vs 3rd/2nd without winner-winner clashes
  let matches=[];
  // map winners to specific opponents
  let orderWinners = ['A','B','C','D','E','F','G','H','I','J','K','L'];
  let thirdPool = [...thirds];
  let runnerPool = [...runners];
  // 1A-1F vs thirds / runners
  matches.push({a:winners.find(w=>w.group==='A'), b:thirdPool[0] || thirdPool[0]});
  matches.push({a:winners.find(w=>w.group==='B'), b:thirdPool[1] || runnerPool[0]});
  matches.push({a:winners.find(w=>w.group==='C'), b:runnerPool.find(r=>r.group==='D') || runnerPool[0]});
  matches.push({a:winners.find(w=>w.group==='D'), b:runnerPool.find(r=>r.group==='E') || runnerPool[1]});
  matches.push({a:winners.find(w=>w.group==='E'), b:runnerPool.find(r=>r.group==='F') || runnerPool[2]});
  matches.push({a:winners.find(w=>w.group==='F'), b:runnerPool.find(r=>r.group==='G') || runnerPool[3]});
  matches.push({a:winners.find(w=>w.group==='G'), b:runnerPool.find(r=>r.group==='H') || runnerPool[4]});
  matches.push({a:winners.find(w=>w.group==='H'), b:thirdPool[2] || thirdPool[2]});
  matches.push({a:winners.find(w=>w.group==='I'), b:runnerPool.find(r=>r.group==='J') || runnerPool[5]});
  matches.push({a:winners.find(w=>w.group==='J'), b:runnerPool.find(r=>r.group==='I') || runnerPool[6]});
  matches.push({a:winners.find(w=>w.group==='K'), b:runnerPool.find(r=>r.group==='K') || runnerPool[7]});
  matches.push({a:winners.find(w=>w.group==='L'), b:thirdPool[3] || thirdPool[3]});
  // remaining runners vs runners / thirds
  let usedRunners=new Set();
  matches.forEach(m=>{ if(m.b && m.b.type==='R') usedRunners.add(m.b.group); });
  let leftRunners = runners.filter(r=>!usedRunners.has(r.group));
  let leftThirds = thirds.slice(4);
  matches.push({a:leftRunners[0] || runners[0], b:leftRunners[1] || leftThirds[0]});
  matches.push({a:leftThirds[1] || leftRunners[2], b:leftThirds[2] || leftRunners[3]});
  matches.push({a:leftThirds[3] || leftRunners[4], b:leftThirds[4] || leftThirds[5]});
  // ensure exactly 16 matches
  while(matches.length<16) matches.push({a:null,b:null});
  return matches.slice(0,16).map((m,idx)=>({aRef:m.a, bRef:m.b, label:`R32-${idx+1}`}));
}
function resolveTeamObj(team){
  if(!team) return null;
  return { c:team.c, f:team.f, group:team.group, pts:team.pts };
}
function updateBracket(){
  computeBest3rds();
  let r32matches = buildR32Matches();
  let container = document.getElementById('bracket-container');
  if(!container) return;
  container.innerHTML = '';
  let r32Winners = r32matches.map((m,idx)=>{
    let winKey = `r32_${idx}`;
    if(gameData.koWinners[winKey]) return gameData.koWinners[winKey];
    return null;
  });
  function renderRound(title, matchesArr, roundPrefix, nextRoundFn=null){
    if(matchesArr.length===0) return;
    let html=`<div class="bracket-round"><h2 class="round-title">${title}</h2><div class="ko-grid">`;
    matchesArr.forEach((match, idx)=>{
      let tA = match.aRef, tB = match.bRef;
      let winKey = `${roundPrefix}_${idx}`;
      let currentWinner = gameData.koWinners[winKey];
      let teamA_disp = tA ? resolveTeamObj(tA) : null;
      let teamB_disp = tB ? resolveTeamObj(tB) : null;
      let winnerExists = currentWinner ? resolveTeamObj(currentWinner) : null;
      html+=`<div class="ko-card"><div class="ko-card-label">${match.label || `Match ${idx+1}`}</div>`;
      html+=`<div class="ko-team ${winnerExists && winnerExists.c===teamA_disp?.c ? 'winner' : ''}" onclick="pickWinnerSimple('${roundPrefix}',${idx},'left','${tA ? JSON.stringify(tA).replace(/"/g,'&quot;') : ''}')">${teamA_disp ? `${teamA_disp.f} ${TN(teamA_disp.c)}` : '🔮 '+T('tbd')}</div>`;
      html+=`<div class="ko-team ${winnerExists && winnerExists.c===teamB_disp?.c ? 'winner' : ''}" onclick="pickWinnerSimple('${roundPrefix}',${idx},'right','${tB ? JSON.stringify(tB).replace(/"/g,'&quot;') : ''}')">${teamB_disp ? `${teamB_disp.f} ${TN(teamB_disp.c)}` : '🔮 '+T('tbd')}</div>`;
      html+=`</div>`;
    });
    html+=`</div></div>`;
    container.innerHTML += html;
  }
  // R32
  let r32list = r32matches.map((m,i)=>({ aRef:m.aRef, bRef:m.bRef, label:m.label }));
  renderRound(T('round32'), r32list, 'r32');
  // R16 (winners pairing)
  let r16matches = [];
  for(let i=0;i<8;i++) r16matches.push({ aRef: gameData.koWinners[`r32_${i*2}`], bRef: gameData.koWinners[`r32_${i*2+1}`], label:`R16-${i+1}` });
  renderRound(T('round16'), r16matches, 'r16');
  // QF
  let qfmatches = [];
  for(let i=0;i<4;i++) qfmatches.push({ aRef: gameData.koWinners[`r16_${i*2}`], bRef: gameData.koWinners[`r16_${i*2+1}`], label:`QF-${i+1}` });
  renderRound(T('qf'), qfmatches, 'qf');
  // SF
  let sfmatches = [];
  for(let i=0;i<2;i++) sfmatches.push({ aRef: gameData.koWinners[`qf_${i*2}`], bRef: gameData.koWinners[`qf_${i*2+1}`], label:`SF-${i+1}` });
  renderRound(T('sf'), sfmatches, 'sf');
  // Final
  let finalmatch = [{ aRef: gameData.koWinners['sf_0'], bRef: gameData.koWinners['sf_1'], label:'FINAL' }];
  renderRound(T('final'), finalmatch, 'f');
  let champ = gameData.koWinners['f_0'];
  let champDiv = document.getElementById('champion-display');
  if(champ){
    champDiv.style.display='block';
    document.getElementById('winner-name').innerHTML = `${champ.f} ${TN(champ.c)} 🏆`;
  } else champDiv.style.display='none';
}
function pickWinnerSimple(round, idx, side, teamJsonRaw){
  let teamObj = null;
  try{ if(teamJsonRaw && teamJsonRaw!=='null') teamObj = JSON.parse(teamJsonRaw); }catch(e){}
  if(!teamObj) return;
  let winKey = `${round}_${idx}`;
  gameData.koWinners[winKey] = teamObj;
  // clear downstream rounds
  let roundsOrder = ['r32','r16','qf','sf','f'];
  let currentIdx = roundsOrder.indexOf(round);
  if(currentIdx>=0){
    for(let i=currentIdx+1; i<roundsOrder.length; i++){
      let prefix = roundsOrder[i];
      for(let key in gameData.koWinners){
        if(key.startsWith(prefix)) delete gameData.koWinners[key];
      }
    }
  }
  updateBracket();
  saveToLocalStorage();
}
// ==================== SHARE & PERSIST ====================
function generateShareURL(){
  let payload = { scores: gameData.scores, koWinners: gameData.koWinners, lang: currentLang };
  let enc = btoa(encodeURIComponent(JSON.stringify(payload)));
  let url = new URL(window.location.href.split('?')[0]);
  url.searchParams.set('p', enc);
  return url.href;
}
function copyLink(){ let url=generateShareURL(); navigator.clipboard.writeText(url).then(()=>showToast(T('copied'))); }
function shareWhatsApp(){ window.open(`https://wa.me/?text=${encodeURIComponent(T('waText')+generateShareURL())}`,'_blank');}
function shareTwitter(){ window.open(`https://twitter.com/intent/tweet?text=${encodeURIComponent(T('twText')+generateShareURL())}`,'_blank');}
function shareFacebook(){ window.open(`https://www.facebook.com/sharer/sharer.php?u=${encodeURIComponent(generateShareURL())}`,'_blank');}
function loadFromURL(){
  let params = new URLSearchParams(window.location.search).get('p');
  if(!params) return;
  try{
    let decoded = JSON.parse(decodeURIComponent(atob(params)));
    if(decoded.scores) gameData.scores = decoded.scores;
    if(decoded.koWinners) gameData.koWinners = decoded.koWinners;
    let lg = decoded.lang || 'en';
    for(let k in GROUPS_DATA) calculateStandings(k);
    computeBest3rds();
    if(lg !== currentLang) setLang(lg);
    else { renderGroupsFull(); renderBest3Panel(); updateBracket(); updateProgress(); }
    saveToLocalStorage();
  }catch(e){}
}
function showTab(tab){
  document.getElementById('groups-view').style.display = tab==='groups'?'block':'none';
  document.getElementById('ko-view').style.display = tab==='ko'?'block':'none';
  document.getElementById('tab1').classList.toggle('active',tab==='groups');
  document.getElementById('tab2').classList.toggle('active',tab==='ko');
  if(tab==='ko') updateBracket();
}
// ==================== INIT ====================
function init(){
  loadFromLocalStorage();
  for(let k in GROUPS_DATA) calculateStandings(k);
  computeBest3rds();
  renderGroupsFull();
  renderBest3Panel();
  updateBracket();
  updateProgress();
  loadFromURL();
  setLang('en');
}
init();
</script>
</body>
</html>
```
