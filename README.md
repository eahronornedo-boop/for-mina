<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Birthday in Heaven - Tito Enrique</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Courier New', Courier, monospace;
    }

    body {
      background-color: #ffe5ec;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      overflow: hidden;
    }

    .content {
      background-color: #fff0f3;
      border: 3px solid #ffb3c1;
      border-radius: 8px;
      width: 350px;
      box-shadow: 0 8px 16px rgba(255, 179, 193, 0.4);
      overflow: hidden;
      position: relative;
    }

    .window-header {
      background-color: #ffb3c1;
      padding: 8px 12px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      color: white;
      font-weight: bold;
    }

    .window-buttons span {
      display: inline-block;
      width: 10px;
      height: 10px;
      background-color: white;
      margin-left: 4px;
      border-radius: 2px;
    }

    .window-body {
      padding: 24px;
      text-align: center;
    }

    .heart-row {
      letter-spacing: 4px;
      margin-bottom: 12px;
      font-size: 22px;
    }

    h1 {
      font-size: 18px;
      color: #594a4e;
      margin-bottom: 20px;
      line-height: 1.5;
    }

    #birthdayMessage {
      display: none;
      color: #ff4d6d;
      font-size: 19px;
      font-weight: bold;
      line-height: 1.5;
      margin-bottom: 18px;
      animation: messagePop 0.8s ease-out forwards;
    }

    .content.finished #birthdayMessage {
      display: block;
    }

    .content.finished #question {
      display: none;
    }

    @keyframes messagePop {
      0% {
        opacity: 0;
        transform: scale(0.5);
      }

      70% {
        transform: scale(1.1);
      }

      100% {
        opacity: 1;
        transform: scale(1);
      }
    }

    .cake-container {
      position: relative;
      width: 150px;
      height: 150px;
      margin: 0 auto 24px auto;
    }

    #cake {
      position: absolute;
      bottom: 10px;
      left: 0;
      width: 150px;
      height: 80px;
      background-color: #6f4e37;
      border-radius: 10px 10px 0 0;
      border-bottom: 6px solid #ffb3c1;
    }

    #cake::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 15px;
      background-color: white;
      border-radius: 10px 10px 0 0;
    }

    .candle {
      background: white;
      border-radius: 10px;
      position: absolute;
      top: 0;
      left: 50%;
      margin-left: -2.5px;
      width: 5px;
      height: 35px;
      opacity: 0;
      transform: translateY(-100px);
      z-index: 2;
    }

    .candle::after {
      content: "";
      top: 25%;
      left: 0;
      position: absolute;
      width: 100%;
      height: 4px;
      background-color: #ff4d6d;
    }

    .candle::before {
      content: "";
      top: 45%;
      left: 0;
      position: absolute;
      width: 100%;
      height: 4px;
      background-color: #ff4d6d;
    }

    .fire {
      border-radius: 100%;
      position: absolute;
      top: -20px;
      left: 50%;
      margin-left: -3.3px;
      width: 6.6px;
      height: 18px;
      background-color: #ff9e00;
      box-shadow:
        0 0 10px #ff9e00,
        0 0 20px #ffd000;
      animation: flicker 0.3s ease-in-out infinite alternate;
    }

    .content.is-won .candle {
      opacity: 1;
      animation: candleIn 500ms ease-out forwards;
    }

    .content.is-won #cake {
      animation: cakeBounce 0.8s ease-in-out;
    }

    .content.blown .fire {
      animation: fireOut 0.7s ease-out forwards;
    }

    @keyframes cakeBounce {
      0% {
        transform: translateY(0) rotate(0deg);
      }

      25% {
        transform: translateY(-20px) rotate(-2deg);
      }

      50% {
        transform: translateY(0) rotate(2deg);
      }

      75% {
        transform: translateY(-8px) rotate(-1deg);
      }

      100% {
        transform: translateY(0) rotate(0deg);
      }
    }

    @keyframes candleIn {
      0% {
        transform: translateY(-100px);
      }

      100% {
        transform: translateY(35px);
      }
    }

    @keyframes flicker {
      0% {
        transform: scale(1);
        opacity: 0.9;
      }

      100% {
        transform: scale(1.15) skewX(3deg);
        opacity: 1;
      }
    }

    @keyframes fireOut {
      0% {
        opacity: 1;
        transform: scale(1);
      }

      50% {
        opacity: 0.5;
        transform: scale(1.3);
      }

      100% {
        opacity: 0;
        transform: scale(0);
      }
    }

    .btn-group {
      display: flex;
      justify-content: center;
      gap: 16px;
    }

    button {
      padding: 8px 20px;
      border: 2px solid #ffb3c1;
      background-color: white;
      color: #ff4d6d;
      font-weight: bold;
      cursor: pointer;
      border-radius: 4px;
      transition: all 0.2s ease;
    }

    button:hover {
      background-color: #ffb3c1;
      color: white;
    }

    #noBtn {
      position: relative;
      z-index: 10;
    }

    .heart {
      position: fixed;
      top: -30px;
      font-size: 25px;
      pointer-events: none;
      animation: fall 3s linear forwards;
      z-index: 100;
    }

    @keyframes fall {
      0% {
        transform: translateY(0) rotate(0deg);
        opacity: 1;
      }

      100% {
        transform: translateY(110vh) rotate(360deg);
        opacity: 0;
      }
    }
  </style>
