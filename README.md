<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Valentine for Priyal 💖</title>
<style>
    body {
        font-family: 'Comic Sans MS', sans-serif;
        text-align: center;
        background: linear-gradient(135deg, #ffe6f0, #ffcccc);
        overflow: hidden;
        margin: 0;
        padding: 0;
        transition: background 5s ease;
    }

    h1 {
        margin-top: 50px;
        color: #ff3366;
        font-size: 3em;
        text-shadow: 2px 2px #fff;
    }

    #question {
        margin-top: 30px;
        font-size: 2em;
    }

    button {
        padding: 15px 30px;
        font-size: 1.5em;
        margin: 20px;
        cursor: pointer;
        border: none;
        border-radius: 12px;
        transition: all 0.2s;
        box-shadow: 0px 5px 15px rgba(0,0,0,0.2);
    }

    #yes {
        background: linear-gradient(45deg, #ff4d6d, #ff99cc);
        color: white;
        animation: pulse 2s infinite;
    }

    #no {
        background-color: #ccc;
    }

    @keyframes pulse {
        0% { transform: scale(1); box-shadow: 0 0 10px #ff99cc; }
        50% { transform: scale(1.1); box-shadow: 0 0 20px #ff4d6d; }
        100% { transform: scale(1); box-shadow: 0 0 10px #ff99cc; }
    }

    .heart {
        position: absolute;
        width: 25px;
        height: 25px;
        background: red;
        transform: rotate(-45deg);
        border-radius: 4px;
    }

    .heart::before,
    .heart::after {
        content: "";
        position: absolute;
        width: 25px;
        height: 25px;
        background: red;
        border-radius: 50%;
    }

    .heart::before { top: -12.5px; left: 0; }
    .heart::after { left: 12.5px; top: 0; }

    .confetti-piece {
        position: absolute;
        width: 12px;
        height: 12px;
        pointer-events: none;
        clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
        animation: fall 3s linear forwards;
    }

    @keyframes fall {
        0% { transform: translateY(0); opacity:1; }
        100% { transform: translateY(100vh); opacity:0; }
    }

    .floating-message {
        position: absolute;
        font-size: 2em;
        color: #ff3366;
        font-weight: bold;
        text-shadow: 1px 1px #fff;
        pointer-events: none;
        opacity: 0;
        animation: floatText 3s forwards;
    }

    @keyframes floatText {
        0% { opacity: 0; transform: translateY(0) scale(1); }
        20% { opacity: 1; transform: translateY(-20px) scale(1.2); }
        100% { opacity: 0; transform: translateY(-150px) scale(1); }
    }

    .share-buttons {
        margin-top: 50px;
    }

    .share-buttons a {
        text-decoration: none;
        color: white;
        padding: 10px 20px;
        margin: 10px;
        border-radius: 8px;
        font-weight: bold;
        transition: transform 0.2s;
    }

    .instagram { background: #C13584; }
    .imessage { background: #007AFF; }
    .share-buttons a:hover { transform: scale(1.1); }
</style>
</head>
<body>

<h1>Will you be my Valentine, Priyal? 💖</h1>
<div id="question">
    <button id="yes">Yes</button>
    <button id="no">No</button>
</div>

<div class="share-buttons">
    <a class="instagram" href="https://www.instagram.com/" target="_blank">Share on Instagram</a>
    <a class="imessage" href="sms:&body=Will you be my Valentine, Priyal? 💖" target="_blank">Share on iMessage</a>
</div>

<audio id="loveSong" src="https://www.bensound.com/bensound-music/bensound-love.mp3"></audio>

<script>
const yesBtn = document.getElementById('yes');
const noBtn = document.getElementById('no');
const song = document.getElementById('loveSong');
let floatingHearts = [];

// Create heart
function createHeart(x, y, color) {
    const heart = document.createElement('div');
    heart.className = 'heart';
    heart.style.left = (x || Math.random() * window.innerWidth) + 'px';
    heart.style.top = (y || window.innerHeight) + 'px';
    heart.style.backgroundColor = color || `hsl(${Math.random()*360}, 70%, 60%)`;
    document.body.appendChild(heart);
    floatingHearts.push({el: heart, x: parseFloat(heart.style.left), y: parseFloat(heart.style.top), dx: Math.random()*2-1, dy: Math.random()*2-1});
}

// Create heart-shaped confetti
function createConfetti(x, y) {
    const confetti = document.createElement('div');
    confetti.className = 'confetti-piece';
    confetti.style.left = (x || Math.random() * window.innerWidth) + 'px';
    confetti.style.top = (y || 0) + 'px';
    confetti.style.backgroundColor = `hsl(${Math.random()*360}, 100%, 50%)`;
    document.body.appendChild(confetti);
    setTimeout(() => confetti.remove(), 3000);
}

// Animate floating hearts
function animateFloatingHearts() {
    floatingHearts.forEach((heartObj) => {
        heartObj.x += heartObj.dx;
        heartObj.y += heartObj.dy;
        heartObj.el.style.left = heartObj.x + 'px';
        heartObj.el.style.top = heartObj.y + 'px';
        if (heartObj.x < 0 || heartObj.x > window.innerWidth-25) heartObj.dx *= -1;
        if (heartObj.y < 0 || heartObj.y > window.innerHeight-25) heartObj.dy *= -1;
    });
    requestAnimationFrame(animateFloatingHearts);
}

// Heart explosion
function explodeHearts(x, y) {
    for (let i = 0; i < 40; i++) {
        createHeart(x + (Math.random()*80-40), y + (Math.random()*80-40));
    }
}

// Floating message
function showMessage(text, x, y) {
    const msg = document.createElement('div');
    msg.className = 'floating-message';
    msg.innerText = text;
    msg.style.left = x + 'px';
    msg.style.top = y + 'px';
    document.body.appendChild(msg);
    setTimeout(() => msg.remove(), 3000);
}

// Background gradient animation
setInterval(() => {
    document.body.style.background = `linear-gradient(135deg, hsl(${Math.random()*360},70%,90%), hsl(${Math.random()*360},80%,95%))`;
}, 8000);

// Confetti rain
function startConfetti() {
    setInterval(() => {
        for (let i = 0; i < 10; i++) createConfetti();
    }, 500);
}

// Yes button click
yesBtn.addEventListener('click', (e) => {
    alert('Yay! 💖 You made my day!');
    song.play();
    explodeHearts(e.clientX, e.clientY);
    showMessage("You made my day! 💖", e.clientX, e.clientY);
    startConfetti();
    animateFloatingHearts();
    yesBtn.disabled = true;
    noBtn.disabled = true;
});

// No button dodging
noBtn.addEventListener('mouseover', () => {
    noBtn.style.position = 'absolute';
    noBtn.style.top = Math.random() * (window.innerHeight - 50) + 'px';
    noBtn.style.left = Math.random() * (window.innerWidth - 100) + 'px';
    noBtn.style.transform = `rotate(${Math.random()*30-15}deg)`;
});

noBtn.addEventListener('click', () => {
    alert('Wrong answer! 😆');
});

// Cursor hearts + confetti trail
document.addEventListener('mousemove', (e) => {
    createHeart(e.clientX, e.clientY);
    createConfetti(e.clientX, e.clientY);
});
</script>
</body>
</html>
