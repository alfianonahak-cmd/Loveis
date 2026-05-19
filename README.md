# Loveis
Loveeeeeee
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>💌 Be My Girl?</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,700;1,400&family=Lato:wght@300;400&display=swap" rel="stylesheet">
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    min-height: 100vh;
    background: #0d0012;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Lato', sans-serif;
    overflow: hidden;
    position: relative;
  }

  /* Starfield */
  .stars {
    position: fixed; inset: 0; pointer-events: none; z-index: 0;
  }
  .star {
    position: absolute;
    border-radius: 50%;
    background: white;
    animation: twinkle var(--d) ease-in-out infinite alternate;
  }
  @keyframes twinkle {
    from { opacity: 0.1; transform: scale(0.8); }
    to   { opacity: 0.9; transform: scale(1.2); }
  }

  /* Floating petals */
  .petal {
    position: fixed;
    font-size: 20px;
    animation: fall linear infinite;
    pointer-events: none;
    z-index: 0;
  }
  @keyframes fall {
    from { transform: translateY(-60px) rotate(0deg); opacity: 1; }
    to   { transform: translateY(110vh) rotate(720deg); opacity: 0; }
  }

  /* Card */
  .card {
    position: relative; z-index: 10;
    background: rgba(255,255,255,0.06);
    backdrop-filter: blur(18px);
    border: 1px solid rgba(255,200,220,0.25);
    border-radius: 28px;
    padding: 52px 44px 48px;
    text-align: center;
    max-width: 400px;
    width: 90vw;
    box-shadow: 0 0 80px rgba(255,100,160,0.15), 0 0 30px rgba(255,100,160,0.08);
    animation: fadeUp 1.2s cubic-bezier(.22,1,.36,1) both;
  }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(40px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* Heart */
  .heart-wrap {
    margin-bottom: 24px;
    animation: heartbeat 1.4s ease-in-out infinite;
  }
  @keyframes heartbeat {
    0%,100% { transform: scale(1); }
    14%      { transform: scale(1.18); }
    28%      { transform: scale(1); }
    42%      { transform: scale(1.12); }
    56%      { transform: scale(1); }
  }
  .heart {
    font-size: 64px;
    display: block;
    filter: drop-shadow(0 0 16px #ff6eb4);
  }

  /* Question text */
  .question {
    font-family: 'Playfair Display', serif;
    font-style: italic;
    font-size: clamp(15px, 4.5vw, 20px);
    color: rgba(255,220,235,0.75);
    letter-spacing: 0.04em;
    margin-bottom: 6px;
    animation: fadeIn 1.4s 0.4s both;
  }
  .main-text {
    font-family: 'Playfair Display', serif;
    font-weight: 700;
    font-size: clamp(32px, 10vw, 52px);
    color: #fff;
    letter-spacing: -0.01em;
    line-height: 1.1;
    margin-bottom: 36px;
    text-shadow: 0 0 40px rgba(255,120,170,0.6);
    animation: fadeIn 1.4s 0.6s both;
  }
  @keyframes fadeIn {
    from { opacity: 0; } to { opacity: 1; }
  }

  /* Buttons */
  .btn-row {
    display: flex;
    gap: 16px;
    justify-content: center;
    align-items: center;
    position: relative;
  }

  .btn {
    font-family: 'Lato', sans-serif;
    font-size: 17px;
    font-weight: 400;
    letter-spacing: 0.08em;
    padding: 14px 38px;
    border-radius: 50px;
    border: none;
    cursor: pointer;
    transition: transform 0.15s, box-shadow 0.15s;
    position: relative;
  }

  .btn-yes {
    background: linear-gradient(135deg, #ff6eb4, #ff3d84);
    color: white;
    box-shadow: 0 4px 24px rgba(255,60,130,0.45);
    animation: fadeIn 1.4s 0.9s both;
  }
  .btn-yes:hover {
    transform: scale(1.07);
    box-shadow: 0 6px 32px rgba(255,60,130,0.65);
  }
  .btn-yes:active { transform: scale(0.98); }

  .btn-no {
    background: rgba(255,255,255,0.08);
    color: rgba(255,200,220,0.8);
    border: 1px solid rgba(255,200,220,0.25);
    transition: transform 0.25s cubic-bezier(.34,1.56,.64,1), opacity 0.2s;
    animation: fadeIn 1.4s 1.1s both;
  }
  .btn-no:hover { opacity: 0.85; }

  /* Yes explosion overlay */
  .yes-overlay {
    display: none;
    position: fixed; inset: 0; z-index: 50;
    background: #fff;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 32px;
  }
  .yes-overlay.show { display: flex; animation: whiteFlash 0.5s cubic-bezier(.22,1,.36,1); }
  @keyframes whiteFlash {
    from { opacity: 0; }
    to   { opacity: 1; }
  }
  .yes-card {
    position: relative; z-index: 2;
    background: rgba(255,255,255,0.85);
    border-radius: 28px;
    padding: 44px 40px 40px;
    max-width: 360px;
    width: 88vw;
    box-shadow: 0 8px 48px rgba(255,80,140,0.18);
    border: 1px solid rgba(255,160,200,0.3);
    animation: cardPop 0.7s 0.2s cubic-bezier(.34,1.56,.64,1) both;
  }
  @keyframes cardPop {
    from { opacity: 0; transform: scale(0.6) translateY(30px); }
    to   { opacity: 1; transform: scale(1) translateY(0); }
  }
  .yes-rose {
    font-size: 56px;
    display: block;
    margin-bottom: 8px;
    animation: roseSpin 1s 0.4s cubic-bezier(.34,1.56,.64,1) both;
  }
  @keyframes roseSpin {
    from { transform: rotate(-20deg) scale(0.4); opacity: 0; }
    to   { transform: rotate(0deg) scale(1); opacity: 1; }
  }
  .yes-title {
    font-family: 'Playfair Display', serif;
    font-weight: 700;
    font-size: clamp(22px, 7vw, 34px);
    color: #e0246a;
    margin-bottom: 10px;
    line-height: 1.2;
    animation: fadeSlide 0.6s 0.5s both;
  }
  .yes-sub {
    font-family: 'Lato', sans-serif;
    font-size: 15px;
    color: #c0456a;
    font-weight: 400;
    letter-spacing: 0.03em;
    line-height: 1.7;
    animation: fadeSlide 0.6s 0.7s both;
  }
  @keyframes fadeSlide {
    from { opacity: 0; transform: translateY(12px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* Flying hearts */
  .fly-heart {
    position: fixed;
    pointer-events: none;
    z-index: 1;
    animation: flyUp linear forwards;
    user-select: none;
  }
  @keyframes flyUp {
    0%   { transform: translateY(0) rotate(var(--rot)) scale(1); opacity: 1; }
    80%  { opacity: 1; }
    100% { transform: translateY(-110vh) rotate(calc(var(--rot) + 180deg)) scale(0.6); opacity: 0; }
  }

  /* Falling roses */
  .fly-rose {
    position: fixed;
    pointer-events: none;
    z-index: 1;
    animation: rosefall linear forwards;
    user-select: none;
  }
  @keyframes rosefall {
    0%   { transform: translateY(-60px) rotate(0deg) scale(1); opacity: 1; }
    100% { transform: translateY(110vh) rotate(540deg) scale(0.7); opacity: 0; }
  }
</style>
</head>
<body>

<!-- Stars -->
<div class="stars" id="stars"></div>

<!-- Petals -->
<div id="petals"></div>

<!-- Main card -->
<div class="card">
  <div class="heart-wrap"><span class="heart">💗</span></div>
  <p class="question">ada sesuatu yang ingin aku tanyakan...</p>
  <div class="main-text">Be My<br>Girl? 🌸</div>
  <div class="btn-row">
    <button class="btn btn-yes" onclick="sayYes()">Yes 💕</button>
    <button class="btn btn-no" id="noBtn" onclick="runAway()">No</button>
  </div>
</div>

<!-- Yes response -->
<div class="yes-overlay" id="yesOverlay">
  <div class="yes-card">
    <span class="yes-rose">🌹</span>
    <div class="yes-title">Selamat Bocah Nakalku!! 🎉</div>
    <p class="yes-sub">Semoga langgeng sama Bapak ini 🌹</p>
  </div>
</div>

<script>
// ---- Stars ----
const starsEl = document.getElementById('stars');
for (let i = 0; i < 120; i++) {
  const s = document.createElement('div');
  s.className = 'star';
  const sz = Math.random() * 2.5 + 0.5;
  s.style.cssText = `width:${sz}px;height:${sz}px;top:${Math.random()*100}%;left:${Math.random()*100}%;--d:${(Math.random()*3+1.5).toFixed(1)}s;animation-delay:${(Math.random()*3).toFixed(1)}s`;
  starsEl.appendChild(s);
}

// ---- Petals ----
const petalsEl = document.getElementById('petals');
const petalEmojis = ['🌸','🌺','🌼','🌷','✨'];
for (let i = 0; i < 14; i++) {
  const p = document.createElement('div');
  p.className = 'petal';
  p.textContent = petalEmojis[i % petalEmojis.length];
  const dur = (Math.random() * 8 + 6).toFixed(1);
  const delay = (Math.random() * 10).toFixed(1);
  p.style.cssText = `left:${Math.random()*100}%;animation-duration:${dur}s;animation-delay:-${delay}s;font-size:${Math.floor(Math.random()*14+14)}px`;
  petalsEl.appendChild(p);
}

// ---- No button runs away ----
let noSize = 17;
function runAway() {
  const btn = document.getElementById('noBtn');
  const card = btn.closest('.card');
  const cardRect = card.getBoundingClientRect();
  const btnRect = btn.getBoundingClientRect();

  // Shrink text slightly each time
  noSize = Math.max(10, noSize - 1.5);
  btn.style.fontSize = noSize + 'px';

  // Random teleport within card bounds, avoiding yes button area
  const margin = 50;
  const maxX = cardRect.width - btn.offsetWidth - margin;
  const maxY = cardRect.height - btn.offsetHeight - margin;
  const randX = Math.random() * maxX + margin/2;
  const randY = Math.random() * maxY + margin/2;

  btn.style.position = 'absolute';
  btn.style.left = randX + 'px';
  btn.style.top  = randY + 'px';
  btn.style.transform = `rotate(${(Math.random()*30-15).toFixed(0)}deg)`;
}

// Make card relatively positioned so absolute children work
document.querySelector('.card').style.position = 'relative';

// ---- Yes ----
function sayYes() {
  document.getElementById('yesOverlay').classList.add('show');

  const heartEmojis = ['💖','💗','💕','💓','❤️','🩷','💞','💝'];
  const roseEmojis  = ['🌹','🌸','🌺','🌷'];

  // Spawn flying hearts continuously
  let heartCount = 0;
  const heartInterval = setInterval(() => {
    for (let b = 0; b < 3; b++) {
      const h = document.createElement('div');
      h.className = 'fly-heart';
      const sz = Math.floor(Math.random() * 28 + 20);
      const rot = (Math.random() * 40 - 20).toFixed(0);
      const dur = (Math.random() * 3 + 2.5).toFixed(1);
      const delay = (Math.random() * 0.6).toFixed(2);
      h.textContent = heartEmojis[Math.floor(Math.random() * heartEmojis.length)];
      h.style.cssText = `left:${Math.random()*100}vw;bottom:0;font-size:${sz}px;--rot:${rot}deg;animation-duration:${dur}s;animation-delay:${delay}s`;
      document.body.appendChild(h);
      setTimeout(() => h.remove(), (parseFloat(dur) + parseFloat(delay) + 0.5) * 1000);
    }
    heartCount++;
    if (heartCount > 40) clearInterval(heartInterval);
  }, 180);

  // Spawn falling roses from top
  let roseCount = 0;
  const roseInterval = setInterval(() => {
    const r = document.createElement('div');
    r.className = 'fly-rose';
    const sz = Math.floor(Math.random() * 22 + 18);
    const dur = (Math.random() * 4 + 3).toFixed(1);
    const delay = (Math.random() * 0.5).toFixed(2);
    r.textContent = roseEmojis[Math.floor(Math.random() * roseEmojis.length)];
    r.style.cssText = `left:${Math.random()*100}vw;top:0;font-size:${sz}px;animation-duration:${dur}s;animation-delay:${delay}s`;
    document.body.appendChild(r);
    setTimeout(() => r.remove(), (parseFloat(dur) + parseFloat(delay) + 0.5) * 1000);
    roseCount++;
    if (roseCount > 35) clearInterval(roseInterval);
  }, 220);
}
</script>
</body>
</html>