</head>

<body>

  <div class="content" id="cardContainer">

    <div class="window-header">
      <span class="title">BIRTHDAY ❤️</span>

      <div class="window-buttons">
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>

    <div class="window-body">

      <div class="heart-row">
        🎂 🕯️ 🎂
      </div>

      <h1 id="question">
        Happy 65th Birthday in Heaven,<br>
        Tito Enrique. ❤️<br><br>
        Mina or Queenie,<br>
        please blow the candle for your Dad.
      </h1>

      <div id="birthdayMessage">
        🎉 Happy 65th Birthday po,<br>
        Tito Enrique! 🎂❤️
      </div>

      <div class="cake-container">

        <div class="candle">
          <div class="fire"></div>
        </div>

        <div id="cake"></div>

      </div>

      <div class="btn-group">

        <button id="yesBtn">YES ❤️</button>
        <button id="noBtn">NO</button>

      </div>

    </div>
  </div>

  <script>
    const yesBtn = document.getElementById("yesBtn");
    const noBtn = document.getElementById("noBtn");
    const cardContainer = document.getElementById("cardContainer");

    yesBtn.addEventListener("click", () => {

      cardContainer.classList.add("is-won");

      setTimeout(() => {
        cardContainer.classList.add("blown");
      }, 1200);

      setTimeout(() => {
        cardContainer.classList.add("finished");
      }, 1800);

      for (let i = 0; i < 25; i++) {

        const heart = document.createElement("div");

        heart.className = "heart";
        heart.textContent = "❤️";

        heart.style.left =
          Math.random() * window.innerWidth + "px";

        heart.style.animationDelay =
          Math.random() * 1.5 + "s";

        document.body.appendChild(heart);

        setTimeout(() => {
          heart.remove();
        }, 4500);
      }
    });

    function iwasButton() {

      const maxX =
        window.innerWidth - noBtn.offsetWidth - 20;

      const maxY =
        window.innerHeight - noBtn.offsetHeight - 20;

      const x =
        Math.max(10, Math.random() * maxX);

      const y =
        Math.max(10, Math.random() * maxY);

      noBtn.style.position = "fixed";
      noBtn.style.left = x + "px";
      noBtn.style.top = y + "px";
    }

    noBtn.addEventListener("mouseenter", iwasButton);

    noBtn.addEventListener("touchstart", (event) => {
      event.preventDefault();
      iwasButton();
    });
  </script>

</body>
</html>
