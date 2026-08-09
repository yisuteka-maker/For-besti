<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Exclusive VIP Gift | For BLEN ❤️</title>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@500;700;800&family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">

    <style>
        :root {
            --bg-black: #070709;
            --card-glass: rgba(18, 18, 24, 0.65);
            --card-border: rgba(255, 255, 255, 0.08);
            --accent-pink: #ff3366;
            --accent-pink-glow: rgba(255, 51, 102, 0.35);
            --accent-gold: #ffd700;
            --accent-gold-glow: rgba(255, 215, 0, 0.25);
            --text-primary: #f8f9fa;
            --text-secondary: #a0a5b5;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Plus Jakarta Sans', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--bg-black);
            color: var(--text-primary);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
            background-image: 
                radial-gradient(circle at 10% 10%, rgba(255, 51, 102, 0.08) 0%, transparent 40%),
                radial-gradient(circle at 90% 80%, rgba(255, 215, 0, 0.06) 0%, transparent 40%);
            background-attachment: fixed;
        }

        /* --- PASSWORD LOCK SCREEN --- */
        #password-screen {
            position: fixed;
            inset: 0;
            z-index: 99999;
            background: rgba(7, 7, 9, 0.96);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            transition: opacity 0.8s cubic-bezier(0.16, 1, 0.3, 1), transform 0.8s cubic-bezier(0.16, 1, 0.3, 1);
        }

        #password-screen.unlocked {
            opacity: 0;
            transform: scale(1.08);
            pointer-events: none;
        }

        .pass-card {
            background: var(--card-glass);
            border: 1px solid rgba(255, 255, 255, 0.12);
            padding: 35px 25px;
            border-radius: 28px;
            width: 100%;
            max-width: 400px;
            text-align: center;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.8), 0 0 30px var(--accent-pink-glow);
            position: relative;
            overflow: hidden;
        }

        .pass-card::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0;
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--accent-pink), var(--accent-gold), transparent);
        }

        .pass-icon {
            width: 70px;
            height: 70px;
            margin: 0 auto 20px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--accent-pink), #b3003b);
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 1.8rem;
            color: #fff;
            box-shadow: 0 0 25px var(--accent-pink-glow);
            animation: heartPulse 2.2s infinite ease-in-out;
        }

        @keyframes heartPulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.08); }
        }

        .pass-card h2 {
            font-family: 'Cinzel', serif;
            font-size: 1.6rem;
            letter-spacing: 1px;
            margin-bottom: 8px;
            background: linear-gradient(135deg, #ffffff, #dcdcdc);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .pass-card p {
            font-size: 0.88rem;
            color: var(--text-secondary);
            margin-bottom: 25px;
        }

        .input-group {
            position: relative;
            margin-bottom: 20px;
        }

        .pass-input {
            width: 100%;
            padding: 14px 18px;
            border-radius: 14px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.15);
            color: #fff;
            font-size: 1rem;
            outline: none;
            text-align: center;
            letter-spacing: 2px;
            transition: all 0.3s ease;
        }

        .pass-input:focus {
            border-color: var(--accent-pink);
            box-shadow: 0 0 15px var(--accent-pink-glow);
            background: rgba(255, 255, 255, 0.08);
        }

        .pass-btn {
            width: 100%;
            padding: 14px;
            border-radius: 14px;
            border: none;
            background: linear-gradient(135deg, var(--accent-pink), #d81b60);
            color: #fff;
            font-weight: 600;
            font-size: 0.95rem;
            letter-spacing: 1px;
            cursor: pointer;
            box-shadow: 0 6px 20px var(--accent-pink-glow);
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .pass-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px var(--accent-pink-glow);
        }

        .error-msg {
            color: #ff4d4d;
            font-size: 0.82rem;
            margin-top: 12px;
            display: none;
            animation: shake 0.4s ease;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            20%, 60% { transform: translateX(-8px); }
            40%, 80% { transform: translateX(8px); }
        }

        /* --- MAIN CONTENT WRAPPER --- */
        .main-wrapper {
            width: 100%;
            max-width: 620px;
            margin: 0 auto;
            padding: 25px 16px 80px 16px;
            display: flex;
            flex-direction: column;
            gap: 32px;
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 1s ease 0.3s, transform 1s ease 0.3s;
        }

        .main-wrapper.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* --- HEADER SECTION --- */
        header {
            text-align: center;
            padding: 35px 20px 25px 20px;
            background: var(--card-glass);
            border: 1px solid var(--card-border);
            border-radius: 28px;
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5);
            position: relative;
            overflow: hidden;
        }

        .vip-badge {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            background: linear-gradient(135deg, rgba(255, 215, 0, 0.15), rgba(255, 51, 102, 0.15));
            border: 1px solid var(--accent-gold);
            color: var(--accent-gold);
            font-size: 0.72rem;
            font-weight: 700;
            letter-spacing: 2px;
            padding: 6px 16px;
            border-radius: 30px;
            text-transform: uppercase;
            margin-bottom: 16px;
            box-shadow: 0 0 15px var(--accent-gold-glow);
        }

        header h1 {
            font-family: 'Cinzel', serif;
            font-size: 2.1rem;
            font-weight: 700;
            background: linear-gradient(135deg, #ffffff 40%, var(--accent-pink) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 10px;
            line-height: 1.25;
        }

        header p {
            color: var(--text-secondary);
            font-size: 0.92rem;
            letter-spacing: 0.5px;
        }

        /* --- CUSTOM MUSIC PLAYER --- */
        .music-player-card {
            background: var(--card-glass);
            border: 1px solid var(--card-border);
            border-radius: 24px;
            padding: 22px;
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            box-shadow: 0 12px 30px rgba(0,0,0,0.5);
            display: flex;
            flex-direction: column;
            gap: 16px;
        }

        .music-top {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .music-meta {
            display: flex;
            align-items: center;
            gap: 14px;
        }

        .disc-icon {
            width: 48px;
            height: 48px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--accent-pink), var(--accent-gold));
            display: flex;
            justify-content: center;
            align-items: center;
            color: #fff;
            font-size: 1.2rem;
            box-shadow: 0 0 20px var(--accent-pink-glow);
            transition: transform 0.5s linear;
        }

        .disc-icon.spinning {
            animation: spin 4s linear infinite;
        }

        @keyframes spin {
            100% { transform: rotate(360deg); }
        }

        .music-info h3 {
            font-size: 1rem;
            font-weight: 600;
            color: #fff;
        }

        .music-info p {
            font-size: 0.8rem;
            color: var(--text-secondary);
        }

        .visualizer {
            display: flex;
            align-items: flex-end;
            gap: 4px;
            height: 22px;
        }

        .v-bar {
            width: 3px;
            background: var(--accent-pink);
            border-radius: 3px;
            height: 4px;
            transition: height 0.2s ease;
        }

        .playing .v-bar {
            animation: bounceBar 1.2s infinite ease-in-out alternate;
        }

        .playing .v-bar:nth-child(1) { animation-delay: 0.1s; }
        .playing .v-bar:nth-child(2) { animation-delay: 0.3s; }
        .playing .v-bar:nth-child(3) { animation-delay: 0.2s; }
        .playing .v-bar:nth-child(4) { animation-delay: 0.5s; }
        .playing .v-bar:nth-child(5) { animation-delay: 0.4s; }

        @keyframes bounceBar {
            0% { height: 4px; }
            100% { height: 20px; background: var(--accent-gold); }
        }

        .music-controls {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .play-btn {
            width: 44px;
            height: 44px;
            border-radius: 50%;
            border: none;
            background: var(--accent-pink);
            color: #fff;
            font-size: 1.1rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 15px var(--accent-pink-glow);
            transition: transform 0.2s ease;
            flex-shrink: 0;
        }

        .play-btn:active {
            transform: scale(0.92);
        }

        .progress-bar-container {
            flex-grow: 1;
            display: flex;
            flex-direction: column;
            gap: 6px;
        }

        .progress-bar {
            width: 100%;
            height: 5px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            width: 0%;
            background: linear-gradient(90deg, var(--accent-pink), var(--accent-gold));
            border-radius: 10px;
            transition: width 0.1s linear;
        }

        .time-display {
            display: flex;
            justify-content: space-between;
            font-size: 0.72rem;
            color: var(--text-secondary);
        }

        /* --- HEARTFELT LETTER CARD --- */
        .letter-card {
            background: var(--card-glass);
            border: 1px solid var(--card-border);
            border-radius: 28px;
            padding: 32px 24px;
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5);
            position: relative;
        }

        .letter-card::before {
            content: '“';
            position: absolute;
            top: 15px;
            right: 25px;
            font-family: 'Cinzel', serif;
            font-size: 5rem;
            color: rgba(255, 255, 255, 0.03);
            line-height: 1;
            pointer-events: none;
        }

        .section-header {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 22px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.08);
            padding-bottom: 14px;
        }

        .section-header i {
            color: var(--accent-pink);
            font-size: 1.2rem;
        }

        .section-header h2 {
            font-family: 'Cinzel', serif;
            font-size: 1.35rem;
            color: var(--accent-gold);
            letter-spacing: 0.5px;
        }

        .letter-text {
            font-size: 0.96rem;
            line-height: 1.85;
            color: #e2e8f0;
            display: flex;
            flex-direction: column;
            gap: 16px;
            text-align: left;
        }

        .letter-text p span.highlight {
            color: var(--accent-pink);
            font-weight: 600;
        }

        .letter-text p span.amharic {
            color: #ffe0b2;
            font-weight: 500;
        }

        /* --- PHOTO CARDS SECTION --- */
        .card-grid {
            display: flex;
            flex-direction: column;
            gap: 30px;
        }

        .photo-card {
            background: var(--card-glass);
            border: 1px solid var(--card-border);
            border-radius: 28px;
            padding: 24px;
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            box-shadow: 0 15px 35px rgba(0,0,0,0.5);
            transition: transform 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
        }

        .img-frame {
            width: 100%;
            border-radius: 20px;
            overflow: hidden;
            position: relative;
            background: #121216;
            box-shadow: 0 10px 25px rgba(0,0,0,0.7);
            cursor: pointer;
        }

        .img-frame img {
            width: 100%;
            height: auto;
            max-height: 480px;
            object-fit: cover;
            display: block;
            transition: transform 0.6s ease;
        }

        .img-frame:hover img {
            transform: scale(1.04);
        }

        .tap-hint {
            position: absolute;
            bottom: 12px;
            right: 12px;
            background: rgba(0, 0, 0, 0.65);
            backdrop-filter: blur(8px);
            color: #fff;
            font-size: 0.72rem;
            padding: 6px 12px;
            border-radius: 20px;
            display: flex;
            align-items: center;
            gap: 6px;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .caption-box {
            margin-top: 18px;
            text-align: center;
        }

        .caption-box p {
            font-size: 0.92rem;
            color: var(--text-secondary);
            line-height: 1.6;
        }

        .caption-box span.amharic-sub {
            display: block;
            margin-top: 6px;
            color: var(--accent-pink);
            font-size: 0.88rem;
            font-weight: 500;
        }

        /* --- SURPRISE BUTTON & MODAL --- */
        .surprise-wrapper {
            background: linear-gradient(135deg, rgba(255, 51, 102, 0.12), rgba(255, 215, 0, 0.08));
            border: 1px solid var(--accent-pink-glow);
            border-radius: 28px;
            padding: 30px 20px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
        }

        .surprise-wrapper h3 {
            font-family: 'Cinzel', serif;
            color: var(--accent-gold);
            font-size: 1.3rem;
            margin-bottom: 8px;
        }

        .surprise-wrapper p {
            font-size: 0.88rem;
            color: var(--text-secondary);
            margin-bottom: 20px;
        }

        .open-surprise-btn {
            background: linear-gradient(135deg, var(--accent-pink), #d81b60);
            color: #fff;
            border: none;
            padding: 15px 34px;
            border-radius: 30px;
            font-weight: 700;
            font-size: 0.95rem;
            letter-spacing: 0.5px;
            cursor: pointer;
            box-shadow: 0 8px 25px var(--accent-pink-glow);
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 10px;
        }

        .open-surprise-btn:hover {
            transform: translateY(-3px) scale(1.02);
            box-shadow: 0 12px 30px var(--accent-pink-glow);
        }

        /* Modal Overlay */
        #surprise-modal {
            position: fixed;
            inset: 0;
            z-index: 999999;
            background: rgba(5, 5, 8, 0.92);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.5s ease;
        }

        #surprise-modal.active {
            opacity: 1;
            pointer-events: auto;
        }

        .modal-card {
            background: var(--card-glass);
            border: 1px solid rgba(255, 215, 0, 0.25);
            padding: 35px 25px;
            border-radius: 30px;
            width: 100%;
            max-width: 440px;
            text-align: center;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.9), 0 0 40px var(--accent-gold-glow);
            transform: scale(0.85);
            transition: transform 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
        }

        #surprise-modal.active .modal-card {
            transform: scale(1);
        }

        .modal-heart-icon {
            font-size: 3.2rem;
            color: var(--accent-pink);
            margin-bottom: 15px;
            animation: heartPulse 1.8s infinite ease-in-out;
            display: inline-block;
            filter: drop-shadow(0 0 15px var(--accent-pink));
        }

        .modal-card h2 {
            font-family: 'Cinzel', serif;
            color: var(--accent-gold);
            font-size: 1.6rem;
            margin-bottom: 14px;
        }

        .modal-card p {
            font-size: 0.95rem;
            line-height: 1.7;
            color: #f1f5f9;
            margin-bottom: 25px;
        }

        .close-modal-btn {
            background: rgba(255, 255, 255, 0.1);
            color: #fff;
            border: 1px solid rgba(255, 255, 255, 0.2);
            padding: 12px 28px;
            border-radius: 25px;
            font-weight: 600;
            font-size: 0.88rem;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .close-modal-btn:hover {
            background: rgba(255, 255, 255, 0.2);
        }

        /* Lightbox Image Viewer */
        #lightbox-modal {
            position: fixed;
            inset: 0;
            z-index: 999999;
            background: rgba(0, 0, 0, 0.95);
            backdrop-filter: blur(15px);
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.4s ease;
        }

        #lightbox-modal.active {
            opacity: 1;
            pointer-events: auto;
        }

        #lightbox-img {
            max-width: 95%;
            max-height: 85vh;
            border-radius: 16px;
            box-shadow: 0 0 35px rgba(255, 51, 102, 0.3);
            object-fit: contain;
        }

        .lightbox-close {
            position: absolute;
            top: 25px;
            right: 25px;
            color: #fff;
            font-size: 2rem;
            cursor: pointer;
            width: 44px;
            height: 44px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
        }

        /* --- FOOTER --- */
        footer {
            text-align: center;
            margin-top: 10px;
            color: var(--text-secondary);
            font-size: 0.8rem;
            letter-spacing: 1px;
        }

        /* --- FLOATING HEARTS PARTICLES --- */
        .floating-heart {
            position: fixed;
            color: var(--accent-pink);
            pointer-events: none;
            z-index: 99999;
            animation: floatAndFade 2.5s cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
            font-size: 20px;
            filter: drop-shadow(0 0 6px var(--accent-pink));
        }

        @keyframes floatAndFade {
            0% {
                opacity: 1;
                transform: translateY(0) scale(0.8) rotate(0deg);
            }
            100% {
                opacity: 0;
                transform: translateY(-140px) scale(1.5) rotate(25deg);
            }
        }

        /* Responsive Breakpoints */
        @media (max-width: 480px) {
            header h1 { font-size: 1.7rem; }
            .pass-card { padding: 30px 20px; }
            .letter-card { padding: 26px 18px; }
            .section-header h2 { font-size: 1.2rem; }
            .music-player-card { padding: 18px; }
        }
    </style>
