const CONFETTI_COLORS = ["#FF9EBB", "#FFC857", "#CBB8FF", "#FFB088", "#7AD0C9", "#E8558E"];

function launchConfetti(count = 90) {
  const layer = document.getElementById("confettiLayer");
  if (!layer) return;
  for (let i = 0; i < count; i++) {
    const piece = document.createElement("div");
    piece.className = "confetti-piece";
    const color = CONFETTI_COLORS[Math.floor(Math.random() * CONFETTI_COLORS.length)];
    const left = Math.random() * 100;
    const duration = 2.6 + Math.random() * 1.8;
    const delay = Math.random() * 0.4;
    const size = 6 + Math.random() * 6;
    const isRound = Math.random() > 0.5;
    piece.style.left = left + "vw";
    piece.style.background = color;
    piece.style.width = size + "px";
    piece.style.height = (size * 1.4) + "px";
    piece.style.borderRadius = isRound ? "50%" : "2px";
    piece.style.animationDuration = duration + "s";
    piece.style.animationDelay = delay + "s";
    layer.appendChild(piece);
    setTimeout(() => piece.remove(), (duration + delay) * 1000 + 200);
  }
}

const celebrateBtn = document.getElementById("celebrateBtn");
if (celebrateBtn) {
  celebrateBtn.addEventListener("click", () => {
    launchConfetti(120);
    document.getElementById("messages")?.scrollIntoView({ behavior: "smooth" });
  });
}

const cutBtn = document.getElementById("cutBtn");
const cakeEl = document.getElementById("cake");
const flameEl = document.getElementById("flame");
const knifeEl = document.getElementById("knife");
const cakeResult = document.getElementById("cakeResult");

const CAKE_LINES = [
  "The candle is out, the cake is cut — officially another year of you running this family begins. 🍰",
  "May this year bring you slightly less to worry about. Slightly. 😌",
  "Cake: cut. Wish: made. You: still everyone's favorite. 💗"
];

if (cutBtn) {
  cutBtn.addEventListener("click", () => {
    cutBtn.disabled = true;
    flameEl.classList.add("out");
    setTimeout(() => { knifeEl.classList.add("slice"); }, 350);
    setTimeout(() => {
      cakeEl.classList.add("cut");
      launchConfetti(70);
      const line = CAKE_LINES[Math.floor(Math.random() * CAKE_LINES.length)];
      cakeResult.textContent = line;
    }, 950);
    setTimeout(() => {
      cutBtn.disabled = false;
      cutBtn.textContent = "Cut again? 🍰";
      cakeEl.classList.remove("cut");
      flameEl.classList.remove("out");
      knifeEl.classList.remove("slice");
    }, 3200);
  });
}

const envelope = document.getElementById("envelope");
function toggleEnvelope() {
  const isOpening = !envelope.classList.contains("open");
  envelope.classList.toggle("open");
  if (isOpening) launchConfetti(50);
}
if (envelope) {
  envelope.addEventListener("click", toggleEnvelope);
  envelope.addEventListener("keydown", (e) => {
    if (e.key === "Enter" || e.key === " ") {
      e.preventDefault();
      toggleEnvelope();
    }
  });
}

// ---------- Lock screen ----------
// ✏️ EDIT: change "Uzma" below to whatever password you want.
const SITE_PASSWORD = "Uzma";

const lockScreen = document.getElementById("lockScreen");
const lockInput = document.getElementById("lockInput");
const lockBtn = document.getElementById("lockBtn");
const lockError = document.getElementById("lockError");
const lockCard = document.querySelector(".lock-card");

document.body.classList.add("locked");

function tryUnlock() {
  const entered = lockInput.value.trim();
  if (entered.toLowerCase() === SITE_PASSWORD.toLowerCase()) {
    lockScreen.classList.add("unlocked");
    document.body.classList.remove("locked");
    const music = document.getElementById("bgMusic");
    if (music) music.play().catch(() => {});
  } else {
    lockError.textContent = "Wrong password, try again";
    lockCard.classList.remove("shake");
    void lockCard.offsetWidth; // restart animation
    lockCard.classList.add("shake");
    lockInput.value = "";
    lockInput.focus();
  }
}

if (lockBtn) {
  lockBtn.addEventListener("click", tryUnlock);
  lockInput.addEventListener("keydown", (e) => {
    if (e.key === "Enter") tryUnlock();
  });
}

// ---------- Mute/unmute music ----------
const muteBtn = document.getElementById("muteBtn");
const bgMusic = document.getElementById("bgMusic");
if (muteBtn && bgMusic) {
  muteBtn.addEventListener("click", () => {
    bgMusic.muted = !bgMusic.muted;
    muteBtn.textContent = bgMusic.muted ? "🔇" : "🔊";
  });
}
