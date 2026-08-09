<!DOCTYPE html>
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
      text-decoration: none;
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
       SCREEN 0 — PREMIUM PASSWORD / WELCOME SCREEN
       ========================================================================== */
    #screen-password {
      text-align: center;
      z-index: 20;
    }
    .pass-card {
      width: clamp(280px, 85vw, 420px);
      padding: clamp(24px, 6vw, 40px) clamp(20px, 5vw, 32px);
      border: 1px solid var(--border-gold);
      background: linear-gradient(165deg, rgba(20, 20, 28, 0.82), rgba(8, 8, 12, 0.92));
      box-shadow: 0 25px 50px rgba(0,0,0,0.9), inset 0 0 20px rgba(255, 79, 163, 0.08);
      display: flex;
      flex-direction: column;
      align-items: center;
      position: relative;
    }
    .pass-brand {
      font-family: var(--font-display);
      font-size: clamp(1.8rem, 6vw, 2.6rem);
      font-weight: 900;
      margin-bottom: 6px;
      letter-spacing: 3px;
    }
    .pass-tagline {
      font-size: clamp(0.8rem, 2.8vw, 0.95rem);
      color: var(--pink-neon);
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 24px;
      font-weight: 600;
    }
    .pass-input-wrap {
      width: 100%;
      margin-bottom: 16px;
      position: relative;
    }
    .pass-input {
      width: 100%;
      padding: 14px 20px;
      border-radius: var(--radius-full);
      background: rgba(255, 255, 255, 0.05);
      border: 1px solid var(--border-gold);
      color: #ffffff;
      font-family: var(--font-sans);
      font-size: 1rem;
      text-align: center;
      outline: none;
      transition: all 0.3s ease;
      letter-spacing: 1.5px;
    }
    .pass-input:focus {
      border-color: var(--pink-neon);
      box-shadow: var(--glow-pink);
      background: rgba(255, 255, 255, 0.09);
    }
    .pass-input::placeholder {
      color: var(--text-dim);
      letter-spacing: 1px;
    }
    .pass-error-msg {
      color: #ff4f6a;
      font-size: 0.85rem;
      min-height: 22px;
      margin-top: 8px;
      letter-spacing: 0.5px;
      opacity: 0;
      transition: opacity 0.3s ease;
    }
    .pass-error-msg.show {
      opacity: 1;
    }

    /* Shake Animation for Wrong Password */
    @keyframes shakeCard {
      0%, 100% { transform: translateX(0); }
      20%, 60% { transform: translateX(-12px); }
      40%, 80% { transform: translateX(12px); }
    }
    .pass-card.shake {
      animation: shakeCard 0.45s cubic-bezier(0.36, 0.07, 0.19, 0.97);
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
    
    /* Box Lid */
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

    /* Ribbons */
    .ribbon-v, .ribbon-h {
      position: absolute;
      background: linear-gradient(90deg, var(--gold-luxury), var(--gold-light), var(--gold-luxury));
      box-shadow: 0 0 10px rgba(212, 175, 55, 0.5);
    }
    .ribbon-v { width: 26px; height: 100%; left: calc(50% - 13px); top: 0; }
    .ribbon-h { width: 100%; height: 26px; top: calc(50% - 13px); left: 0; }

    /* Internal Glow Light Source */
    .gift-internal-glow {
      position: absolute;
      top: 0; left: 0; width: 100%; height: 100%;
      background: radial-gradient(circle, rgba(255, 79, 163, 0.9) 0%, rgba(212, 175, 55, 0.8) 50%, transparent 80%);
      opacity: 0;
      transition: opacity 0.8s ease;
      pointer-events: none;
      transform: translateZ(0);
    }

    /* Open State Animations */
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
      margin-bottom: 8px;
    }
    .creator-tag {
      font-size: 0.95rem;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--gold-light);
      margin-bottom: 25px;
    }
    .action-row {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center;
      margin-bottom: 20px;
    }
    .insta-btn {
      background: linear-gradient(135deg, rgba(225, 48, 108, 0.25), rgba(253, 29, 29, 0.25));
      border-color: rgba(225, 48, 108, 0.5);
    }
    .insta-btn:hover {
      border-color: #e1306c;
      box-shadow: 0 0 25px rgba(225, 48, 108, 0.5);
    }
    
    /* Copy Username Block */
    .copy-user-wrapper {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      padding: 6px 16px;
      border-radius: var(--radius-full);
      background: rgba(15, 15, 22, 0.7);
      border: 1px solid var(--border-gold);
      box-shadow: 0 10px 25px rgba(0,0,0,0.5);
    }
    .user-handle {
      font-size: 0.9rem;
      color: var(--gold-light);
      font-weight: 600;
      letter-spacing: 1px;
    }
    .btn-copy-small {
      background: linear-gradient(135deg, var(--pink-deep), var(--pink-neon));
      border: none;
      color: #fff;
      padding: 6px 14px;
      border-radius: var(--radius-full);
      font-size: 0.75rem;
      font-weight: 600;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 6px;
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }
    .btn-copy-small:active { transform: scale(0.92); }

    /* ==========================================================================
       DEVICE / CONNECTION INFO CARD & TOAST NOTIFICATION
       ========================================================================== */
    .info-toggle-btn {
      position: fixed;
      bottom: max(16px, env(safe-area-inset-bottom));
      left: max(16px, env(safe-area-inset-left));
      z-index: 150;
      background: rgba(10, 10, 14, 0.85);
      backdrop-filter: blur(15px);
      -webkit-backdrop-filter: blur(15px);
      border: 1px solid var(--border-glass);
      color: var(--text-dim);
      padding: 6px 14px;
      border-radius: var(--radius-full);
      font-size: 0.75rem;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 6px;
      transition: all 0.3s ease;
      opacity: 0;
      pointer-events: none;
    }
    .info-toggle-btn.visible {
      opacity: 0.85;
      pointer-events: auto;
    }
    .info-toggle-btn:hover {
      opacity: 1;
      border-color: var(--border-gold);
      color: #fff;
    }
    
    .info-card {
      position: fixed;
      bottom: max(55px, env(safe-area-inset-bottom));
      left: max(16px, env(safe-area-inset-left));
      z-index: 150;
      width: clamp(260px, 80vw, 320px);
      padding: 16px 20px;
      border-radius: var(--radius-md);
      background: var(--bg-glass);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      border: 1px solid var(--border-gold);
      box-shadow: var(--shadow-deep);
      opacity: 0;
      visibility: hidden;
      transform: translateY(10px) scale(0.95);
      transition: all 0.3s var(--ease-cinematic);
      font-size: 0.8rem;
      color: var(--text-muted);
    }
    .info-card.show {
      opacity: 1;
      visibility: visible;
      transform: translateY(0) scale(1);
    }
    .info-title {
      font-size: 0.85rem;
      color: var(--gold-light);
      margin-bottom: 10px;
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 1px;
      border-bottom: 1px solid rgba(255,255,255,0.08);
      padding-bottom: 4px;
    }
    .info-row {
      display: flex;
      justify-content: space-between;
      padding: 4px 0;
      border-bottom: 1px solid rgba(255,255,255,0.04);
    }
    .info-row:last-child { border-bottom: none; }
    .info-label { color: var(--text-dim); }
    .info-val { color: #ffffff; font-weight: 500; text-align: right; }

    /* Universal Toast Notification */
    .toast-notification {
      position: fixed;
      bottom: max(30px, env(safe-area-inset-bottom));
      left: 50%;
      transform: translateX(-50%) translateY(50px);
      background: var(--bg-glass);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      border: 1px solid var(--border-gold);
      color: var(--gold-light);
      padding: 10px 24px;
      border-radius: var(--radius-full);
      font-size: 0.85rem;
      letter-spacing: 1px;
      box-shadow: var(--glow-gold), var(--shadow-deep);
      opacity: 0;
      pointer-events: none;
      transition: all 0.4s var(--ease-cinematic);
      z-index: 2000;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .toast-notification.show {
      opacity: 1;
      transform: translateX(-50%) translateY(0);
    }
  </style>
</head>
<body class="lang-en">

  <canvas id="particleCanvas"></canvas>
  <div class="cinematic-overlay"></div>
  <div class="film-grain"></div>
  <div class="ambient-light-1"></div>
  <div class="ambient-light-2"></div>

  <!-- Header Controls -->
  <div class="top-controls">
    <div class="lang-switcher">
      <div class="lang-indicator" id="langIndicator"></div>
      <button class="lang-btn active" id="btnEN" onclick="setLanguage('en')">EN</button>
      <button class="lang-btn" id="btnAM" onclick="setLanguage('am')">አማ</button>
    </div>

    <div class="audio-control">
      <button class="audio-btn" id="audioToggleBtn" onclick="toggleAudio()" aria-label="Toggle Audio">
        <svg id="audioIcon" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <polygon points="11 5 6 9 2 9 2 15 6 15 11 19 11 5"></polygon>
          <path d="M19.07 4.93a10 10 0 0 1 0 14.14M15.54 8.46a5 5 0 0 1 0 7.07"></path>
        </svg>
      </button>
      <div class="audio-bars" id="audioBars">
        <div class="audio-bar"></div>
        <div class="audio-bar"></div>
        <div class="audio-bar"></div>
        <div class="audio-bar"></div>
      </div>
      <div class="music-toast" id="musicToast">Music On</div>
    </div>
  </div>

  <div id="app">

    <!-- SCREEN 0: PREMIUM PASSWORD SCREEN -->
    <section class="screen active" id="screen-password">
      <div class="pass-card glass-panel" id="passCard">
        <h1 class="pass-brand title-gold">BLEN</h1>
        <p class="pass-tagline" data-key="passTagline">PRIVATE EXPERIENCE</p>
        <p class="opening-subtext" style="font-size:0.9rem; margin-bottom:20px; animation:none; opacity:1; transform:none;" data-key="passSub">ለአንቺ ብቻ የተዘጋጀ</p>
        
        <div class="pass-input-wrap">
          <input type="password" id="passInput" class="pass-input" autocomplete="off" placeholder="Enter Password..." data-key-placeholder="passPlaceholder">
          <div class="pass-error-msg" id="passErrorMsg" data-key="passError">የይለፍ ቃሉ ትክክል አይደለም</div>
        </div>

        <button class="btn-luxury" style="width:100%; margin-top:8px;" onclick="validatePassword()">
          <span data-key="passBtn">Unlock Experience</span>
        </button>
      </div>
    </section>

    <!-- SCREEN 1: OPENING -->
    <section class="screen" id="screen-opening" onclick="nextScreen()">
      <div class="opening-content">
        <div class="spotlight-radial"></div>
        <p class="opening-subtext" data-key="openingSub">A private digital gift created exclusively for you.</p>
        <div class="tap-hint">
          <span data-key="tapToBegin">Tap Anywhere To Begin</span>
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
        </div>
      </div>
    </section>

    <!-- SCREEN 2: BLEN REVEAL -->
    <section class="screen" id="screen-reveal">
      <div class="name-container">
        <span class="letter">B</span>
        <span class="letter">L</span>
        <span class="letter">E</span>
        <span class="letter">N</span>
      </div>
      <p class="reveal-subtitle" data-key="revealSub">This experience was built for you</p>
      <p class="welcome-text" data-key="welcomeText">Every detail, every motion, and every word here was crafted to honor your presence.</p>
      <div class="reveal-btn-wrap" style="margin-top: 10px;">
        <button class="btn-luxury" onclick="nextScreen()">
          <span data-key="btnExplore">Explore Memories</span>
        </button>
      </div>
    </section>

    <!-- SCREEN 3: MEMORIES CAROUSEL -->
    <section class="screen" id="screen-memories">
      <div class="section-header">
        <h2 class="section-title title-gold" data-key="memoriesTitle">Captured Moments</h2>
        <p class="section-subtitle" data-key="memoriesSub">Swipe or click to relive our favorite highlights</p>
      </div>

      <div class="carousel-container-wrap">
        <button class="carousel-arrow prev" onclick="prevSlide()" aria-label="Previous Slide">&#10094;</button>
        <div class="carousel-viewport" id="carouselViewport">
          <div class="carousel-track" id="carouselTrack"></div>
        </div>
        <button class="carousel-arrow next" onclick="nextSlide()" aria-label="Next Slide">&#10095;</button>
      </div>

      <div class="carousel-info">
        <div class="carousel-counter" id="carouselCounter">01 / 05</div>
        <div class="carousel-nav-dots" id="carouselDots"></div>
        <p class="swipe-hint" data-key="swipeHint">Swipe left or right to navigate</p>
        <button class="btn-luxury" style="margin-top: 10px;" onclick="nextScreen()">
          <span data-key="btnContinue">Continue Journey</span>
        </button>
      </div>
    </section>

    <!-- SCREEN 4: TYPEWRITER LETTER -->
    <section class="screen" id="screen-letter">
      <div class="letter-card glass-panel">
        <div class="letter-body" id="letterBody"></div>
        <div class="letter-signature" id="letterSig">— Yisshak</div>
      </div>
      <button class="btn-luxury" style="margin-top: 25px;" onclick="nextScreen()">
        <span data-key="btnProceed">Proceed Further</span>
      </button>
    </section>

    <!-- SCREEN 5: COUNTDOWN -->
    <section class="screen" id="screen-countdown">
      <p class="section-subtitle" style="margin-bottom: 20px;" data-key="countdownText">Preparing your special reveal...</p>
      <div class="countdown-num" id="countdownNum">3</div>
    </section>

    <!-- SCREEN 6: 3D GIFT BOX -->
    <section class="screen" id="screen-gift">
      <h2 class="section-title title-gold" data-key="giftTitle">A Token For You</h2>
      <p class="section-subtitle" data-key="giftSub">Tap the luxury box to unwrap your gift</p>

      <div class="gift-stage" id="giftBox" onclick="openGift()">
        <div class="gift-cube">
          <div class="cube-face face-front"><div class="ribbon-v"></div></div>
          <div class="cube-face face-back"><div class="ribbon-v"></div></div>
          <div class="cube-face face-right"><div class="ribbon-h"></div></div>
          <div class="cube-face face-left"><div class="ribbon-h"></div></div>
          <div class="cube-face face-bottom"></div>
          
          <div class="gift-lid">
            <div class="lid-face lid-top"><div class="ribbon-v"></div><div class="ribbon-h"></div></div>
            <div class="lid-face lid-front"><div class="ribbon-v"></div></div>
            <div class="lid-face lid-left"></div>
            <div class="lid-face lid-right"></div>
            <div class="lid-face lid-back"><div class="ribbon-v"></div></div>
          </div>
          <div class="gift-internal-glow"></div>
        </div>
      </div>
    </section>

    <!-- SCREEN 7: FINAL REVEAL -->
    <section class="screen" id="screen-final">
      <div class="avatar-frame">
        <div class="avatar-img-wrap">
          <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&q=80&w=600" alt="Blen Portrait">
        </div>
      </div>
      <div class="reveal-msg" id="finalMsg">
        <span data-key="finalLine1">You shine brighter than any star.</span>
        <span data-key="finalLine2">Thank you for being such an extraordinary part of life.</span>
        <span class="final-highlight" data-key="finalLine3">Always cherished, forever special.</span>
      </div>
      <button class="btn-luxury" style="margin-top: 35px;" onclick="nextScreen()">
        <span data-key="btnFinish">Finish Experience</span>
      </button>
    </section>

    <!-- SCREEN 8: ENDING -->
    <section class="screen" id="screen-ending">
      <h2 class="ending-title title-gold" data-key="endingTitle">Thank You, Blen</h2>
      <p class="creator-tag" data-key="endingSub">Specially Designed By Yisshak</p>

      <div class="action-row">
        <button class="btn-luxury" onclick="restartExperience()">
          <span data-key="btnReplay">Replay Experience</span>
        </button>

        <!-- Instagram Direct Link Button -->
        <a href="https://instagram.com/lan_yisu" target="_blank" rel="noopener noreferrer" class="btn-luxury insta-btn">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect>
            <path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path>
            <line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line>
          </svg>
          <span data-key="instaBtn">Instagram</span>
        </a>
      </div>

      <!-- Copy Username Container -->
      <div class="copy-user-wrapper">
        <span class="user-handle">@lan_yisu</span>
        <button class="btn-copy-small" onclick="copyUsername('lan_yisu')">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <rect x="9" y="9" width="13" height="13" rx="2" ry="2"></rect>
            <path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"></path>
          </svg>
          <span data-key="copyBtn">Copy</span>
        </button>
      </div>
    </section>

  </div>

  <!-- Collapsible Device Connection Info Widget -->
  <button class="info-toggle-btn" id="infoToggleBtn" onclick="toggleInfoCard()">
    <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"></circle><line x1="12" y1="16" x2="12" y2="12"></line><line x1="12" y1="8" x2="12.01" y2="8"></line></svg>
    <span data-key="connBtn">Connection Info</span>
  </button>

  <div class="info-card" id="infoCard">
    <div class="info-title" data-key="connTitle">Device & Connection</div>
    <div class="info-row"><span class="info-label" data-key="infoDevice">Device</span><span class="info-val" id="infoDeviceVal">Android</span></div>
    <div class="info-row"><span class="info-label" data-key="infoBrowser">Browser</span><span class="info-val" id="infoBrowserVal">Chrome</span></div>
    <div class="info-row"><span class="info-label" data-key="infoRes">Resolution</span><span class="info-val" id="infoResVal">1080x2400</span></div>
    <div class="info-row"><span class="info-label" data-key="infoLang">Language</span><span class="info-val" id="infoLangVal">en-US</span></div>
    <div class="info-row"><span class="info-label" data-key="infoZone">Timezone</span><span class="info-val" id="infoZoneVal">Africa/Addis_Ababa</span></div>
    <div class="info-row"><span class="info-label" data-key="infoIp">IP Address</span><span class="info-val" id="infoIpVal">Loading...</span></div>
  </div>

  <!-- Lightbox Modal -->
  <div class="lightbox" id="lightbox">
    <button class="lightbox-close" onclick="closeLightbox()">&times;</button>
    <button class="lightbox-nav prev" onclick="lightboxNav(-1)">&#10094;</button>
    <div class="lightbox-content">
      <img class="lightbox-img" id="lightboxImg" src="" alt="Enlarged Memory">
      <div class="lightbox-caption" id="lightboxCaption"></div>
    </div>
    <button class="lightbox-nav next" onclick="lightboxNav(1)">&#10095;</button>
  </div>

  <!-- Universal Toast Notification -->
  <div class="toast-notification" id="toastNotification">
    <span id="toastMsg">Copied ✓</span>
  </div>

  <!-- Background Audio -->
  <audio id="bgAudio" loop preload="auto">
    <source src="https://cdn.pixabay.com/download/audio/2022/05/27/audio_1808fbf07a.mp3?filename=cinematic-time-lapse-115672.mp3" type="audio/mpeg">
  </audio>

  <script>
    /* ==========================================================================
       DATA & DICTIONARY
       ========================================================================== */
    const translations = {
      en: {
        passTagline: "PRIVATE EXPERIENCE",
        passSub: "Created exclusively for you",
        passPlaceholder: "Enter Password...",
        passBtn: "Unlock Experience",
        passError: "Incorrect password. Try again!",
        openingSub: "A private digital gift created exclusively for you.",
        tapToBegin: "Tap Anywhere To Begin",
        revealSub: "This experience was built for you",
        welcomeText: "Every detail, every motion, and every word here was crafted to honor your presence.",
        btnExplore: "Explore Memories",
        memoriesTitle: "Captured Moments",
        memoriesSub: "Swipe or click to relive our favorite highlights",
        swipeHint: "Swipe left or right to navigate",
        btnContinue: "Continue Journey",
        btnProceed: "Proceed Further",
        countdownText: "Preparing your special reveal...",
        giftTitle: "A Token For You",
        giftSub: "Tap the luxury box to unwrap your gift",
        finalLine1: "You shine brighter than any star.",
        finalLine2: "Thank you for being such an extraordinary part of life.",
        finalLine3: "Always cherished, forever special.",
        btnFinish: "Finish Experience",
        endingTitle: "Thank You, Blen",
        endingSub: "Specially Designed By Yisshak",
        btnReplay: "Replay Experience",
        instaBtn: "Instagram",
        copyBtn: "Copy",
        copiedToast: "Copied ✓",
        connBtn: "Connection Info",
        connTitle: "Device & Connection",
        infoDevice: "Device",
        infoBrowser: "Browser",
        infoRes: "Resolution",
        infoLang: "Language",
        infoZone: "Timezone",
        infoIp: "IP Address",
        letterText: "Dear Blen,\n\nWords often fall short when trying to express how much you mean to those around you. You bring warmth, brilliance, and an irreplaceable light into every moment.\n\nThis small experience is simply a mirror reflecting back a fraction of the beauty and joy you share so effortlessly with the world.\n\nMay your journey ahead be filled with endless happiness, boundless peace, and profound love."
      },
      am: {
        passTagline: "የግል ገጠመኝ",
        passSub: "ለአንቺ ብቻ የተዘጋጀ",
        passPlaceholder: "የይለፍ ቃል ያስገቡ...",
        passBtn: "ልምዱን ይክፈቱ",
        passError: "የይለፍ ቃሉ ትክክል አይደለም",
        openingSub: "ለእርስዎ ብቻ በልዩ ሁኔታ የተዘጋጀ ዲጂታል ስጦታ።",
        tapToBegin: "ለመጀመር የትም ቦታ ይጫኑ",
        revealSub: "ይህ ገጠመኝ ለእርስዎ የተሰራ ነው",
        welcomeText: "እያንዳንዱ ዝርዝር፣ እንቅስቃሴ እና ቃል የእርስዎን መኖር ለማክበር በጥንቃቄ ተዘጋጅቷል።",
        btnExplore: "ትዝታዎችን ይመልከቱ",
        memoriesTitle: "የተያዙ ትዝታዎች",
        memoriesSub: "ተወዳጅ ጊዜያትን ለማስታወስ ያንሸራቱ ወይም ይጫኑ",
        swipeHint: "ለማሰስ ወደ ግራ ወይም ቀኝ ያንሸራቱ",
        btnContinue: "ጉዞውን ይቀጥሉ",
        btnProceed: "ወደፊት ይቀጥሉ",
        countdownText: "ልዩ ስጦታዎን በማዘጋጀት ላይ...",
        giftTitle: "የእርስዎ ስጦታ",
        giftSub: "ስጦታዎን ለመክፈት ሳጥኑን ይጫኑ",
        finalLine1: "ከማንኛውም ኮከብ በላይ ታበራለህ።",
        finalLine2: "በሕይወቴ ውስጥ የነበረህ ድንቅ ቦታ በጣም አመሰግናለሁ።",
        finalLine3: "ሁልጊዜ የምትወደድ፣ ለዘላለም ልዩ።",
        btnFinish: "ልምዱን ያጠናቅቁ",
        endingTitle: "እናመሰግናለን ብሌን",
        endingSub: "በይስሐቅ በልዩ ሁኔታ የተዘጋጀ",
        btnReplay: "እንደገና ያስጀምሩ",
        instaBtn: "ኢንስታግራም",
        copyBtn: "ኮፒ",
        copiedToast: "ተኮፒ አድርጓል ✓",
        connBtn: "የግንኙነት መረጃ",
        connTitle: "የመሣሪያ እና ግንኙነት",
        infoDevice: "መሣሪያ",
        infoBrowser: "ብራውዘር",
        infoRes: "ሪዞሉሽን",
        infoLang: "ቋንቋ",
        infoZone: "ታይም ዞን",
        infoIp: "አይፒ አድራሻ",
        letterText: "ውድ ብሌን፣\n\nበዙሪያህ ላሉት ሰዎች ምን ያህል ትርጉም እንዳለህ ለመግለጽ ቃላት ብዙውን ጊዜ ያጥራሉ። ለእያንዳንዱ ቅጽበት ሙቀት፣ ብሩህነት እና የማይተካ ብርሃን ታመጣለህ።\n\nይህ ትንሽ ዲጂታል ስጦታ ለዓለም የምታካፍለውን ውበት እና ደስታ የሚያንፀባርቅ መስታወት ነው።\n\nወደፊት የሚጠብቅህ ጉዞ በደስታ፣ በሰላም እና በፍቅር የተሞላ ይሁን።"
      }
    };

    const memories = [
      { img: "https://images.unsplash.com/photo-1517841905240-472988babdf9?auto=format&fit=crop&q=80&w=800", caption: "Joyful Moments" },
      { img: "https://images.unsplash.com/photo-1524504388940-b1c1722653e1?auto=format&fit=crop&q=80&w=800", caption: "Elegance & Grace" },
      { img: "https://images.unsplash.com/photo-1494790108377-be9c29b29330?auto=format&fit=crop&q=80&w=800", caption: "Radiant Smiles" },
      { img: "https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&q=80&w=800", caption: "Timeless Beauty" },
      { img: "https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?auto=format&fit=crop&q=80&w=800", caption: "Unforgettable Memories" }
    ];

    /* ==========================================================================
       GLOBAL STATE MANAGEMENT
       ========================================================================== */
    let currentLang = 'en';
    let currentScreenIndex = 0;
    let isAudioPlaying = false;
    let activeSlideIndex = 0;
    let isTyping = false;
    let typewriterTimeout;
    let particleParticlesList = [];

    const screens = [
      'screen-password',
      'screen-opening',
      'screen-reveal',
      'screen-memories',
      'screen-letter',
      'screen-countdown',
      'screen-gift',
      'screen-final',
      'screen-ending'
    ];

    /* ==========================================================================
       INITIALIZATION & PARTICLES
       ========================================================================== */
    window.addEventListener('DOMContentLoaded', () => {
      initParticles();
      buildCarousel();
      updateLanguageUI();
      detectConnectionInfo();

      // Enter key listener for password field
      const passInput = document.getElementById('passInput');
      if (passInput) {
        passInput.addEventListener('keydown', (e) => {
          if (e.key === 'Enter') {
            validatePassword();
          }
        });
      }
    });

    // Particle Canvas Animation
    function initParticles() {
      const canvas = document.getElementById('particleCanvas');
      const ctx = canvas.getContext('2d');
      let width = canvas.width = window.innerWidth;
      let height = canvas.height = window.innerHeight;

      window.addEventListener('resize', () => {
        width = canvas.width = window.innerWidth;
        height = canvas.height = window.innerHeight;
      });

      particleParticlesList = Array.from({ length: 45 }, () => ({
        x: Math.random() * width,
        y: Math.random() * height,
        size: Math.random() * 2.5 + 0.5,
        speedX: (Math.random() - 0.5) * 0.3,
        speedY: -Math.random() * 0.5 - 0.2,
        opacity: Math.random() * 0.6 + 0.2,
        color: Math.random() > 0.5 ? '#ff4fa3' : '#d4af37'
      }));

      function render() {
        ctx.clearRect(0, 0, width, height);
        particleParticlesList.forEach((p) => {
          p.x += p.speedX;
          p.y += p.speedY;
          if (p.y < 0) {
            p.y = height;
            p.x = Math.random() * width;
          }
          if (p.x < 0 || p.x > width) p.x = Math.random() * width;

          ctx.beginPath();
          ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
          ctx.fillStyle = p.color;
          ctx.globalAlpha = p.opacity;
          ctx.shadowBlur = 10;
          ctx.shadowColor = p.color;
          ctx.fill();
        });
        requestAnimationFrame(render);
      }
      render();
    }

    // Particle Burst Effect on Password Unlock
    function triggerParticleBurst() {
      const canvas = document.getElementById('particleCanvas');
      const width = canvas.width;
      const height = canvas.height;

      for (let i = 0; i < 60; i++) {
        const angle = Math.random() * Math.PI * 2;
        const speed = Math.random() * 8 + 3;
        particleParticlesList.push({
          x: width / 2,
          y: height / 2,
          size: Math.random() * 4 + 1.5,
          speedX: Math.cos(angle) * speed,
          speedY: Math.sin(angle) * speed,
          opacity: 1,
          color: Math.random() > 0.5 ? '#ff4fa3' : '#d4af37'
        });
      }
    }

    /* ==========================================================================
       PASSWORD VALIDATION & UNLOCK
       ========================================================================== */
    function validatePassword() {
      const input = document.getElementById('passInput');
      const card = document.getElementById('passCard');
      const errorMsg = document.getElementById('passErrorMsg');
      const val = input.value.trim().toLowerCase();

      if (val === 'my besti') {
        errorMsg.classList.remove('show');
        triggerParticleBurst();
        
        // Attempt audio playback on user gesture unlock
        const audio = document.getElementById('bgAudio');
        audio.play().then(() => {
          isAudioPlaying = true;
          document.getElementById('audioBars').classList.add('playing');
        }).catch(() => {});

        // Show connection info button after unlock
        document.getElementById('infoToggleBtn').classList.add('visible');

        setTimeout(() => {
          nextScreen();
        }, 400);
      } else {
        card.classList.remove('shake');
        void card.offsetWidth; // Trigger reflow for shake restart
        card.classList.add('shake');
        errorMsg.classList.add('show');
        input.value = '';
        input.focus();
      }
    }

    /* ==========================================================================
       SCREEN NAVIGATION
       ========================================================================== */
    function showScreen(index) {
      if (index < 0 || index >= screens.length) return;
      
      const currentScreen = document.getElementById(screens[currentScreenIndex]);
      const targetScreen = document.getElementById(screens[index]);

      currentScreen.classList.remove('active');
      currentScreenIndex = index;

      setTimeout(() => {
        targetScreen.classList.add('active');
        onScreenActivate(screens[index]);
      }, 300);
    }

    function nextScreen() {
      showScreen(currentScreenIndex + 1);
    }

    function restartExperience() {
      const giftBox = document.getElementById('giftBox');
      if (giftBox) giftBox.classList.remove('open');
      showScreen(1); // Jump to opening screen directly
    }

    function onScreenActivate(screenId) {
      if (screenId === 'screen-letter') {
        startTypewriter();
      } else if (screenId === 'screen-countdown') {
        startCountdown();
      } else if (screenId === 'screen-final') {
        animateFinalMessage();
      }
    }

    /* ==========================================================================
       LANGUAGE SWITCHER
       ========================================================================== */
    function setLanguage(lang) {
      currentLang = lang;
      document.body.className = `lang-${lang}`;
      
      const indicator = document.getElementById('langIndicator');
      const btnEN = document.getElementById('btnEN');
      const btnAM = document.getElementById('btnAM');

      if (lang === 'am') {
        indicator.style.transform = 'translateX(100%)';
        btnAM.classList.add('active');
        btnEN.classList.remove('active');
      } else {
        indicator.style.transform = 'translateX(0%)';
        btnEN.classList.add('active');
        btnAM.classList.remove('active');
      }

      updateLanguageUI();

      if (screens[currentScreenIndex] === 'screen-letter') {
        startTypewriter();
      }
    }

    function updateLanguageUI() {
      const langData = translations[currentLang];
      
      document.querySelectorAll('[data-key]').forEach(el => {
        const key = el.getAttribute('data-key');
        if (langData[key]) {
          el.textContent = langData[key];
        }
      });

      document.querySelectorAll('[data-key-placeholder]').forEach(el => {
        const key = el.getAttribute('data-key-placeholder');
        if (langData[key]) {
          el.placeholder = langData[key];
        }
      });
    }

    /* ==========================================================================
       AUDIO CONTROLLER
       ========================================================================== */
    function toggleAudio() {
      const audio = document.getElementById('bgAudio');
      const audioBars = document.getElementById('audioBars');
      const toast = document.getElementById('musicToast');

      if (isAudioPlaying) {
        audio.pause();
        audioBars.classList.remove('playing');
        toast.textContent = "Music Off";
      } else {
        audio.play().catch(() => {});
        audioBars.classList.add('playing');
        toast.textContent = "Music On";
      }
      isAudioPlaying = !isAudioPlaying;

      toast.classList.add('show');
      setTimeout(() => toast.classList.remove('show'), 2000);
    }

    /* ==========================================================================
       3D CAROUSEL & TOUCH SYSTEM
       ========================================================================== */
    function buildCarousel() {
      const track = document.getElementById('carouselTrack');
      const dotsContainer = document.getElementById('carouselDots');
      track.innerHTML = '';
      dotsContainer.innerHTML = '';

      memories.forEach((item, idx) => {
        const card = document.createElement('div');
        card.className = 'carousel-card';
        card.innerHTML = `
          <img src="${item.img}" alt="${item.caption}">
          <div class="card-caption">${item.caption}</div>
        `;
        card.onclick = () => {
          if (idx === activeSlideIndex) {
            openLightbox(idx);
          } else {
            activeSlideIndex = idx;
            updateCarousel();
          }
        };
        track.appendChild(card);

        const dot = document.createElement('div');
        dot.className = `dot ${idx === 0 ? 'active' : ''}`;
        dot.onclick = () => {
          activeSlideIndex = idx;
          updateCarousel();
        };
        dotsContainer.appendChild(dot);
      });

      updateCarousel();
      initSwipeGesture();
    }

    function updateCarousel() {
      const cards = document.querySelectorAll('.carousel-card');
      const dots = document.querySelectorAll('.dot');
      const total = memories.length;

      cards.forEach((card, idx) => {
        const offset = idx - activeSlideIndex;
        const absOffset = Math.abs(offset);

        if (offset === 0) {
          card.style.transform = `translateX(0px) translateZ(150px) rotateY(0deg)`;
          card.style.opacity = '1';
          card.style.filter = 'blur(0px)';
          card.style.zIndex = '10';
          card.classList.add('active-card');
        } else if (absOffset === 1) {
          const dir = offset > 0 ? 1 : -1;
          card.style.transform = `translateX(${dir * 180}px) translateZ(0px) rotateY(${-dir * 25}deg)`;
          card.style.opacity = '0.7';
          card.style.filter = 'blur(2px)';
          card.style.zIndex = '5';
          card.classList.remove('active-card');
        } else {
          const dir = offset > 0 ? 1 : -1;
          card.style.transform = `translateX(${dir * 280}px) translateZ(-150px) rotateY(${-dir * 40}deg)`;
          card.style.opacity = '0.2';
          card.style.filter = 'blur(6px)';
          card.style.zIndex = '1';
          card.classList.remove('active-card');
        }
      });

      dots.forEach((dot, idx) => {
        dot.className = `dot ${idx === activeSlideIndex ? 'active' : ''}`;
      });

      document.getElementById('carouselCounter').textContent = `0${activeSlideIndex + 1} / 0${total}`;
    }

    function nextSlide() {
      activeSlideIndex = (activeSlideIndex + 1) % memories.length;
      updateCarousel();
    }

    function prevSlide() {
      activeSlideIndex = (activeSlideIndex - 1 + memories.length) % memories.length;
      updateCarousel();
    }

    function initSwipeGesture() {
      const viewport = document.getElementById('carouselViewport');
      let startX = 0;
      let dist = 0;

      viewport.addEventListener('touchstart', (e) => {
        startX = e.touches[0].clientX;
      }, { passive: true });

      viewport.addEventListener('touchend', (e) => {
        dist = e.changedTouches[0].clientX - startX;
        if (dist < -40) nextSlide();
        if (dist > 40) prevSlide();
      }, { passive: true });
    }

    /* ==========================================================================
       LIGHTBOX SYSTEM
       ========================================================================== */
    let lightboxIndex = 0;

    function openLightbox(idx) {
      lightboxIndex = idx;
      const lightbox = document.getElementById('lightbox');
      const img = document.getElementById('lightboxImg');
      const caption = document.getElementById('lightboxCaption');

      img.src = memories[idx].img;
      caption.textContent = memories[idx].caption;
      lightbox.classList.add('active');
    }

    function closeLightbox() {
      document.getElementById('lightbox').classList.remove('active');
    }

    function lightboxNav(dir) {
      lightboxIndex = (lightboxIndex + dir + memories.length) % memories.length;
      openLightbox(lightboxIndex);
    }

    /* ==========================================================================
       TYPEWRITER LETTER
       ========================================================================== */
    function startTypewriter() {
      clearTimeout(typewriterTimeout);
      const letterBody = document.getElementById('letterBody');
      const sig = document.getElementById('letterSig');
      const text = translations[currentLang].letterText;
      
      letterBody.innerHTML = '';
      sig.classList.remove('visible');

      let idx = 0;
      isTyping = true;

      const cursor = document.createElement('span');
      cursor.className = 'typing-cursor';

      function type() {
        if (idx < text.length) {
          letterBody.textContent = text.slice(0, idx + 1);
          letterBody.appendChild(cursor);
          idx++;
          typewriterTimeout = setTimeout(type, 35);
        } else {
          isTyping = false;
          if (cursor.parentNode) cursor.parentNode.removeChild(cursor);
          sig.classList.add('visible');
        }
      }
      type();
    }

    /* ==========================================================================
       COUNTDOWN SYSTEM
       ========================================================================== */
    function startCountdown() {
      const numDisplay = document.getElementById('countdownNum');
      let count = 3;

      function updateNum() {
        numDisplay.textContent = count;
        numDisplay.classList.remove('num-animate');
        void numDisplay.offsetWidth; // Trigger reflow
        numDisplay.classList.add('num-animate');

        if (count > 1) {
          count--;
          setTimeout(updateNum, 1000);
        } else {
          setTimeout(() => nextScreen(), 1000);
        }
      }
      updateNum();
    }

    /* ==========================================================================
       3D GIFT BOX & FINAL REVEAL ANIMATIONS
       ========================================================================== */
    function openGift() {
      const giftBox = document.getElementById('giftBox');
      if (giftBox.classList.contains('open')) return;

      giftBox.classList.add('open');
      setTimeout(() => {
        nextScreen();
      }, 1400);
    }

    function animateFinalMessage() {
      const spans = document.querySelectorAll('#finalMsg span');
      spans.forEach((span, idx) => {
        span.classList.remove('visible');
        setTimeout(() => {
          span.classList.add('visible');
        }, idx * 800 + 400);
      });
    }

    /* ==========================================================================
       COPY TO CLIPBOARD & TOAST SYSTEM
       ========================================================================== */
    function copyUsername(text) {
      if (navigator.clipboard && navigator.clipboard.writeText) {
        navigator.clipboard.writeText(text).then(() => {
          showToast(translations[currentLang].copiedToast || "Copied ✓");
        }).catch(() => {
          fallbackCopy(text);
        });
      } else {
        fallbackCopy(text);
      }
    }

    function fallbackCopy(text) {
      const textArea = document.createElement("textarea");
      textArea.value = text;
      textArea.style.position = "fixed";
      textArea.style.opacity = "0";
      document.body.appendChild(textArea);
      textArea.focus();
      textArea.select();
      try {
        document.execCommand('copy');
        showToast(translations[currentLang].copiedToast || "Copied ✓");
      } catch (err) {
        showToast("Copied ✓");
      }
      document.body.removeChild(textArea);
    }

    function showToast(message) {
      const toast = document.getElementById('toastNotification');
      const msgEl = document.getElementById('toastMsg');
      msgEl.textContent = message;
      toast.classList.add('show');
      setTimeout(() => toast.classList.remove('show'), 2500);
    }

    /* ==========================================================================
       DEVICE / CONNECTION INFO DETECTOR
       ========================================================================== */
    function toggleInfoCard() {
      const card = document.getElementById('infoCard');
      card.classList.toggle('show');
    }

    function detectConnectionInfo() {
      const ua = navigator.userAgent;
      
      // 1. Device Type
      let device = "Desktop";
      if (/Android/i.test(ua)) device = "Android";
      else if (/iPhone|iPad|iPod/i.test(ua)) device = "iPhone / iPad";
      document.getElementById('infoDeviceVal').textContent = device;

      // 2. Browser Name
      let browser = "Browser";
      if (ua.includes("Chrome") && !ua.includes("Edg") && !ua.includes("OPR")) browser = "Chrome";
      else if (ua.includes("Safari") && !ua.includes("Chrome")) browser = "Safari";
      else if (ua.includes("Firefox")) browser = "Firefox";
      else if (ua.includes("Edg")) browser = "Edge";
      else if (ua.includes("OPR") || ua.includes("Opera")) browser = "Opera";
      document.getElementById('infoBrowserVal').textContent = browser;

      // 3. Screen Resolution
      document.getElementById('infoResVal').textContent = `${window.screen.width} x ${window.screen.height}`;

      // 4. Language
      document.getElementById('infoLangVal').textContent = navigator.language || "en-US";

      // 5. Time Zone
      try {
        document.getElementById('infoZoneVal').textContent = Intl.DateTimeFormat().resolvedOptions().timeZone || "Unknown";
      } catch (e) {
        document.getElementById('infoZoneVal').textContent = "Unknown";
      }

      // 6. Public IP Fetch via HTTPS API
      fetch('https://api.ipify.org?format=json')
        .then(res => res.json())
        .then(data => {
          if (data && data.ip) {
            document.getElementById('infoIpVal').textContent = data.ip;
          } else {
            document.getElementById('infoIpVal').textContent = "Unavailable";
          }
        })
        .catch(() => {
          document.getElementById('infoIpVal').textContent = "Protected";
        });
    }
  </script>
</body>
</html>
