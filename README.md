<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Special VIP Gift | BLEN</title>

    <!-- PWA -->
    <meta name="theme-color" content="#0B0B0B">
    <meta name="description" content="A special digital gift prepared for Blen">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <link rel="manifest" href="data:application/json,{%22name%22:%22Digital%20Gift%22,%22short_name%22:%22Gift%22,%22start_url%22:%22.%22,%22display%22:%22standalone%22,%22background_color%22:%22%230B0B0B%22,%22theme_color%22:%22%23FF4FA3%22}">

    <!-- Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+Ethiopic:wght@300;400;600;700&family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">

    <!-- Confetti -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <style>
        :root {
            --bg-black: #0B0B0B;
            --neon-pink: #FF4FA3;
            --neon-pink-glow: rgba(255, 79, 163, 0.4);
            --gold: #D4AF37;
            --gold-glow: rgba(212, 175, 55, 0.3);
            --text-white: #FFFFFF;
            --text-muted: rgba(255, 255, 255, 0.7);
            --glass-bg: rgba(255, 255, 255, 0.03);
            --glass-border: rgba(255, 255, 255, 0.08);
            --glass-blur: blur(16px);
            --font-main: 'Inter', 'Noto Sans Ethiopic', sans-serif;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            -webkit-tap-highlight-color: transparent;
            user-select: none;
        }

        body {
            background-color: var(--bg-black);
            color: var(--text-white);
            font-family: var(--font-main);
            overflow-x: hidden;
            width: 100vw;
            min-height: 100vh;
            position: relative;
        }

        /* Language switcher */
        .lang-switcher {
            position: fixed;
            top: 20px;
            left: 20px;
            z-index: 1000;
            display: flex;
            gap: 6px;
            background: var(--glass-bg);
            backdrop-filter: var(--glass-blur);
            -webkit-backdrop-filter: var(--glass-blur);
            border: 1px solid var(--glass-border);
            border-radius: 50px;
            padding: 5px;
            box-shadow: 0 8px 32px rgba(0,0,0,0.5);
        }
        .lang-btn {
            background: transparent;
            border: none;
            color: var(--text-muted);
            font-size: 0.8rem;
            font-weight: 600;
            padding: 7px 14px;
            border-radius: 40px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: var(--font-main);
            letter-spacing: 0.5px;
        }
        .lang-btn.active {
            background: linear-gradient(135deg, #FF4FA3 0%, #D4145A 100%);
            color: #fff;
            box-shadow: 0 0 15px var(--neon-pink-glow);
        }
        .lang-btn:not(.active):hover {
            color: var(--neon-pink);
        }

        /* Canvases */
        #particle-canvas, #petal-canvas, #sparkle-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }
        #petal-canvas { z-index: 2; }
        #sparkle-canvas { z-index: 3; }

        /* Audio control */
        .audio-control {
            position: fixed;
            top: 20px;
            right: 20px;
            z-index: 1000;
            background: var(--glass-bg);
            backdrop-filter: var(--glass-blur);
            -webkit-backdrop-filter: var(--glass-blur);
            border: 1px solid var(--glass-border);
            border-radius: 50px;
            padding: 8px 16px;
            display: flex;
            align-items: center;
            gap: 10px;
            box-shadow: 0 8px 32px rgba(0,0,0,0.5);
            transition: transform 0.3s ease, border-color 0.3s ease;
        }
        .audio-control:hover {
            border-color: var(--neon-pink);
            transform: translateY(-2px);
        }
        .music-btn {
            background: none;
            border: none;
            color: var(--neon-pink);
            font-size: 1.2rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            width: 24px;
            height: 24px;
        }
        .music-btn.playing {
            animation: pulse-glow 2s infinite alternate;
        }
        .volume-slider {
            width: 60px;
            accent-color: var(--neon-pink);
            cursor: pointer;
        }

        h1, h2, h3 { text-align: center; }

        .pink-glow-text {
            color: var(--neon-pink);
            text-shadow: 0 0 15px var(--neon-pink-glow);
        }
        .gold-glow-text {
            color: var(--gold);
            text-shadow: 0 0 15px var(--gold-glow);
        }

        .btn-primary {
            background: linear-gradient(135deg, #FF4FA3 0%, #D4145A 100%);
            color: #FFF;
            border: none;
            padding: 16px 36px;
            font-size: 1rem;
            font-weight: 600;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 0 25px var(--neon-pink-glow);
            transition: all 0.3s cubic-bezier(0.25, 1, 0.5, 1);
            letter-spacing: 1px;
            font-family: var(--font-main);
        }
        .btn-primary:active {
            transform: scale(0.96);
            box-shadow: 0 0 10px var(--neon-pink-glow);
        }

        .glass-card {
            background: var(--glass-bg);
            backdrop-filter: var(--glass-blur);
            -webkit-backdrop-filter: var(--glass-blur);
            border: 1px solid var(--glass-border);
            border-radius: 24px;
            padding: 32px 24px;
            box-shadow: 0 16px 40px rgba(0,0,0,0.6);
            position: relative;
            z-index: 10;
        }

        .screen {
            position: fixed;
            inset: 0;
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 10;
            opacity: 0;
            pointer-events: none;
            transition: opacity 1s cubic-bezier(0.4, 0, 0.2, 1);
            padding: 24px;
        }
        .screen.active {
            opacity: 1;
            pointer-events: auto;
        }

        /* Opening */
        #opening-screen {
            background: var(--bg-black);
            z-index: 100;
            cursor: pointer;
        }
        .opening-text-1 {
            font-size: 1.25rem;
            font-weight: 300;
            opacity: 0;
            transform: translateY(10px);
            transition: all 1.5s ease;
            color: var(--text-muted);
            text-align: center;
            max-width: 320px;
            line-height: 1.6;
        }
        .opening-text-2 {
            margin-top: 24px;
            font-size: 0.9rem;
            letter-spacing: 1px;
            color: var(--neon-pink);
            opacity: 0;
            animation: pulse-glow 2s infinite alternate;
            transition: opacity 1s ease;
        }

        /* Cinematic name */
        #welcome-screen {
            background: radial-gradient(ellipse at center, #1a0a12 0%, #0B0B0B 70%);
            overflow: hidden;
        }
        .cinematic-name-container {
            position: relative;
            text-align: center;
            z-index: 20;
            transform: scale(0.85);
            opacity: 0;
            transition: transform 2.8s cubic-bezier(0.16, 1, 0.3, 1), opacity 1.8s ease;
        }
        .cinematic-name-container.revealed {
            transform: scale(1);
            opacity: 1;
        }
        .name-letters {
            display: flex;
            justify-content: center;
            gap: 0.08em;
            flex-wrap: wrap;
            margin-bottom: 8px;
        }
        .name-letter {
            font-size: clamp(3.8rem, 14vw, 7.5rem);
            font-weight: 700;
            color: var(--neon-pink);
            text-shadow:
                0 0 10px var(--neon-pink),
                0 0 30px var(--neon-pink-glow),
                0 0 60px rgba(255, 79, 163, 0.35),
                0 0 100px rgba(255, 79, 163, 0.2);
            opacity: 0;
            transform: translateY(40px) scale(0.7);
            display: inline-block;
            transition: all 0.7s cubic-bezier(0.22, 1, 0.36, 1);
            letter-spacing: -0.02em;
        }
        .name-letter.visible {
            opacity: 1;
            transform: translateY(0) scale(1);
        }
        .name-letter.heart {
            font-size: clamp(3rem, 11vw, 5.5rem);
            margin-left: 0.15em;
            animation: heartBeat 1.4s ease-in-out infinite;
        }

        .welcome-message {
            max-width: 420px;
            margin-top: 36px;
            font-size: 1.05rem;
            line-height: 1.85;
            color: #E8E8E8;
            text-align: center;
            opacity: 0;
            transform: translateY(25px);
            transition: all 1.4s cubic-bezier(0.22, 1, 0.36, 1) 0.3s;
        }
        .welcome-message.show {
            opacity: 1;
            transform: translateY(0);
        }
        .welcome-message p { margin-bottom: 14px; }
        .welcome-message .highlight {
            color: var(--gold);
            text-shadow: 0 0 12px var(--gold-glow);
        }

        .welcome-next-btn {
            margin-top: 40px;
            opacity: 0;
            transform: translateY(20px);
            transition: all 1s ease 0.6s;
            pointer-events: none;
        }
        .welcome-next-btn.show {
            opacity: 1;
            transform: translateY(0);
            pointer-events: auto;
        }

        /* Gallery */
        .gallery-container {
            width: 100%;
            max-width: 380px;
            height: 400px;
            perspective: 1000px;
            position: relative;
            margin-bottom: 30px;
        }
        .carousel-3d {
            width: 100%;
            height: 100%;
            position: absolute;
            transform-style: preserve-3d;
            transition: transform 0.8s cubic-bezier(0.25, 1, 0.5, 1);
        }
        .carousel-card {
            position: absolute;
            width: 260px;
            height: 350px;
            left: 50%;
            top: 50%;
            margin-left: -130px;
            margin-top: -175px;
            border-radius: 20px;
            overflow: hidden;
            border: 1px solid var(--glass-border);
            box-shadow: 0 10px 30px rgba(0,0,0,0.8);
            background: #151515;
            transition: opacity 0.5s ease;
        }
        .carousel-card img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .lightbox {
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.95);
            z-index: 2000;
            display: flex;
            justify-content: center;
            align-items: center;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.4s ease;
        }
        .lightbox.active {
            opacity: 1;
            pointer-events: auto;
        }
        .lightbox img {
            max-width: 90%;
            max-height: 80vh;
            border-radius: 12px;
            box-shadow: 0 0 30px var(--neon-pink-glow);
        }

        /* Letter */
        .letter-card {
            max-width: 500px;
            width: 100%;
            min-height: 250px;
            text-align: left;
            position: relative;
        }
        .letter-content {
            font-family: var(--font-main);
            font-size: 1.05rem;
            line-height: 1.8;
            color: #E0E0E0;
            white-space: pre-wrap;
        }
        .cursor {
            display: inline-block;
            width: 2px;
            height: 1.2rem;
            background-color: var(--neon-pink);
            vertical-align: middle;
            animation: blink 0.8s infinite;
        }

        /* Countdown */
        .countdown-title {
            font-size: 1.5rem;
            margin-bottom: 20px;
            color: var(--text-muted);
        }
        .countdown-number {
            font-size: 6rem;
            font-weight: 700;
            color: var(--neon-pink);
            text-shadow: 0 0 30px var(--neon-pink-glow);
            animation: scalePulse 1s infinite alternate;
        }

        /* Gift box */
        .gift-container {
            width: 180px;
            height: 180px;
            position: relative;
            perspective: 1000px;
            margin-bottom: 40px;
            cursor: pointer;
        }
        .gift-box {
            width: 100%;
            height: 100%;
            position: relative;
            transform-style: preserve-3d;
            transition: transform 0.5s ease;
        }
        .gift-box:hover {
            transform: rotateY(15deg) rotateX(10deg);
        }
        .gift-face {
            position: absolute;
            width: 180px;
            height: 180px;
            background: linear-gradient(135deg, #1A1A1A 0%, #050505 100%);
            border: 1px solid rgba(255, 79, 163, 0.3);
            box-shadow: inset 0 0 15px rgba(255, 79, 163, 0.1);
        }
        .gift-face.front  { transform: rotateY(  0deg) translateZ(90px); }
        .gift-face.back   { transform: rotateY(180deg) translateZ(90px); }
        .gift-face.right  { transform: rotateY( 90deg) translateZ(90px); }
        .gift-face.left   { transform: rotateY(-90deg) translateZ(90px); }
        .gift-face.top    { transform: rotateX( 90deg) translateZ(90px); transition: transform 0.8s ease; }
        .gift-face.bottom { transform: rotateX(-90deg) translateZ(90px); }

        .ribbon-v, .ribbon-h {
            position: absolute;
            background: linear-gradient(135deg, #FF4FA3 0%, #D4145A 100%);
            box-shadow: 0 0 10px var(--neon-pink-glow);
        }
        .ribbon-v { width: 30px; height: 100%; left: 75px; top: 0; }
        .ribbon-h { width: 100%; height: 30px; left: 0; top: 75px; }

        .gift-box.open .gift-face.top {
            transform: rotateX(160deg) translateZ(90px);
        }

        /* Reveal */
        .profile-frame {
            width: 180px;
            height: 180px;
            border-radius: 50%;
            padding: 5px;
            background: linear-gradient(135deg, var(--neon-pink), var(--gold));
            box-shadow: 0 0 30px var(--neon-pink-glow);
            margin-bottom: 24px;
            animation: float 4s ease-in-out infinite;
        }
        .profile-frame img {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            object-fit: cover;
        }
        .reveal-message {
            font-size: 1.1rem;
            line-height: 1.8;
            text-align: center;
            max-width: 360px;
            color: #E0E0E0;
            margin-bottom: 30px;
        }

        /* Ending */
        .ending-title {
            font-size: 1.8rem;
            margin-bottom: 12px;
        }
        .ending-author {
            font-size: 0.95rem;
            letter-spacing: 1px;
            color: var(--text-muted);
            margin-top: 8px;
        }
        .heart-glow {
            font-size: 2.5rem;
            margin-top: 20px;
            color: var(--neon-pink);
            animation: pulse-glow 1.5s infinite alternate;
        }

        @keyframes pulse-glow {
            0% { transform: scale(1); filter: drop-shadow(0 0 5px var(--neon-pink-glow)); }
            100% { transform: scale(1.1); filter: drop-shadow(0 0 20px var(--neon-pink)); }
        }
        @keyframes scalePulse {
            0% { transform: scale(0.9); opacity: 0.7; }
            100% { transform: scale(1.1); opacity: 1; }
        }
        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0; }
        }
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        @keyframes heartBeat {
            0%, 100% { transform: scale(1); }
            15% { transform: scale(1.18); }
            30% { transform: scale(1); }
            45% { transform: scale(1.12); }
            60% { transform: scale(1); }
        }
    </style>
