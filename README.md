<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Rewind Studio — Imagine. Create. Rewind.</title>
  <meta name="description" content="Rewind Studio — Serveur Discord dédié à la création, au développement, au graphisme, au montage vidéo et au partage entre créateurs.">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&family=Orbitron:wght@600;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg: #0a0a0a;
      --bg-card: #121212;
      --bg-card-hover: #1a1a1a;
      --yellow: #ffd600;
      --yellow-soft: #ffe44d;
      --yellow-dim: rgba(255, 214, 0, 0.15);
      --text: #f5f5f5;
      --text-muted: #a0a0a0;
      --border: rgba(255, 214, 0, 0.2);
      --radius: 16px;
      --transition: 0.25s cubic-bezier(0.4, 0, 0.2, 1);
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      font-family: 'Inter', system-ui, sans-serif;
      background: var(--bg);
      color: var(--text);
      line-height: 1.6;
      overflow-x: hidden;
    }

    /* Background effects */
    .bg-glow {
      position: fixed;
      top: -20%;
      left: 50%;
      transform: translateX(-50%);
      width: 120%;
      height: 60vh;
      background: radial-gradient(ellipse at center, rgba(255, 214, 0, 0.08) 0%, transparent 70%);
      pointer-events: none;
      z-index: 0;
    }

    /* Navbar */
    nav {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      z-index: 100;
      padding: 1rem 2rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: rgba(10, 10, 10, 0.85);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--border);
      transition: var(--transition);
    }

    nav.scrolled {
      padding: 0.75rem 2rem;
      background: rgba(10, 10, 10, 0.95);
    }

    .nav-logo {
      display: flex;
      align-items: center;
      gap: 0.75rem;
      text-decoration: none;
      color: var(--text);
    }

    .nav-logo img {
      height: 40px;
      width: auto;
    }

    .nav-logo span {
      font-family: 'Orbitron', sans-serif;
      font-weight: 700;
      font-size: 1.15rem;
      letter-spacing: 0.5px;
    }

    .nav-logo span .accent {
      color: var(--yellow);
    }

    .nav-links {
      display: flex;
      align-items: center;
      gap: 2rem;
    }

    .nav-links a {
      color: var(--text-muted);
      text-decoration: none;
      font-weight: 500;
      font-size: 0.95rem;
      transition: color var(--transition);
    }

    .nav-links a:hover {
      color: var(--yellow);
    }

    .btn {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.7rem 1.4rem;
      border-radius: 999px;
      font-weight: 600;
      font-size: 0.95rem;
      text-decoration: none;
      transition: all var(--transition);
      cursor: pointer;
      border: none;
    }

    .btn-primary {
      background: var(--yellow);
      color: #0a0a0a;
    }

    .btn-primary:hover {
      background: var(--yellow-soft);
      transform: translateY(-2px);
      box-shadow: 0 8px 24px rgba(255, 214, 0, 0.35);
    }

    .btn-outline {
      background: transparent;
      color: var(--yellow);
      border: 1.5px solid var(--yellow);
    }

    .btn-outline:hover {
      background: var(--yellow-dim);
      transform: translateY(-2px);
    }

    /* Hero */
    .hero {
      position: relative;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 8rem 1.5rem 4rem;
      z-index: 1;
      overflow: hidden;
    }

    .hero-bg {
      position: absolute;
      inset: 0;
      background: 
        linear-gradient(180deg, rgba(10,10,10,0.3) 0%, rgba(10,10,10,0.85) 60%, var(--bg) 100%),
        url('logo.png') center/cover no-repeat;
      opacity: 0.35;
      filter: blur(2px) brightness(0.6);
      z-index: -1;
    }

    .hero-content {
      max-width: 900px;
      animation: fadeUp 0.9s ease-out;
    }

    .hero-badge {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.4rem 1rem;
      background: var(--yellow-dim);
      border: 1px solid var(--border);
      border-radius: 999px;
      font-size: 0.85rem;
      font-weight: 500;
      color: var(--yellow);
      margin-bottom: 1.5rem;
    }

    .hero h1 {
      font-family: 'Orbitron', sans-serif;
      font-size: clamp(2.8rem, 8vw, 4.5rem);
      font-weight: 700;
      line-height: 1.1;
      margin-bottom: 1rem;
      letter-spacing: -1px;
    }

    .hero h1 .yellow {
      color: var(--yellow);
      text-shadow: 0 0 40px rgba(255, 214, 0, 0.4);
    }

    .hero-tagline {
      font-size: 1.25rem;
      color: var(--text-muted);
      max-width: 620px;
      margin: 0 auto 2.5rem;
    }

    .hero-cta {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      justify-content: center;
    }

    .hero-stats {
      display: flex;
      justify-content: center;
      gap: 3rem;
      margin-top: 4rem;
      flex-wrap: wrap;
    }

    .stat {
      text-align: center;
    }

    .stat-value {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.8rem;
      font-weight: 700;
      color: var(--yellow);
    }

    .stat-label {
      font-size: 0.9rem;
      color: var(--text-muted);
      margin-top: 0.25rem;
    }

    /* Sections */
    section {
      position: relative;
      z-index: 1;
      padding: 5rem 1.5rem;
    }

    .container {
      max-width: 1100px;
      margin: 0 auto;
    }

    .section-header {
      text-align: center;
      margin-bottom: 3.5rem;
    }

    .section-header h2 {
      font-family: 'Orbitron', sans-serif;
      font-size: clamp(1.8rem, 4vw, 2.4rem);
      margin-bottom: 0.75rem;
    }

    .section-header p {
      color: var(--text-muted);
      max-width: 560px;
      margin: 0 auto;
      font-size: 1.05rem;
    }

    /* Categories grid */
    .categories {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 1.5rem;
    }

    .card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 1.75rem;
      transition: all var(--transition);
      position: relative;
      overflow: hidden;
    }

    .card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      height: 3px;
      background: linear-gradient(90deg, var(--yellow), transparent);
      opacity: 0;
      transition: opacity var(--transition);
    }

    .card:hover {
      background: var(--bg-card-hover);
      border-color: rgba(255, 214, 0, 0.4);
      transform: translateY(-4px);
      box-shadow: 0 12px 40px rgba(0, 0, 0, 0.4);
    }

    .card:hover::before {
      opacity: 1;
    }

    .card-icon {
      width: 48px;
      height: 48px;
      display: flex;
      align-items: center;
      justify-content: center;
      background: var(--yellow-dim);
      border-radius: 12px;
      font-size: 1.5rem;
      margin-bottom: 1.25rem;
      color: var(--yellow);
    }

    .card h3 {
      font-size: 1.2rem;
      font-weight: 700;
      margin-bottom: 0.6rem;
    }

    .card p {
      color: var(--text-muted);
      font-size: 0.95rem;
      line-height: 1.55;
    }

    /* About */
    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 3rem;
      align-items: center;
    }

    .about-text h2 {
      font-family: 'Orbitron', sans-serif;
      font-size: 2rem;
      margin-bottom: 1.25rem;
    }

    .about-text p {
      color: var(--text-muted);
      margin-bottom: 1rem;
      font-size: 1.05rem;
    }

    .about-highlight {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 2rem;
      text-align: center;
    }

    .about-highlight .big-text {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.6rem;
      color: var(--yellow);
      margin-bottom: 0.75rem;
    }

    /* Why join */
    .why-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 1.25rem;
    }

    .why-item {
      display: flex;
      align-items: flex-start;
      gap: 1rem;
      padding: 1.25rem;
      background: var(--bg-card);
      border-radius: 12px;
      border: 1px solid transparent;
      transition: var(--transition);
    }

    .why-item:hover {
      border-color: var(--border);
      background: var(--bg-card-hover);
    }

    .why-icon {
      flex-shrink: 0;
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      background: var(--yellow-dim);
      border-radius: 10px;
      color: var(--yellow);
      font-size: 1.2rem;
    }

    .why-item h4 {
      font-size: 1rem;
      margin-bottom: 0.25rem;
    }

    .why-item p {
      font-size: 0.9rem;
      color: var(--text-muted);
    }

    /* CTA */
    .cta-section {
      text-align: center;
      padding: 6rem 1.5rem;
    }

    .cta-box {
      max-width: 700px;
      margin: 0 auto;
      background: linear-gradient(135deg, rgba(255, 214, 0, 0.1), rgba(255, 214, 0, 0.03));
      border: 1px solid var(--border);
      border-radius: 24px;
      padding: 3.5rem 2rem;
    }

    .cta-box h2 {
      font-family: 'Orbitron', sans-serif;
      font-size: clamp(1.8rem, 4vw, 2.3rem);
      margin-bottom: 1rem;
    }

    .cta-box p {
      color: var(--text-muted);
      margin-bottom: 2rem;
      font-size: 1.1rem;
    }

    .cta-box .btn-primary {
      font-size: 1.1rem;
      padding: 0.9rem 2rem;
    }

    /* Footer */
    footer {
      border-top: 1px solid var(--border);
      padding: 2.5rem 1.5rem;
      text-align: center;
      color: var(--text-muted);
      font-size: 0.9rem;
    }

    footer .logo-text {
      font-family: 'Orbitron', sans-serif;
      color: var(--text);
      font-weight: 600;
      margin-bottom: 0.5rem;
    }

    footer a {
      color: var(--yellow);
      text-decoration: none;
    }

    /* Animations */
    @keyframes fadeUp {
      from {
        opacity: 0;
        transform: translateY(30px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .reveal {
      opacity: 0;
      transform: translateY(24px);
      transition: opacity 0.6s ease, transform 0.6s ease;
    }

    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* Mobile */
    .menu-toggle {
      display: none;
      background: none;
      border: none;
      color: var(--text);
      font-size: 1.5rem;
      cursor: pointer;
    }

    @media (max-width: 768px) {
      nav {
        padding: 1rem 1.25rem;
      }

      .nav-links {
        display: none;
        position: absolute;
        top: 100%;
        left: 0;
        right: 0;
        background: rgba(10, 10, 10, 0.98);
        flex-direction: column;
        padding: 1.5rem;
        gap: 1.25rem;
        border-bottom: 1px solid var(--border);
      }

      .nav-links.open {
        display: flex;
      }

      .menu-toggle {
        display: block;
      }

      .about-grid {
        grid-template-columns: 1fr;
        gap: 2rem;
      }

      .hero-stats {
        gap: 1.5rem;
      }

      .stat-value {
        font-size: 1.4rem;
      }
    }
  </style>
</head>
<body>
  <div class="bg-glow"></div>

  <!-- Navbar -->
  <nav id="navbar">
    <a href="#" class="nav-logo">
      <img src="logo.png" alt="Rewind Studio Logo">
      <span>Rewind<span class="accent">Studio</span></span>
    </a>
    <button class="menu-toggle" id="menuToggle" aria-label="Menu">☰</button>
    <div class="nav-links" id="navLinks">
      <a href="#categories">Compétences</a>
      <a href="#about">Communauté</a>
      <a href="#why">Pourquoi nous</a>
      <a href="https://discord.gg/rwdev" class="btn btn-primary" target="_blank" rel="noopener">Rejoindre Discord</a>
    </div>
  </nav>

  <!-- Hero -->
  <section class="hero">
    <div class="hero-bg"></div>
    <div class="hero-content">
      <div class="hero-badge">
        <span>✦</span> Serveur Discord Créatif
      </div>
      <h1>
        <span class="yellow">Rewind</span> Studio
      </h1>
      <p class="hero-tagline">
        Bienvenue chez Rewind Studio, un serveur Discord dédié à la création, au développement et au partage entre passionnés.
      </p>
      <div class="hero-cta">
        <a href="https://discord.gg/rwdev" class="btn btn-primary" target="_blank" rel="noopener">
          Rejoindre le serveur
        </a>
        <a href="#categories" class="btn btn-outline">Découvrir les compétences</a>
      </div>
      <div class="hero-stats">
        <div class="stat">
          <div class="stat-value">Dev</div>
          <div class="stat-label">Discord & FiveM</div>
        </div>
        <div class="stat">
          <div class="stat-value">Design</div>
          <div class="stat-label">Graphisme & UI</div>
        </div>
        <div class="stat">
          <div class="stat-value">Vidéo</div>
          <div class="stat-label">Montage & Trailer</div>
        </div>
        <div class="stat">
          <div class="stat-value">Collab</div>
          <div class="stat-label">Projets & Réseau</div>
        </div>
      </div>
    </div>
  </section>

  <!-- Categories -->
  <section id="categories">
    <div class="container">
      <div class="section-header reveal">
        <h2>Nos <span style="color:var(--yellow)">compétences</span></h2>
        <p>Un espace pour chaque créateur. Présente tes services, collabore et progresse ensemble.</p>
      </div>
      <div class="categories">
        <div class="card reveal">
          <div class="card-icon">🤖</div>
          <h3>Développeurs Discord</h3>
          <p>Création de bots, automatisations, systèmes personnalisés et solutions sur mesure pour vos serveurs Discord.</p>
        </div>
        <div class="card reveal">
          <div class="card-icon">🎮</div>
          <h3>Développeurs FiveM</h3>
          <p>Scripts, serveurs, interfaces, systèmes RP et développement sur mesure pour tous vos projets FiveM.</p>
        </div>
        <div class="card reveal">
          <div class="card-icon">🎨</div>
          <h3>Graphistes</h3>
          <p>Logos, bannières, visuels, interfaces et identités graphiques pour donner vie à vos projets.</p>
        </div>
        <div class="card reveal">
          <div class="card-icon">🎬</div>
          <h3>Monteurs vidéo</h3>
          <p>Montage, clips, trailers, présentations et contenus pour vos réseaux ou vos communautés.</p>
        </div>
        <div class="card reveal">
          <div class="card-icon">🗺️</div>
          <h3>Mappeurs</h3>
          <p>Création de maps, environnements, mapping FiveM et univers immersifs pour vos serveurs.</p>
        </div>
        <div class="card reveal">
          <div class="card-icon">💼</div>
          <h3>Créateurs & Freelances</h3>
          <p>Un espace pour présenter vos services, trouver des collaborateurs et travailler sur des projets communs.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- About -->
  <section id="about">
    <div class="container">
      <div class="about-grid">
        <div class="about-text reveal">
          <h2>Une communauté <span style="color:var(--yellow)">avant tout</span></h2>
          <p>
            Rewind Studio rassemble des passionnés et des créateurs de différents domaines afin de partager leurs compétences, s’entraider et construire des projets ensemble.
          </p>
          <p>
            Que tu sois développeur, graphiste, monteur, mappeur ou freelance, tu trouveras ici un espace bienveillant pour échanger, progresser et créer.
          </p>
        </div>
        <div class="about-highlight reveal">
          <div class="big-text">Imagine. Create. Rewind.</div>
          <p style="color:var(--text-muted)">Le slogan de ceux qui passent de l’idée à la réalité.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- Why join -->
  <section id="why">
    <div class="container">
      <div class="section-header reveal">
        <h2>Pourquoi rejoindre <span style="color:var(--yellow)">Rewind Studio</span> ?</h2>
        <p>Plus qu’un simple serveur, une vraie communauté de créateurs.</p>
      </div>
      <div class="why-grid">
        <div class="why-item reveal">
          <div class="why-icon">💬</div>
          <div>
            <h4>Échanger avec d’autres créateurs</h4>
            <p>Discute librement avec des passionnés dans tous les domaines.</p>
          </div>
        </div>
        <div class="why-item reveal">
          <div class="why-icon">📂</div>
          <div>
            <h4>Présenter tes services & portfolio</h4>
            <p>Montre ton travail et fais-toi connaître facilement.</p>
          </div>
        </div>
        <div class="why-item reveal">
          <div class="why-icon">🤝</div>
          <div>
            <h4>Trouver des collaborateurs</h4>
            <p>Monte des projets à plusieurs et complète tes compétences.</p>
          </div>
        </div>
        <div class="why-item reveal">
          <div class="why-icon">📚</div>
          <div>
            <h4>Partager tes connaissances</h4>
            <p>Aide les autres et apprends de nouvelles techniques.</p>
          </div>
        </div>
        <div class="why-item reveal">
          <div class="why-icon">🚀</div>
          <div>
            <h4>Participer à des projets</h4>
            <p>Rejoins des créations collectives et gagne de l’expérience.</p>
          </div>
        </div>
        <div class="why-item reveal">
          <div class="why-icon">🌐</div>
          <div>
            <h4>Développer ton réseau</h4>
            <p>Élargis tes contacts dans le milieu créatif et gaming.</p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Final CTA -->
  <section class="cta-section">
    <div class="cta-box reveal">
      <h2>Prêt à créer avec nous ?</h2>
      <p>Rejoins dès maintenant Rewind Studio et fais partie d’une communauté qui imagine, crée et avance ensemble.</p>
      <a href="https://discord.gg/rwdev" class="btn btn-primary" target="_blank" rel="noopener">
        Rejoindre Discord →
      </a>
    </div>
  </section>

  <!-- Footer -->
  <footer>
    <div class="logo-text">Rewind Studio</div>
    <p>Imagine. Create. Rewind.</p>
    <p style="margin-top:1rem">
      <a href="https://discord.gg/rwdev" target="_blank" rel="noopener">discord.gg/rwdev</a>
    </p>
    <p style="margin-top:1.5rem;font-size:0.8rem;opacity:0.7">
      © 2026 Rewind Studio — Tous droits réservés
    </p>
  </footer>

  <script>
    // Navbar scroll effect
    const navbar = document.getElementById('navbar');
    window.addEventListener('scroll', () => {
      navbar.classList.toggle('scrolled', window.scrollY > 40);
    });

    // Mobile menu
    const menuToggle = document.getElementById('menuToggle');
    const navLinks = document.getElementById('navLinks');
    menuToggle.addEventListener('click', () => {
      navLinks.classList.toggle('open');
    });

    // Close menu on link click
    navLinks.querySelectorAll('a').forEach(link => {
      link.addEventListener('click', () => navLinks.classList.remove('open'));
    });

    // Reveal on scroll
    const reveals = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
        }
      });
    }, { threshold: 0.15 });

    reveals.forEach(el => observer.observe(el));
  </script>
</body>
</html>
