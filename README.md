<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
  <title>Special VIP Gift | BLEN</title>

  <!-- PWA & Mobile Web App Meta Tags -->
  <meta name="theme-color" content="#050505">
  <meta name="description" content="A private cinematic digital experience prepared specially for Blen by Yisshak.">
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">

  <!-- Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700;900&family=Noto+Sans+Ethiopic:wght@300;400;600;700&family=Plus+Jakarta+Sans:wght@300;400;500;600;700&family=Great+Vibes&display=swap" rel="stylesheet">

  <style>
    /* ==========================================================================
       1. CORE DESIGN SYSTEM & VARIABLES
       ========================================================================== */
    :root {
      --bg-dark: #050505;
      --bg-surface: #0b0b0b;
      --bg-glass: rgba(18, 18, 24, 0.68);
      --border-glass: rgba(255, 255, 255, 0.08);
      --border-gold: rgba(212, 175, 55, 0.35);

      --pink-neon: #ff4fa3;
      --pink-deep: #d4145a;
      --gold-luxury: #d4af37;
      --gold-light: #f3e5ab;
      
      --text-main: #ffffff;
      --text-muted: rgba(255, 255, 255, 0.72);
      --text-dim: rgba(255, 255, 255, 0.45);

      --font-display: 'Cinzel', serif;
      --font-cursive: 'Great Vibes', cursive;
      --font-sans: 'Plus Jakarta Sans', sans-serif;
      --font-ethiopic: 'Noto Sans Ethiopic', sans-serif;

      --radius-sm: 12px;
      --radius-md: 20px;
      --radius-lg: 32px;
      --radius-full: 9999px;

      --glow-pink: 0 0 30px rgba(255, 79, 163, 0.35);
      --glow-gold: 0 0 30px rgba(212, 175, 55, 0.3);
      --shadow-deep: 0 20px 50px rgba(0, 0, 0, 0.85);

      --ease-cinematic: cubic-bezier(0.16, 1, 0.3, 1);
      --ease-bounce: cubic-bezier(0.34, 1.56, 0.64, 1);
    }

    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      -webkit-tap-highlight-color: transparent;
      user-select: none;
    }

    html, body {
      width: 100%;
      height: 100%;
      overflow: hidden;
      background-color: var(--bg-dark);
      color: var(--text-main);
      font-family: var(--font-sans);
      font-size: 16px;
      line-height: 1.6;
      -webkit-font-smoothing: antialiased;
      position: fixed;
    }

    body.lang-am {
      font-family: var(--font-ethiopic), var(--font-sans);
    }

    /* Ambient Canvas */
    #particleCanvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 1;
      pointer-events: none;
    }

    /* Cinematic Film Grain & Vignette Overlay */
    .cinematic-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 2;
      pointer-events: none;
      background: radial-gradient(circle at center, transparent 35%, rgba(5, 5, 5, 0.9) 100%);
      box-shadow: inset 0 0 120px rgba(0,0,0,0.95);
    }

    /* Film Grain Noise Overlay via SVG Data URI */
    .film-grain {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      z-index: 2;
      pointer-events: none;
      opacity: 0.035;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.8' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)'/%3E%3C/svg%3E");
    }

    /* Floating Ambient Lights */
    .ambient-light-1, .ambient-light-2 {
      position: fixed;
      border-radius: 50%;
      filter: blur(120px);
      pointer-events: none;
      z-index: 1;
      opacity: 0.22;
      animation: floatLight 18s ease-in-out infinite alternate;
    }
    .ambient-light-1 {
      width: 50vw; height: 50vw;
      background: var(--pink-deep);
      top: -15vw; left: -15vw;
    }
    .ambient-light-2 {
      width: 55vw; height: 55vw;
      background: var(--gold-luxury);
      bottom: -20vw; right: -20vw;
      animation-delay: -9s;
    }

    @keyframes floatLight {
      0% { transform: translate(0, 0) scale(1); }
      50% { transform: translate(6%, 10%) scale(1.1); }
      100% { transform: translate(-4%, -6%) scale(0.95); }
    }

    /* App Container */
    #app {
      position: relative;
      width: 100%;
      height: 100%;
      z-index: 3;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    /* Header Controls (Language & Audio) */
    .top-controls {
      position: fixed;
      top: calc(16px + env(safe-area-inset-top));
      left: 0;
      width: 100%;
      padding: 0 max(20px, env(safe-area-inset-right)) 0 max(20px, env(safe-area-inset-left));
      display: flex;
      justify-content: space-between;
      align-items: center;
      z-index: 100;
      pointer-events: none;
    }
    .top-controls * {
      pointer-events: auto;
    }

    /* Glass Panels & Buttons */
    .glass-panel {
      background: var(--bg-glass);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      border: 1px solid var(--border-glass);
      border-radius: var(--radius-md);
      box-shadow: var(--shadow-deep);
    }

    /* Luxury Segmented Language Control */
    .lang-switcher {
      position: relative;
      display: flex;
      padding: 4px;
      border-radius: var(--radius-full);
      background: rgba(10, 10, 14, 0.75);
      border: 1px solid var(--border-glass);
      box-shadow: 0 8px 20px rgba(0,0,0,0.4);
    }
    .lang-btn {
      position: relative;
      z-index: 2;
      background: transparent;
      border: none;
      color: var(--text-muted);
      padding: 6px 16px;
      font-size: 0.8rem;
      font-weight: 600;
      min-height: 36px;
      border-radius: var(--radius-full);
      cursor: pointer;
      transition: color 0.3s ease;
    }
    .lang-btn.active {
      color: #ffffff;
    }
    .lang-indicator {
      position: absolute;
      top: 4px; left: 4px;
      width: calc(50% - 4px);
      height: calc(100% - 8px);
      background: linear-gradient(135deg, var(--pink-deep), var(--pink-neon));
      border-radius: var(--radius-full);
      box-shadow: 0 0 12px rgba(255, 79, 163, 0.4);
      z-index: 1;
      transition: transform 0.4s var(--ease-cinematic);
    }

    /* Audio Widget */
    .audio-control {
      position: relative;
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 6px 14px;
      border-radius: var(--radius-full);
      background: rgba(10, 10, 14, 0.75);
      border: 1px solid var(--border-glass);
      box-shadow: 0 8px 20px rgba(0,0,0,0.4);
    }
    .audio-btn {
      background: transparent;
      border: none;
      color: var(--gold-light);
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      width: 32px;
      height: 32px;
      border-radius: 50%;
      transition: transform 0.2s ease, color 0.3s ease;
    }
    .audio-btn:active { transform: scale(0.9); }
    .audio-bars {
      display: flex;
      align-items: flex-end;
      gap: 3px;
      height: 14px;
    }
    .audio-bar {
      width: 2px;
      height: 100%;
      background: var(--pink-neon);
      border-radius: 2px;
      transform-origin: bottom;
      animation: soundWave 1.2s ease-in-out infinite alternate;
      animation-play-state: paused;
    }
    .audio-bar:nth-child(2) { animation-delay: 0.2s; }
    .audio-bar:nth-child(3) { animation-delay: 0.4s; }
    .audio-bar:nth-child(4) { animation-delay: 0.1s; }
    .playing .audio-bar { animation-play-state: running; }

    /* Music Toast Indicator */
    .music-toast {
      position: absolute;
      right: 0;
      top: 48px;
      background: var(--bg-glass);
      backdrop-filter: blur(15px);
      -webkit-backdrop-filter: blur(15px);
      border: 1px solid var(--border-gold);
      color: var(--gold-light);
      padding: 4px 12px;
      border-radius: var(--radius-full);
      font-size: 0.75rem;
      letter-spacing: 0.5px;
      white-space: nowrap;
      opacity: 0;
      transform: translateY(-8px);
      transition: all 0.4s var(--ease-cinematic);
      pointer-events: none;
    }
    .music-toast.show {
      opacity: 1;
      transform: translateY(0);
    }

    @keyframes soundWave {
      0% { transform: scaleY(0.2); }
      100% { transform: scaleY(1); }
    }

    /* Premium Button Base */
    .btn-luxury {
      position: relative;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 12px;
      padding: 16px 36px;
      min-height: 48px;
      background: linear-gradient(135deg, rgba(212, 175, 55, 0.15), rgba(255, 79, 163, 0.25));
      border: 1px solid var(--border-gold);
      border-radius: var(--radius-full);
      color: var(--text-main);
      font-family: var(--font-sans);
      font-weight: 600;
      font-size: 0.95rem;
      letter-spacing: 1.5px;
      text-transform: uppercase;
      cursor: pointer;
      overflow: hidden;
      backdrop-filter: blur(10px);
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5), inset 0 0 15px rgba(255, 255, 255, 0.05);
      transition: all 0.4s var(--ease-cinematic);
      outline: none;
    }
    .btn-luxury:focus-visible {
      outline: 2px solid var(--pink-neon);
      outline-offset: 4px;
    }
    .btn-luxury::before {
      content: '';
      position: absolute;
      top: 0; left: -100%;
      width: 60%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.25), transparent);
      transform: skewX(-20deg);
      transition: left 0.75s ease;
    }
    .btn-luxury:hover {
      transform: translateY(-3px) scale(1.02);
      border-color: var(--pink-neon);
      box-shadow: var(--glow-pink), 0 15px 35px rgba(0,0,0,0.6);
    }
    .btn-luxury:hover::before { left: 180%; }
    .btn-luxury:active { transform: translateY(1px) scale(0.98); }

    /* Screen Management System */
    .screen {
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: clamp(60px, 12vh, 90px) max(20px, env(safe-area-inset-right)) max(30px, env(safe-area-inset-bottom)) max(20px, env(safe-area-inset-left));
      opacity: 0;
      visibility: hidden;
      pointer-events: none;
      transition: opacity 0.9s var(--ease-cinematic), transform 0.9s var(--ease-cinematic), filter 0.9s ease;
      transform: scale(0.96) translateY(20px);
      filter: blur(10px);
      z-index: 10;
    }
    .screen.active {
      opacity: 1;
      visibility: visible;
      pointer-events: auto;
      transform: scale(1) translateY(0);
      filter: blur(0px);
    }

    /* Typography Utilities */
    .title-gold {
      font-family: var(--font-display);
      background: linear-gradient(135deg, #ffffff 20%, var(--gold-light) 60%, var(--gold-luxury) 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      text-shadow: 0 10px 20px rgba(0,0,0,0.5);
    }
    .title-pink {
      background: linear-gradient(135deg, #ffffff 20%, var(--pink-neon) 80%, var(--pink-deep) 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    /* ==========================================================================
       SCREEN 1 — CINEMATIC OPENING
       ========================================================================== */
    #screen-opening {
      cursor: pointer;
      text-align: center;
    }
    .opening-content {
      position: relative;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }
    .spotlight-radial {
      position: absolute;
      width: 320px;
      height: 320px;
      background: radial-gradient(circle, rgba(255, 79, 163, 0.12) 0%, transparent 70%);
      border-radius: 50%;
      pointer-events: none;
      animation: pulseSpotlight 6s ease-in-out infinite alternate;
    }
    @keyframes pulseSpotlight {
      0% { transform: scale(0.8); opacity: 0.5; }
      100% { transform: scale(1.2); opacity: 0.9; }
    }
    .opening-subtext {
      position: relative;
      font-size: clamp(1.05rem, 3.8vw, 1.3rem);
      letter-spacing: 2px;
      color: var(--text-muted);
      margin-bottom: 28px;
      font-weight: 300;
      max-width: 460px;
      opacity: 0;
      transform: translateY(15px);
      animation: fadeInSmooth 2s var(--ease-cinematic) 0.5s forwards;
    }
    .tap-hint {
      position: relative;
      display: inline-flex;
      align-items: center;
      gap: 10px;
      font-size: 0.85rem;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--gold-luxury);
      opacity: 0;
      animation: pulseGlow 2.5s infinite ease-in-out 2s, fadeInSmooth 1.5s ease 1.8s forwards;
    }
    @keyframes pulseGlow {
      0%, 100% { opacity: 0.4; transform: scale(0.98); }
      50% { opacity: 0.95; transform: scale(1.03); filter: drop-shadow(0 0 8px var(--gold-luxury)); }
    }
    @keyframes fadeInSmooth {
      to { opacity: 1; transform: translateY(0); }
    }

    /* ==========================================================================
       SCREEN 2 — BLEN REVEAL
       ========================================================================== */
    #screen-reveal { text-align: center; }
    .name-container {
      display: flex;
      gap: clamp(6px, 2.5vw, 16px);
      margin-bottom: 12px;
      justify-content: center;
      align-items: center;
    }
    .letter {
      font-family: var(--font-display);
      font-size: clamp(3.2rem, 13vw, 6.8rem);
      font-weight: 900;
      color: #fff;
      display: inline-block;
      opacity: 0;
      filter: blur(20px);
      transform: scale(1.8) translateY(-20px);
      text-shadow: 0 0 30px rgba(255, 79, 163, 0.6), 0 0 60px rgba(212, 175, 55, 0.4);
      background: linear-gradient(180deg, #ffffff 30%, var(--pink-neon) 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    .screen.active .letter {
      animation: letterReveal 1.2s var(--ease-cinematic) forwards;
    }
    .letter:nth-child(1) { animation-delay: 0.2s; }
    .letter:nth-child(2) { animation-delay: 0.4s; }
    .letter:nth-child(3) { animation-delay: 0.6s; }
    .letter:nth-child(4) { animation-delay: 0.8s; }
    .letter:nth-child(5) { animation-delay: 1.0s; }

    .reveal-subtitle {
      font-size: clamp(0.85rem, 2.8vw, 1rem);
      letter-spacing: 2.5px;
      text-transform: uppercase;
      color: var(--gold-light);
      margin-bottom: 24px;
      opacity: 0;
      transform: translateY(10px);
    }
    .screen.active .reveal-subtitle {
      animation: fadeInSmooth 1.2s ease 1.2s forwards;
    }

    @keyframes letterReveal {
      to {
        opacity: 1;
        filter: blur(0px);
        transform: scale(1) translateY(0);
      }
    }

    .welcome-text {
      max-width: 480px;
      font-size: clamp(0.95rem, 3.2vw, 1.2rem);
      color: var(--text-muted);
      margin-bottom: 35px;
      opacity: 0;
      transform: translateY(15px);
    }
    .screen.active .welcome-text {
      animation: fadeInSmooth 1.2s ease 1.5s forwards;
    }
    .screen.active .reveal-btn-wrap {
      opacity: 0;
      animation: fadeInSmooth 1s ease 1.9s forwards;
    }

    /* ==========================================================================
       SCREEN 3 — MEMORIES 3D CAROUSEL
       ========================================================================== */
    #screen-memories {
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      padding: clamp(60px, 10vh, 90px) 0 clamp(20px, 3vh, 40px) 0;
    }
    .section-header {
      text-align: center;
      padding: 0 20px;
      z-index: 5;
    }
    .section-title {
      font-size: clamp(1.5rem, 5vw, 2.4rem);
      letter-spacing: 2px;
      margin-bottom: 6px;
    }
    .section-subtitle {
      font-size: 0.85rem;
      color: var(--text-muted);
      letter-spacing: 1px;
    }

    .carousel-container-wrap {
      position: relative;
      width: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .carousel-viewport {
      width: 100%;
      height: clamp(300px, 45vh, 440px);
      perspective: 1000px;
      position: relative;
      display: flex;
      align-items: center;
      justify-content: center;
      overflow: hidden;
      touch-action: pan-y;
    }
    .carousel-track {
      position: absolute;
      width: 100%;
      height: 100%;
      transform-style: preserve-3d;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .carousel-card {
      position: absolute;
      width: clamp(220px, 62vw, 320px);
      height: clamp(290px, 40vh, 410px);
      border-radius: var(--radius-md);
      overflow: hidden;
      background: var(--bg-surface);
      border: 1px solid var(--border-glass);
      box-shadow: 0 20px 40px rgba(0,0,0,0.8);
      transition: transform 0.6s var(--ease-cinematic), filter 0.6s ease, opacity 0.6s ease, border-color 0.4s ease, box-shadow 0.4s ease;
      cursor: pointer;
      will-change: transform, filter;
    }
    .carousel-card img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      pointer-events: none;
      transition: transform 0.8s ease;
      background-color: #121218;
    }
    .carousel-card:hover img {
      transform: scale(1.06);
    }
    .carousel-card .card-caption {
      position: absolute;
      bottom: 0; left: 0; width: 100%;
      padding: 24px 16px 16px 16px;
      background: linear-gradient(0deg, rgba(5,5,5,0.95) 0%, rgba(5,5,5,0.5) 70%, transparent 100%);
      font-size: 0.85rem;
      color: #fff;
      text-align: center;
      letter-spacing: 0.5px;
    }

    .carousel-card.active-card {
      border-color: var(--pink-neon);
      box-shadow: var(--glow-pink), 0 25px 50px rgba(0,0,0,0.9);
    }

    /* Carousel Desktop Navigation Arrows */
    .carousel-arrow {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      z-index: 15;
      background: var(--bg-glass);
      backdrop-filter: blur(10px);
      border: 1px solid var(--border-glass);
      color: #ffffff;
      width: 44px;
      height: 44px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      transition: all 0.3s ease;
      opacity: 0.8;
    }
    .carousel-arrow:hover {
      opacity: 1;
      border-color: var(--pink-neon);
      background: rgba(255, 79, 163, 0.2);
    }
    .carousel-arrow.prev { left: clamp(10px, 4vw, 40px); }
    .carousel-arrow.next { right: clamp(10px, 4vw, 40px); }

    @media (max-width: 768px) {
      .carousel-arrow { display: none; }
    }

    /* Carousel Progress & Indicator */
    .carousel-info {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 10px;
      z-index: 5;
    }
    .carousel-counter {
      font-size: 0.8rem;
      letter-spacing: 2px;
      color: var(--gold-light);
      font-family: var(--font-display);
    }
    .carousel-nav-dots {
      display: flex;
      gap: 8px;
      justify-content: center;
      align-items: center;
    }
    .dot {
      width: 8px; height: 8px;
      border-radius: 50%;
      background: rgba(255,255,255,0.2);
      transition: all 0.4s ease;
      cursor: pointer;
    }
    .dot.active {
      width: 24px;
      border-radius: 12px;
      background: var(--pink-neon);
      box-shadow: 0 0 10px var(--pink-neon);
    }

    /* First-time Swipe Hint */
    .swipe-hint {
      font-size: 0.75rem;
      letter-spacing: 1px;
      color: var(--text-dim);
      margin-top: 4px;
      animation: fadeOutHint 6s forwards 3s;
    }
    @keyframes fadeOutHint { to { opacity: 0; visibility: hidden; } }

    /* ==========================================================================
       SCREEN 3.5 — LIGHTBOX
       ========================================================================== */
    .lightbox {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(5, 5, 8, 0.95);
      backdrop-filter: blur(25px);
      -webkit-backdrop-filter: blur(25px);
      z-index: 1000;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.4s var(--ease-cinematic);
      padding: max(20px, env(safe-area-inset-top)) max(20px, env(safe-area-inset-right)) max(20px, env(safe-area-inset-bottom)) max(20px, env(safe-area-inset-left));
    }
    .lightbox.active {
      opacity: 1;
      pointer-events: auto;
    }
    .lightbox-content {
      position: relative;
      max-width: 90vw;
      max-height: 75vh;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    .lightbox-img {
      max-width: 100%;
      max-height: 70vh;
      border-radius: var(--radius-md);
      box-shadow: 0 25px 60px rgba(0,0,0,0.95);
      border: 1px solid var(--border-glass);
      transform: scale(0.92);
      transition: transform 0.4s var(--ease-cinematic);
      object-fit: contain;
    }
    .lightbox.active .lightbox-img {
      transform: scale(1);
    }
    .lightbox-caption {
      margin-top: 16px;
      color: #ffffff;
      font-size: 0.95rem;
      letter-spacing: 1px;
      text-align: center;
    }
    .lightbox-close {
      position: absolute;
      top: max(20px, env(safe-area-inset-top));
      right: max(20px, env(safe-area-inset-right));
      background: rgba(255,255,255,0.1);
      border: 1px solid var(--border-glass);
      color: #fff;
      width: 44px; height: 44px;
      border-radius: 50%;
      font-size: 1.4rem;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: background 0.3s ease;
      z-index: 1001;
    }
    .lightbox-close:hover { background: rgba(255, 79, 163, 0.3); }

    .lightbox-nav {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      background: rgba(255,255,255,0.08);
      border: 1px solid var(--border-glass);
      color: #fff;
      width: 44px; height: 44px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      transition: all 0.3s ease;
      z-index: 1001;
    }
    .lightbox-nav.prev { left: clamp(10px, 3vw, 30px); }
    .lightbox-nav.next { right: clamp(10px, 3vw, 30px); }
    .lightbox-nav:hover { background: var(--pink-neon); }

    /* ==========================================================================
       SCREEN 4 — TYPEWRITER LETTER
       ========================================================================== */
    #screen-letter {
      width: 100%;
      max-width: 620px;
    }
    .letter-card {
      width: 100%;
      max-height: 58vh;
      display: flex;
      flex-direction: column;
      padding: clamp(20px, 4.5vw, 36px);
      border: 1px solid var(--border-gold);
      position: relative;
      overflow-y: auto;
      background: linear-gradient(165deg, rgba(20, 20, 26, 0.8), rgba(10, 10, 14, 0.9));
      box-shadow: inset 0 0 30px rgba(212, 175, 55, 0.05), var(--shadow-deep);
      -webkit-overflow-scrolling: touch;
    }
    .letter-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; width: 100%; height: 3px;
      background: linear-gradient(90deg, var(--gold-luxury), var(--pink-neon), var(--gold-luxury));
    }
    .letter-body {
      min-height: 180px;
      font-size: clamp(0.92rem, 3.1vw, 1.08rem);
      line-height: 1.85;
      color: rgba(255, 255, 255, 0.92);
      white-space: pre-wrap;
      font-weight: 300;
    }
    .lang-am .letter-body {
      font-family: var(--font-ethiopic);
      line-height: 2.1;
      font-size: clamp(0.95rem, 3.2vw, 1.1rem);
    }
    .typing-cursor {
      display: inline-block;
      width: 2px;
      height: 1.2em;
      background: var(--pink-neon);
      margin-left: 3px;
      vertical-align: middle;
      animation: blinkCursor 0.8s infinite;
    }
    @keyframes blinkCursor { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }

    .letter-signature {
      margin-top: 24px;
      text-align: right;
      font-family: var(--font-cursive);
      font-size: 1.6rem;
      color: var(--gold-light);
      opacity: 0;
      transition: opacity 1s ease;
    }
    .letter-signature.visible { opacity: 1; }

    /* ==========================================================================
       SCREEN 5 — COUNTDOWN
       ========================================================================== */
    #screen-countdown { text-align: center; }
    .countdown-num {
      font-family: var(--font-display);
      font-size: clamp(6.5rem, 26vw, 12rem);
      font-weight: 900;
      line-height: 1;
      background: linear-gradient(135deg, var(--gold-light), var(--pink-neon));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      filter: drop-shadow(0 0 40px rgba(255,79,163,0.5));
      will-change: transform, opacity, filter;
    }
    .num-animate {
      animation: countScaleBlur 0.9s cubic-bezier(0.16, 1, 0.3, 1) forwards;
    }
    @keyframes countScaleBlur {
      0% { transform: scale(0.4); opacity: 0; filter: blur(20px); }
      50% { transform: scale(1.15); opacity: 1; filter: blur(0px); }
      100% { transform: scale(1); opacity: 1; filter: blur(0px); }
    }

    /* ==========================================================================
       SCREEN 6 — 3D GIFT BOX
       ========================================================================== */
    #screen-gift {
      perspective: 1200px;
      text-align: center;
    }
    .gift-stage {
      width: clamp(180px, 45vw, 220px);
      height: clamp(180px, 45vw, 220px);
      position: relative;
      transform-style: preserve-3d;
      margin: 30px auto 40px auto;
      cursor: pointer;
      animation: floatGift 5s ease-in-out infinite alternate;
    }
    @keyframes floatGift {
      0% { transform: translateY(0) rotateX(12deg) rotateY(-15deg); }
      100% { transform: translateY(-16px) rotateX(18deg) rotateY(15deg); }
    }

    .gift-cube {
      width: 100%; height: 100%;
      position: absolute;
      transform-style: preserve-3d;
      transition: transform 0.5s ease;
    }
    .cube-face {
      position: absolute;
      width: 100%; height: 100%;
      background: linear-gradient(135deg, #1a121d, #0d0810);
      border: 1px solid rgba(212, 175, 55, 0.35);
      box-shadow: inset 0 0 30px rgba(255, 79, 163, 0.15);
    }
    .face-front  { transform: rotateY(  0deg) translateZ(clamp(90px, 22.5vw, 110px)); }
    .face-back   { transform: rotateY(180deg) translateZ(clamp(90px, 22.5vw, 110px)); }
    .face-right  { transform: rotateY( 90deg) translateZ(clamp(90px, 22.5vw, 110px)); }
    .face-left   { transform: rotateY(-90deg) translateZ(clamp(90px, 22.5vw, 110px)); }
    .face-bottom { transform: rotateX(-90deg) translateZ(clamp(90px, 22.5vw, 110px)); box-shadow: 0 40px 60px #000; }
    
    .gift-lid {
      position: absolute;
      width: calc(100% + 10px);
      height: 45px;
      top: -5px; left: -5px;
      transform-style: preserve-3d;
      transform-origin: back;
      transition: transform 1.2s var(--ease-cinematic);
    }
    .lid-face {
      position: absolute;
      background: linear-gradient(135deg, #241628, #120a16);
      border: 1px solid rgba(212, 175, 55, 0.45);
    }
    .lid-top    { width: 100%; height: clamp(190px, 47vw, 230px); transform: rotateX(90deg) translateZ(22px); }
    .lid-front  { width: 100%; height: 45px;  transform: translateZ(clamp(95px, 23.5vw, 115px)); }
    .lid-left   { width: clamp(190px, 47vw, 230px); height: 45px;  transform: rotateY(-90deg) translateZ(5px); }
    .lid-right  { width: clamp(190px, 47vw, 230px); height: 45px;  transform: rotateY(90deg) translateZ(clamp(185px, 42.5vw, 225px)); }
    .lid-back   { width: 100%; height: 45px;  transform: rotateY(180deg) translateZ(clamp(95px, 23.5vw, 115px)); }

    .ribbon-v, .ribbon-h {
      position: absolute;
      background: linear-gradient(90deg, var(--gold-luxury), var(--gold-light), var(--gold-luxury));
      box-shadow: 0 0 10px rgba(212, 175, 55, 0.5);
    }
    .ribbon-v { width: 26px; height: 100%; left: calc(50% - 13px); top: 0; }
    .ribbon-h { width: 100%; height: 26px; top: calc(50% - 13px); left: 0; }

    .gift-internal-glow {
      position: absolute;
      top: 0; left: 0; width: 100%; height: 100%;
      background: radial-gradient(circle, rgba(255, 79, 163, 0.9) 0%, rgba(212, 175, 55, 0.8) 50%, transparent 80%);
      opacity: 0;
      transition: opacity 0.8s ease;
      pointer-events: none;
      transform: translateZ(0);
    }

    .gift-stage.open .gift-lid {
      transform: translateY(-130px) rotateX(-120deg) rotateY(15deg);
    }
    .gift-stage.open .gift-internal-glow {
      opacity: 1;
    }

    /* ==========================================================================
       SCREEN 7 — FINAL REVEAL
       ========================================================================== */
    #screen-final { text-align: center; }
    .avatar-frame {
      width: clamp(130px, 32vw, 180px);
      height: clamp(130px, 32vw, 180px);
      border-radius: 50%;
      padding: 5px;
      background: linear-gradient(135deg, var(--gold-luxury), var(--pink-neon));
      box-shadow: var(--glow-pink), var(--glow-gold);
      margin-bottom: 25px;
      animation: avatarFloat 4s ease-in-out infinite alternate;
    }
    .avatar-img-wrap {
      width: 100%; height: 100%;
      border-radius: 50%;
      overflow: hidden;
      background: var(--bg-surface);
    }
    .avatar-img-wrap img {
      width: 100%; height: 100%;
      object-fit: cover;
    }
    @keyframes avatarFloat {
      0% { transform: translateY(0) scale(1); }
      100% { transform: translateY(-10px) scale(1.03); }
    }

    .reveal-msg {
      max-width: 520px;
      font-size: clamp(1.05rem, 3.6vw, 1.4rem);
      line-height: 1.8;
      font-weight: 300;
      color: #fff;
    }
    .reveal-msg span {
      display: block;
      opacity: 0;
      transform: translateY(15px);
      transition: opacity 0.8s var(--ease-cinematic), transform 0.8s var(--ease-cinematic);
    }
    .reveal-msg span.visible {
      opacity: 1;
      transform: translateY(0);
    }
    .reveal-msg .final-highlight {
      color: var(--pink-neon);
      font-weight: 600;
      margin-top: 15px;
      text-shadow: 0 0 15px rgba(255, 79, 163, 0.4);
    }

    /* ==========================================================================
       SCREEN 8 — ENDING
       ========================================================================== */
    #screen-ending { text-align: center; }
    .ending-title {
      font-size: clamp(1.7rem, 5.5vw, 2.8rem);
      margin-bottom: 12px;
    }
    .creator-tag {
      font-size: 0.95rem;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--gold-light);
      margin-bottom: 25px;
      opacity: 0.85;
    }
    .heart-icon {
      font-size: 3.2rem;
      display: inline-block;
      color: var(--pink-neon);
      filter: drop-shadow(0 0 20px var(--pink-neon));
      animation: heartBeat 1.6s ease-in-out infinite;
      margin-bottom: 25px;
    }
    @keyframes heartBeat {
      0%, 100% { transform: scale(1); }
      15% { transform: scale(1.22); }
      30% { transform: scale(1); }
      45% { transform: scale(1.12); }
    }

    .replay-btn-wrap {
      margin-top: 10px;
    }

    @media (max-width: 390px) {
      .top-controls { padding: 0 12px; }
      .btn-luxury { padding: 14px 26px; font-size: 0.85rem; }
      .letter-card { padding: 18px; }
      .name-container { gap: 4px; }
    }

    @media (prefers-reduced-motion: reduce) {
      *, ::before, ::after {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.01ms !important;
      }
      .spotlight-radial, .heart-icon, .avatar-frame, .gift-stage {
        animation: none !important;
      }
    }
  </style>
</head>
<body>

  <!-- Background Particle System -->
  <canvas id="particleCanvas"></canvas>
  <div class="cinematic-overlay"></div>
  <div class="film-grain"></div>
  <div class="ambient-light-1"></div>
  <div class="ambient-light-2"></div>

  <!-- Top Header Controls -->
  <header class="top-controls">
    <div class="lang-switcher" role="radiogroup" aria-label="Language selection">
      <div class="lang-indicator" id="langIndicator"></div>
      <button class="lang-btn active" id="btn-en" role="radio" aria-checked="true" onclick="setLanguage('en')">EN</button>
      <button class="lang-btn" id="btn-am" role="radio" aria-checked="false" onclick="setLanguage('am')">አማ</button>
    </div>
    
    <div class="audio-control glass-panel" id="audio-widget">
      <button class="audio-btn" id="audio-toggle" aria-label="Toggle Background Music" onclick="toggleAudio()">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <path d="M9 18V5l12-2v13"></path>
          <circle cx="6" cy="18" r="3"></circle>
          <circle cx="18" cy="16" r="3"></circle>
        </svg>
      </button>
      <div class="audio-bars" aria-hidden="true">
        <div class="audio-bar"></div>
        <div class="audio-bar"></div>
        <div class="audio-bar"></div>
        <div class="audio-bar"></div>
      </div>
      <div class="music-toast" id="musicToast">Music On</div>
    </div>
  </header>

  <!-- Audio Element -->
  <audio id="bg-music" loop preload="auto">
    <source src="https://cdn.pixabay.com/download/audio/2022/05/27/audio_1808fbf07a.mp3?filename=piano-moment-113941.mp3" type="audio/mpeg">
  </audio>

  <!-- Main Application Container -->
  <main id="app">

    <!-- SCREEN 1: CINEMATIC OPENING -->
    <section class="screen active" id="screen-opening" onclick="nextScreen()" role="button" tabindex="0" aria-label="Tap to begin experience">
      <div class="opening-content">
        <div class="spotlight-radial"></div>
        <p class="opening-subtext" data-en="Someone prepared something special just for you... ❤️" data-am="ለአንቺ የተዘጋጀ ልዩ ስጦታ አለ... ❤️">
          Someone prepared something special just for you... ❤️
        </p>
        <div class="tap-hint" data-en="Tap anywhere to continue" data-am="ለመቀጠል የትም ቦታ ይነኩ">
          <span>Tap anywhere to continue</span>
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M5 12h14M12 5l7 7-7 7"/>
          </svg>
        </div>
      </div>
    </section>

    <!-- SCREEN 2: BLEN REVEAL -->
    <section class="screen" id="screen-reveal">
      <div class="name-container" aria-label="BLEN">
        <span class="letter">B</span>
        <span class="letter">L</span>
        <span class="letter">E</span>
        <span class="letter">N</span>
        <span class="letter" style="color: var(--pink-neon)">❤️</span>
      </div>
      <div class="reveal-subtitle" data-en="Something made only for you" data-am="ለአንቺ ብቻ የተሠራ">Something made only for you</div>
      <p class="welcome-text" data-en="Welcome to your private digital world. Prepared with love and care." data-am="እንኳን ወደ እራስሽ ዲጂታል ዓለም በሰላም መጣሽ። በፍቅርና በጥንቃቄ የተዘጋጀ።">
        Welcome to your private digital world. Prepared with love and care.
      </p>
      <div class="reveal-btn-wrap">
        <button class="btn-luxury" onclick="nextScreen()" data-en="Begin Experience" data-am="ጉዞውን ይጀምሩ">
          Begin Experience
        </button>
      </div>
    </section>

    <!-- SCREEN 3: MEMORIES GALLERY -->
    <section class="screen" id="screen-memories">
      <div class="section-header">
        <h2 class="section-title title-gold" data-en="Memories We Share" data-am="የምናጋራቸው ትዝታዎች">Memories We Share</h2>
        <p class="section-subtitle" data-en="Swipe or drag to explore" data-am="ለማየት ወደ ጎን ይሳቡ">Swipe or drag to explore</p>
      </div>

      <div class="carousel-container-wrap">
        <button class="carousel-arrow prev" onclick="prevCarouselCard()" aria-label="Previous photo">&#10094;</button>
        
        <div class="carousel-viewport" id="carouselViewport">
          <div class="carousel-track" id="carouselTrack"></div>
        </div>

        <button class="carousel-arrow next" onclick="nextCarouselCard()" aria-label="Next photo">&#10095;</button>
      </div>

      <div class="carousel-info">
        <div class="carousel-counter" id="carouselCounter">01 / 05</div>
        <div class="carousel-nav-dots" id="carouselDots"></div>
        <div class="swipe-hint" data-en="‹ Swipe left or right ›" data-am="‹ ወደ ግራ ወይም ቀኝ ይሳቡ ›">‹ Swipe left or right ›</div>
      </div>

      <div style="text-align: center; margin-top: 10px;">
        <button class="btn-luxury" onclick="nextScreen()" data-en="Continue Journey" data-am="ቀጥል">
          Continue Journey
        </button>
      </div>
    </section>

    <!-- SCREEN 4: TYPEWRITER LETTER -->
    <section class="screen" id="screen-letter">
      <div class="letter-card glass-panel" id="letterCard">
        <div class="letter-body" id="typewriterTarget"></div>
        <span class="typing-cursor" id="typingCursor"></span>
        <div class="letter-signature" id="letterSignature">
          With love,<br>Yisshak
        </div>
      </div>
      <div style="margin-top: 25px; opacity: 0;" id="letter-btn-wrap">
        <button class="btn-luxury" onclick="nextScreen()" data-en="Next Surprise" data-am="ቀጣይ ስጦታ">
          Next Surprise
        </button>
      </div>
    </section>

    <!-- SCREEN 5: COUNTDOWN -->
    <section class="screen" id="screen-countdown">
      <p class="opening-subtext" style="opacity: 1; transform: none; margin-bottom: 10px;" data-en="One last amazing thing..." data-am="አንድ የመጨረሻ ድንቅ ነገር...">
        One last amazing thing...
      </p>
      <div class="countdown-num" id="countdown-val">3</div>
    </section>

    <!-- SCREEN 6: 3D GIFT BOX -->
    <section class="screen" id="screen-gift">
      <h2 class="section-title title-pink" style="margin-bottom: 6px;" data-en="A Gift For You" data-am="ለአንቺ የተዘጋጀ ስጦታ">A Gift For You</h2>
      <p class="section-subtitle" data-en="Tap the box to unlock your surprise" data-am="ስጦታውን ለመክፈት ሳጥኑን ይነኩ">Tap the box to unlock your surprise</p>

      <div class="gift-stage" id="giftBox" onclick="openGift()" role="button" tabindex="0" aria-label="Open 3D Gift Box">
        <div class="gift-cube">
          <div class="cube-face face-front"><div class="ribbon-v"></div><div class="ribbon-h"></div></div>
          <div class="cube-face face-back"><div class="ribbon-v"></div><div class="ribbon-h"></div></div>
          <div class="cube-face face-right"><div class="ribbon-v"></div><div class="ribbon-h"></div></div>
          <div class="cube-face face-left"><div class="ribbon-v"></div><div class="ribbon-h"></div></div>
          <div class="cube-face face-bottom"></div>
          <div class="gift-internal-glow"></div>
        </div>
        <div class="gift-lid">
          <div class="lid-face lid-top"><div class="ribbon-v"></div><div class="ribbon-h"></div></div>
          <div class="lid-face lid-front"><div class="ribbon-v"></div></div>
          <div class="lid-face lid-left"><div class="ribbon-v"></div></div>
          <div class="lid-face lid-right"><div class="ribbon-v"></div></div>
          <div class="lid-face lid-back"><div class="ribbon-v"></div></div>
        </div>
      </div>

      <button class="btn-luxury" onclick="openGift()" id="openGiftBtn" data-en="🎁 Open Your Gift" data-am="🎁 ስጦታውን ክፈች">
        🎁 Open Your Gift
      </button>
    </section>

    <!-- SCREEN 7: FINAL REVEAL -->
    <section class="screen" id="screen-final">
      <div class="avatar-frame">
        <div class="avatar-img-wrap">
          <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&q=80&w=600" alt="Blen Profile Photo" id="profileImage">
        </div>
      </div>
      <div class="reveal-msg">
        <span data-en="Every smile," data-am="እያንዳንዱ ፈገግታ፣">Every smile,</span>
        <span data-en="every memory," data-am="እያንዳንዱ ትዝታ፣">every memory,</span>
        <span data-en="every moment..." data-am="እያንዳንዱ ቅጽበት...">every moment...</span>
        <span class="final-highlight" data-en="Thank you for being part of my life. ❤️" data-am="በሕይወቴ ውስጥ ስላለሽ አመሰግናለሁ። ❤️">Thank you for being part of my life. ❤️</span>
      </div>
      <div style="margin-top: 35px;">
        <button class="btn-luxury" onclick="nextScreen()" data-en="Final Note" data-am="የመጨረሻው ገጽ">
          Final Note
        </button>
      </div>
    </section>

    <!-- SCREEN 8: ENDING -->
    <section class="screen" id="screen-ending">
      <h2 class="ending-title title-gold" data-en="Made especially for you ❤️" data-am="ለአንቺ ብቻ የተዘጋጀ ❤️">Made especially for you ❤️</h2>
      <p class="creator-tag" data-en="Created by Yisshak" data-am="በይስሐቅ የተፈጠረ">Created by Yisshak</p>
      <div class="heart-icon">💖</div>
      <div class="replay-btn-wrap">
        <button class="btn-luxury" onclick="replayExperience()" data-en="↻ Replay Experience" data-am="↻ ድጋሚ ያጫውቱ">
          ↻ Replay Experience
        </button>
      </div>
    </section>

  </main>

  <!-- Gallery Lightbox -->
  <div class="lightbox" id="lightbox" role="dialog" aria-modal="true" aria-label="Photo Lightbox">
    <button class="lightbox-close" onclick="closeLightbox()" aria-label="Close Lightbox">&times;</button>
    <button class="lightbox-nav prev" onclick="navigateLightbox(-1)" aria-label="Previous Image">&#10094;</button>
    <div class="lightbox-content">
      <img src="" alt="Enlarged Memory Photo" class="lightbox-img" id="lightboxImg">
      <div class="lightbox-caption" id="lightboxCaption"></div>
    </div>
    <button class="lightbox-nav next" onclick="navigateLightbox(1)" aria-label="Next Image">&#10095;</button>
  </div>

  <!-- JavaScript Application Logic -->
  <script>
    const STATE = {
      currentScreen: 0,
      language: 'en',
      isPlayingAudio: false,
      isGiftOpened: false,
      carouselIndex: 0,
      typingInProgress: false,
      countdownRunning: false,
      lightboxIndex: 0
    };

    const SCREENS = [
      'screen-opening',
      'screen-reveal',
      'screen-memories',
      'screen-letter',
      'screen-countdown',
      'screen-gift',
      'screen-final',
      'screen-ending'
    ];

    const GALLERY_DATA = [
      { url: 'https://images.unsplash.com/photo-1517841905240-472988babdf9?auto=format&fit=crop&q=80&w=800', capEn: 'Unforgettable Moments', capAm: 'የማይረሱ ቅጽበቶች' },
      { url: 'https://images.unsplash.com/photo-1524504388940-b1c1722653e1?auto=format&fit=crop&q=80&w=800', capEn: 'Pure Joy & Laughter', capAm: 'ደስታ እና ሳቅ' },
      { url: 'https://images.unsplash.com/photo-1494790108377-be9c29b29330?auto=format&fit=crop&q=80&w=800', capEn: 'Cherished Memories', capAm: 'የተወደዱ ትዝታዎች' },
      { url: 'https://images.unsplash.com/photo-1539571696357-5a69c17a67c6?auto=format&fit=crop&q=80&w=800', capEn: 'Shared Journeys', capAm: 'አብረው ያሳለፏቸው መንገዶች' },
      { url: 'https://images.unsplash.com/photo-1517841905240-472988babdf9?auto=format&fit=crop&q=80&w=800', capEn: 'Forever Friends', capAm: 'የዘላለም ጓደኝነት' }
    ];

    const LETTER_TEXTS = {
      en: `Dear Blen,\n\nSome people make the world brighter just by being in it, and you are truly one of those rare souls. From every shared laugh to every quiet moment of support, having you as a friend is a gift I cherish deeply.\n\nThis digital experience is just a tiny gesture to celebrate you, your warmth, and the incredible person you are.\n\nThank you for every beautiful memory.`,
      am: `ውድ ብሌን፥\n\nአንዳንድ ሰዎች በሕይወት በመኖራቸው ብቻ ዓለምን ያበራሉ። አንቺ በእውነት ከነዚያ അപூர்ብ ከሆኑ ሰዎች አንዷ ነሽ። አብረን ካሳለፍነው ሳቅ እስከ ተደረገልኝ ድጋፍ ድረስ፡ አንቺን እንደ ጓደኛ ማግኘት ትልቅ ስጦታ ነው።\n\nይህ ዲጂታል ማስታወሻ ያንቺን ደግነትና ድንቅነት ለማክበር የተዘጋጀ ትንሽ ስጦታ ነው።\n\nስለ ሁሉም ውብ ትዝታዎች አመሰግናለሁ።`
    };

    /* Particle Canvas Engine */
    const canvas = document.getElementById('particleCanvas');
    const ctx = canvas.getContext('2d');
    let particles = [];
    let canvasWidth = canvas.width = window.innerWidth;
    let canvasHeight = canvas.height = window.innerHeight;
    let particleAnimationId = null;
    let isPageVisible = true;

    window.addEventListener('resize', () => {
      canvasWidth = canvas.width = window.innerWidth;
      canvasHeight = canvas.height = window.innerHeight;
    });

    document.addEventListener('visibilitychange', () => {
      isPageVisible = !document.hidden;
      if (isPageVisible && !particleAnimationId) {
        animateParticles();
      }
    });

    class Particle {
      constructor(isBurst = false, originX = 0, originY = 0) {
        this.reset(isBurst, originX, originY);
      }

      reset(isBurst = false, originX = 0, originY = 0) {
        this.isBurst = isBurst;
        if (isBurst) {
          this.x = originX;
          this.y = originY;
          this.size = Math.random() * 4 + 2;
          this.speedY = (Math.random() - 0.5) * 10;
          this.speedX = (Math.random() - 0.5) * 10;
          this.opacity = 1;
          this.life = 1;
          this.decay = Math.random() * 0.02 + 0.015;
        } else {
          this.x = Math.random() * canvasWidth;
          this.y = canvasHeight + Math.random() * 100;
          this.size = Math.random() * 3 + 1;
          this.speedY = Math.random() * 1.2 + 0.4;
          this.speedX = (Math.random() - 0.5) * 0.5;
          this.opacity = Math.random() * 0.6 + 0.2;
          this.color = Math.random() > 0.4 ? '#ff4fa3' : '#d4af37';
          this.isHeart = Math.random() > 0.82;
        }
      }

      update() {
        if (this.isBurst) {
          this.x += this.speedX;
          this.y += this.speedY;
          this.life -= this.decay;
          this.opacity = Math.max(0, this.life);
        } else {
          this.y -= this.speedY;
          this.x += this.speedX;
          if (this.y < -20) this.reset();
        }
      }

      draw() {
        if (this.opacity <= 0) return;
        ctx.fillStyle = this.color || '#ff4fa3';
        ctx.globalAlpha = this.opacity;

        if (this.isHeart) {
          ctx.font = `${this.size * 3}px serif`;
          ctx.fillText('♥', this.x, this.y);
        } else {
          ctx.beginPath();
          ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
          ctx.fill();
        }
      }
    }

    function initParticles() {
      const count = window.innerWidth < 600 ? 30 : 60;
      particles = [];
      for (let i = 0; i < count; i++) {
        particles.push(new Particle());
      }
    }

    function animateParticles() {
      if (!isPageVisible) {
        particleAnimationId = null;
        return;
      }
      ctx.clearRect(0, 0, canvasWidth, canvasHeight);
      
      for (let i = particles.length - 1; i >= 0; i--) {
        const p = particles[i];
        p.update();
        p.draw();
        
        if (p.isBurst && p.life <= 0) {
          particles.splice(i, 1);
        }
      }
      particleAnimationId = requestAnimationFrame(animateParticles);
    }

    initParticles();
    animateParticles();

    function triggerParticleBurst(x, y, count = 35) {
      for (let i = 0; i < count; i++) {
        particles.push(new Particle(true, x, y));
      }
    }

    /* Screen Controller */
    function goToScreen(index) {
      if (index < 0 || index >= SCREENS.length) return;

      const currentEl = document.getElementById(SCREENS[STATE.currentScreen]);
      const nextEl = document.getElementById(SCREENS[index]);

      currentEl.classList.remove('active');
      STATE.currentScreen = index;
      nextEl.classList.add('active');

      if (SCREENS[index] === 'screen-letter') {
        startTypewriter();
      } else if (SCREENS[index] === 'screen-countdown') {
        runCountdown();
      } else if (SCREENS[index] === 'screen-final') {
        runFinalReveal();
      }
    }

    function nextScreen() {
      if (!STATE.isPlayingAudio && STATE.currentScreen === 0) {
        toggleAudio();
      }
      triggerParticleBurst(canvasWidth / 2, canvasHeight / 2, 15);
      goToScreen(STATE.currentScreen + 1);
    }

    /* Audio System */
    const audio = document.getElementById('bg-music');
    const audioWidget = document.getElementById('audio-widget');
    const musicToast = document.getElementById('musicToast');
    let toastTimer = null;

    function showMusicToast(text) {
      musicToast.textContent = text;
      musicToast.classList.add('show');
      if (toastTimer) clearTimeout(toastTimer);
      toastTimer = setTimeout(() => {
        musicToast.classList.remove('show');
      }, 1600);
    }

    function toggleAudio() {
      if (STATE.isPlayingAudio) {
        audio.pause();
        audioWidget.classList.remove('playing');
        STATE.isPlayingAudio = false;
        showMusicToast("Muted");
      } else {
        audio.play().then(() => {
          audioWidget.classList.add('playing');
          STATE.isPlayingAudio = true;
          showMusicToast("Music On");
        }).catch(() => {});
      }
    }

    /* Language Switcher */
    function setLanguage(lang) {
      STATE.language = lang;

      const btnEn = document.getElementById('btn-en');
      const btnAm = document.getElementById('btn-am');
      const indicator = document.getElementById('langIndicator');

      if (lang === 'am') {
        btnEn.classList.remove('active');
        btnAm.classList.add('active');
        btnEn.setAttribute('aria-checked', 'false');
        btnAm.setAttribute('aria-checked', 'true');
        indicator.style.transform = 'translateX(100%)';
        document.body.classList.add('lang-am');
      } else {
        btnAm.classList.remove('active');
        btnEn.classList.add('active');
        btnAm.setAttribute('aria-checked', 'false');
        btnEn.setAttribute('aria-checked', 'true');
        indicator.style.transform = 'translateX(0%)';
        document.body.classList.remove('lang-am');
      }

      document.querySelectorAll('[data-en]').forEach(el => {
        const text = el.getAttribute(`data-${lang}`);
        if (text) el.textContent = text;
      });

      renderCarousel();
      if (SCREENS[STATE.currentScreen] === 'screen-letter') {
        startTypewriter();
      }
    }

    /* 3D Carousel System */
    const track = document.getElementById('carouselTrack');
    const dotsContainer = document.getElementById('carouselDots');
    const counterEl = document.getElementById('carouselCounter');

    function renderCarousel() {
      track.innerHTML = '';
      dotsContainer.innerHTML = '';

      GALLERY_DATA.forEach((item, index) => {
        const card = document.createElement('div');
        card.className = 'carousel-card';
        const caption = STATE.language === 'am' ? item.capAm : item.capEn;
        
        card.innerHTML = `
          <img src="${item.url}" alt="${caption}" loading="lazy" onerror="this.onerror=null;this.src='data:image/svg+xml,%3Csvg xmlns=\'http://www.w3.org/2000/svg\' width=\'100%25\' height=\'100%25\'%3E%3Crect width=\'100%25\' height=\'100%25\' fill=\'%23121218\'/%3E%3Ctext x=\'50%25\' y=\'50%25\' fill=\'%23d4af37\' dominant-baseline=\'middle\' text-anchor=\'middle\' font-size=\'14\'%3EMemory Photo%3C/text%3E%3C/svg%3E';">
          <div class="card-caption">${caption}</div>
        `;
        
        card.onclick = () => {
          if (index === STATE.carouselIndex) {
            openLightbox(index);
          } else {
            STATE.carouselIndex = index;
            updateCarousel();
          }
        };

        track.appendChild(card);

        const dot = document.createElement('div');
        dot.className = `dot ${index === STATE.carouselIndex ? 'active' : ''}`;
        dot.onclick = () => {
          STATE.carouselIndex = index;
          updateCarousel();
        };
        dotsContainer.appendChild(dot);
      });

      updateCarousel();
    }

    function updateCarousel() {
      const cards = track.children;
      const total = cards.length;

      Array.from(cards).forEach((card, i) => {
        const offset = i - STATE.carouselIndex;
        const absOffset = Math.abs(offset);

        if (absOffset > 2) {
          card.style.opacity = '0';
          card.style.pointerEvents = 'none';
          return;
        }

        const translateX = offset * 180;
        const translateZ = -absOffset * 150;
        const rotateY = offset * -15;

        card.style.opacity = absOffset === 0 ? '1' : '0.6';
        card.style.filter = absOffset === 0 ? 'blur(0px) brightness(1.05)' : 'blur(4px) brightness(0.7)';
        card.style.transform = `translateX(${translateX}px) translateZ(${translateZ}px) rotateY(${rotateY}deg)`;
        card.style.zIndex = `${10 - absOffset}`;
        card.classList.toggle('active-card', absOffset === 0);
      });

      counterEl.textContent = `0${STATE.carouselIndex + 1} / 0${total}`;
      Array.from(dotsContainer.children).forEach((dot, i) => {
        dot.classList.toggle('active', i === STATE.carouselIndex);
      });
    }

    function prevCarouselCard() {
      if (STATE.carouselIndex > 0) {
        STATE.carouselIndex--;
        updateCarousel();
      }
    }

    function nextCarouselCard() {
      if (STATE.carouselIndex < GALLERY_DATA.length - 1) {
        STATE.carouselIndex++;
        updateCarousel();
      }
    }

    let startX = 0;
    const viewport = document.getElementById('carouselViewport');
    
    viewport.addEventListener('touchstart', e => startX = e.touches[0].clientX, {passive: true});
    viewport.addEventListener('touchend', e => {
      const diffX = startX - e.changedTouches[0].clientX;
      if (Math.abs(diffX) > 40) {
        if (diffX > 0) nextCarouselCard();
        else prevCarouselCard();
      }
    }, {passive: true});

    document.addEventListener('keydown', e => {
      if (SCREENS[STATE.currentScreen] === 'screen-memories') {
        if (e.key === 'ArrowLeft') prevCarouselCard();
        if (e.key === 'ArrowRight') nextCarouselCard();
      }
      if (e.key === 'Escape') closeLightbox();
    });

    renderCarousel();

    /* Lightbox System */
    function openLightbox(index) {
      STATE.lightboxIndex = index;
      updateLightboxContent();
      document.getElementById('lightbox').classList.add('active');
    }

    function closeLightbox() {
      document.getElementById('lightbox').classList.remove('active');
    }

    function navigateLightbox(dir) {
      STATE.lightboxIndex += dir;
      if (STATE.lightboxIndex < 0) STATE.lightboxIndex = GALLERY_DATA.length - 1;
      if (STATE.lightboxIndex >= GALLERY_DATA.length) STATE.lightboxIndex = 0;
      updateLightboxContent();
    }

    function updateLightboxContent() {
      const item = GALLERY_DATA[STATE.lightboxIndex];
      const caption = STATE.language === 'am' ? item.capAm : item.capEn;
      document.getElementById('lightboxImg').src = item.url;
      document.getElementById('lightboxCaption').textContent = `${caption} (${STATE.lightboxIndex + 1}/${GALLERY_DATA.length})`;
    }

    /* Typewriter System */
    let typingTimer = null;

    function startTypewriter() {
      const target = document.getElementById('typewriterTarget');
      const cursor = document.getElementById('typingCursor');
      const signature = document.getElementById('letterSignature');
      const btnWrap = document.getElementById('letter-btn-wrap');
      const text = LETTER_TEXTS[STATE.language];

      target.textContent = '';
      cursor.style.display = 'inline-block';
      signature.classList.remove('visible');
      btnWrap.style.opacity = '0';
      btnWrap.style.transform = 'translateY(15px)';

      if (typingTimer) clearInterval(typingTimer);

      let idx = 0;
      STATE.typingInProgress = true;

      typingTimer = setInterval(() => {
        if (idx < text.length) {
          target.textContent += text.charAt(idx);
          idx++;
          document.getElementById('letterCard').scrollTop = document.getElementById('letterCard').scrollHeight;
        } else {
          clearInterval(typingTimer);
          STATE.typingInProgress = false;
          cursor.style.display = 'none';
          signature.classList.add('visible');

          btnWrap.style.transition = 'all 0.8s var(--ease-cinematic)';
          btnWrap.style.opacity = '1';
          btnWrap.style.transform = 'translateY(0)';
        }
      }, 32);
    }

    /* Countdown Animator */
    function runCountdown() {
      if (STATE.countdownRunning) return;
      STATE.countdownRunning = true;

      const numEl = document.getElementById('countdown-val');
      let val = 3;

      function animateNum(n) {
        numEl.textContent = n;
        numEl.classList.remove('num-animate');
        void numEl.offsetWidth;
        numEl.classList.add('num-animate');
        triggerParticleBurst(canvasWidth / 2, canvasHeight / 2, 20);
      }

      animateNum(val);

      const timer = setInterval(() => {
        val--;
        if (val > 0) {
          animateNum(val);
        } else {
          clearInterval(timer);
          STATE.countdownRunning = false;
          nextScreen();
        }
      }, 1000);
    }

    /* 3D Gift Unboxing */
    function openGift() {
      if (STATE.isGiftOpened) return;
      STATE.isGiftOpened = true;

      const giftBox = document.getElementById('giftBox');
      const openBtn = document.getElementById('openGiftBtn');

      giftBox.classList.add('open');
      openBtn.style.opacity = '0';
      openBtn.style.pointerEvents = 'none';

      if (navigator.vibrate) {
        navigator.vibrate([80, 40, 180]);
      }

      triggerParticleBurst(canvasWidth / 2, canvasHeight / 2, 60);

      setTimeout(() => {
        nextScreen();
      }, 1600);
    }

    /* Final Reveal Animator */
    function runFinalReveal() {
      const lines = document.querySelectorAll('.reveal-msg span');
      lines.forEach(line => line.classList.remove('visible'));

      lines.forEach((line, index) => {
        setTimeout(() => {
          line.classList.add('visible');
          triggerParticleBurst(canvasWidth / 2, canvasHeight / 2 - 50, 10);
        }, (index + 1) * 750);
      });
    }

    /* Replay Experience */
    function replayExperience() {
      STATE.isGiftOpened = false;
      STATE.carouselIndex = 0;
      
      const giftBox = document.getElementById('giftBox');
      const openBtn = document.getElementById('openGiftBtn');
      giftBox.classList.remove('open');
      openBtn.style.opacity = '1';
      openBtn.style.pointerEvents = 'auto';

      updateCarousel();
      goToScreen(0);
    }
  </script>
</body>
</html>