</head>
<body>

    <!-- Language Switcher -->
    <div class="lang-switcher">
        <button class="lang-btn active" data-lang="en" id="btn-en">EN</button>
        <button class="lang-btn" data-lang="am" id="btn-am">አማ</button>
    </div>

    <!-- Background canvases -->
    <canvas id="particle-canvas"></canvas>
    <canvas id="petal-canvas"></canvas>
    <canvas id="sparkle-canvas"></canvas>

    <!-- Audio -->
    <div class="audio-control">
        <button class="music-btn" id="music-toggle" aria-label="Toggle music">🎵</button>
        <input type="range" class="volume-slider" id="volume-control" min="0" max="1" step="0.05" value="0.5">
        <audio id="bg-music" loop preload="auto">
            <source src="https://cdn.pixabay.com/download/audio/2022/05/27/audio_1808fbf07a.mp3?filename=piano-moment-111718.mp3" type="audio/mpeg">
        </audio>
        <audio id="reveal-sound" preload="auto">
            <source src="https://cdn.pixabay.com/download/audio/2021/08/04/audio_0625c1539c.mp3?filename=success-1-6297.mp3" type="audio/mpeg">
        </audio>
    </div>

    <!-- 1. Opening -->
    <section class="screen active" id="opening-screen">
        <div class="opening-text-1" id="opening-text" data-en="Someone prepared something special just for you... ❤️" data-am="አንድ ሰው ለእርስዎ የሚሆን ልዩ ነገር አዘጋጅቷል... ❤️">Someone prepared something special just for you... ❤️</div>
        <div class="opening-text-2" id="tap-text" data-en="Tap anywhere to continue" data-am="ለመቀጠል የትም ቦታ ይንኩ">Tap anywhere to continue</div>
    </section>

    <!-- 2. Cinematic Welcome -->
    <section class="screen" id="welcome-screen">
        <div class="cinematic-name-container" id="name-container">
            <div class="name-letters" id="name-letters"></div>
        </div>

        <div class="welcome-message" id="welcome-message">
            <!-- Content set by JS -->
        </div>

        <button class="btn-primary welcome-next-btn" id="welcome-next" data-en="Continue" data-am="ቀጥል">Continue</button>
    </section>

    <!-- 3. Gallery -->
    <section class="screen" id="gallery-screen">
        <h2 class="pink-glow-text" style="margin-bottom: 20px;" data-en="Memories We Share" data-am="የምናስታውሳቸው ትዝታዎች">Memories We Share</h2>
        <div class="gallery-container">
            <div class="carousel-3d" id="carousel">
                <div class="carousel-card"><img src="https://images.unsplash.com/photo-1518199266791-5375a83190b7?w=500&q=80" alt="Memory 1" loading="lazy"></div>
                <div class="carousel-card"><img src="https://images.unsplash.com/photo-1516589178581-6cd7833ae3b2?w=500&q=80" alt="Memory 2" loading="lazy"></div>
                <div class="carousel-card"><img src="https://images.unsplash.com/photo-1522673607200-164d1b6ce486?w=500&q=80" alt="Memory 3" loading="lazy"></div>
                <div class="carousel-card"><img src="https://images.unsplash.com/photo-1492684223066-81342ee5ff30?w=500&q=80" alt="Memory 4" loading="lazy"></div>
                <div class="carousel-card"><img src="https://images.unsplash.com/photo-1529156069898-49953e39b3ac?w=500&q=80" alt="Memory 5" loading="lazy"></div>
            </div>
        </div>
        <button class="btn-primary" id="gallery-next" data-en="Next Surprise" data-am="ቀጣይ አስደናቂ ነገር">Next Surprise</button>
    </section>

    <!-- Lightbox -->
    <div class="lightbox" id="lightbox">
        <img id="lightbox-img" src="" alt="Full photo">
    </div>

    <!-- 4. Letter -->
    <section class="screen" id="letter-screen">
        <div class="glass-card letter-card">
            <h3 class="gold-glow-text" style="margin-bottom: 16px; font-size: 1.3rem;" data-en="A Message Written for You" data-am="ለእርስዎ የተጻፈ መልእክት">A Message Written for You</h3>
            <div class="letter-content" id="typewriter-text"></div><span class="cursor" id="cursor"></span>
        </div>
        <button class="btn-primary" id="letter-next" style="margin-top: 30px; display: none;" data-en="Continue" data-am="ቀጥል">Continue</button>
    </section>

    <!-- 5. Countdown -->
    <section class="screen" id="countdown-screen">
        <div class="countdown-title" data-en="One last amazing thing..." data-am="አንድ የመጨረሻ አስደናቂ ነገር...">One last amazing thing...</div>
        <div class="countdown-number" id="countdown-timer">3</div>
    </section>

    <!-- 6. Gift -->
    <section class="screen" id="gift-screen">
        <div class="gift-container" id="gift-container">
            <div class="gift-box" id="gift-box">
                <div class="gift-face front"><div class="ribbon-v"></div><div class="ribbon-h"></div></div>
                <div class="gift-face back"><div class="ribbon-v"></div><div class="ribbon-h"></div></div>
                <div class="gift-face right"><div class="ribbon-v"></div><div class="ribbon-h"></div></div>
                <div class="gift-face left"><div class="ribbon-v"></div><div class="ribbon-h"></div></div>
                <div class="gift-face top"><div class="ribbon-v"></div><div class="ribbon-h"></div></div>
                <div class="gift-face bottom"></div>
            </div>
        </div>
        <button class="btn-primary" id="open-gift-btn" data-en="🎁 Open Your Gift" data-am="🎁 ስጦታዎን ይክፈቱ">🎁 Open Your Gift</button>
    </section>

    <!-- 7. Reveal -->
    <section class="screen" id="reveal-screen">
        <div class="profile-frame">
            <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=500&q=80" alt="Your photo">
        </div>
        <div class="reveal-message" id="reveal-message">
            <!-- set by JS -->
        </div>
        <button class="btn-primary" id="reveal-next" data-en="Final Note" data-am="የመጨረሻ ማስታወሻ">Final Note</button>
    </section>

    <!-- 8. Ending -->
    <section class="screen" id="ending-screen">
        <h2 class="ending-title pink-glow-text" data-en="Made especially for you ❤️" data-am="በልዩ ሁኔታ ለብሌን የተዘጋጀ ❤️">Made especially for you ❤️</h2>
        <div class="ending-author" data-en="Created by Yisshak" data-am="የተሰራው በ Yisshak">Created by Yisshak</div>
        <div class="heart-glow">💖</div>
    </section>

    <script>
        /* ========== LANGUAGE SYSTEM ========== */
        let currentLang = 'en'; // Default: English

        const translations = {
            welcome: {
                en: `<p>«Hi, <span class="highlight">BLEN</span>! 👋</p>
                     <p>Welcome to a little surprise made especially for you.</p>
                     <p>Every page you're about to see was created with care to celebrate our friendship and bring a smile to your face.</p>
                     <p>Take your time, enjoy every moment, and don't forget to open your gift at the end. 🎁✨»</p>`,
                am: `<p>«ሰላም <span class="highlight">ብሌን</span>! 👋</p>
                     <p>ለእርስዎ በልዩ ሁኔታ የተዘጋጀ ትንሽ አስደናቂ ስጦታ እንኳን በደህና መጡ።</p>
                     <p>የሚመጡት እያንዳንዱ ገጽ የጓደኝነታችንን ለማክበር እና ፈገግታን ለማምጣት በጥንቃቄ ተዘጋጅቷል።</p>
                     <p>ጊዜዎን ይውሰዱ፣ እያንዳንዱን ቅጽበት ይደሰቱ፣ እና በመጨረሻ ስጦታዎን መክፈትዎን አይርሱ። 🎁✨»</p>`
            },
            letter: {
                en: `From the moment you entered my life, everything became brighter.

Thank you for the beautiful friendship, the fun times we shared, the games we played, and all the unforgettable memories.

This digital gift is a small way to remind you how special you are to me — today and always! ✨`,
                am: `ወደ ሕይወቴ ከገባህበት/ሽበት ቅጽበት ጀምሮ ሁሉም ነገር የበለጠ ብሩህ ሆኗል::

ስለ መልካም ጓደኝነትህ/ሽ፣ አብረን ላሳለፍናቸው አስደሳች ጊዜያት፣ ላቀረብናቸው ጨዋታዎች እና ላልተረሱ ትዝታዎች ሁሉ በጣም አመሰግናለሁ::

ይህ ዲጂታል ስጦታ ለእኔ ምን ያህል ልዩ እንደሆንክ/ሽ ለማስታወስ የተደረገች ትንሽ ስጦታ ናት—ዛሬም ሁልጊዜም! ✨`
            },
            reveal: {
                en: `«Every smile,<br>every memory,<br>every moment...<br><br>Thank you for being part of my life. ❤️»`,
                am: `«እያንዳንዱ ፈገግታ፣<br>እያንዳንዱ ትዝታ፣<br>እያንዳንዱ ቅጽበት...<br><br>የሕይወቴ አካል ስለሆንክ/ሽ አመሰግናለሁ:: ❤️»`
            }
        };

        function setLanguage(lang) {
            currentLang = lang;
            document.documentElement.lang = lang;

            // Update all elements with data-en / data-am
            document.querySelectorAll('[data-en]').forEach(el => {
                const text = el.getAttribute(`data-${lang}`);
                if (text !== null) el.textContent = text;
            });

            // Welcome message
            const welcomeMsg = document.getElementById('welcome-message');
            if (welcomeMsg) welcomeMsg.innerHTML = translations.welcome[lang];

            // Reveal message
            const revealMsg = document.getElementById('reveal-message');
            if (revealMsg) revealMsg.innerHTML = translations.reveal[lang];

            // Update button states
            document.querySelectorAll('.lang-btn').forEach(btn => {
                btn.classList.toggle('active', btn.dataset.lang === lang);
            });

            // If letter is already typing / finished, re-render it
            if (document.getElementById('letter-screen').classList.contains('active') || 
                document.getElementById('typewriter-text').textContent.length > 0) {
                // just update the stored text; if currently typing it will use new lang next time
            }
        }

        // Language buttons
        document.getElementById('btn-en').addEventListener('click', (e) => {
            e.stopPropagation();
            setLanguage('en');
        });
        document.getElementById('btn-am').addEventListener('click', (e) => {
            e.stopPropagation();
            setLanguage('am');
        });

        // Initialize English
        setLanguage('en');

        /* ========== AUDIO ========== */
        const audio = document.getElementById('bg-music');
        const revealSound = document.getElementById('reveal-sound');
        const musicBtn = document.getElementById('music-toggle');
        const volumeSlider = document.getElementById('volume-control');

        function initAudio() {
            audio.volume = volumeSlider.value;
            audio.play().then(() => {
                musicBtn.classList.add('playing');
            }).catch(() => {});
        }

        musicBtn.addEventListener('click', (e) => {
            e.stopPropagation();
            if (audio.paused) {
                audio.play();
                musicBtn.classList.add('playing');
            } else {
                audio.pause();
                musicBtn.classList.remove('playing');
            }
        });

        volumeSlider.addEventListener('input', (e) => {
            audio.volume = e.target.value;
            if (revealSound) revealSound.volume = e.target.value;
        });

        /* ========== PARTICLES ========== */
        const pCanvas = document.getElementById('particle-canvas');
        const pCtx = pCanvas.getContext('2d');
        let particles = [];

        function resizeCanvas() {
            pCanvas.width = window.innerWidth;
            pCanvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        class Particle {
            constructor() { this.reset(); }
            reset() {
                this.x = Math.random() * pCanvas.width;
                this.y = pCanvas.height + 20;
                this.size = Math.random() * 12 + 6;
                this.speedY = Math.random() * 1.5 + 0.5;
                this.opacity = Math.random() * 0.5 + 0.2;
                this.isHeart = Math.random() > 0.4;
            }
            update() {
                this.y -= this.speedY;
                this.x += Math.sin(this.y * 0.02) * 0.5;
                if (this.y < -20) this.reset();
            }
            draw() {
                pCtx.fillStyle = `rgba(255, 79, 163, ${this.opacity})`;
                if (this.isHeart) {
                    pCtx.font = `${this.size}px serif`;
                    pCtx.fillText('❤️', this.x, this.y);
                } else {
                    pCtx.beginPath();
                    pCtx.arc(this.x, this.y, this.size / 4, 0, Math.PI * 2);
                    pCtx.fill();
                }
            }
        }

        for (let i = 0; i < 25; i++) particles.push(new Particle());

        function animateParticles() {
            pCtx.clearRect(0, 0, pCanvas.width, pCanvas.height);
            particles.forEach(p => { p.update(); p.draw(); });
            requestAnimationFrame(animateParticles);
        }
        animateParticles();

        /* ========== PETALS ========== */
        const petalCanvas = document.getElementById('petal-canvas');
        const petalCtx = petalCanvas.getContext('2d');
        let petals = [];

        function resizePetalCanvas() {
            petalCanvas.width = window.innerWidth;
            petalCanvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizePetalCanvas);
        resizePetalCanvas();

        class Petal {
            constructor() { this.reset(); }
            reset() {
                this.x = Math.random() * petalCanvas.width;
                this.y = -20;
                this.size = Math.random() * 10 + 8;
                this.speedY = Math.random() * 1.2 + 0.8;
                this.speedX = Math.random() * 1 - 0.5;
                this.rotation = Math.random() * 360;
                this.rotSpeed = Math.random() * 2 - 1;
                this.opacity = Math.random() * 0.6 + 0.3;
            }
            update() {
                this.y += this.speedY;
                this.x += Math.sin(this.y * 0.01) + this.speedX;
                this.rotation += this.rotSpeed;
                if (this.y > petalCanvas.height + 20) this.reset();
            }
            draw() {
                petalCtx.save();
                petalCtx.translate(this.x, this.y);
                petalCtx.rotate((this.rotation * Math.PI) / 180);
                petalCtx.fillStyle = `rgba(255, 79, 163, ${this.opacity})`;
                petalCtx.beginPath();
                petalCtx.ellipse(0, 0, this.size, this.size / 2, 0, 0, Math.PI * 2);
                petalCtx.fill();
                petalCtx.restore();
            }
        }

        for (let i = 0; i < 20; i++) petals.push(new Petal());

        function animatePetals() {
            petalCtx.clearRect(0, 0, petalCanvas.width, petalCanvas.height);
            petals.forEach(pt => { pt.update(); pt.draw(); });
            requestAnimationFrame(animatePetals);
        }
        animatePetals();

        /* ========== SPARKLES ========== */
        const sparkleCanvas = document.getElementById('sparkle-canvas');
        const sparkleCtx = sparkleCanvas.getContext('2d');
        let sparkles = [];

        function resizeSparkleCanvas() {
            sparkleCanvas.width = window.innerWidth;
            sparkleCanvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeSparkleCanvas);
        resizeSparkleCanvas();

        class Sparkle {
            constructor() { this.reset(); }
            reset() {
                this.x = Math.random() * sparkleCanvas.width;
                this.y = Math.random() * sparkleCanvas.height * 0.7 + sparkleCanvas.height * 0.1;
                this.size = Math.random() * 4 + 2;
                this.life = 0;
                this.maxLife = Math.random() * 60 + 40;
                this.opacity = 0;
            }
            update() {
                this.life++;
                if (this.life < this.maxLife / 2) {
                    this.opacity = this.life / (this.maxLife / 2);
                } else {
                    this.opacity = 1 - (this.life - this.maxLife / 2) / (this.maxLife / 2);
                }
                if (this.life >= this.maxLife) this.reset();
            }
            draw() {
                sparkleCtx.save();
                sparkleCtx.globalAlpha = this.opacity * 0.9;
                sparkleCtx.fillStyle = '#D4AF37';
                sparkleCtx.shadowBlur = 8;
                sparkleCtx.shadowColor = '#D4AF37';
                sparkleCtx.beginPath();
                const s = this.size;
                sparkleCtx.moveTo(this.x, this.y - s);
                sparkleCtx.lineTo(this.x + s * 0.3, this.y - s * 0.3);
                sparkleCtx.lineTo(this.x + s, this.y);
                sparkleCtx.lineTo(this.x + s * 0.3, this.y + s * 0.3);
                sparkleCtx.lineTo(this.x, this.y + s);
                sparkleCtx.lineTo(this.x - s * 0.3, this.y + s * 0.3);
                sparkleCtx.lineTo(this.x - s, this.y);
                sparkleCtx.lineTo(this.x - s * 0.3, this.y - s * 0.3);
                sparkleCtx.closePath();
                sparkleCtx.fill();
                sparkleCtx.restore();
            }
        }

        for (let i = 0; i < 18; i++) sparkles.push(new Sparkle());

        function animateSparkles() {
            sparkleCtx.clearRect(0, 0, sparkleCanvas.width, sparkleCanvas.height);
            sparkles.forEach(s => { s.update(); s.draw(); });
            requestAnimationFrame(animateSparkles);
        }
        animateSparkles();

        /* ========== SCREEN SWITCH ========== */
        function switchScreen(fromId, toId) {
            document.getElementById(fromId).classList.remove('active');
            setTimeout(() => {
                document.getElementById(toId).classList.add('active');
            }, 500);
        }

        /* ========== OPENING ========== */
        const openingScreen = document.getElementById('opening-screen');
        const openingText = document.getElementById('opening-text');
        const tapText = document.getElementById('tap-text');

        setTimeout(() => {
            openingText.style.opacity = '1';
            openingText.style.transform = 'translateY(0)';
        }, 500);

        setTimeout(() => {
            tapText.style.opacity = '1';
        }, 4500);

        openingScreen.addEventListener('click', () => {
            initAudio();
            switchScreen('opening-screen', 'welcome-screen');
            setTimeout(startCinematicReveal, 600);
        });

        /* ========== CINEMATIC NAME REVEAL ========== */
        function startCinematicReveal() {
            const name = "BLEN";
            const container = document.getElementById('name-letters');
            const nameContainer = document.getElementById('name-container');
            const message = document.getElementById('welcome-message');
            const nextBtn = document.getElementById('welcome-next');

            container.innerHTML = '';

            for (let i = 0; i < name.length; i++) {
                const span = document.createElement('span');
                span.className = 'name-letter';
                span.textContent = name[i];
                container.appendChild(span);
            }
            const heart = document.createElement('span');
            heart.className = 'name-letter heart';
            heart.textContent = '❤️';
            container.appendChild(heart);

            nameContainer.classList.add('revealed');

            try {
                revealSound.volume = volumeSlider.value * 0.7;
                revealSound.currentTime = 0;
                revealSound.play().catch(() => {});
            } catch (e) {}

            const letters = container.querySelectorAll('.name-letter');
            letters.forEach((letter, index) => {
                setTimeout(() => {
                    letter.classList.add('visible');
                    if (index === letters.length - 1) {
                        if (typeof confetti === 'function') {
                            confetti({
                                particleCount: 60,
                                spread: 70,
                                origin: { y: 0.4 },
                                colors: ['#FF4FA3', '#D4AF37', '#FFFFFF'],
                                scalar: 0.9
                            });
                        }
                    }
                }, 180 + index * 220);
            });

            setTimeout(() => {
                message.classList.add('show');
            }, 180 + letters.length * 220 + 400);

            setTimeout(() => {
                nextBtn.classList.add('show');
            }, 180 + letters.length * 220 + 1200);
        }

        document.getElementById('welcome-next').addEventListener('click', () => {
            switchScreen('welcome-screen', 'gallery-screen');
            setupCarousel();
        });

        /* ========== GALLERY ========== */
        const carousel = document.getElementById('carousel');
        const cards = document.querySelectorAll('.carousel-card');
        const totalCards = cards.length;
        let currentAngle = 0;
        let cardAngle = 360 / totalCards;
        let startX = 0;
        let isDragging = false;

        function setupCarousel() {
            const radius = Math.round((260 / 2) / Math.tan(Math.PI / totalCards)) + 20;
            cards.forEach((card, index) => {
                const angle = cardAngle * index;
                card.style.transform = `rotateY(${angle}deg) translateZ(${radius}px)`;
                
                card.addEventListener('click', () => {
                    const img = card.querySelector('img');
                    document.getElementById('lightbox-img').src = img.src;
                    document.getElementById('lightbox').classList.add('active');
                });
            });
        }

        const galleryContainer = document.querySelector('.gallery-container');
        
        galleryContainer.addEventListener('touchstart', (e) => {
            startX = e.touches[0].clientX;
            isDragging = true;
        });

        galleryContainer.addEventListener('touchmove', (e) => {
            if (!isDragging) return;
            const deltaX = e.touches[0].clientX - startX;
            carousel.style.transform = `rotateY(${currentAngle + (deltaX * 0.5)}deg)`;
        });

        galleryContainer.addEventListener('touchend', (e) => {
            if (!isDragging) return;
            const deltaX = e.changedTouches[0].clientX - startX;
            currentAngle += deltaX * 0.5;
            isDragging = false;
        });

        document.getElementById('lightbox').addEventListener('click', () => {
            document.getElementById('lightbox').classList.remove('active');
        });

        document.getElementById('gallery-next').addEventListener('click', () => {
            switchScreen('gallery-screen', 'letter-screen');
            startTypewriter();
        });

        /* ========== TYPEWRITER LETTER ========== */
        let typewriterRunning = false;

        function startTypewriter() {
            const typewriterContainer = document.getElementById('typewriter-text');
            const letterNextBtn = document.getElementById('letter-next');
            const letterText = translations.letter[currentLang];

            typewriterContainer.textContent = "";
            letterNextBtn.style.display = 'none';
            document.getElementById('cursor').style.display = 'inline-block';
            typewriterRunning = true;

            let charIndex = 0;
            function type() {
                if (!typewriterRunning) return;
                if (charIndex < letterText.length) {
                    typewriterContainer.textContent += letterText.charAt(charIndex);
                    charIndex++;
                    setTimeout(type, 40);
                } else {
                    document.getElementById('cursor').style.display = 'none';
                    letterNextBtn.style.display = 'inline-block';
                    typewriterRunning = false;
                }
            }
            type();
        }

        document.getElementById('letter-next').addEventListener('click', () => {
            switchScreen('letter-screen', 'countdown-screen');
            startCountdown();
        });

        /* ========== COUNTDOWN ========== */
        function startCountdown() {
            let count = 3;
            const timerEl = document.getElementById('countdown-timer');
            timerEl.textContent = count;
            const interval = setInterval(() => {
                count--;
                if (count > 0) {
                    timerEl.textContent = count;
                } else {
                    clearInterval(interval);
                    switchScreen('countdown-screen', 'gift-screen');
                }
            }, 1000);
        }

        /* ========== GIFT ========== */
        const giftBox = document.getElementById('gift-box');
        const openGiftBtn = document.getElementById('open-gift-btn');

        function triggerGiftOpening() {
            giftBox.classList.add('open');

            if (navigator.vibrate) navigator.vibrate([100, 50, 200]);

            if (typeof confetti === 'function') {
                confetti({
                    particleCount: 120,
                    spread: 80,
                    origin: { y: 0.6 },
                    colors: ['#FF4FA3', '#D4AF37', '#FFFFFF']
                });
            }

            setTimeout(() => {
                switchScreen('gift-screen', 'reveal-screen');
            }, 1500);
        }

        openGiftBtn.addEventListener('click', triggerGiftOpening);
        document.getElementById('gift-container').addEventListener('click', triggerGiftOpening);

        /* ========== ENDING ========== */
        document.getElementById('reveal-next').addEventListener('click', () => {
            switchScreen('reveal-screen', 'ending-screen');
        });

        /* Service Worker */
        if ('serviceWorker' in navigator) {
            window.addEventListener('load', () => {
                const swCode = `self.addEventListener('fetch', function(e) { e.respondWith(fetch(e.request)); });`;
                const blob = new Blob([swCode], { type: 'text/javascript' });
                const url = URL.createObjectURL(blob);
                navigator.serviceWorker.register(url).catch(() => {});
            });
        }
    </script>
</body>
</html>
