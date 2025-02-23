
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Carrossel Giratório com Links de Afiliado</title>
  <style>
    /* Estilo geral */
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background-color: #000000;    
      color: #1eff00;
      margin: 0;
      padding: 0;
      overflow: hidden;
    }

    /* Título */
    .neon-title {
      font-size: 2rem;
      color: #ff0000;
      text-transform: uppercase;
      animation: neon 1.5s infinite alternate;
    }

    @keyframes neon {
      from {
        text-shadow: 0 0 5px #ff0000, 0 0 10px #36f007, 0 0 20px #15fc00, 0 0 40px #1900ff, 0 0 80px #f6fa00;
      }
      to {
        text-shadow: 0 0 10px #ff0202, 0 0 20px #5dfd00, 0 0 30px #0bff02, 0 0 50px #1000f7, 0 0 100px #e8f803;
      }
    }

    /* Instruções */
    .instructions {
      margin: 10px 0;
      font-size: 1rem;
    }

    /* Botão de controle */
    button {
      padding: 10px 20px;
      font-size: 1rem;
      background-color: #fc0000;
      color: #f7f2f2;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin: 10px;
    }

    button:hover {
      background-color: #48ff00;
    }

    /* Carrossel */
    .carousel-container {
      display: flex;
      justify-content: center;
      align-items: center;
      perspective: 1000px;
      height: 300px;
      margin-top: 20px;
    }

    .carousel {
      display: flex;
      justify-content: center;
      align-items: center;
      transform-style: preserve-3d;
      animation: rotate 20s linear infinite;
    }

    .carousel-item {
      position: absolute;
      width: 150px; /* Tamanho fixo para quadrados */
      height: 150px; /* Tamanho fixo para quadrados */
      transition: transform 0.5s ease;
      border: 2px solid #000000; /* Borda para destacar os quadrados */
      border-radius: 10px;
      overflow: hidden;
      box-shadow: 0 0 10px rgb(113, 252, 0);
    }

    .carousel-item img {
      width: 100%;
      height: 100%;
      object-fit: cover; /* Garante que a imagem preencha o quadrado sem distorção */
      border-radius: 10px;
      transition: transform 0.3s ease;
    }

    /* Efeito de zoom ao passar o mouse */
    .carousel-item:hover img {
      transform: scale(1.3);
    }

    /* Indicação de clique */
    .carousel-item::after {
      content: "Clique para Comprar";
      position: absolute;
      bottom: 10px;
      left: 50%;
      transform: translateX(-50%);
      font-size: 0.8rem;
      font-weight: bold;
      color: #080000;
      background-color: rgb(8, 255, 41);
      padding: 5px 10px;
      border-radius: 5px;
      opacity: 0;
      transition: opacity 0.3s ease;
    }

    .carousel-item:hover::after {
      opacity: 1;
    }

    /* Posicionamento das imagens em 3D */
    .carousel-item:nth-child(1) { transform: rotateY(0deg) translateZ(250px); }
    .carousel-item:nth-child(2) { transform: rotateY(45deg) translateZ(250px); }
    .carousel-item:nth-child(3) { transform: rotateY(90deg) translateZ(250px); }
    .carousel-item:nth-child(4) { transform: rotateY(135deg) translateZ(250px); }
    .carousel-item:nth-child(5) { transform: rotateY(180deg) translateZ(250px); }
    .carousel-item:nth-child(6) { transform: rotateY(225deg) translateZ(250px); }
    .carousel-item:nth-child(7) { transform: rotateY(270deg) translateZ(250px); }
    .carousel-item:nth-child(8) { transform: rotateY(315deg) translateZ(250px); }

    /* Animação de rotação automática */
    @keyframes rotate {
      from {
        transform: rotateY(0deg);
      }
      to {
        transform: rotateY(360deg);
      }
    }

    /* Frase única centralizada */
    .phrase-container {
      position: relative;
      height: 100px;
      margin-top: -50px; /* Aproxima da parte inferior do carrossel */
      perspective: 1000px;
    }

    .phrase {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: 1.5rem;
      font-weight: bold;
      text-transform: uppercase;
      opacity: 0;
      animation: fadeInOut 2s ease-in-out forwards;
    }

    /* Cores neon diferentes para cada frase */
    .phrase.red {
      color: #77ff4d;
      text-shadow: 0 0 5px #050000, 0 0 10px #ff0000, 0 0 20px #ff4da6, 0 0 40px #ff4da6;
    }

    .phrase.blue {
      color: #ff0000;
      text-shadow: 0 0 5px #ff0101, 0 0 10px #0011ff, 0 0 20px #00ffff, 0 0 40px #00ffff;
    }

    .phrase.green {
      color: #00ff00;
      text-shadow: 0 0 5px #000000, 0 0 10px #d2f702, 0 0 20px #00ff00, 0 0 40px #00ff00;
    }

    .phrase.purple {
      color: #008cff;
      text-shadow: 0 0 5px #000000, 0 0 10px #fc0505, 0 0 20px #8a2be2, 0 0 40px #8a2be2;
    }

    .phrase.orange {
      color: #d9ff00;
      text-shadow: 0 0 5px #070400, 0 0 10px #4c00ff, 0 0 20px #ffa500, 0 0 40px #ffa500;
    }

    /* Animação de aparecer e desaparecer */
    @keyframes fadeInOut {
      0% {
        opacity: 0;
      }
      10% {
        opacity: 1;
      }
      90% {
        opacity: 1;
      }
      100% {
        opacity: 0;
      }
    }

    /* Responsividade */
    @media (max-width: 768px) {
      .neon-title {
        font-size: 1.5rem;
      }

      .instructions {
        font-size: 0.9rem;
      }

      .carousel-item {
        width: 120px; /* Reduz o tamanho dos quadrados */
        height: 120px;
      }

      button {
        padding: 8px 16px;
        font-size: 0.9rem;
      }

      .phrase {
        font-size: 1.2rem;
      }

      .carousel-item::after {
        font-size: 0.7rem;
      }
    }

    @media (max-width: 480px) {
      .neon-title {
        font-size: 1.2rem;
      }

      .instructions {
        font-size: 0.8rem;
      }

      .carousel-item {
        width: 90px; /* Reduz ainda mais o tamanho dos quadrados */
        height: 90px;
      }

      button {
        padding: 6px 12px;
        font-size: 0.8rem;
      }

      .phrase {
        font-size: 1rem;
      }

      .carousel-item::after {
        font-size: 0.6rem;
      }
    }
  </style>
