[U<!crishack html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Te amo Sandra 💖</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@700&display=swap');

    html, body {
      margin: 0;
      padding: 0;
      overflow: hidden;
      height: 100%;
      background: #ffccdd;
      font-family: 'Orbitron', sans-serif;
      animation: fondo 15s infinite alternate;
    }

    @keyframes fondo {
      0% { background: #000; }
      100% { background: #ffccdd; }
    }

    #mensaje {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      color: #ff33cc;
      font-size: 2.8rem;
      text-align: center;
      text-shadow: 0 0 5px #ff33cc, 0 0 10px #ff66ff, 0 0 20px #ff33cc;
      z-index: 10;
      pointer-events: none;
    }

    .teamo {
      position: fixed;
      color: #ff33cc;
      font-weight: bold;
      font-size: 1.2rem;
      animation: caer 5s linear forwards;
      pointer-events: none;
      text-shadow: 0 0 4px #ff33cc, 0 0 8px #ff66ff;
    }

    @keyframes caer {
      0% { transform: translateY(-50px); opacity: 1; }
      100% { transform: translateY(110vh); opacity: 0; }
    }

    .textoFlotante {
      position: fixed;
      font-size: 1.8rem;
      color: #ff33cc;
      text-shadow: 0 0 8px #ff33cc, 0 0 15px #ff66ff;
      pointer-events: none;
      animation: flotar 2s ease-out forwards;
    }

    @keyframes flotar {
      0% { opacity: 1; transform: translateY(0) scale(1); }
      100% { opacity: 0; transform: translateY(-100px) scale(1.3); }
    }

    .corazon {
      position: fixed;
      width: 14px;
      height: 14px;
      background: red;
      transform: rotate(45deg);
      animation: explotar 1.2s ease-out forwards;
    }

    .corazon::before,
    .corazon::after {
      content: '';
      position: absolute;
      width: 14px;
      height: 14px;
      background: red;
      border-radius: 50%;
    }

    .corazon::before {
      top: -7px;
      left: 0;
    }

    .corazon::after {
      top: 0;
      left: -7px;
    }

    @keyframes explotar {
      to {
        transform: translate(var(--x), var(--y)) scale(0.5);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

<div id="mensaje">Eres mi todo, Sandra 💖</div>

<script>
  const frases = [
    "Eres mi sol en días nublados ☀️", "Mi razón de sonreír 💖", "Te amo con el alma 💕",
    "Eres única 💎", "Contigo todo es mejor 🌈", "Mi princesa hermosa 👑", "Gracias por existir 🌟",
    "Eres el amor de mi vida 💞", "Siempre tú, mi todo ❤️", "Nunca dejes de brillar ✨",
    "Mi complemento perfecto 💑", "El destino nos unió 🌠", "Te amo hasta el infinito 🚀",
    "Cada segundo contigo vale oro 🕰️", "Eres magia pura 🪄", "Eres la melodía de mi vida 🎶",
    "Juntos, siempre 🌹", "Mi cielo, mi todo 🌌", "Tus ojos son mi paz 🥰", "Eres mi hogar 🏡",
    "No hay nadie como tú ❤️‍🔥", "Mi sueño hecho realidad 💫", "Tu sonrisa lo cura todo 🌷",
    "Te elijo mil veces más 💘", "Te amo sin medida 📏", "Mi corazón late por ti 💓",
    "Nuestro amor es eterno ⏳", "Me haces tan feliz 😍", "Mi locura favorita 🤪",
    "Cada día contigo es un regalo 🎁", "Gracias por tanto amor 💗",
    // ... agrega más si quieres
  ];

  let fraseIndex = 0;
  setInterval(() => {
    const mensaje = document.getElementById("mensaje");
    mensaje.textContent = frases[fraseIndex % frases.length];
    fraseIndex++;
  }, 5000);

  // Lluvia hacker de "Te amo"
  function crearTeAmoHacker() {
    const texto = document.createElement("div");
    texto.className = "teamo";
    texto.textContent = "Te amo";
    texto.style.left = Math.random() * window.innerWidth + "px";
    texto.style.top = "-30px";
    document.body.appendChild(texto);
    setTimeout(() => texto.remove(), 5000);
  }
  setInterval(crearTeAmoHacker, 150);

  // Al mover el dedo o mouse, crear textos flotantes
  let isDragging = false;
  let lastX = 0;
  let lastY = 0;

  function crearTextoFlotante(x, y) {
    lastX = x;
    lastY = y;

    const texto = document.createElement("div");
    texto.className = "textoFlotante";
    texto.textContent = "Te amo";
    texto.style.left = x + "px";
    texto.style.top = y + "px";
    document.body.appendChild(texto);

    setTimeout(() => texto.remove(), 2000);
  }

  function crearExplosion(x, y) {
    for (let i = 0; i < 10; i++) {
      const corazon = document.createElement("div");
      corazon.className = "corazon";
      corazon.style.left = x + "px";
      corazon.style.top = y + "px";

      const angle = Math.random() * Math.PI * 2;
      const distance = 60 + Math.random() * 30;
      corazon.style.setProperty("--x", `px`);
      corazon.style.setProperty("--y", `px`);

      document.body.appendChild(corazon);
      setTimeout(() => corazon.remove(), 1200);
    }
  }

  function onPointerDown(e) {
    isDragging = true;
    crearTextoFlotante(e.clientX, e.clientY);
  }

  function onPointerMove(e) {
    if (isDragging) {
      crearTextoFlotante(e.clientX, e.clientY);
    }
  }

  function onPointerUp() {
    isDragging = false;
    crearExplosion(lastX, lastY);
  }

  window.addEventListener("mousedown", onPointerDown);
  window.addEventListener("mousemove", onPointerMove);
  window.addEventListener("mouseup", onPointerUp);

  window.addEventListener("touchstart", e => {
    onPointerDown(e.touches[0]);
  }, { passive: true });

  window.addEventListener("touchmove", e => {
    onPointerMove(e.touches[0]);
  }, { passive: true });

  window.addEventListener("touchend", onPointerUp);
</script>
</body>
</html>ploading EspecialSM.html…]()
