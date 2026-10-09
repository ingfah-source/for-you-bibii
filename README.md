# for-you-bibii
index.html
```html
<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>For You, Bibii 💜</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
      font-family: "Tahoma", sans-serif;
      background: linear-gradient(135deg, #f8f3ff, #e8d9ff, #fffaff);
      color: #72519b;
    }

    .sparkles {
      position: fixed;
      inset: 0;
      pointer-events: none;
      overflow: hidden;
    }

    .sparkle {
      position: absolute;
      font-size: 20px;
      opacity: 0.7;
      animation: float 5s ease-in-out infinite;
    }

    .sparkle:nth-child(1) {
      top: 12%;
      left: 12%;
    }

    .sparkle:nth-child(2) {
      top: 20%;
      right: 13%;
      animation-delay: 1s;
    }

    .sparkle:nth-child(3) {
      bottom: 18%;
      left: 16%;
      animation-delay: 2s;
    }

    .sparkle:nth-child(4) {
      bottom: 13%;
      right: 12%;
      animation-delay: 0.5s;
    }

    .sparkle:nth-child(5) {
      top: 48%;
      right: 7%;
      animation-delay: 1.5s;
    }

    @keyframes float {
      0%, 100% {
        transform: translateY(0) rotate(0deg);
      }
      50% {
        transform: translateY(-15px) rotate(15deg);
      }
    }

    .card {
      position: relative;
      width: min(320px, calc(100vw - 32px));
      min-height: 390px;
      padding: 28px 20px 24px;
      border: 2px solid rgba(255, 255, 255, 0.95);
      border-radius: 28px;
      background: rgba(255, 255, 255, 0.82);
      box-shadow: 0 12px 40px rgba(132, 93, 177, 0.2);
      text-align: center;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 15px;
      z-index: 1;
    }

    .wand {
      font-size: 36px;
      animation: wandBounce 2s ease-in-out infinite;
    }

    @keyframes wandBounce {
      0%, 100% {
        transform: rotate(-10deg) translateY(0);
      }
      50% {
        transform: rotate(10deg) translateY(-6px);
      }
    }

    h1 {
      margin: 0;
      font-size: 23px;
      color: #8964b5;
    }

    .subtitle {
      margin: 0;
      font-size: 13px;
      line-height: 1.8;
      color: #a18ab9;
    }

    .message {
      width: 100%;
      min-height: 94px;
      padding: 20px 14px;
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 18px;
      background: linear-gradient(135deg, #f5edff, #fff8ff);
      border: 1px solid #e9d8ff;
      color: #7954a3;
      font-size: 16px;
      font-weight: bold;
      line-height: 1.9;
      overflow-wrap: anywhere;
      animation: appear 0.5s ease;
    }

    .hidden {
      display: none !important;
    }

    @keyframes appear {
      from {
        opacity: 0;
        transform: translateY(8px) scale(0.96);
      }
      to {
        opacity: 1;
        transform: translateY(0) scale(1);
      }
    }

    button {
      font-family: inherit;
      cursor: pointer;
      border: none;
      border-radius: 999px;
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }

    .yes {
      padding: 13px 22px;
      background: linear-gradient(135deg, #c9a5ff, #a67be8);
      color: white;
      font-size: 14px;
      font-weight: bold;
      box-shadow: 0 5px 15px rgba(166, 123, 232, 0.3);
      animation: pulse 1.6s ease-in-out infinite;
    }

    .yes:hover {
      transform: scale(1.07);
    }

    @keyframes pulse {
      0%, 100% {
        box-shadow: 0 5px 15px rgba(166, 123, 232, 0.25);
      }
      50% {
        box-shadow: 0 5px 22px rgba(166, 123, 232, 0.55);
      }
    }

    .no-area {
      position: relative;
      width: 100%;
      height: 48px;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .no {
      position: absolute;
      padding: 10px 15px;
      background: #fff;
      border: 1px solid #e4d3f8;
      color: #a38bb9;
      font-size: 12px;
      white-space: nowrap;
    }

    .next {
      padding: 11px 23px;
      background: #eee2ff;
      color: #805aa8;
      font-size: 14px;
      font-weight: bold;
    }

    .next:hover {
      transform: scale(1.05);
    }

    .footer {
      margin: 0;
      font-size: 11px;
      color: #b29dc7;
    }
  </style>
</head>

<body>
  <div class="sparkles" aria-hidden="true">
    <span class="sparkle">✦</span>
    <span class="sparkle">✨</span>
    <span class="sparkle">🪄</span>
    <span class="sparkle">✧</span>
    <span class="sparkle">⋆</span>
  </div>

  <main class="card">
    <div class="wand" aria-hidden="true">🪄</div>

    <h1>For You, Bibii ♡</h1>

    <p class="subtitle" id="subtitle">
      มีคำอวยพรเล็ก ๆ มาฝากนะ<br>
      กดรับหน่อยได้ไหม ?
    </p>

    <div class="message hidden" id="message" aria-live="polite"></div>

    <button class="yes" id="yesButton" type="button">
      กดเพื่อรับคำอวยพร ✨
    </button>

    <button class="next hidden" id="nextButton" type="button">
      อ่านต่ออีกนิด ♡
    </button>

    <div class="no-area" id="noArea">
      <button class="no" id="noButton" type="button">
        ไม่กดหรอก ! ไม่อยากได้ !
      </button>
    </div>

    <p class="footer" id="footer">ส่งความใจดีเล็ก ๆ ไปให้เธอ 💜</p>
  </main>

  <script>
    const blessings = [
      "ขอให้ทุกอย่างราบรื่น ✨",
      "ทุกอย่างจะผ่านไปได้ด้วยดี ขอให้มั่นใจ 👊🏻",
      "รักเด็กนะเว้ย เพราะงั้น ขอให้ทุกอย่างโอเค ขอให้เธอไม่กลัวเกินไป ขอให้ปลอดภัย ขอให้เธอไม่เจ็บมากเท่าที่ควรนะ !"
    ];

    const subtitle = document.getElementById("subtitle");
    const message = document.getElementById("message");
    const yesButton = document.getElementById("yesButton");
    const nextButton = document.getElementById("nextButton");
    const noButton = document.getElementById("noButton");
    const noArea = document.getElementById("noArea");
    const footer = document.getElementById("footer");

    let currentIndex = -1;

    function showBlessing() {
      currentIndex++;

      message.classList.remove("hidden");

      // เล่นแอนิเมชันข้อความใหม่ทุกครั้ง
      message.style.animation = "none";
      void message.offsetWidth;
      message.style.animation = "appear 0.5s ease";

      message.textContent = blessings[currentIndex];

      subtitle.classList.add("hidden");
      yesButton.classList.add("hidden");
      noArea.classList.add("hidden");

      if (currentIndex < blessings.length - 1) {
        nextButton.classList.remove("hidden");
      } else {
        nextButton.classList.add("hidden");
        footer.textContent = "ขอให้เธอได้รับแต่สิ่งดี ๆ นะ ♡";
      }
    }

    yesButton.addEventListener("click", showBlessing);
    nextButton.addEventListener("click", showBlessing);

    function moveNoButton() {
      const areaRect = noArea.getBoundingClientRect();
      const buttonRect = noButton.getBoundingClientRect();

      const maxX = Math.max(0, areaRect.width - buttonRect.width);
      const randomX = Math.random() * maxX;

      noButton.style.left = randomX + "px";
      noButton.style.transform = "none";
    }

    noButton.addEventListener("pointerenter", moveNoButton);

    noButton.addEventListener("click", function () {
      moveNoButton();
    });
  </script>
</body>
</html>
```
