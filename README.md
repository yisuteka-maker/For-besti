<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
  <title>Special VIP Gift | BLEN</title>

  <!-- PWA Meta Tags -->
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
       1. CORE DESIGN SYSTEM & CSS VARIABLES
       ========================================================================== */
    :root {
      --bg-dark: #050505;
      --bg-surface: #0b0b0b;
      --bg-glass: rgba(18, 18, 22, 0.65);
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
      --shadow-deep: 0 20px 50px rgba(0, 0, 0, 0.8);

      --ease-cinematic: cubic-bezier(0.16, 1, 0.3, 1);
      --ease-bounce: cubic-bezier(0.34, 1.56, 0.64, 1);
    }

    /* Reset & Base Setup */
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

    /* Vignette & Ambient Glow */
    .cinematic-vignette {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 2;
      pointer-events: none;
      background: radial-gradient(circle at center, transparent 40%, rgba(5, 5, 5, 0.85) 100%);
      box-shadow: inset 0 0 100px rgba(0,0,0,0.9);
    }

    /* Floating Ambient Lights */
    .ambient-light-1, .ambient-light-2 {
      position: fixed;
      border-radius: 50%;
      filter: blur(100px);
      pointer-events: none;
      z-index: 1;
      opacity: 0.25;
      animation: floatLight 18s ease-in-out infinite alternate;
    }
    .ambient-light-1 {
      width: 40vw; height: 40vw;
      background: var(--pink-deep);
      top: -10vw; left: -10vw;
    }
    .ambient-light-2 {
      width: 45vw; height: 45vw;
      background: var(--gold-luxury);
      bottom: -15vw; right: -15vw;
      animation-delay: -9s;
    }

    @keyframes floatLight {
      0% { transform: translate(0, 0) scale(1); }
      50% { transform: translate(8%, 12%) scale(1.15); }
      100% { transform: translate(-5%, -8%) scale(0.9); }
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
      padding: 0 20px;
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

    .lang-switcher {
      display: flex;
      padding: 4px;
      border-radius: var(--radius-full);
      background: rgba(10, 10, 14, 0.7);
      border: 1px solid var(--border-glass);
    }
    .lang-btn {
      background: transparent;
      border: none;
      color: var(--text-muted);
      padding: 6px 14px;
      font-size: 0.8rem;
      font-weight: 600;
      border-radius: var(--radius-full);
      cursor: pointer;
      transition: all 0.3s var(--ease-cinematic);
    }
    .lang-btn.active {
      background: linear-gradient(135deg, var(--pink-deep), var(--pink-neon));
      color: #fff;
      box-shadow: 0 0 12px rgba(255, 79, 163, 0.4);
    }

    /* Audio Widget */
    .audio-control {
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 6px 14px;
      border-radius: var(--radius-full);
      background: rgba(10, 10, 14, 0.7);
      border: 1px solid var(--border-glass);
    }
    .audio-btn {
      background: transparent;
      border: none;
      color: var(--gold-light);
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      width: 28px;
      height: 28px;
      border-radius: 50%;
      transition: transform 0.2s ease;
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
      padding: 30px 20px;
      opacity: 0;
      visibility: hidden;
      pointer-events: none;
      transition: opacity 1.2s var(--ease-cinematic), transform 1.2s var(--ease-cinematic), filter 1.2s ease;
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
    .opening-subtext {
      font-size: 1.15rem;
      letter-spacing: 2px;
      color: var(--text-muted);
      margin-bottom: 24px;
      font-weight: 300;
      opacity: 0;
      transform: translateY(15px);
      animation: fadeInSmooth 2s var(--ease-cinematic) 0.5s forwards;
    }
    .tap-hint {
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
      gap: 12px;
      margin-bottom: 20px;
      justify-content: center;
    }
    .letter {
      font-family: var(--font-display);
      font-size: clamp(3.2rem, 12vw, 6.5rem);
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

    @keyframes letterReveal {
      to {
        opacity: 1;
        filter: blur(0px);
        transform: scale(1) translateY(0);
      }
    }

    .welcome-text {
      max-width: 480px;
      font-size: clamp(1rem, 3.5vw, 1.25rem);
      color: var(--text-muted);
      margin-bottom: 35px;
      opacity: 0;
      transform: translateY(15px);
    }
    .screen.active .welcome-text {
      animation: fadeInSmooth 1.2s ease 1.3s forwards;
    }
    .screen.active .reveal-btn-wrap {
      opacity: 0;
      animation: fadeInSmooth 1s ease 1.8s forwards;
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
      padding: clamp(60px, 10vh, 90px) 0 clamp(20px, 4vh, 40px) 0;
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

    .carousel-viewport {
      width: 100%;
      height: 52vh;
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
      width: clamp(230px, 62vw, 320px);
      height: clamp(320px, 42vh, 440px);
      border-radius: var(--radius-md);
      overflow: hidden;
      background: var(--bg-surface);
      border: 1px solid var(--border-glass);
      box-shadow: 0 20px 40px rgba(0,0,0,0.8);
      transition: transform 0.6s var(--ease-cinematic), filter 0.6s ease, opacity 0.6s ease, border-color 0.4s ease;
      cursor: pointer;
      will-change: transform, filter;
    }
    .carousel-card img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      pointer-events: none;
      transition: transform 0.8s ease;
    }
    .carousel-card:hover img {
      transform: scale(1.06);
    }
    .carousel-card .card-caption {
      position: absolute;
      bottom: 0; left: 0; width: 100%;
      padding: 20px 16px 14px 16px;
      background: linear-gradient(0deg, rgba(5,5,5,0.95) 0%, rgba(5,5,5,0.4) 70%, transparent 100%);
      font-size: 0.85rem;
      color: #fff;
      text-align: center;
      letter-spacing: 0.5px;
    }

    .carousel-nav-dots {
      display: flex;
      gap: 10px;
      justify-content: center;
      align-items: center;
      z-index: 5;
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

    /* Lightbox */
    .lightbox {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(5, 5, 8, 0.95);
      backdrop-filter: blur(25px);
      z-index: 1000;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.4s ease;
      padding: 20px;
    }
    .lightbox.active {
      opacity: 1;
      pointer-events: auto;
    }
    .lightbox-img {
      max-width: 92%;
      max-height: 75vh;
      border-radius: var(--radius-md);
      box-shadow: 0 25px 60px rgba(0,0,0,0.9);
      border: 1px solid var(--border-glass);
      transform: scale(0.9);
      transition: transform 0.4s var(--ease-cinematic);
    }
    .lightbox.active .lightbox-img {
      transform: scale(1);
    }
    .lightbox-close {
      position: absolute;
      top: clamp(20px, 4vh, 40px);
      right: 25px;
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
    }

    /* ==========================================================================
       SCREEN 4 — TYPEWRITER LETTER
       ========================================================================== */
    #screen-letter {
      width: 100%;
      max-width: 640px;
    }
    .letter-card {
      width: 100%;
      padding: clamp(24px, 5vw, 40px);
      border: 1px solid var(--border-gold);
      position: relative;
      overflow: hidden;
      background: linear-gradient(165deg, rgba(20, 20, 25, 0.75), rgba(10, 10, 12, 0.85));
    }
    .letter-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; width: 100%; height: 3px;
      background: linear-gradient(90deg, var(--gold-luxury), var(--pink-neon), var(--gold-luxury));
    }
    .letter-body {
      min-height: 200px;
      font-size: clamp(0.95rem, 3.2vw, 1.1rem);
      line-height: 1.85;
      color: rgba(255, 255, 255, 0.9);
      white-space: pre-wrap;
      font-weight: 300;
    }
    .lang-am .letter-body {
      font-family: var(--font-ethiopic);
      line-height: 2.1;
      font-size: clamp(1rem, 3.4vw, 1.15rem);
    }
    .typing-cursor {
      display: inline-block;
      width: 2px;
      height: 1.2em;
      background: var(--pink-neon);
      margin-left: 3px;
      vertical-align: middle;
      animation: blink 0.8s infinite;
    }
    @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }

    /* ==========================================================================
       SCREEN 5 — COUNTDOWN
       ========================================================================== */
    #screen-countdown { text-align: center; }
    .countdown-num {
      font-family: var(--font-display);
      font-size: clamp(6rem, 25vw, 12rem);
      font-weight: 900;
      line-height: 1;
      background: linear-gradient(135deg, var(--gold-light), var(--pink-neon));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      filter: drop-shadow(0 0 40px rgba(255,79,163,0.5));
      animation: countPulse 0.9s cubic-bezier(0.11, 0, 0.5, 0) infinite alternate;
    }
    @keyframes countPulse {
      0% { transform: scale(0.85); opacity: 0.3; filter: blur(10px); }
      100% { transform: scale(1.1); opacity: 1; filter: blur(0px); }
    }

    /* ==========================================================================
       SCREEN 6 — 3D GIFT BOX
       ========================================================================== */
    #screen-gift {
      perspective: 1200px;
      text-align: center;
    }
    .gift-stage {
      width: 220px;
      height: 220px;
      position: relative;
      transform-style: preserve-3d;
      margin: 40px auto 50px auto;
      cursor: pointer;
      animation: floatGift 5s ease-in-out infinite alternate;
    }
    @keyframes floatGift {
      0% { transform: translateY(0) rotateX(12deg) rotateY(-15deg); }
      100% { transform: translateY(-18px) rotateX(18deg) rotateY(15deg); }
    }

    .gift-cube {
      width: 100%; height: 100%;
      position: absolute;
      transform-style: preserve-3d;
      transition: transform 0.5s ease;
    }
    .cube-face {
      position: absolute;
      width: 220px; height: 220px;
      background: linear-gradient(135deg, #18121a, #0d0810);
      border: 1px solid rgba(212, 175, 55, 0.3);
      box-shadow: inset 0 0 30px rgba(255, 79, 163, 0.15);
    }
    .face-front  { transform: rotateY(  0deg) translateZ(110px); }
    .face-back   { transform: rotateY(180deg) translateZ(110px); }
    .face-right  { transform: rotateY( 90deg) translateZ(110px); }
    .face-left   { transform: rotateY(-90deg) translateZ(110px); }
    .face-bottom { transform: rotateX(-90deg) translateZ(110px); box-shadow: 0 40px 60px #000; }
    
    /* Box Lid */
    .gift-lid {
      position: absolute;
      width: 230px; height: 50px;
      top: -5px; left: -5px;
      transform-style: preserve-3d;
      transform-origin: back;
      transition: transform 1.2s var(--ease-cinematic);
    }
    .lid-face {
      position: absolute;
      background: linear-gradient(135deg, #221626, #120a16);
      border: 1px solid rgba(212, 175, 55, 0.4);
    }
    .lid-top    { width: 230px; height: 230px; transform: rotateX(90deg) translateZ(25px); }
    .lid-front  { width: 230px; height: 50px;  transform: translateZ(115px); }
    .lid-left   { width: 230px; height: 50px;  transform: rotateY(-90deg) translateZ(115px); }
    .lid-right  { width: 230px; height: 50px;  transform: rotateY(90deg) translateZ(115px); }
    .lid-back   { width: 230px; height: 50px;  transform: rotateY(180deg) translateZ(115px); }

    /* Ribbons */
    .ribbon-v, .ribbon-h {
      position: absolute;
      background: linear-gradient(90deg, var(--gold-luxury), var(--gold-light), var(--gold-luxury));
      box-shadow: 0 0 10px rgba(212, 175, 55, 0.5);
    }
    .ribbon-v { width: 30px; height: 100%; left: 95px; top: 0; }
    .ribbon-h { width: 100%; height: 30px; top: 95px; left: 0; }

    /* Open State Animations */
    .gift-stage.open .gift-lid {
      transform: translateY(-120px) rotateX(-110deg) rotateY(15deg);
    }
    .gift-stage.open .gift-cube {
      animation: explodeLight 1.5s forwards 0.2s;
    }

    /* ==========================================================================
       SCREEN 7 — FINAL REVEAL
       ========================================================================== */
    #screen-final { text-align: center; }
    .avatar-frame {
      width: clamp(140px, 35vw, 190px);
      height: clamp(140px, 35vw, 190px);
      border-radius: 50%;
      padding: 6px;
      background: linear-gradient(135deg, var(--gold-luxury), var(--pink-neon));
      box-shadow: var(--glow-pink), var(--glow-gold);
      margin-bottom: 30px;
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
      100% { transform: translateY(-12px) scale(1.03); }
    }

    .reveal-msg {
      max-width: 520px;
      font-size: clamp(1.1rem, 3.8vw, 1.45rem);
      line-height: 1.8;
      font-weight: 300;
      color: #fff;
    }
    .reveal-msg span {
      display: block;
      opacity: 0;
      transform: translateY(15px);
      transition: all 0.8s var(--ease-cinematic);
    }
    .reveal-msg span.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* ==========================================================================
       SCREEN 8 — ENDING
       ========================================================================== */
    #screen-ending { text-align: center; }
    .ending-title {
      font-size: clamp(1.8rem, 6vw, 3rem);
      margin-bottom: 12px;
    }
    .creator-tag {
      font-size: 1rem;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--gold-light);
      margin-bottom: 30px;
      opacity: 0.8;
    }
    .heart-icon {
      font-size: 3.5rem;
      display: inline-block;
      color: var(--pink-neon);
      filter: drop-shadow(0 0 20px var(--pink-neon));
      animation: heartBeat 1.6s ease-in-out infinite;
    }
    @keyframes heartBeat {
      0%, 100% { transform: scale(1); }
      15% { transform: scale(1.25); }
      30% { transform: scale(1); }
      45% { transform: scale(1.15); }
    }

    /* Media Queries for Small Mobile Devices */
    @media (max-width: 430px) {
      .top-controls { padding: 0 12px; }
      .btn-luxury { padding: 14px 28px; font-size: 0.85rem; }
      .letter-card { padding: 20px; }
      .carousel-viewport { height: 48vh; }
    }

    @media (prefers-reduced-motion: reduce) {
      *, ::before, ::after {
        animation-duration: 0.01ms !important;
        transition-duration: 0.01ms !important;
      }
    }
  </style>
</head>
<body>

  <!-- Background Particle System -->
  <canvas id="particleCanvas"></canvas>
  <div class="cinematic-vignette"></div>
  <div class="ambient-light-1"></div>
  <div class="ambient-light-2"></div>

  <!-- Header Controls -->
  <header class="top-controls">
    <div class="lang-switcher">
      <button class="lang-btn active" id="btn-en" onclick="setLanguage('en')">EN</button>
      <button class="lang-btn" id="btn-am" onclick="setLanguage('am')">አማ</button>
    </div>
    
    <div class="audio-control glass-panel" id="audio-widget">
      <button class="audio-btn" id="audio-toggle" aria-label="Toggle Music" onclick="toggleAudio()">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M9 18V5l12-2v13"></path>
          <circle cx="6" cy="18" r="3"></circle>
          <circle cx="18" cy="16" r="3"></circle>
        </svg>
      </button>
      <div class="audio-bars">
        <div class="audio-bar"></div>
        <div class="audio-bar"></div>
        <div class="audio-bar"></div>
        <div class="audio-bar"></div>
      </div>
    </div>
  </header>

  <!-- Audio Element -->
  <audio id="bg-music" loop preload="auto">
    <source src="https://cdn.pixabay.com/download/audio/2022/05/27/audio_1808fbf07a.mp3?filename=piano-moment-113941.mp3" type="audio/mpeg">
  </audio>

  <!-- Main Application Container -->
  <main id="app">

    <!-- SCREEN 1: CINEMATIC OPENING -->
    <section class="screen active" id="screen-opening" onclick="nextScreen()">
      <p class="opening-subtext" data-en="Someone prepared something special just for you... ❤️" data-am="ለአንቺ የተዘጋጀ ልዩ ስጦታ አለ... ❤️">
        Someone prepared something special just for you... ❤️
      </p>
      <div class="tap-hint" data-en="Tap anywhere to continue" data-am="ለመቀጠል የትም ቦታ ይነኩ">
        <span>Tap anywhere to continue</span>
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M5 12h14M12 5l7 7-7 7"/>
        </svg>
      </div>
    </section>

    <!-- SCREEN 2: BLEN REVEAL -->
    <section class="screen" id="screen-reveal">
      <div class="name-container">
        <span class="letter">B</span>
        <span class="letter">L</span>
        <span class="letter">E</span>
        <span class="letter">N</span>
        <span class="letter" style="color: var(--pink-neon)">❤️</span>
      </div>
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
        <p class="section-subtitle" data-en="Swipe or drag to navigate" data-am="ለማየት ወደ ጎን ይሳቡ">Swipe or drag to navigate</p>
      </div>

      <div class="carousel-viewport" id="carouselViewport">
        <div class="carousel-track" id="carouselTrack">
          <!-- Dynamically populated carousel cards -->
        </div>
      </div>

      <div class="carousel-nav-dots" id="carouselDots"></div>

      <div style="text-align: center; margin-top: 15px;">
        <button class="btn-luxury" onclick="nextScreen()" data-en="Continue Journey" data-am="ቀጥል">
          Continue Journey
        </button>
      </div>
    </section>

    <!-- SCREEN 4: TYPEWRITER LETTER -->
    <section class="screen" id="screen-letter">
      <div class="letter-card glass-panel">
        <div class="letter-body" id="typewriterTarget"></div>
        <span class="typing-cursor" id="typingCursor"></span>
      </div>
      <div style="margin-top: 30px; opacity: 0;" id="letter-btn-wrap">
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
      <h2 class="section-title title-pink" style="margin-bottom: 10px;" data-en="A Gift For You" data-am="ለአንቺ የተዘጋጀ ስጦታ">A Gift For You</h2>
      <p class="section-subtitle" data-en="Tap the box to unlock your surprise" data-am="ስጦታውን ለመክፈት ሳጥኑን ይነኩ">Tap the box to unlock your surprise</p>

      <div class="gift-stage" id="giftBox" onclick="openGift()">
        <div class="gift-cube">
          <div class="cube-face face-front"><div class="ribbon-v"></div><div class="ribbon-h"></div></div>
          <div class="cube-face face-back"><div class="ribbon-v"></div><div class="ribbon-h"></div></div>
          <div class="cube-face face-right"><div class="ribbon-v"></div><div class="ribbon-h"></div></div>
          <div class="cube-face face-left"><div class="ribbon-v"></div><div class="ribbon-h"></div></div>
          <div class="cube-face face-bottom"></div>
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
          <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&q=80&w=600" alt="Blen Profile">
        </div>
      </div>
      <div class="reveal-msg">
        <span data-en="Every smile," data-am="እያንዳንዱ ፈገግታ፣">Every smile,</span>
        <span data-en="every memory," data-am="እያንዳንዱ ትዝታ፣">every memory,</span>
        <span data-en="every moment..." data-am="እያንዳንዱ ቅጽበት...">every moment...</span>
        <span style="color: var(--pink-neon); font-weight: 600; margin-top: 15px;" data-en="Thank you for being part of my life. ❤️" data-am="በሕይወቴ ውስጥ ስላለሽ አመሰግናለሁ። ❤️">Thank you for being part of my life. ❤️</span>
      </div>
      <div style="margin-top: 40px;">
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
    </section>

  </main>

  <!-- Gallery Lightbox -->
  <div class="lightbox" id="lightbox">
    <button class="lightbox-close" onclick="closeLightbox()">&times;</button>
    <img src="" alt="Enlarged Memory" class="lightbox-img" id="lightboxImg">
  </div>

  <!-- JavaScript Application Logic -->
  <script>
    /* ==========================================================================
       1. GLOBAL STATE & CONFIGURATION
       ========================================================================== */
    const STATE = {
      currentScreen: 0,
      language: 'en',
      isPlayingAudio: false,
      isGiftOpened: false,
      carouselIndex: 0,
      typingInProgress: false
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
      am: `ውድ ብሌን፥\n\nአንዳንድ ሰዎች በሕይወት በመኖራቸው ብቻ ዓለምን ያበራሉ። አንቺ በእውነት ከነዚያ ಅಪூர்ብ ከሆኑ ሰዎች አንዷ ነሽ። አብረን ካሳለፍነው ሳቅ እስከ ተደረገልኝ ድጋፍ ድረስ፡ አንቺን እንደ ጓደኛ ማግኘት ትልቅ ስጦታ ነው።\n\nይህ ዲጂታል ማስታወሻ ያንቺን ደግነትና ድንቅነት ለማክበር የተዘጋጀ ትንሽ ስጦታ ነው።\n\nስለ ሁሉም ውብ ትዝታዎች አመሰግናለሁ።`
    };

    /* ==========================================================================
       2. PARTICLE CANVAS ENGINE
       ========================================================================== */
    const canvas = document.getElementById('particleCanvas');
    const ctx = canvas.getContext('2d');
    let particles = [];
    let canvasWidth = canvas.width = window.innerWidth;
    let canvasHeight = canvas.height = window.innerHeight;

    window.addEventListener('resize', () => {
      canvasWidth = canvas.width = window.innerWidth;
      canvasHeight = canvas.height = window.innerHeight;
    });

    class Particle {
      constructor() {
        this.reset();
      }

      reset() {
        this.x = Math.random() * canvasWidth;
        this.y = canvasHeight + Math.random() * 100;
        this.size = Math.random() * 3 + 1;
        this.speedY = Math.random() * 1.2 + 0.4;
        this.speedX = (Math.random() - 0.5) * 0.5;
        this.opacity = Math.random() * 0.6 + 0.2;
        this.color = Math.random() > 0.4 ? '#ff4fa3' : '#d4af37';
        this.isHeart = Math.random() > 0.8;
      }

      update() {
        this.y -= this.speedY;
        this.x += this.speedX;
        if (this.y < -20) this.reset();
      }

      draw() {
        ctx.fillStyle = this.color;
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
      const count = window.innerWidth < 600 ? 35 : 70;
      particles = [];
      for (let i = 0; i < count; i++) {
        particles.push(new Particle());
      }
    }

    function animateParticles() {
      ctx.clearRect(0, 0, canvasWidth, canvasHeight);
      particles.forEach(p => {
        p.update();
        p.draw();
      });
      requestAnimationFrame(animateParticles);
    }

    initParticles();
    animateParticles();

    /* ==========================================================================
       3. NAVIGATION & SCREEN CONTROLLER
       ========================================================================== */
    function goToScreen(index) {
      if (index < 0 || index >= SCREENS.length) return;

      const currentEl = document.getElementById(SCREENS[STATE.currentScreen]);
      const nextEl = document.getElementById(SCREENS[index]);

      currentEl.classList.remove('active');
      STATE.currentScreen = index;
      nextEl.classList.add('active');

      // Trigger Screen Specific Actions
      if (SCREENS[index] === 'screen-letter') {
        startTypewriter();
      } else if (SCREENS[index] === 'screen-countdown') {
        runCountdown();
      } else if (SCREENS[index] === 'screen-final') {
        runFinalReveal();
      }
    }

    function nextScreen() {
      // Auto Start Audio on First Gesture
      if (!STATE.isPlayingAudio && STATE.currentScreen === 0) {
        toggleAudio();
      }
      goToScreen(STATE.currentScreen + 1);
    }

    /* ==========================================================================
       4. AUDIO SYSTEM
       ========================================================================== */
    const audio = document.getElementById('bg-music');
    const audioWidget = document.getElementById('audio-widget');

    function toggleAudio() {
      if (STATE.isPlayingAudio) {
        audio.pause();
        audioWidget.classList.remove('playing');
        STATE.isPlayingAudio = false;
      } else {
        audio.play().then(() => {
          audioWidget.classList.add('playing');
          STATE.isPlayingAudio = true;
        }).catch(() => {
          // Autoplay blocked fallback
        });
      }
    }

    /* ==========================================================================
       5. INTERNATIONALIZATION (EN / AM)
       ========================================================================== */
    function setLanguage(lang) {
      STATE.language = lang;

      document.getElementById('btn-en').classList.toggle('active', lang === 'en');
      document.getElementById('btn-am').classList.toggle('active', lang === 'am');

      if (lang === 'am') {
        document.body.classList.add('lang-am');
      } else {
        document.body.classList.remove('lang-am');
      }

      // Update all data-en / data-am attribute elements
      document.querySelectorAll('[data-en]').forEach(el => {
        const text = el.getAttribute(`data-${lang}`);
        if (text) el.textContent = text;
      });

      // Update Active Screen Dynamic Content
      renderCarousel();
      if (SCREENS[STATE.currentScreen] === 'screen-letter') {
        startTypewriter();
      }
    }

    /* ==========================================================================
       6. SCREEN 3: 3D CAROUSEL SYSTEM
       ========================================================================== */
    const track = document.getElementById('carouselTrack');
    const dotsContainer = document.getElementById('carouselDots');

    function renderCarousel() {
      track.innerHTML = '';
      dotsContainer.innerHTML = '';

      GALLERY_DATA.forEach((item, index) => {
        // Create Card
        const card = document.createElement('div');
        card.className = 'carousel-card';
        const caption = STATE.language === 'am' ? item.capAm : item.capEn;
        
        card.innerHTML = `
          <img src="${item.url}" alt="${caption}" loading="lazy">
          <div class="card-caption">${caption}</div>
        `;
        
        card.onclick = () => {
          if (index === STATE.carouselIndex) {
            openLightbox(item.url);
          } else {
            STATE.carouselIndex = index;
            updateCarousel();
          }
        };

        track.appendChild(card);

        // Create Navigation Dot
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

        card.style.opacity = absOffset === 0 ? '1' : '0.65';
        card.style.filter = absOffset === 0 ? 'blur(0px)' : 'blur(3px)';
        card.style.transform = `translateX(${translateX}px) translateZ(${translateZ}px) rotateY(${rotateY}deg)`;
        card.style.zIndex = `${10 - absOffset}`;
        card.style.borderColor = absOffset === 0 ? 'var(--pink-neon)' : 'var(--border-glass)';
      });

      // Update Dots
      Array.from(dotsContainer.children).forEach((dot, i) => {
        dot.classList.toggle('active', i === STATE.carouselIndex);
      });
    }

    // Touch Swipe Gesture Handling
    let startX = 0;
    const viewport = document.getElementById('carouselViewport');
    
    viewport.addEventListener('touchstart', e => startX = e.touches[0].clientX, {passive: true});
    viewport.addEventListener('touchend', e => {
      const diffX = startX - e.changedTouches[0].clientX;
      if (Math.abs(diffX) > 40) {
        if (diffX > 0 && STATE.carouselIndex < GALLERY_DATA.length - 1) STATE.carouselIndex++;
        else if (diffX < 0 && STATE.carouselIndex > 0) STATE.carouselIndex--;
        updateCarousel();
      }
    }, {passive: true});

    renderCarousel();

    /* Lightbox Functions */
    function openLightbox(url) {
      document.getElementById('lightboxImg').src = url;
      document.getElementById('lightbox').classList.add('active');
    }
    function closeLightbox() {
      document.getElementById('lightbox').classList.remove('active');
    }

    /* ==========================================================================
       7. SCREEN 4: TYPEWRITER SYSTEM
       ========================================================================== */
    let typingTimer = null;

    function startTypewriter() {
      const target = document.getElementById('typewriterTarget');
      const btnWrap = document.getElementById('letter-btn-wrap');
      const text = LETTER_TEXTS[STATE.language];

      target.textContent = '';
      btnWrap.style.opacity = '0';
      btnWrap.style.transform = 'translateY(15px)';

      if (typingTimer) clearInterval(typingTimer);

      let idx = 0;
      typingTimer = setInterval(() => {
        if (idx < text.length) {
          target.textContent += text.charAt(idx);
          idx++;
        } else {
          clearInterval(typingTimer);
          btnWrap.style.transition = 'all 0.8s ease';
          btnWrap.style.opacity = '1';
          btnWrap.style.transform = 'translateY(0)';
        }
      }, 35);
    }

    /* ==========================================================================
       8. SCREEN 5: COUNTDOWN ANIMATOR
       ========================================================================== */
    function runCountdown() {
      const numEl = document.getElementById('countdown-val');
      let val = 3;
      numEl.textContent = val;

      const timer = setInterval(() => {
        val--;
        if (val > 0) {
          numEl.textContent = val;
        } else {
          clearInterval(timer);
          nextScreen();
        }
      }, 1000);
    }

    /* ==========================================================================
       9. SCREEN 6: 3D GIFT UNBOXING
       ========================================================================== */
    function openGift() {
      if (STATE.isGiftOpened) return;
      STATE.isGiftOpened = true;

      const giftBox = document.getElementById('giftBox');
      const openBtn = document.getElementById('openGiftBtn');

      giftBox.classList.add('open');
      openBtn.style.opacity = '0';

      // Mobile Vibration Support
      if (navigator.vibrate) {
        navigator.vibrate([100, 50, 200]);
      }

      // Sparkle Burst Particle Effect
      for (let i = 0; i < 40; i++) {
        const p = new Particle();
        p.x = canvasWidth / 2;
        p.y = canvasHeight / 2;
        p.speedY = (Math.random() - 0.5) * 8;
        p.speedX = (Math.random() - 0.5) * 8;
        particles.push(p);
      }

      setTimeout(() => {
        nextScreen();
      }, 1600);
    }

    /* ==========================================================================
       10. SCREEN 7: FINAL REVEAL ANIMATOR
       ========================================================================== */
    function runFinalReveal() {
      const lines = document.querySelectorAll('.reveal-msg span');
      lines.forEach(line => line.classList.remove('visible'));

      lines.forEach((line, index) => {
        setTimeout(() => {
          line.classList.add('visible');
        }, (index + 1) * 700);
      });
    }
  </script>
</body>
</html>
