# Permission-
Be my valentine 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Important Question 💘</title>

  <!-- Instagram preview -->
  <meta property="og:title" content="Priyal, will you be my Valentine? 💕" />
  <meta property="og:description" content="There is only one correct answer 😌" />
  <meta property="og:type" content="website" />

  <style>
    body {
      margin: 0;
      height: 100vh;
      overflow: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      font-family: 'Poppins', 'Comic Sans MS', sans-serif;
      text-align: center;
    }

    .card {
      background: white;
      padding: 30px;
      border-radius: 24px;
      box-shadow: 0 20px 40px rgba(0,0,0,0.25);
      max-width: 340px;
      width: 90%;
      position: relative;
      z-index: 10;
    }

    h1 {
      font-size: 1.6rem;
      margin-bottom: 10px;
    }

    p {
      margin-bottom: 20px;
      color: #666;
    }

    button {
      font-size: 1.2rem;
      padding: 12px 26px;
      margin: 10px;
      border: none;
      border-radius: 999px;
      cursor: pointer;
      transition: transform 0.15s ease;
    }

    button:hover {
      transform: scale(1.08);
    }

    .yes {
      background: #ff4d6d;
      color: white;
    }

    .no {
      background: #eee;
      color: #555;
      position: absolute;
    }

    .shake {
      animation: shake 0.3s;
    }

    @keyframes shake {
      0% { transform: translateX(0); }
      25% { transform: translateX(-5px); }
      50% { transform: translateX(5px); }
      75% { transform: translateX(-5px); }
      100% { transform: translateX(0); }
    }

    .message {
      font-size: 1.4rem;
      display: none;
      color: #ff4d6d;
    }

    /* Floating hearts */
    .heart {
      position: absolute;
      bottom: -20px;
      font-size: 20px;
      animation: float 6s linear infinite;
      opacity: 0.85;
    }

    @keyframes float {
      0% {
        transform: translateY(0) scale(1);
        opacity: 1;
      }
      100% {
        transform: translateY(-110vh) scale(1.6);
        opacity: 0;
      }
    }

    /* Confetti */
    .confetti {
      position: absolute;
      width: 8px;
      height: 8px;
      background: red;
      animation: fall 2.5s linear forwards;
    }

    @keyframes fall {
      0% { transform: translateY(0) rotate(0deg); }
      100% { transform: translateY(100vh) rotate(720deg); }
    }
  </style>
</head>

<body>

  <!-- Autoplay music -->
  <audio autoplay loop>
    <source src="https://www.bensound.com/bensound-music/bensound-love.mp3" type="audio/mpeg">
  </audio>

  <div class="card">
    <h1>Hey Priyal 💕</h1>
    <p>Very serious question. Think carefully.</p>

    <button class="yes" onclick="sayYes()">YES 💖</button>
    <button class="no" id="noBtn">NO 🙃</button>

    <div class="message" id="message">
      YAYYY 🥰💘<br>
      I knew it.<br>
      You’re officially my Valentine 😘
    </div>
  </div>

  <script>
    const noBtn = document.getElementById("noBtn");

    function moveNo() {
      const x = Math.random() * (window.innerWidth - 120);
      const y = Math.random() * (window.innerHeight - 60);
      noBtn.style.left = x + "px";
      noBtn.style.top = y + "px";
      noBtn.classList.add("shake");
      setTimeout(() => noBtn.classList.remove("shake"), 300);
    }

    noBtn.addEventListener("mouseover", moveNo);
    noBtn.addEventListener("click", () => {
      moveNo();
      alert("❌ WRONG ANSWER ❌\nPlease try again 😌");
    });

    function sayYes() {
      document.querySelector(".yes").style.display = "none";
      noBtn.style.display = "none";
      document.querySelector("p").style.display = "none";
      document.getElementById("message").style.display = "block";
      confettiBoom();
    }

    function confettiBoom() {
      for (let i = 0; i < 120; i++) {
        const conf = document.createElement("div");
        conf.className = "confetti";
        conf.style.left = Math.random() * 100 + "vw";
        conf.style.background = `hsl(${Math.random() * 360}, 100%, 60%)`;
        conf.style.animationDuration = Math.random() * 1.5 + 1.5 + "s";
        document.body.appendChild(conf);
        setTimeout(() => conf.remove(), 3000);
      }
    }

    function createHeart() {
      const heart = document.createElement("div");
      heart.className = "heart";
      heart.innerText = "💖";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.fontSize = Math.random() * 20 + 15 + "px";
      heart.style.animationDuration = Math.random() * 3 + 4 + "s";
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 7000);
    }

    setInterval(createHeart, 350);
  </script>

</body>
</html>
