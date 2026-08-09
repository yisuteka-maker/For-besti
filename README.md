<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Surprise Card for Besti</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      background: #09090e;
      color: #ffffff;
      height: 100vh;
      width: 100vw;
      display: flex;
      flex-direction: column;
      justify-content: center; /* መካከለኛ ላይ ያደርገዋል */
      align-items: center;    /* በአግድም መካከለኛ ያደርገዋል */
      padding: 0 24px;         /* በግራና በቀኝ በኩል በቂ Gap ይተዋል */
      overflow: hidden;
      position: relative;
    }

    /* Background Particles Canvas */
    #particles-canvas {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 1;
      pointer-events: none;
    }

    /* Music & Lang Control Header */
    .header-nav {
      position: absolute;
      top: 20px;
      left: 0;
      right: 0;
      padding: 0 24px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      z-index: 100;
    }

    .lang-btn, .music-btn {
      background: rgba(255, 255, 255, 0.08);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      border: 1px solid rgba(255, 255, 255, 0.15);
      color: #fff;
      padding: 8px 16px;
      border-radius: 20px;
      cursor: pointer;
      font-size: 13px;
      font-weight: 500;
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .lang-btn:hover, .music-btn:hover {
      background: rgba(255, 255, 255, 0.2);
    }

    .lang-btn .active {
      background: #e91e63;
      padding: 2px 6px;
      border-radius: 10px;
      font-size: 11px;
    }

    /* Main Container (Centered) */
    .main-container {
      width: 100%;
      max-width: 400px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      z-index: 10;
    }

    /* 3D Box Container */
    .perspective-wrapper {
      perspective: 1000px;
      width: 100%;
      margin-bottom: 25px;
    }

    .card-3d {
      width: 100%;
      min-height: 170px;
      background: linear-gradient(145deg, rgba(255, 255, 255, 0.06), rgba(255, 255, 255, 0.01));
      border: 1px solid rgba(212, 175, 55, 0.4);
      border-radius: 20px;
      padding: 25px;
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.6);
      transform-style: preserve-3d;
      transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
    }

    .card-3d.flip {
      transform: rotateY(180deg);
    }

    .card-text {
      font-size: 17px;
      line-height: 1.6;
      color: #eaeaea;
      word-break: break-word;
      font-weight: 400;
    }

    /* Glowing Main Action Button */
    .btn-action {
      width: 100%;
      background: linear-gradient(135deg, #4a154b, #6b114d);
      color: #ffffff;
      border: 1px solid rgba(255, 255, 255, 0.2);
      padding: 16px;
      border-radius: 30px;
      font-size: 15px;
      font-weight: 600;
      letter-spacing: 1.5px;
      cursor: pointer;
      box-shadow: 0 8px 25px rgba(107, 17, 77, 0.4);
      transition: all 0.3s ease;
      text-transform: uppercase;
    }

    .btn-action:active {
      transform: scale(0.98);
    }

    /* Feedback / Instagram Section */
    .feedback-section {
      display: none;
      width: 100%;
      text-align: center;
      animation: fadeIn 0.8s ease forwards;
    }

    .feedback-section h3 {
      font-size: 18px;
      margin-bottom: 15px;
      color: #f3a6c8;
      font-weight: 500;
    }

    textarea {
      width: 100%;
      height: 130px;
      background: rgba(255, 255, 255, 0.04);
      border: 1px solid rgba(255, 255, 255, 0.18);
      border-radius: 16px;
      padding: 15px;
      color: #fff;
      font-size: 15px;
      resize: none;
      outline: none;
      margin-bottom: 18px;
    }

    textarea:focus {
      border-color: #d4af37;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(12px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>

  <!-- Background Particle Effects -->
  <canvas id="particles-canvas"></canvas>

  <!-- Top Navigation Header -->
  <div class="header-nav">
    <button class="lang-btn" id="langBtn" onclick="toggleLanguage()">
      <span id="langEN" class="active">EN</span>
      <span id="langAM">አማ</span>
    </button>
    <button class="music-btn" onclick="toggleAudio()">
      🎵 <span id="musicText">Music</span>
    </button>
  </div>

  <!-- Background Music (የሙዚቃ ፋይልህን በ music.mp3 ስም አስቀምጥ) -->
  <audio id="bgMusic" loop>
    <source src="music.mp3" type="audio/mpeg">
  </audio>

  <!-- Centered Content Wrapper -->
  <div class="main-container">

    <!-- 3D Card Display Area -->
    <div id="surpriseArea" style="width: 100%;">
      <div class="perspective-wrapper">
        <div class="card-3d" id="card3D">
          <p class="card-text" id="cardMessage">Thank you for every beautiful memory.</p>
        </div>
      </div>
      <button class="btn-action" id="nextBtn" onclick="nextSurprise()">NEXT SURPRISE</button>
    </div>

    <!-- Final Feedback & Direct Instagram Message Section -->
    <div class="feedback-section" id="feedbackSection">
      <h3 id="feedbackTitle">ሀሳብሽን/አስተያየትሽን ጻፊልኝ 💌</h3>
      <textarea id="userFeedback" placeholder="ስለ ስጦታው የተሰማሽን እዚህ ጋር ፃፊ..."></textarea>
      <button class="btn-action" id="sendBtn" onclick="sendToInstagram()">ለ YISU ላክ (INSTAGRAM)</button>
    </div>

  </div>

  <script>
    // Data Storage for English and Amharic
    const data = {
      en: {
        messages: [
          "Thank you for every beautiful memory.",
          "You bring so much light and brightness into my world ✨",
          "Every moment spent with you is truly special 💖",
          "How did you feel looking through all of this?"
        ],
        btnNext: "NEXT SURPRISE",
        feedbackTitle: "Write your thoughts/feedback 💌",
        placeholder: "Type your feedback here...",
        sendBtn: "SEND TO YISU (INSTAGRAM)"
      },
      am: {
        messages: [
          "ለእያንዳንዱ ያሳለፍነው ውብ ትዝታ አመሰግናለሁ።",
          "በህይወቴ ላይ ብዙ ብርሃንና ደስታን ጨምረሻል ✨",
          "ከአንቺ ጋር ያሳለፍኩት እያንዳንዱ ጊዜ ልዩ ነው 💖",
          "ይህንን ሁሉ ስታይ ምን ተሰማሽ?"
        ],
        btnNext: "ቀጣይ አስደናቂ ነገር",
        feedbackTitle: "ሀሳብሽን/አስተያየትሽን ጻፊልኝ 💌",
        placeholder: "ስለ ስጦታው የተሰማሽን እዚህ ጋር ፃፊ...",
        sendBtn: "ለ YISU ላክ (INSTAGRAM)"
      }
    };

    let currentLang = 'en';
    let currentIndex = 0;

    const card3D = document.getElementById("card3D");
    const cardMessage = document.getElementById("cardMessage");
    const surpriseArea = document.getElementById("surpriseArea");
    const feedbackSection = document.getElementById("feedbackSection");
    const bgMusic = document.getElementById("bgMusic");
    const nextBtn = document.getElementById("nextBtn");
    const feedbackTitle = document.getElementById("feedbackTitle");
    const userFeedback = document.getElementById("userFeedback");
    const sendBtn = document.getElementById("sendBtn");

    // Audio Controller
    function toggleAudio() {
      if (bgMusic.paused) {
        bgMusic.play();
        document.getElementById("musicText").textContent = "Pause";
      } else {
        bgMusic.pause();
        document.getElementById("musicText").textContent = "Music";
      }
    }

    // Language Toggle logic
    function toggleLanguage() {
      currentLang = currentLang === 'en' ? 'am' : 'en';
      
      document.getElementById("langEN").classList.toggle("active", currentLang === 'en');
      document.getElementById("langAM").classList.toggle("active", currentLang === 'am');

      cardMessage.textContent = data[currentLang].messages[currentIndex];
      nextBtn.textContent = data[currentLang].btnNext;
      feedbackTitle.textContent = data[currentLang].feedbackTitle;
      userFeedback.placeholder = data[currentLang].placeholder;
      sendBtn.textContent = data[currentLang].sendBtn;
    }

    // Next Card Flip Logic
    function nextSurprise() {
      card3D.classList.add("flip");

      setTimeout(() => {
        currentIndex++;
        if (currentIndex < data[currentLang].messages.length) {
          cardMessage.textContent = data[currentLang].messages[currentIndex];
        } else {
          surpriseArea.style.display = "none";
          feedbackSection.style.display = "block";
        }
        card3D.classList.remove("flip");
      }, 300);
    }

    // Redirect to Instagram DM with copied message
    function sendToInstagram() {
      const text = userFeedback.value.trim();
      const targetIG = "lan_yisu";

      if (!text) {
        alert(currentLang === 'en' ? "Please write your feedback first!" : "እባክሽን አስቀድመሽ አስተያየትሽን ፃፊ!");
        return;
      }

      navigator.clipboard.writeText(text).then(() => {
        alert(currentLang === 'en' ? "Message copied! Paste it in Instagram DM." : "ጽሁፉ ኮፒ ሆኗል! Instagram DM ሲከፈት Paste በይው።");
        window.location.href = `https://ig.me/m/${targetIG}`;
      }).catch(() => {
        window.location.href = `https://ig.me/m/${targetIG}`;
      });
    }

    // Particle Animation Background Code
    const canvas = document.getElementById('particles-canvas');
    const ctx = canvas.getContext('2d');
    let particles = [];

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }
    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();

    class Particle {
      constructor() {
        this.x = Math.random() * canvas.width;
        this.y = Math.random() * canvas.height;
        this.size = Math.random() * 3 + 1;
        this.speedX = Math.random() * 0.5 - 0.25;
        this.speedY = Math.random() * 0.5 - 0.25;
        this.color = `rgba(243, 166, 200, ${Math.random() * 0.5 + 0.2})`;
      }
      update() {
        this.x += this.speedX;
        this.y += this.speedY;
        if (this.x < 0 || this.x > canvas.width) this.speedX *= -1;
        if (this.y < 0 || this.y > canvas.height) this.speedY *= -1;
      }
      draw() {
        ctx.fillStyle = this.color;
        ctx.beginPath();
        ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
        ctx.fill();
      }
    }

    function initParticles() {
      particles = [];
      for (let i = 0; i < 45; i++) {
        particles.push(new Particle());
      }
    }

    function animateParticles() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      particles.forEach(p => {
        p.update();
        p.draw();
      });
      requestAnimationFrame(animateParticles);
    }

    initParticles();
    animateParticles();
  </script>
</body>
</html>