</head>
<body>

    <!-- PASSWORD LOCK OVERLAY -->
    <div id="password-screen">
        <div class="pass-card">
            <div class="pass-icon">
                <i class="fas fa-lock"></i>
            </div>
            <h2>VIP ENTRY</h2>
            <p>Enter the private key to unlock BLEN's gift</p>
            
            <form onsubmit="handlePasswordSubmit(event)">
                <div class="input-group">
                    <input type="password" id="passInput" class="pass-input" placeholder="•••••••••" autocomplete="off" required>
                </div>
                <button type="submit" class="pass-btn">
                    <span>Unlock Gift</span>
                    <i class="fas fa-key"></i>
                </button>
            </form>
            <div id="errorMsg" class="error-msg">Incorrect Passcode. Try again!</div>
        </div>
    </div>

    <!-- MAIN VIP CONTENT WRAPPER -->
    <div class="main-wrapper" id="mainWrapper">

        <!-- HEADER -->
        <header>
            <div class="vip-badge">
                <i class="fas fa-crown"></i>
                <span>Private VIP Gift</span>
            </div>
            <h1>Special VIP Gift | BLEN ❤️</h1>
            <p>Curated with deep appreciation & eternal memories</p>
        </header>

        <!-- CUSTOM MUSIC PLAYER -->
        <div class="music-player-card">
            <div class="music-top">
                <div class="music-meta">
                    <div class="disc-icon" id="discIcon">
                        <i class="fas fa-music"></i>
                    </div>
                    <div class="music-info">
                        <h3>Special Atmosphere</h3>
                        <p>Background Soundtrack</p>
                    </div>
                </div>
                <!-- Equalizer Visualizer -->
                <div class="visualizer" id="visualizer">
                    <div class="v-bar"></div>
                    <div class="v-bar"></div>
                    <div class="v-bar"></div>
                    <div class="v-bar"></div>
                    <div class="v-bar"></div>
                </div>
            </div>

            <div class="music-controls">
                <button class="play-btn" id="playBtn" onclick="togglePlayPause()">
                    <i class="fas fa-play" id="playIcon"></i>
                </button>
                <div class="progress-bar-container">
                    <div class="progress-bar" id="progressBar" onclick="seekAudio(event)">
                        <div class="progress-fill" id="progressFill"></div>
                    </div>
                    <div class="time-display">
                        <span id="currentTime">0:00</span>
                        <span id="durationTime">0:00</span>
                    </div>
                </div>
            </div>
            <!-- Audio Tag using existing file -->
            <audio id="bgAudio" loop preload="auto">
                <source src="music.mp3" type="audio/mpeg">
            </audio>
        </div>

        <!-- HEARTFELT LETTER SECTION -->
        <div class="letter-card">
            <div class="section-header">
                <i class="fas fa-envelope-open-text"></i>
                <h2>To My Dearest Blen</h2>
            </div>
            <div class="letter-text">
                <p>
                    Some people enter our lives and subtly make everything brighter without even trying. <span class="highlight">Dearest Blen</span>, you are genuinely one of those rare souls. From the very beginning, your presence has brought an irreplaceable warmth and genuine light into my world.
                </p>
                <p>
                    <span class="amharic">የኔ ልዩ</span>, words often fall short when trying to express how much I appreciate you. Your kindness, your laughter, and the authentic grace you carry in everything you do are qualities I deeply admire. Knowing you has been a true blessing, and every memory we share holds a special place in my heart.
                </p>
                <p>
                    I put my genuine effort into crafting this VIP digital gift specifically for you because standard words weren't enough. <span class="amharic">አብረን ያሳለፍናቸው ቀናት እና የምንጋራቸው ውብ ትዝታዎች በልቤ ውስጥ ለዘላለም የታተሙ ናቸው።</span> Every line of code and detail here was built with pure care and gratitude.
                </p>
                <p>
                    Thank you for simply being who you are — authentic, thoughtful, and wonderful. As time moves forward, my greatest hope is to see you achieve every single dream in your heart, to share countless more joyful moments, and to always be a steadfast friend in your corner. <span class="amharic">ሁልጊዜም በህይወትሽ ውስጥ ደስታና ስኬት እንዲበዛልሽ እመኛለሁ!</span> ❤️
                </p>
            </div>
        </div>

        <!-- PHOTO GALLERY CARDS -->
        <div class="card-grid">

            <!-- PHOTO 1: my besti .jpg -->
            <div class="photo-card">
                <div class="section-header">
                    <i class="fas fa-heart"></i>
                    <h2>My Besti ✨</h2>
                </div>
                <div class="img-frame" onclick="openLightbox('my%20besti%20.jpg')">
                    <img src="my%20besti%20.jpg" alt="My Besti">
                    <div class="tap-hint">
                        <i class="fas fa-expand"></i> Tap to expand
                    </div>
                </div>
                <div class="caption-box">
                    <p>A truly cherished person who adds magic and brightness to everyday moments.</p>
                    <span class="amharic-sub">"ለኔ ሁልጊዜም ልዩ እና ውድ የሆንሽ ጓደኛዬ!"</span>
                </div>
            </div>

            <!-- PHOTO 2: besti pic.jpg -->
            <div class="photo-card">
                <div class="section-header">
                    <i class="fas fa-camera"></i>
                    <h2>Our Best Memory ❤️</h2>
                </div>
                <div class="img-frame" onclick="openLightbox('besti%20pic.jpg')">
                    <img src="besti%20pic.jpg" alt="Best Memory With Blen">
                    <div class="tap-hint">
                        <i class="fas fa-expand"></i> Tap to expand
                    </div>
                </div>
                <div class="caption-box">
                    <p>A captured moment suspended in time, filled with warmth and genuine joy.</p>
                    <span class="amharic-sub">"ያሳለፍነው ይህ ውብ አጋጣሚ ሁልጊዜም በልቤ ውስጥ ትልቅ ቦታ አለው።"</span>
                </div>
            </div>

            <!-- PHOTO 3: 20260809_232425.jpg -->
            <div class="photo-card">
                <div class="section-header">
                    <i class="fas fa-sparkles" style="color: var(--accent-gold);"></i>
                    <h2>Precious Moments 💫</h2>
                </div>
                <div class="img-frame" onclick="openLightbox('20260809_232425.jpg')">
                    <img src="20260809_232425.jpg" alt="Special Snapshot">
                    <div class="tap-hint">
                        <i class="fas fa-expand"></i> Tap to expand
                    </div>
                </div>
                <div class="caption-box">
                    <p>Every small memory built together becomes a timeless treasure.</p>
                    <span class="amharic-sub">"የማይረሱ ውብ አጋጣሚዎች ሁልጊዜም አብረውን ይኖራሉ።"</span>
                </div>
            </div>

            <!-- PHOTO 4: for expectashn .jpg -->
            <div class="photo-card" style="border-color: rgba(255, 215, 0, 0.15);">
                <div class="section-header">
                    <i class="fas fa-star" style="color: var(--accent-gold);"></i>
                    <h2 style="color: #fff;">The Future I Hope For ✨</h2>
                </div>
                <div class="img-frame" onclick="openLightbox('for%20expectashn%20.jpg')">
                    <img src="for%20expectashn%20.jpg" alt="Future Expectations">
                    <div class="tap-hint">
                        <i class="fas fa-expand"></i> Tap to expand
                    </div>
                </div>
                <div class="caption-box">
                    <p>Looking ahead to a future of boundless growth, happiness, and shared victories.</p>
                    <span class="amharic-sub">"ወደፊት አብረን ይበልጥ እንደምናድግና ትልልቅ ስኬቶችን እንደምንጨብጥ ሙሉ እምነት አለኝ።"</span>
                </div>
            </div>

        </div>

        <!-- INTERACTIVE SURPRISE MODAL TRIGGER -->
        <div class="surprise-wrapper">
            <h3>A Little Extra Surprise</h3>
            <p>Tap the button below to reveal a final personal message</p>
            <button class="open-surprise-btn" onclick="openSurpriseModal()">
                <i class="fas fa-gift"></i>
                <span>Open Surprise 🎁</span>
            </button>
        </div>

        <!-- FOOTER -->
        <footer>
            <p>DESIGNED EXCLUSIVELY FOR BLEN • VIP EDITION</p>
        </footer>

    </div>

    <!-- CUSTOM SURPRISE MODAL -->
    <div id="surprise-modal">
        <div class="modal-card">
            <i class="fas fa-heart modal-heart-icon"></i>
            <h2>You Are Truly Precious ✨</h2>
            <p>
                Dear Blen, thank you for being an exceptional person. <br><br>
                <span style="color: #ffe0b2;">"ይህ ትንሽ ስጦታ ላንቺ ያለኝን ጥልቅ አክብሮትና ፍቅር ለማሳየት የተዘጋጀ ነው። Always remember how deeply loved and appreciated you are!"</span>
            </p>
            <button class="close-modal-btn" onclick="closeSurpriseModal()">Close with Love ❤️</button>
        </div>
    </div>

    <!-- LIGHTBOX IMAGE MODAL -->
    <div id="lightbox-modal" onclick="closeLightbox()">
        <span class="lightbox-close">&times;</span>
        <img id="lightbox-img" src="" alt="Enlarged View">
    </div>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        // --- PASSWORD SYSTEM ---
        const SECRET_PASS = "anchi#komata";

        function handlePasswordSubmit(e) {
            e.preventDefault();
            const input = document.getElementById('passInput').value.trim();
            const errorMsg = document.getElementById('errorMsg');
            const passScreen = document.getElementById('password-screen');
            const mainWrapper = document.getElementById('mainWrapper');

            if (input === SECRET_PASS) {
                errorMsg.style.display = 'none';
                passScreen.classList.add('unlocked');
                mainWrapper.classList.add('visible');

                // Try playing audio after user interaction unlock
                const audio = document.getElementById('bgAudio');
                audio.play().then(() => {
                    updatePlayerUI(true);
                }).catch(() => {
                    updatePlayerUI(false);
                });
            } else {
                errorMsg.style.display = 'block';
                const inputEl = document.getElementById('passInput');
                inputEl.style.borderColor = '#ff4d4d';
                setTimeout(() => {
                    inputEl.style.borderColor = 'rgba(255, 255, 255, 0.15)';
                }, 1000);
            }
        }

        // --- MUSIC PLAYER LOGIC ---
        const audio = document.getElementById('bgAudio');
        const playBtn = document.getElementById('playBtn');
        const playIcon = document.getElementById('playIcon');
        const discIcon = document.getElementById('discIcon');
        const visualizer = document.getElementById('visualizer');
        const progressFill = document.getElementById('progressFill');
        const currentTimeEl = document.getElementById('currentTime');
        const durationTimeEl = document.getElementById('durationTime');

        function togglePlayPause() {
            if (audio.paused) {
                audio.play().then(() => {
                    updatePlayerUI(true);
                }).catch(err => console.log("Playback blocked:", err));
            } else {
                audio.pause();
                updatePlayerUI(false);
            }
        }

        function updatePlayerUI(isPlaying) {
            if (isPlaying) {
                playIcon.className = "fas fa-pause";
                discIcon.classList.add('spinning');
                visualizer.classList.add('playing');
            } else {
                playIcon.className = "fas fa-play";
                discIcon.classList.remove('spinning');
                visualizer.classList.remove('playing');
            }
        }

        audio.addEventListener('timeupdate', () => {
            if (audio.duration) {
                const pct = (audio.currentTime / audio.duration) * 100;
                progressFill.style.width = pct + '%';
                currentTimeEl.textContent = formatTime(audio.currentTime);
                durationTimeEl.textContent = formatTime(audio.duration);
            }
        });

        function seekAudio(e) {
            const bar = document.getElementById('progressBar');
            const rect = bar.getBoundingClientRect();
            const clickX = e.clientX - rect.left;
            const width = rect.width;
            if (audio.duration) {
                audio.currentTime = (clickX / width) * audio.duration;
            }
        }

        function formatTime(sec) {
            const m = Math.floor(sec / 60);
            const s = Math.floor(sec % 60);
            return `${m}:${s < 10 ? '0' : ''}${s}`;
        }

        // --- SURPRISE MODAL LOGIC ---
        function openSurpriseModal() {
            const modal = document.getElementById('surprise-modal');
            modal.classList.add('active');
            triggerHeartBurst();
        }

        function closeSurpriseModal() {
            const modal = document.getElementById('surprise-modal');
            modal.classList.remove('active');
        }

        // --- LIGHTBOX IMAGE LOGIC ---
        function openLightbox(imgSrc) {
            const modal = document.getElementById('lightbox-modal');
            const img = document.getElementById('lightbox-img');
            img.src = imgSrc;
            modal.classList.add('active');
        }

        function closeLightbox() {
            document.getElementById('lightbox-modal').classList.remove('active');
        }

        // --- FLOATING HEARTS ON TAP ---
        document.addEventListener('click', function(e) {
            if (e.target.tagName === 'INPUT' || e.target.tagName === 'BUTTON') return;
            createFloatingHeart(e.clientX, e.clientY);
        });

        function createFloatingHeart(x, y) {
            const heart = document.createElement('div');
            heart.className = 'floating-heart';
            heart.innerHTML = '❤️';
            heart.style.left = (x - 10) + 'px';
            heart.style.top = (y - 10) + 'px';
            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 2500);
        }

        function triggerHeartBurst() {
            for (let i = 0; i < 18; i++) {
                setTimeout(() => {
                    const x = window.innerWidth / 2 + (Math.random() * 240 - 120);
                    const y = window.innerHeight / 2 + (Math.random() * 240 - 120);
                    createFloatingHeart(x, y);
                }, i * 70);
            }
        }
    </script>
</body>
</html>
