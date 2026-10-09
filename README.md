# for-you-bibii
Index.html
```html
<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>คำอวยพร 💜</title>

<style>
* { box-sizing: border-box; }

body {
  margin: 0;
  min-height: 100vh;
  display: grid;
  place-items: center;
  overflow: hidden;
  font-family: sans-serif;
  background: linear-gradient(135deg,#fff,#eee3ff,#f9f5ff);
  color: #70478e;
}

.card {
  position: relative;
  width: min(320px, 90vw);
  height: 420px;
  padding: 28px 22px;
  border: 2px solid #d2b6ed;
  border-radius: 24px;
  background: rgba(255,255,255,.94);
  box-shadow: 0 12px 35px #b89bd633;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  overflow: hidden;
}

.decoration {
  position: absolute;
  color: #b58cdb;
  animation: twinkle 2s infinite alternate;
}
.top-left { top: 15px; left: 18px; }
.top-right { top: 15px; right: 18px; }
.bottom-left { bottom: 15px; left: 18px; }
.bottom-right { bottom: 15px; right: 18px; }

@keyframes twinkle {
  from { opacity: .3; transform: scale(.8); }
  to { opacity: 1; transform: scale(1.2); }
}

.wand {
  font-size: 48px;
  animation: float 2s ease-in-out infinite;
}

@keyframes float {
  50% { transform: translateY(-8px) rotate(8deg); }
}

h1 {
  font-size: 30px;
  margin: 12px 0 5px;
}

.subtitle {
  font-size: 13px;
  color: #a08ab2;
  margin-bottom: 25px;
}

button {
  font-family: inherit;
  cursor: pointer;
  border: none;
}

.yes {
  background: linear-gradient(135deg,#b58add,#8050a7);
  color: white;
  padding: 13px 18px;
  border-radius: 14px;
  font-size: 16px;
  box-shadow: 0 5px 15px #9870b944;
  animation: pulse 1.4s infinite;
}

@keyframes pulse {
  50% { transform: scale(1.06); }
}

.no {
  position: absolute;
  bottom: 58px;
  background: #f0e5fa;
  color: #795b91;
  padding: 10px 13px;
  border-radius: 12px;
  font-size: 13px;
  max-width: 85%;
}

.message {
  width: 100%;
  padding: 22px 14px;
  border: 2px solid #d5b9ed;
  border-radius: 18px;
  background: #fcf9ff;
  font-size: 15px;
  line-height: 1.9;
  overflow-wrap: anywhere;
  animation: appear .45s ease;
}

.message .wand {
  font-size: 38px;
  margin-bottom: 10px;
}

@keyframes appear {
  from { opacity: 0; transform: scale(.75) translateY(10px); }
  to { opacity: 1; transform: scale(1) translateY(0); }
}

.spark {
  position: fixed;
  z-index: 5;
  pointer-events: none;
  animation: burst .8s forwards ease-out;
}

@keyframes burst {
  to {
    transform: translate(var(--x),var(--y)) rotate(180deg) scale(.3);
    opacity: 0;
  }
}

.hidden { display: none !important; }

#finalNote {
  font-size: 12px;
  color: #a08ab2;
  margin-top: 14px;
}
</style>
</head>

<body>
<main class="card">
  <span class="decoration top-left">✦</span>
  <span class="decoration top-right">✧</span>
  <span class="decoration bottom-left">⋆</span>
  <span class="decoration bottom-right">✦</span>

  <section id="intro">
    <div class="wand">🪄</div>
    <h1>มีอะไรจะให้ 💜</h1>
    <div class="subtitle">กดดูสิ... ไม่กัดหรอก</div>

    <button class="yes" id="receive">
      กดเพื่อรับคำอวยพร
    </button>

    <button class="no" id="nope">
      ไม่กดหรอก ! ไม่อยากได้ !
    </button>
  </section>

  <section id="content" class="hidden">
    <div class="message" id="message"></div>
    <button class="yes" id="next" style="margin-top:18px">
      กดรับคำอวยพร 💜
    </button>
    <div id="finalNote"></div>
  </section>
</main>

<script>
const intro = document.getElementById("intro");
const content = document.getElementById("content");
const message = document.getElementById("message");
const next = document.getElementById("next");
const receive = document.getElementById("receive");
const nope = document.getElementById("nope");
const finalNote = document.getElementById("finalNote");

const words = [
  "ขอให้ทุกอย่างราบรื่น",

  "ทุกอย่างจะผ่านไปได้ด้วยดี<br>ขอให้มั่นใจ 👊🏻",

  "รักเด็กนะเว้ย เพราะงั้น<br><br>" +
  "ขอให้ทุกอย่างโอเค<br>" +
  "ขอให้เธอไม่กลัวเกินไป<br>" +
  "ขอให้ปลอดภัย<br>" +
  "ขอให้เธอไม่เจ็บมากเท่าที่ควรนะ !"
];

let index = 0;

function sparkle(x, y) {
  const symbols = ["✦", "✧", "✨", "⋆", "💜"];

  for (let i = 0; i < 16; i++) {
    const s = document.createElement("span");
    s.className = "spark";
    s.textContent = symbols[Math.floor(Math.random() * symbols.length)];
    s.style.left = x + "px";
    s.style.top = y + "px";
    s.style.fontSize = (14 + Math.random() * 14) + "px";
    s.style.setProperty("--x", (Math.random() - .5) * 200 + "px");
    s.style.setProperty("--y", (Math.random() - .5) * 200 + "px");
    document.body.appendChild(s);
    setTimeout(() => s.remove(), 850);
  }
}

function showBlessing(x, y) {
  sparkle(x, y);
  intro.classList.add("hidden");
  content.classList.remove("hidden");

  message.innerHTML =
    '<div class="wand">🪄</div>' + words[index];

  // เริ่มแอนิเมชันใหม่ทุกครั้ง
  message.style.animation = "none";
  void message.offsetWidth;
  message.style.animation = "appear .45s ease";

  index++;

  if (index >= words.length) {
    next.classList.add("hidden");
    finalNote.textContent = "ส่งกำลังใจให้เสมอนะ ✨";
  }
}

receive.addEventListener("click", (e) => {
  showBlessing(e.clientX, e.clientY);
});

next.addEventListener("click", (e) => {
  showBlessing(e.clientX, e.clientY);
});

function moveButton() {
  const card = document.querySelector(".card");
  const area = card.getBoundingClientRect();
  const button = nope.getBoundingClientRect();

  const maxX = Math.max(0, (area.width - button.width) / 2 - 8);
  const maxY = 65;

  const x = (Math.random() * 2 - 1) * maxX;
  const y = (Math.random() * 2 - 1) * maxY;

  nope.style.transform = `translate(${x}px,${y}px)`;
}

nope.addEventListener("pointerenter", moveButton);
nope.addEventListener("click", moveButton);
</script>
</body>
</html>
```
