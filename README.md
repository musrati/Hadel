<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Surprise 🌹</title>
  <style>
    :root{
      --bg1: #0f172a;
      --bg2: #0b1220;
      --accent: #ff6b81;
      --glass: rgba(255,255,255,0.06);
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family: 'Segoe UI', Roboto, system-ui, -apple-system, sans-serif;
      background: radial-gradient(1000px 600px at 10% 20%, rgba(255,107,129,0.06), transparent),
                  linear-gradient(180deg,var(--bg1),var(--bg2));
      color: #fff;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:30px;
    }
    .card{
      width:min(860px,92vw);
      background: linear-gradient(180deg, rgba(255,255,255,0.03), rgba(255,255,255,0.02));
      border-radius:20px;
      padding:48px;
      text-align:center;
      box-shadow: 0 10px 30px rgba(2,6,23,0.6);
      backdrop-filter: blur(6px) saturate(120%);
      position:relative;
      overflow:hidden;
    }
    h1.name{
      margin:0 0 18px 0;
      font-weight:800;
      font-size:64px;
      letter-spacing:2px;
      line-height:0.9;
      text-transform:uppercase;
      color:transparent;
      -webkit-text-stroke: 1px rgba(255,255,255,0.06);
      background: linear-gradient(90deg,#fff, #ffd1dc);
      -webkit-background-clip: text;
      background-clip: text;
      filter: drop-shadow(0 6px 18px rgba(255,107,129,0.08));
    }
    p.subtitle{
      margin:0 0 28px 0;
      opacity:0.9;
      font-size:18px;
    }
    .btn{
      --btn-h:64px;
      height:var(--btn-h);
      display:inline-flex;
      align-items:center;
      justify-content:center;
      padding:0 26px;
      border-radius:999px;
      background: linear-gradient(90deg, rgba(255,107,129,0.95), rgba(255,173,188,0.95));
      color:#111;
      font-weight:700;
      font-size:18px;
      border:none;
      cursor:pointer;
      transform:translateY(0);
      transition: transform .18s ease, box-shadow .18s ease;
      box-shadow: 0 8px 30px rgba(255,107,129,0.12);
    }
    .btn:active{ transform: translateY(2px) scale(.995) }

    .heart{
      display:inline-block;
      width:26px;height:26px;margin-left:10px;
      transform:translateY(0);
      transition: transform .2s ease;
    }
    .btn.celebrate .heart{ transform: scale(1.15) translateY(-2px) }

    /* reveal area */
    .reveal{
      margin-top:36px;
      min-height:120px;
      display:flex;
      align-items:center;
      justify-content:center;
      pointer-events:none;
    }
    .message{
      font-size:48px;
      font-weight:900;
      opacity:0;
      transform: translateY(18px) scale(.98);
      transition: opacity .44s cubic-bezier(.2,.9,.2,1), transform .44s cubic-bezier(.2,.9,.2,1);
      text-shadow: 0 14px 40px rgba(0,0,0,0.6);
      -webkit-text-stroke: 0px rgba(0,0,0,0.08);
      display:flex;align-items:center;gap:12px;
    }
    .message.show{ opacity:1; transform: translateY(0) scale(1) }
    .message .love{
      color:var(--accent);
      filter: drop-shadow(0 6px 18px rgba(255,107,129,0.18));
    }
    /* small tip */
    .hint{position:absolute;right:18px;top:18px;font-size:12px;opacity:0.6}

    /* Confetti canvas full */
    #confetti{ position:absolute; inset:0; pointer-events:none; z-index:4 }

    @media (max-width:520px){
      h1.name{ font-size:36px }
      .message{ font-size:30px }
      .btn{ height:56px }
    }
  </style>
</head>
<body>
  <div class="card">
    <div class="hint">Replace <code>HER_NAME</code> in the file with her real name</div>
    <h1 class="name">HER_NAME</h1>
    <p class="subtitle">Click the button below — watch the magic ✨</p>

    <button class="btn" id="showBtn">Open <svg class="heart" viewBox="0 0 24 24"><path fill="currentColor" d="M12 21s-7.5-4.35-9.5-7.1C.75 9.9 4.4 6 8.5 7.2 10.17 7.78 11 9 12 10.3c1-1.3 1.83-2.52 3.5-3.1C19.6 6 23.25 9.9 21.5 13.9 19.5 16.65 12 21 12 21z"/></svg></button>

    <div class="reveal">
      <div class="message" id="message"><span class="love">I ♥ U</span><span id="text">I love you</span></div>
    </div>

    <canvas id="confetti"></canvas>
  </div>

  <script>
    // --- Simple confetti particle system (no libraries) ---
    const canvas = document.getElementById('confetti');
    const ctx = canvas.getContext('2d');
    let W=0,H=0, particles=[];
    function resize(){ W=canvas.width=canvas.offsetWidth; H=canvas.height=canvas.offsetHeight }
    new ResizeObserver(resize).observe(canvas);

    function rand(min,max){return Math.random()*(max-min)+min}
    function makeParticles(x,y,count){
      for(let i=0;i<count;i++){
        particles.push({
          x:x, y:y,
          vx: rand(-6,6), vy: rand(-10,-2),
          size: rand(6,12),
          angle: rand(0,Math.PI*2),
          angularVel: rand(-0.2,0.2),
          life: rand(60,120),
          color: ['#ff6b81','#ffd1dc','#fff3f6','#ffc6e0'][Math.floor(rand(0,4))]
        });
      }
    }
    function update(){
      ctx.clearRect(0,0,W,H);
      for(let i=particles.length-1;i>=0;i--){
        const p=particles[i];
        p.vy += 0.25; // gravity
        p.x += p.vx; p.y += p.vy; p.angle += p.angularVel; p.life--;
        ctx.save();
        ctx.translate(p.x,p.y);
        ctx.rotate(p.angle);
        ctx.fillStyle=p.color;
        ctx.fillRect(-p.size/2,-p.size/2,p.size,p.size*0.6);
        ctx.restore();
        if(p.y>H+50||p.life<=0) particles.splice(i,1);
      }
      requestAnimationFrame(update);
    }
    update();

    // Button logic
    const btn = document.getElementById('showBtn');
    const msg = document.getElementById('message');
    const text = document.getElementById('text');
    btn.addEventListener('click', ()=>{
      btn.classList.add('celebrate');
      // show message
      msg.classList.add('show');
      // create confetti from center-top
      const rect = document.querySelector('.card').getBoundingClientRect();
      const cx = rect.width/2; const cy = 30;
      makeParticles(cx, cy, 80);
      // little extra burst at center
      makeParticles(cx, rect.height/2, 40);
      // small heart popup animation on the button
      setTimeout(()=> btn.classList.remove('celebrate'), 900);

      // optional: tiny typing effect for the text
      const full = 'I love you';
      text.textContent='';
      let i=0;
      const t = setInterval(()=>{ text.textContent += full[i++]||''; if(i>full.length){ clearInterval(t) } }, 90);

      // disable button after click to keep surprise
      btn.disabled = true;
      btn.style.cursor='default';
    });

    // Accessibility: allow Enter/Space
    btn.addEventListener('keyup', (e)=>{ if(e.key==='Enter' || e.key===' ') btn.click() });

    // small auto-focus
    btn.focus();
  </script>
</body>
</html>
