<html lang="mn">
<head>
  <meta charset="utf-8">
  <title>Миний Захидал</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');

    body {
      margin: 0;
      font-family: 'Press Start 2P', cursive;
      background: linear-gradient(135deg, #ff9edb, #ff7cc8, #ffb6f2);
      color: #fff;
      text-align: center;
      overflow-x: hidden;
    }
    .screen {
      height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }
    .btn {
      background: #fff;
      color: #ff4fa0;
      padding: 15px 25px;
      border-radius: 12px;
      text-decoration: none;
      font-size: 16px;
      box-shadow: 0 5px 0 #ff4fa0;
      cursor: pointer;
      transition: all 0.2s;
    }
    .btn:hover {
      transform: translateY(-3px);
    }
    .envelope {
      position: relative;
      width: 300px;
      height: 200px;
      background: #fff;
      margin: 20px auto;
      border-radius: 8px;
      box-shadow: 0 8px 16px rgba(0,0,0,0.2);
      cursor: pointer;
      overflow: hidden;
    }
    .flap {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 50%;
      background: #ff4fa0;
      clip-path: polygon(0 0, 100% 0, 50% 100%);
      transition: transform 1s;
      transform-origin: top;
    }
    .envelope.open .flap {
      transform: rotateX(180deg);
    }
    .letter {
      opacity: 0;
      padding: 20px;
      color: #333;
      font-family: sans-serif;
      line-height: 1.5;
      transition: opacity 1.5s;
      text-align: left;
    }
    .envelope.open .letter {
      opacity: 1;
    }
    .hearts {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: -1;
    }
    .heart {
      position: absolute;
      font-size: 18px;
      color: #fff;
      animation: floatUp 5s linear infinite;
    }
    @keyframes floatUp {
      0% { transform: translateY(100vh) scale(1); opacity: 1; }
      100% { transform: translateY(-10vh) scale(1.5); opacity: 0; }
    }
  </style>
</head>
<body>

  <!-- Эхний дэлгэц -->
  <div class="screen" id="start">
    <h1>💌 Хайрын Захидал</h1>
    <button class="btn" onclick="goLetter()">✨ Энд дарна уу ✨</button>
  </div>

  <!-- Захидлын дэлгэц -->
  <div class="screen" id="letter" style="display:none;">
    <div class="envelope" onclick="this.classList.toggle('open')">
      <div class="flap"></div>
      <div class="letter">
        <p>Өөрийгөө ч ойлгохгүй 
          Өдөр хоногууд хүнд 
          Яах гэж амьдарч байгаагаа 
          Өөрөөсөө асуугаад л сууна.</p>

        <p>Чимээгүйхэн чи ирсэн
Сэтгэл дотор минь гэрэл асаасан.<br>
        Эргэлзэж, төөрсөн намайг
Эр хүн шиг болгосон.</p>

        <p>Чи л намайг өөрчилсөн
Харанхуй дундаас гэрэл рүү татсан. Амьдрал утгатай санагдсан
Анх удаа зүрх минь баярласан.</p>

      </div>
    </div>
    <p style="font-size:12px; margin-top:10px;">✉️ Захиа дээр дарж нээгээрэй ✉️</p>
  </div>

  <!-- Pixel hearts animation -->
  <div class="hearts" id="hearts"></div>

  <script>
    function goLetter() {
      document.getElementById("start").style.display = "none";
      document.getElementById("letter").style.display = "flex";
    }

    // Floating hearts generator
    const hearts = document.getElementById("hearts");
    function createHeart() {
      const heart = document.createElement("div");
      heart.className = "heart";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.animationDuration = 3 + Math.random() * 2 + "s";
      heart.innerHTML = "❤";
      hearts.appendChild(heart);
      setTimeout(() => heart.remove(), 5000);
    }
    setInterval(createHeart, 400);
  </script>
</body>
</html>
