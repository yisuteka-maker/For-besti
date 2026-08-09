<!DOCTYPE html>
<html lang="am">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Special VIP Gift | BLEN ❤️</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --bg-dark: #050505;
            --bg-card: rgba(255, 255, 255, 0.04);
            --border-color: rgba(255, 255, 255, 0.09);
            --accent-pink: #ff4b72;
            --accent-glow: rgba(255, 75, 114, 0.4);
            --gold: #ffd700;
            --text-main: #f0f0f0;
            --text-sub: #b0b0b0;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--bg-dark);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            overflow-x: hidden;
            padding: 20px 15px 80px 15px;
            position: relative;
        }

        /* Glowing Background Lighting */
        .bg-glow {
            position: fixed;
            width: 320px;
            height: 320px;
            border-radius: 50%;
            background: radial-gradient(circle, var(--accent-glow) 0%, transparent 70%);
            top: -100px;
            left: -100px;
            z-index: 0;
            pointer-events: none;
        }

        .bg-glow-2 {
            position: fixed;
            width: 350px;
            height: 350px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(255, 215, 0, 0.15) 0%, transparent 70%);
            bottom: -100px;
            right: -100px;
            z-index: 0;
            pointer-events: none;
        }

        .container {
            width: 100%;
            max-width: 550px;
            z-index: 1;
            display: flex;
            flex-direction: column;
            gap: 25px;
        }

        /* Header Section */
        header {
            text-align: center;
            padding: 28px 18px;
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 24px;
            backdrop-filter: blur(16px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.6);
            position: relative;
            overflow: hidden;
        }

        header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: linear-gradient(90deg, transparent, var(--accent-pink), var(--gold), transparent);
        }

        .badge {
            display: inline-block;
            background: linear-gradient(135deg, var(--accent-pink), #e63956);
            color: #fff;
            font-size: 0.75rem;
            font-weight: 700;
            letter-spacing: 2px;
            padding: 5px 14px;
            border-radius: 20px;
            text-transform: uppercase;
            margin-bottom: 12px;
            box-shadow: 0 4px 12px var(--accent-glow);
        }

        header h1 {
            font-size: 1.9rem;
            font-weight: 800;
            background: linear-gradient(135deg, #fff 30%, #e0e0e0 60%, var(--accent-pink));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 8px;
        }

        header p {
            color: var(--text-sub);
            font-size: 0.95rem;
        }

        /* Music Player Section */
        .music-card {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            padding: 18px;
            backdrop-filter: blur(12px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.5);
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .music-header {
            display: flex;
            align-items: center;
            gap: 14px;
        }

        .music-icon {
            width: 44px;
            height: 44px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--accent-pink), var(--gold));
            display: flex;
            justify-content: center;
            align-items: center;
            color: #fff;
            font-size: 1.2rem;
            box-shadow: 0 4px 15px var(--accent-glow);
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.06); }
            100% { transform: scale(1); }
        }

        .music-info h3 {
            font-size: 1rem;
            color: #fff;
        }

        .music-info p {
            font-size: 0.8rem;
            color: var(--text-sub);
        }

        audio {
            width: 100%;
            height: 40px;
            border-radius: 8px;
            outline: none;
        }

        /* Long Letter Section */
        .letter-card {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 24px;
            padding: 26px 22px;
            backdrop-filter: blur(16px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            position: relative;
        }

        .letter-title {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.25rem;
            font-weight: 700;
            color: var(--gold);
            margin-bottom: 16px;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 10px;
        }

        .letter-body {
            font-size: 0.95rem;
            line-height: 1.8;
            color: #e0e0e0;
            text-align: justify;
            display: flex;
            flex-direction: column;
            gap: 14px;
        }

        .letter-body p {
            text-indent: 15px;
        }

        .letter-highlight {
            color: var(--accent-pink);
            font-weight: 600;
        }

        /* Image Cards */
        .card {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 24px;
            padding: 20px;
            backdrop-filter: blur(12px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            transition: transform 0.3s ease, border-color 0.3s ease;
        }

        .card:hover {
            transform: translateY(-4px);
            border-color: rgba(255, 75, 114, 0.4);
        }

        .card-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 16px;
            padding-bottom: 10px;
            border-bottom: 1px solid var(--border-color);
        }

        .card-title {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.15rem;
            font-weight: 700;
            color: #fff;
        }

        .card-title i {
            color: var(--accent-pink);
        }

        .img-container {
            width: 100%;
            border-radius: 16px;
            overflow: hidden;
            background: #1a1a1a;
            box-shadow: 0 8px 20px rgba(0,0,0,0.6);
        }

        .img-container img {
            width: 100%;
            height: auto;
            max-height: 500px;
            object-fit: cover;
            display: block;
            transition: transform 0.5s ease;
        }

        .card:hover .img-container img {
            transform: scale(1.03);
        }

        .card-caption {
            margin-top: 14px;
            font-size: 0.92rem;
            color: var(--text-sub);
            line-height: 1.6;
            text-align: center;
        }

        /* Interactive Surprise Section */
        .interactive-box {
            background: linear-gradient(135deg, rgba(255, 75, 114, 0.15), rgba(255, 215, 0, 0.08));
            border: 1px solid var(--accent-glow);
            border-radius: 22px;
            padding: 25px;
            text-align: center;
            box-shadow: 0 8px 25px rgba(0,0,0,0.4);
        }

        .interactive-box h3 {
            color: var(--gold);
            font-size: 1.2rem;
            margin-bottom: 8px;
        }

        .interactive-box p {
            font-size: 0.88rem;
            color: #ddd;
            margin-bottom: 18px;
        }

        .btn-action {
            background: linear-gradient(135deg, var(--accent-pink), #e63956);
            color: white;
            border: none;
            padding: 14px 28px;
            border-radius: 30px;
            font-weight: 700;
            font-size: 0.95rem;
            cursor: pointer;
            box-shadow: 0 4px 18px var(--accent-glow);
            transition: transform 0.2s ease, box-shadow 0.2s ease;
            display: inline-flex;
            align-items: center;
            gap: 10px;
        }

        .btn-action:active {
            transform: scale(0.95);
        }

        footer {
            text-align: center;
            margin-top: 10px;
            color: #666;
            font-size: 0.82rem;
        }

        /* Floating Hearts Particles */
        .heart-particle {
            position: fixed;
            color: var(--accent-pink);
            font-size: 22px;
            pointer-events: none;
            animation: floatUp 2.5s ease-out forwards;
            z-index: 9999;
        }

        @keyframes floatUp {
            0% {
                opacity: 1;
                transform: translateY(0) scale(1) rotate(0deg);
            }
            100% {
                opacity: 0;
                transform: translateY(-130px) scale(1.6) rotate(25deg);
            }
        }
    </style>
</head>
<body>

    <div class="bg-glow"></div>
    <div class="bg-glow-2"></div>

    <div class="container">

        <!-- Header -->
        <header>
            <span class="badge">Exclusive VIP Gift</span>
            <h1>Special VIP Gift | BLEN ❤️</h1>
            <p>Unforgettable Moments & Eternal Memories</p>
        </header>

        <!-- Music Player Section -->
        <div class="music-card">
            <div class="music-header">
                <div class="music-icon">
                    <i class="fas fa-music"></i>
                </div>
                <div class="music-info">
                    <h3>Special Soundtrack</h3>
                    <p>Playing background melody: music.mp3</p>
                </div>
            </div>
            <audio controls loop preload="auto">
                <source src="music.mp3" type="audio/mpeg">
                Your browser does not support audio element.
            </audio>
        </div>

        <!-- Comprehensive Special Letter (~2000+ Characters) -->
        <div class="letter-card">
            <div class="letter-title">
                <i class="fas fa-envelope-open-text"></i>
                <span>ለእሷ የተጻፈ ልዩ መልእክት (A Heartfelt Letter)</span>
            </div>
            <div class="letter-body">
                <p>
                    <span class="letter-highlight">ውድ ብሌን (Blen)፤</span> በህይወታችን ውስጥ ብዙ ሰዎች ይመጣሉ ይሄዳሉ፤ አንዳንዶቹ ግን መጥተው በልባችን ውስጥ የማይጠፋ ትልቅ አሻራ ጥለው ያልፋሉ። ላንቺ ያለኝ ቦታ እና ክብር ከምንም በላይ ልዩ ነው። ይህ የዲጂታል ማስታወሻ የተዘጋጀው ላንቺ ያለኝን ጥልቅ አክብሮት፣ ፍቅር እና አድናቆት ገላጭ ይሆን ዘንድ ነው።
                </p>
                <p>
                    አብረን ያሳለፍናቸው ጊዜያት፣ ፈገግታዎችሽ፣ እና የምንጋራቸው ውብ ትዝታዎች በሙሉ ለኔ ሁሌም በልቤ ውስጥ የሚታደሱ ውድ ሀብቶቼ ናቸው። ህይወት በማንኛውም መንገድ ቢሄድ፣ አጠገቤ በመሆንሽ እና በህይወቴ ውስጥ በመኖሬ የተሰማኝን ደስታ በቃላት መግለጽ ይከብደኛል። በየቀኑ የምታሳዪው ደግነት እና አዎንታዊ ህልም ለኔ ትልቅ ብርታት ነው።
                </p>
                <p>
                    <span class="letter-highlight">Best Memorial:</span> አብረን ያሳለፍናቸው ቀናት እና ትዝታዎች በስዕል ብቻ ሳይሆን በልቤ ውስጥ ለዘላለም የታተሙ ናቸው። ያሳለፍናቸው ውብ ጊዜያት ሁሌም ወደ ኋላ እየተመለስኩ ሳስባቸው በፊቴ ላይ ትልቅ ፈገግታ ያመጣሉ።
                </p>
                <p>
                    <span class="letter-highlight">Future Expectation:</span> ወደፊት በሚጠብቁን ቀናት ደግሞ አብረን ይበልጥ እንደምናድግ፣ ትልልቅ ህልሞቻችንን እንደምናሳካ እና ከዚህ በላይ የተዋቡ አዳዲስ ስኬቶችንና ትዝታዎችን እንደምንፈጥር ሙሉ እምነት አለኝ። ህልሞችሽን ስታሳኪ ለማየትና ሁሌም ከጎንሽ ለመሆን ዝግጁ ነኝ።
                </p>
                <p>
                    ይህ ትንሽ ስጦታ ላንቺ ያለኝን ልዩ ቦታ ለማሳየት የተዘጋጀ ሲሆን፣ ሁልጊዜም በህይወትሽ ውስጥ ደስታ፣ ሰላም እና ስኬት እንዲበዛልሽ እመኛለሁ። መልካሙን ሁሉ ለውዷ ብሌን! ❤️
                </p>
            </div>
        </div>

        <!-- Best Memorial Section -->
        <div class="card">
            <div class="card-header">
                <div class="card-title">
                    <i class="fas fa-heart"></i>
                    <span>Best Memorial 📸</span>
                </div>
            </div>
            <div class="img-container">
                <img src="besti%20pic.jpg" alt="Best Memorial Picture">
            </div>
            <p class="card-caption">
                "Every moment spent with you is a memory I will treasure forever." ✨
            </p>
        </div>

        <!-- Expectation Section -->
        <div class="card">
            <div class="card-header">
                <div class="card-title">
                    <i class="fas fa-star"></i>
                    <span>Future Expectation ✨</span>
                </div>
            </div>
            <div class="img-container">
                <img src="for%20expectashn%20.jpg" alt="Expectation Picture">
            </div>
            <p class="card-caption">
                "Looking forward to an even brighter future filled with achievements and joy together." 🌟
            </p>
        </div>

        <!-- Interactive Surprise Section -->
        <div class="interactive-box">
            <h3>Touch for a Surprise ✨</h3>
            <p>Click the button below or tap anywhere on the screen!</p>
            <button class="btn-action" onclick="showSurprise(event)">
                <i class="fas fa-gift"></i> Open Surprise
            </button>
        </div>

        <footer>
            <p>Designed Specially for BLEN • Created with Love</p>
        </footer>

    </div>

    <script>
        // Floating Hearts Animation on Click
        document.addEventListener('click', function(e) {
            createHeart(e.clientX, e.clientY);
        });

        function createHeart(x, y) {
            const heart = document.createElement('div');
            heart.classList.add('heart-particle');
            heart.innerHTML = '❤️';
            heart.style.left = (x - 12) + 'px';
            heart.style.top = (y - 12) + 'px';
            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 2500);
        }

        function showSurprise(e) {
            e.stopPropagation();
            for(let i = 0; i < 20; i++) {
                setTimeout(() => {
                    const x = window.innerWidth / 2 + (Math.random() * 260 - 130);
                    const y = window.innerHeight / 2 + (Math.random() * 260 - 130);
                    createHeart(x, y);
                }, i * 70);
            }
            alert("❤️ You are truly one of a kind! Thank you for being in my life.");
        }
    </script>
</body>
</html>
