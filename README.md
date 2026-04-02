<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Invictus — The Fitness Hub</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&family=Orbitron:wght@700;800;900&display=swap');

    :root{
      --bg:#070707;
      --panel:#101114;
      --panel-2:#15171d;
      --text:#f5f7fb;
      --muted:#a2a8b3;
      --line:rgba(255,255,255,.08);
      --primary:#ff6a00;
      --secondary:#ff2d55;
      --tertiary:#7c3aed;
      --success:#22c55e;
      --shadow:0 20px 60px rgba(0,0,0,.45);
      --radius:24px;
      --max:1200px;
    }

    *{box-sizing:border-box;margin:0;padding:0}
    html{scroll-behavior:smooth}
    body{
      font-family:Inter,system-ui,-apple-system,Segoe UI,Roboto,sans-serif;
      background:
        radial-gradient(circle at 10% 10%, rgba(255,106,0,.14), transparent 28%),
        radial-gradient(circle at 90% 10%, rgba(124,58,237,.14), transparent 24%),
        radial-gradient(circle at 50% 100%, rgba(255,45,85,.12), transparent 30%),
        var(--bg);
      color:var(--text);
      line-height:1.6;
      overflow-x:hidden;
    }

    ::selection{background:rgba(255,106,0,.35);color:#fff}
    ::-webkit-scrollbar{width:12px}
    ::-webkit-scrollbar-track{background:#0b0c10}
    ::-webkit-scrollbar-thumb{
      border-radius:999px;
      border:2px solid #0b0c10;
      background:linear-gradient(180deg,var(--primary),var(--secondary),var(--tertiary));
      background-size:200% 200%;
      animation:thumbGlow 6s ease infinite;
    }
    @keyframes thumbGlow{
      0%,100%{background-position:0% 0%}
      50%{background-position:0% 100%}
    }

    a{text-decoration:none;color:inherit}
    img{display:block;max-width:100%}

    .bg-grid{
      position:fixed; inset:0; pointer-events:none; z-index:-2;
      background-image:
        linear-gradient(rgba(255,255,255,.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,.03) 1px, transparent 1px);
      background-size:48px 48px;
      mask-image:radial-gradient(circle at center, black 35%, transparent 80%);
      opacity:.3;
    }

    .orb, .orb-2{
      position:fixed; border-radius:50%; filter:blur(60px); pointer-events:none; z-index:-1;
    }
    .orb{
      width:280px;height:280px; left:-80px; top:10%;
      background:radial-gradient(circle, rgba(255,106,0,.35), transparent 70%);
      animation:float 10s ease-in-out infinite;
    }
    .orb-2{
      width:320px;height:320px; right:-100px; top:35%;
      background:radial-gradient(circle, rgba(124,58,237,.28), transparent 70%);
      animation:float 12s ease-in-out infinite reverse;
    }
    @keyframes float{
      0%,100%{transform:translateY(0) translateX(0)}
      50%{transform:translateY(-18px) translateX(12px)}
    }

    .container{width:min(var(--max), calc(100% - 32px)); margin-inline:auto}
    .section{padding:96px 0}
    .section-head{
      display:flex; align-items:end; justify-content:space-between; gap:20px; margin-bottom:34px; flex-wrap:wrap;
    }
    .eyebrow{
      display:inline-flex; align-items:center; gap:10px; padding:8px 14px;
      border:1px solid rgba(255,255,255,.1);
      background:rgba(255,255,255,.04);
      border-radius:999px; color:#ffd1bb; font-size:.88rem;
      backdrop-filter:blur(12px);
    }
    .eyebrow::before{
      content:""; width:8px; height:8px; border-radius:50%;
      background:linear-gradient(135deg,var(--primary),var(--secondary));
      box-shadow:0 0 16px rgba(255,106,0,.7);
    }
    h1,h2,h3,h4{line-height:1.05}
    h1{
      font-family:Orbitron, Inter, sans-serif;
      font-size:clamp(2.8rem, 7vw, 6rem);
      letter-spacing:.04em;
      text-transform:uppercase;
    }
    h2{
      font-size:clamp(2rem, 4vw, 3.4rem);
      font-weight:900;
    }
    .muted{color:var(--muted)}
    .lead{font-size:1.07rem;color:#c8ced8;max-width:680px}

    .btns{display:flex; gap:14px; flex-wrap:wrap}
    .btn{
      display:inline-flex; align-items:center; justify-content:center; gap:10px;
      min-height:52px; padding:0 20px; border-radius:16px; font-weight:700;
      border:1px solid transparent; transition:.3s ease; cursor:pointer;
    }
    .btn-primary{
      background:linear-gradient(135deg,var(--primary),var(--secondary));
      color:#fff; box-shadow:0 18px 36px rgba(255,106,0,.25);
    }
    .btn-primary:hover{transform:translateY(-2px) scale(1.01); box-shadow:0 22px 42px rgba(255,106,0,.32)}
    .btn-secondary{
      background:rgba(255,255,255,.04); border-color:rgba(255,255,255,.12); color:#fff;
      backdrop-filter:blur(10px);
    }
    .btn-secondary:hover{background:rgba(255,255,255,.08); transform:translateY(-2px)}

    .glass{
      background:linear-gradient(180deg, rgba(255,255,255,.07), rgba(255,255,255,.03));
      border:1px solid rgba(255,255,255,.1);
      backdrop-filter:blur(16px);
      box-shadow:var(--shadow);
    }

    header{
      position:fixed; top:16px; left:0; right:0; z-index:1000;
      transition:.3s ease;
    }
    .nav{
      width:min(var(--max), calc(100% - 24px)); margin:auto;
      display:flex; align-items:center; justify-content:space-between;
      padding:14px 18px; border-radius:20px;
      background:rgba(12,13,17,.55); border:1px solid rgba(255,255,255,.08);
      backdrop-filter:blur(18px);
    }
    header.scrolled .nav{
      background:rgba(12,13,17,.78);
      box-shadow:0 18px 40px rgba(0,0,0,.35);
    }
    .brand{
      display:flex; align-items:center; gap:12px; font-weight:900; letter-spacing:.05em;
    }
    .brand-mark{
      width:42px; height:42px; border-radius:14px;
      display:grid; place-items:center;
      background:linear-gradient(135deg,var(--primary),var(--secondary));
      box-shadow:0 10px 30px rgba(255,106,0,.25);
      font-family:Orbitron,sans-serif;
    }
    .brand span strong{display:block; font-family:Orbitron,sans-serif; font-size:1rem}
    .brand span small{display:block; color:var(--muted); font-size:.72rem; margin-top:-2px}

    .nav-links{display:flex; align-items:center; gap:22px}
    .nav-links a{color:#d7dbe3; font-weight:600; font-size:.96rem; transition:.2s}
    .nav-links a:hover{color:#fff}
    .menu-btn{
      display:none; width:48px; height:48px; border:none; color:#fff;
      border-radius:14px; background:rgba(255,255,255,.05); cursor:pointer;
      border:1px solid rgba(255,255,255,.08);
    }
    .mobile-menu{
      display:none; margin-top:10px; padding:12px; border-radius:18px;
      background:rgba(12,13,17,.92); border:1px solid rgba(255,255,255,.08);
      backdrop-filter:blur(18px);
    }
    .mobile-menu a{
      display:block; padding:14px 10px; border-radius:12px; color:#d7dbe3; font-weight:600;
    }
    .mobile-menu a:hover{background:rgba(255,255,255,.05); color:#fff}

    .hero{
      min-height:100svh;
      display:grid; align-items:center;
      padding:124px 0 48px;
      position:relative;
    }
    .hero-grid{
      display:grid; grid-template-columns:1.1fr .9fr; gap:42px; align-items:center;
    }
    .hero-copy p{margin:22px 0 28px}
    .hero-title .accent{
      display:block;
      background:linear-gradient(90deg,#fff,#ffcfaa,#ff6a00);
      -webkit-background-clip:text; background-clip:text; color:transparent;
    }
    .hero-stats{
      display:grid; grid-template-columns:repeat(3,1fr); gap:14px; margin-top:26px;
      max-width:680px;
    }
    .stat{
      padding:18px; border-radius:20px;
    }
    .stat strong{
      display:block; font-size:1.8rem; font-weight:900;
      background:linear-gradient(90deg,#fff,#ffc9a5); -webkit-background-clip:text; color:transparent;
    }
    .stat span{color:var(--muted); font-size:.92rem}

    .hero-visual{
      position:relative; perspective:1200px;
    }
    .visual-shell{
      position:relative; transform-style:preserve-3d;
      transform:rotateY(-8deg) rotateX(4deg);
    }
    .visual-main{
      overflow:hidden; border-radius:30px; position:relative;
      border:1px solid rgba(255,255,255,.1);
      box-shadow:0 30px 70px rgba(0,0,0,.45);
    }
    .visual-main img{
      width:100%; height:min(70vh,640px); object-fit:cover;
      transform:scale(1.04); filter:contrast(1.04) saturate(1.05);
    }
    .visual-main::after{
      content:"";
      position:absolute; inset:0;
      background:
        linear-gradient(180deg, rgba(0,0,0,.12), rgba(0,0,0,.45)),
        radial-gradient(circle at 20% 20%, rgba(255,255,255,.14), transparent 32%);
    }
    .floating-card{
      position:absolute; padding:16px 18px; border-radius:22px;
      background:rgba(12,13,17,.72); border:1px solid rgba(255,255,255,.12);
      backdrop-filter:blur(14px); box-shadow:var(--shadow);
      transform-style:preserve-3d;
    }
    .floating-card strong{font-size:1.1rem}
    .floating-card small{display:block; color:var(--muted)}
    .float-a{left:-24px; top:28px; animation:float 8s ease-in-out infinite}
    .float-b{right:-18px; bottom:40px; animation:float 9s ease-in-out infinite reverse}
    .mini-badge{
      position:absolute; left:20px; bottom:20px; padding:10px 14px; border-radius:999px;
      background:linear-gradient(135deg, rgba(255,106,0,.95), rgba(255,45,85,.95));
      font-weight:800; box-shadow:0 20px 34px rgba(255,106,0,.24);
    }

    .logos{
      padding-top:10px;
      display:grid; grid-template-columns:repeat(4,1fr); gap:14px;
    }
    .logo-pill{
      text-align:center; padding:16px; border-radius:18px; color:#e7eaf0; font-weight:700;
      background:rgba(255,255,255,.04); border:1px solid rgba(255,255,255,.08);
    }

    .grid-3{display:grid; grid-template-columns:repeat(3,1fr); gap:20px}
    .card{
      padding:24px; border-radius:26px; position:relative; overflow:hidden;
      transition:transform .35s ease, border-color .3s ease, box-shadow .35s ease;
      transform-style:preserve-3d;
    }
    .card:hover{
      transform:translateY(-8px);
      border-color:rgba(255,106,0,.3);
      box-shadow:0 24px 52px rgba(0,0,0,.35);
    }
    .card .icon{
      width:56px; height:56px; border-radius:18px; display:grid; place-items:center;
      margin-bottom:18px;
      background:linear-gradient(135deg, rgba(255,106,0,.16), rgba(255,45,85,.16));
      border:1px solid rgba(255,255,255,.08);
      font-size:1.4rem;
    }
    .card h3{font-size:1.35rem; margin-bottom:10px}
    .card p{color:var(--muted)}
    .chip{
      display:inline-block; margin-top:14px; padding:8px 12px; border-radius:999px;
      background:rgba(255,255,255,.05); color:#f3d3c4; font-size:.84rem; font-weight:700;
      border:1px solid rgba(255,255,255,.08);
    }

    .about{
      display:grid; grid-template-columns:1fr 1fr; gap:28px; align-items:center;
    }
    .stack{
      position:relative; min-height:520px;
    }
    .stack .img{
      position:absolute; overflow:hidden; border-radius:28px;
      border:1px solid rgba(255,255,255,.1); box-shadow:var(--shadow);
    }
    .stack .img img{width:100%; height:100%; object-fit:cover}
    .stack .img-1{inset:0 15% 18% 0}
    .stack .img-2{inset:38% 0 0 30%; transform:rotate(-5deg)}
    .stack .img-3{inset:12% 0 auto 48%; height:160px; transform:rotate(8deg)}
    .bullet-list{display:grid; gap:14px; margin:26px 0}
    .bullet{
      display:flex; gap:14px; align-items:flex-start; padding:14px 16px; border-radius:18px;
      background:rgba(255,255,255,.04); border:1px solid rgba(255,255,255,.08);
    }
    .bullet i{
      width:28px; height:28px; flex:none; border-radius:50%; display:grid; place-items:center;
      background:linear-gradient(135deg,var(--primary),var(--secondary)); font-style:normal; font-weight:900;
    }

    .gallery{
      display:grid;
      grid-template-columns:repeat(12,1fr);
      gap:16px;
    }
    .gallery-item{
      position:relative; overflow:hidden; border-radius:24px;
      border:1px solid rgba(255,255,255,.08); min-height:240px;
      box-shadow:var(--shadow);
    }
    .gallery-item img{
      width:100%; height:100%; object-fit:cover; transition:transform .6s ease;
    }
    .gallery-item:hover img{transform:scale(1.08)}
    .gallery-item::after{
      content:""; position:absolute; inset:0;
      background:linear-gradient(180deg, transparent 35%, rgba(0,0,0,.55));
    }
    .gallery-item span{
      position:absolute; left:18px; bottom:16px; z-index:1; font-weight:800; letter-spacing:.04em;
    }
    .g1{grid-column:span 5; min-height:420px}
    .g2{grid-column:span 4}
    .g3{grid-column:span 3}
    .g4{grid-column:span 3}
    .g5{grid-column:span 4}
    .g6{grid-column:span 5}
    .g7{grid-column:span 12; min-height:320px}

    .pricing{
      display:grid; grid-template-columns:repeat(3,1fr); gap:20px;
    }
    .price-card{
      padding:28px; border-radius:28px; position:relative;
    }
    .price-card.popular{
      background:linear-gradient(180deg, rgba(255,106,0,.14), rgba(255,45,85,.08));
      border-color:rgba(255,106,0,.24);
      transform:translateY(-10px);
    }
    .tag{
      position:absolute; top:18px; right:18px;
      padding:8px 12px; border-radius:999px; font-size:.78rem; font-weight:800;
      background:linear-gradient(135deg,var(--primary),var(--secondary));
    }
    .price{
      font-size:3rem; font-weight:900; margin:12px 0 14px;
      font-family:Orbitron,Inter,sans-serif;
    }
    .price small{font-size:1rem; color:var(--muted); font-family:Inter,sans-serif}
    .feature-list{display:grid; gap:12px; margin:20px 0 24px}
    .feature-list li{
      list-style:none; color:#d8dde6; display:flex; gap:10px; align-items:center;
    }
    .feature-list li::before{
      content:"✓"; color:#fff; font-weight:900;
      width:20px;height:20px; border-radius:50%; display:grid; place-items:center;
      background:linear-gradient(135deg,var(--primary),var(--secondary));
      font-size:.78rem;
    }

    .contact-wrap{
      display:grid; grid-template-columns:1fr .95fr; gap:24px;
    }
    .contact-card,.form-card{padding:28px; border-radius:28px}
    .contact-info{display:grid; gap:16px; margin-top:24px}
    .info-row{
      display:flex; gap:14px; align-items:flex-start; padding:14px 16px; border-radius:18px;
      background:rgba(255,255,255,.04); border:1px solid rgba(255,255,255,.08);
    }
    .info-row b{display:block}
    .info-row span{color:var(--muted); font-size:.95rem}
    .info-icon{
      width:44px; height:44px; border-radius:14px; display:grid; place-items:center;
      background:linear-gradient(135deg, rgba(255,106,0,.15), rgba(255,45,85,.15));
      border:1px solid rgba(255,255,255,.08); flex:none;
    }

    form{display:grid; gap:14px}
    .input-row{display:grid; grid-template-columns:1fr 1fr; gap:14px}
    input, select, textarea{
      width:100%; background:rgba(255,255,255,.04); color:#fff; border:1px solid rgba(255,255,255,.08);
      border-radius:16px; padding:15px 16px; font:inherit; outline:none; transition:.25s;
    }
    input:focus, select:focus, textarea:focus{
      border-color:rgba(255,106,0,.42);
      box-shadow:0 0 0 4px rgba(255,106,0,.12);
    }
    textarea{min-height:136px; resize:vertical}
    option{color:#111}

    footer{
      padding:22px 0 34px; color:var(--muted);
    }
    .footer-bar{
      display:flex; align-items:center; justify-content:space-between; gap:20px; flex-wrap:wrap;
      padding-top:20px; border-top:1px solid rgba(255,255,255,.08);
    }

    .scroll-rail{
      position:fixed; right:16px; top:50%; transform:translateY(-50%) perspective(800px) rotateY(-18deg);
      width:16px; height:220px; border-radius:999px; z-index:1001;
      background:linear-gradient(180deg, rgba(255,255,255,.08), rgba(255,255,255,.02));
      border:1px solid rgba(255,255,255,.08);
      box-shadow:0 20px 40px rgba(0,0,0,.32), inset 0 0 0 1px rgba(255,255,255,.04);
      overflow:hidden;
    }
    .scroll-rail::before{
      content:""; position:absolute; inset:0;
      background:repeating-linear-gradient(
        180deg,
        rgba(255,255,255,.08) 0px,
        rgba(255,255,255,.08) 2px,
        transparent 2px,
        transparent 12px
      );
      opacity:.18;
    }
    .scroll-thumb{
      position:absolute; left:2px; top:2px; width:10px; height:58px; border-radius:999px;
      background:linear-gradient(180deg, #ffb16a, var(--primary), var(--secondary), var(--tertiary));
      box-shadow:
        0 0 25px rgba(255,106,0,.45),
        inset 0 1px 0 rgba(255,255,255,.45);
      transition:height .15s linear;
      transform-style:preserve-3d;
    }
    .scroll-thumb::before{
      content:""; position:absolute; inset:2px; border-radius:999px;
      background:linear-gradient(180deg, rgba(255,255,255,.55), transparent 35%, transparent 65%, rgba(255,255,255,.18));
      mix-blend-mode:screen;
    }

    .reveal{
      opacity:0; transform:translateY(30px) scale(.98);
      transition:opacity .8s ease, transform .8s cubic-bezier(.2,.8,.2,1);
    }
    .reveal.in-view{
      opacity:1; transform:none;
    }

    .tilt{transition:transform .18s ease}

    .toast{
      position:fixed; left:50%; bottom:24px; transform:translateX(-50%) translateY(20px);
      padding:14px 18px; border-radius:16px; background:#11141a;
      border:1px solid rgba(255,255,255,.1); color:#fff; box-shadow:var(--shadow);
      opacity:0; pointer-events:none; transition:.35s ease; z-index:2000;
    }
    .toast.show{opacity:1; transform:translateX(-50%) translateY(0)}

    @media (max-width: 1024px){
      .hero-grid,.about,.contact-wrap{grid-template-columns:1fr}
      .grid-3,.pricing{grid-template-columns:1fr 1fr}
      .hero-visual{order:-1}
      .logos{grid-template-columns:repeat(2,1fr)}
      .g1,.g2,.g3,.g4,.g5,.g6,.g7{grid-column:span 6}
      .g7{min-height:260px}
    }

    @media (max-width: 768px){
      .section{padding:74px 0}
      .nav-links{display:none}
      .menu-btn{display:grid; place-items:center}
      .mobile-menu.show{display:block}
      .hero{padding-top:108px}
      .hero-stats,.grid-3,.pricing,.input-row,.logos{grid-template-columns:1fr}
      .g1,.g2,.g3,.g4,.g5,.g6,.g7{grid-column:span 12; min-height:240px}
      .stack{min-height:420px}
      .stack .img-1{inset:0 10% 22% 0}
      .stack .img-2{inset:42% 0 0 25%}
      .stack .img-3{display:none}
      .scroll-rail{height:150px; right:10px}
      .float-a{left:8px; top:10px}
      .float-b{right:8px; bottom:12px}
      .contact-card,.form-card,.card,.price-card{padding:22px}
    }
  </style>
</head>
<body>
  <div class="bg-grid"></div>
  <div class="orb"></div>
  <div class="orb-2"></div>

  <div class="scroll-rail" aria-hidden="true">
    <div class="scroll-thumb" id="scrollThumb"></div>
  </div>

  <header id="siteHeader">
    <div class="nav">
      <a href="#home" class="brand">
        <div class="brand-mark">I</div>
        <span><strong>INVICTUS</strong><small>The Fitness Hub</small></span>
      </a>

      <nav class="nav-links">
        <a href="#programs">Programs</a>
        <a href="#about">About</a>
        <a href="#gallery">Gallery</a>
        <a href="#pricing">Membership</a>
        <a href="#contact">Contact</a>
      </nav>

      <div style="display:flex;align-items:center;gap:10px">
        <a href="#contact" class="btn btn-primary" style="min-height:46px;padding:0 16px">Join Now</a>
        <button class="menu-btn" id="menuBtn" aria-label="Toggle menu">
          <svg width="22" height="22" viewBox="0 0 24 24" fill="none">
            <path d="M4 7h16M4 12h16M4 17h16" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
          </svg>
        </button>
      </div>
    </div>
    <div class="container">
      <div class="mobile-menu" id="mobileMenu">
        <a href="#programs">Programs</a>
        <a href="#about">About</a>
        <a href="#gallery">Gallery</a>
        <a href="#pricing">Membership</a>
        <a href="#contact">Contact</a>
      </div>
    </div>
  </header>

  <main id="home">
    <section class="hero container">
      <div class="hero-grid">
        <div class="hero-copy reveal">
          <span class="eyebrow">Train Hard. Stay Invictus.</span>
          <h1 class="hero-title" style="margin-top:18px">
            <span class="accent">Invictus</span>
            The Fitness Hub
          </h1>
          <p class="lead">
            Build strength, burn fat, and unlock elite performance in a bold training space designed for serious transformation.
          </p>
          <div class="btns">
            <a href="#contact" class="btn btn-primary">Book Free Trial</a>
            <a href="#gallery" class="btn btn-secondary">Explore Gym</a>
          </div>

          <div class="hero-stats">
            <div class="stat glass reveal">
              <strong>24/7</strong>
              <span>Access for members</span>
            </div>
            <div class="stat glass reveal">
              <strong>8+</strong>
              <span>Training zones</span>
            </div>
            <div class="stat glass reveal">
              <strong>100%</strong>
              <span>Result-driven coaching</span>
            </div>
          </div>
        </div>

        <div class="hero-visual reveal">
          <div class="visual-shell tilt">
            <div class="visual-main">
              <img src="https://img.sanishtech.com/u/27568eafaf0e9487ce3bd66603e9dd95.jpg" alt="Invictus gym training space" />
              <div class="mini-badge">Power • Discipline • Results</div>
            </div>
            <div class="floating-card float-a">
              <strong>Strength Zone</strong>
              <small>Premium machines & free weights</small>
            </div>
            <div class="floating-card float-b">
              <strong>HIIT & Functional</strong>
              <small>High-energy classes every week</small>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="container section" style="padding-top:12px">
      <div class="logos reveal">
        <div class="logo-pill">Strength Training</div>
        <div class="logo-pill">Cross Training</div>
        <div class="logo-pill">Personal Coaching</div>
        <div class="logo-pill">Body Transformation</div>
      </div>
    </section>

    <section class="section container" id="programs">
      <div class="section-head reveal">
        <div>
          <span class="eyebrow">Signature Programs</span>
          <h2 style="margin-top:16px">Train for power, endurance, and confidence</h2>
        </div>
        <p class="lead">Every program at Invictus is structured to push limits while keeping form, recovery, and consistency at the center.</p>
      </div>

      <div class="grid-3">
        <article class="card glass tilt reveal">
          <div class="icon">🏋️</div>
          <h3>Strength & Muscle</h3>
          <p>Progressive overload, guided technique, and full-body strength blocks for sustainable muscle growth.</p>
          <span class="chip">Barbell • Dumbbell • Machines</span>
        </article>

        <article class="card glass tilt reveal">
          <div class="icon">⚡</div>
          <h3>HIIT Conditioning</h3>
          <p>Explosive circuits to elevate heart rate, improve stamina, and sharpen athletic performance fast.</p>
          <span class="chip">Fat Burn • Cardio • Agility</span>
        </article>

        <article class="card glass tilt reveal">
          <div class="icon">🧘</div>
          <h3>Mobility & Recovery</h3>
          <p>Restore movement quality, reduce stiffness, and recover smarter with focused flexibility sessions.</p>
          <span class="chip">Stretch • Mobility • Recovery</span>
        </article>
      </div>
    </section>

    <section class="section container" id="about">
      <div class="about">
        <div class="stack reveal">
          <div class="img img-1 tilt">
            <img src="https://img.sanishtech.com/u/f30e4b81750a9370046b51f5737faedc.jpg" alt="Invictus panoramic gym interior" />
          </div>
          <div class="img img-2 tilt">
            <img src="https://img.sanishtech.com/u/9a3b49617155f9cfbe5d6db3611cae92.jpg" alt="Invictus training area" />
          </div>
          <div class="img img-3 tilt glass">
            <img src="https://img.sanishtech.com/u/cad5f82d0af6bdba80c8044abc2588b3.jpg" alt="Invictus gym setup" />
          </div>
        </div>

        <div class="reveal">
          <span class="eyebrow">Why Invictus</span>
          <h2 style="margin-top:16px">A gym built for real transformation</h2>
          <p class="lead" style="margin-top:18px">
            Invictus The Fitness Hub blends elite equipment, motivating energy, and performance-based coaching to help beginners and advanced athletes train with purpose.
          </p>

          <div class="bullet-list">
            <div class="bullet">
              <i>✓</i>
              <div>
                <strong>Modern training environment</strong>
                <p class="muted">Spacious layout, premium machines, and dedicated zones for every workout style.</p>
              </div>
            </div>
            <div class="bullet">
              <i>✓</i>
              <div>
                <strong>Personal attention</strong>
                <p class="muted">Programs tailored for weight loss, lean muscle, strength building, and athletic development.</p>
              </div>
            </div>
            <div class="bullet">
              <i>✓</i>
              <div>
                <strong>Community-driven motivation</strong>
                <p class="muted">Train alongside people who show up with discipline, intensity, and consistency.</p>
              </div>
            </div>
          </div>

          <a href="#pricing" class="btn btn-primary">View Memberships</a>
        </div>
      </div>
    </section>

    <section class="section container" id="gallery">
      <div class="section-head reveal">
        <div>
          <span class="eyebrow">Gym Tour</span>
          <h2 style="margin-top:16px">Experience the Invictus atmosphere</h2>
        </div>
        <p class="lead">A premium setup designed to help you focus, move better, and train harder every single day.</p>
      </div>

      <div class="gallery">
        <div class="gallery-item g1 reveal tilt">
          <img src="https://img.sanishtech.com/u/27568eafaf0e9487ce3bd66603e9dd95.jpg" alt="Invictus gym equipment area" loading="lazy">
          <span>Main Floor</span>
        </div>
        <div class="gallery-item g2 reveal tilt">
          <img src="https://img.sanishtech.com/u/e59421cd8bddeaf002f0260178e27b19.jpg" alt="Invictus workout zone" loading="lazy">
          <span>Workout Zone</span>
        </div>
        <div class="gallery-item g3 reveal tilt">
          <img src="https://img.sanishtech.com/u/5c3c5e804ade044812a79a52b094354b.jpg" alt="Invictus machines section" loading="lazy">
          <span>Machines</span>
        </div>
        <div class="gallery-item g4 reveal tilt">
          <img src="https://img.sanishtech.com/u/c960241e3be097c6ee55cd7379663b54.jpg" alt="Invictus interior corner" loading="lazy">
          <span>Energy Space</span>
        </div>
        <div class="gallery-item g5 reveal tilt">
          <img src="https://img.sanishtech.com/u/cad5f82d0af6bdba80c8044abc2588b3.jpg" alt="Invictus training setup" loading="lazy">
          <span>Power Setup</span>
        </div>
        <div class="gallery-item g6 reveal tilt">
          <img src="https://img.sanishtech.com/u/9a3b49617155f9cfbe5d6db3611cae92.jpg" alt="Invictus full gym view" loading="lazy">
          <span>Functional Training</span>
        </div>
        <div class="gallery-item g7 reveal tilt">
          <img src="https://img.sanishtech.com/u/f30e4b81750a9370046b51f5737faedc.jpg" alt="Invictus wide gym interior" loading="lazy">
          <span>Train Without Limits</span>
        </div>
      </div>
    </section>

    <section class="section container" id="pricing">
      <div class="section-head reveal">
        <div>
          <span class="eyebrow">Membership Plans</span>
          <h2 style="margin-top:16px">Choose your grind level</h2>
        </div>
        <p class="lead">Flexible plans for casual training, consistent progress, and full coaching support.</p>
      </div>

      <div class="pricing">
        <article class="price-card glass reveal tilt">
          <h3>Starter</h3>
          <div class="price">₹999 <small>/ month</small></div>
          <p class="muted">Perfect for beginners starting their fitness journey.</p>
          <ul class="feature-list">
            <li>Gym floor access</li>
            <li>Basic assessment</li>
            <li>Locker facility</li>
            <li>1 trainer consultation</li>
          </ul>
          <a href="#contact" class="btn btn-secondary" style="width:100%">Get Started</a>
        </article>

        <article class="price-card glass popular reveal tilt">
          <div class="tag">Most Popular</div>
          <h3>Pro</h3>
          <div class="price">₹1,999 <small>/ month</small></div>
          <p class="muted">Best value for serious training and faster results.</p>
          <ul class="feature-list">
            <li>Unlimited access</li>
            <li>HIIT & group classes</li>
            <li>Custom workout plan</li>
            <li>Nutrition guidance</li>
          </ul>
          <a href="#contact" class="btn btn-primary" style="width:100%">Join Pro</a>
        </article>

        <article class="price-card glass reveal tilt">
          <h3>Elite</h3>
          <div class="price">₹3,499 <small>/ month</small></div>
          <p class="muted">Premium support with focused coaching and accountability.</p>
          <ul class="feature-list">
            <li>Everything in Pro</li>
            <li>Personal training sessions</li>
            <li>Body composition tracking</li>
            <li>Priority support</li>
          </ul>
          <a href="#contact" class="btn btn-secondary" style="width:100%">Go Elite</a>
        </article>
      </div>
    </section>

    <section class="section container" id="contact">
      <div class="contact-wrap">
        <div class="contact-card glass reveal">
          <span class="eyebrow">Contact Us</span>
          <h2 style="margin-top:16px">Start your Invictus journey today</h2>
          <p class="lead" style="margin-top:16px">
            Book a free trial, ask about plans, or visit the gym and feel the energy in person.
          </p>

          <div class="contact-info">
            <div class="info-row">
              <div class="info-icon">📍</div>
              <div>
                <b>Location</b>
                <span>Invictus The Fitness Hub, Your City</span>
              </div>
            </div>
            <div class="info-row">
              <div class="info-icon">📞</div>
              <div>
                <b>Phone</b>
                <span>+91 98765 43210</span>
              </div>
            </div>
            <div class="info-row">
              <div class="info-icon">⏰</div>
              <div>
                <b>Hours</b>
                <span>Open daily • 24/7 for members</span>
              </div>
            </div>
          </div>
        </div>

        <div class="form-card glass reveal">
          <form id="leadForm">
            <div class="input-row">
              <input type="text" placeholder="Your name" required>
              <input type="tel" placeholder="Phone number" required>
            </div>
            <div class="input-row">
              <input type="email" placeholder="Email address" required>
              <select required>
                <option value="">Select goal</option>
                <option>Weight Loss</option>
                <option>Muscle Gain</option>
                <option>Strength Training</option>
                <option>General Fitness</option>
              </select>
            </div>
            <textarea placeholder="Tell us about your fitness goal"></textarea>
            <button class="btn btn-primary" type="submit" style="width:100%">Book Free Trial</button>
          </form>
        </div>
      </div>
    </section>
  </main>

  <footer class="container">
    <div class="footer-bar">
      <div>© 2026 Invictus — The Fitness Hub</div>
      <div>Built for strength, discipline, and unstoppable progress.</div>
    </div>
  </footer>

  <div class="toast" id="toast">Thanks! Your free trial request has been sent.</div>

  <script>
    const header = document.getElementById('siteHeader');
    const scrollThumb = document.getElementById('scrollThumb');
    const menuBtn = document.getElementById('menuBtn');
    const mobileMenu = document.getElementById('mobileMenu');
    const toast = document.getElementById('toast');
    const form = document.getElementById('leadForm');

    function updateScrollUI() {
      const doc = document.documentElement;
      const scrollTop = doc.scrollTop || document.body.scrollTop;
      const maxScroll = doc.scrollHeight - doc.clientHeight;
      const progress = maxScroll > 0 ? scrollTop / maxScroll : 0;
      const rail = document.querySelector('.scroll-rail');
      const railHeight = rail.clientHeight - 4;
      const thumbHeight = Math.max(42, railHeight * 0.18);
      const y = (railHeight - thumbHeight) * progress;
      const rot = (progress * 40) - 20;
      scrollThumb.style.height = thumbHeight + 'px';
      scrollThumb.style.transform = `translateY(${y}px) rotateX(${rot * 0.28}deg) translateZ(12px)`;
      header.classList.toggle('scrolled', scrollTop > 20);
    }

    updateScrollUI();
    window.addEventListener('scroll', updateScrollUI, { passive: true });
    window.addEventListener('resize', updateScrollUI);

    menuBtn.addEventListener('click', () => {
      mobileMenu.classList.toggle('show');
    });

    document.querySelectorAll('.mobile-menu a').forEach(link => {
      link.addEventListener('click', () => mobileMenu.classList.remove('show'));
    });

    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) entry.target.classList.add('in-view');
      });
    }, { threshold: 0.12 });

    document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

    document.querySelectorAll('.tilt').forEach(card => {
      card.addEventListener('mousemove', (e) => {
        const r = card.getBoundingClientRect();
        const x = e.clientX - r.left;
        const y = e.clientY - r.top;
        const rx = ((y / r.height) - 0.5) * -10;
        const ry = ((x / r.width) - 0.5) * 12;
        card.style.transform = `perspective(1000px) rotateX(${rx}deg) rotateY(${ry}deg) translateY(-4px)`;
      });
      card.addEventListener('mouseleave', () => {
        card.style.transform = '';
      });
    });

    form.addEventListener('submit', (e) => {
      e.preventDefault();
      toast.classList.add('show');
      form.reset();
      setTimeout(() => toast.classList.remove('show'), 2600);
    });
  </script>
</body>
</html>