</head>
<body>
  <!-- Título -->
  <h1 class="neon-title">Shop das Ofertas</h1>

  <!-- Texto explicativo -->
  <p class="instructions">Gire o carrossel e veja nossas ofertas exclusivas!</p>

  <!-- Botão de pausa -->
  <button id="toggleButton">Pausar Carrossel</button>

  <!-- Carrossel -->
  <div class="carousel-container">
    <div class="carousel" id="carousel">
      <!-- Item 1 -->
      <a href="https://google.com" target="_blank" class="carousel-item">
        <img src="imagem8.jpg.jpg" alt="Produto 1">
      </a>
      <!-- Item 2 -->
      <a href="https://exemplo.com/produto2" target="_blank" class="carousel-item">
        <img src="imagem1.jpg.jpg"alt="Produto 2"> 
        
        " alt="Produto 2">
      </a>
      <!-- Item 3 -->
      <a href="https://exemplo.com/produto3" target="_blank" class="carousel-item">
        <img src="imagem3.jpg.jpg" alt="Produto 3">
      </a>
      <!-- Item 4 -->
      <a href="https://exemplo.com/produto4" target="_blank" class="carousel-item">
        <img src="imagem4.jpg.jpg" alt="Produto 4">
      </a>
      <!-- Item 5 -->
      <a href="https://exemplo.com/produto5" target="_blank" class="carousel-item">
        <img src="imagem5.jpg.jpg" alt="Produto 5">
      </a>
      <!-- Item 6 -->
      <a href="https://exemplo.com/produto6" target="_blank" class="carousel-item">
        <img src="imagem7.jpg.jpg" alt="Produto 6">
      </a>
      <!-- Item 7 -->
      <a href="https://exemplo.com/produto7" target="_blank" class="carousel-item">
        <img src="imagem9.jpg.jpg" alt="Produto 7">
      </a>
      <!-- Item 8 -->
      <a href="https://exemplo.com/produto8" target="_blank" class="carousel-item">
        <img src="imagem2.jpg.jpg" alt="Produto 8">
      </a>
    </div>
    </audio>
  </div>

  <!-- Frases únicas centralizadas -->
  <div class="phrase-container" id="phraseContainer"></div>

  <script>
    // Controle do carrossel
    let isPaused = false;
    const carousel = document.getElementById("carousel");
    const toggleButton = document.getElementById("toggleButton");

    // Pausar ou retomar a animação
    toggleButton.addEventListener("click", () => {
      isPaused = !isPaused;
      if (isPaused) {
        carousel.style.animationPlayState = "paused";
        toggleButton.textContent = "Iniciar Carrossel";
      } else {
        carousel.style.animationPlayState = "running";
        toggleButton.textContent = "Pausar Carrossel";
      }
    });

    // Frases e cores neon
    const phrases = [
      { text: "🔥 Compre Agora!", color: "red" },
      { text: "🛍️ Últimas Unidades!", color: "blue" },
      { text: "💰 Desconto Exclusivo!", color: "green" },
      { text: "📢 Promoção Imperdível!", color: "purple" },
      { text: "⏰ Aproveite Já!", color: "orange" },
      { text: "🌟 Qualidade Garantida!", color: "red" },
      { text: "💥 Compre Já!", color: "blue" },
      { text: "🎁 Frete Grátis!", color: "green" }
    ];

    let currentIndex = 0;

    function showPhrase() {
      const phraseContainer = document.getElementById("phraseContainer");

      // Remove a frase anterior
      phraseContainer.innerHTML = "";

      // Cria a nova frase
      const phraseElement = document.createElement("div");
      phraseElement.classList.add("phrase", phrases[currentIndex].color);
      phraseElement.textContent = phrases[currentIndex].text;

      // Adiciona a frase ao contêiner
      phraseContainer.appendChild(phraseElement);

      // Atualiza o índice para a próxima frase
      currentIndex = (currentIndex + 1) % phrases.length;
    }

    // Mostra uma frase a cada 2 segundos
    setInterval(showPhrase, 2000);
  </script>
</body>


</body>
  </html>
