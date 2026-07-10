<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Para Minha Garota Hello Kitty 🎀</title>
    <!-- Fonte fofa e elegante do Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Fredoka+One&family=Quicksand:wght@500;700&display=swap" rel="stylesheet">
    
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background-color: #ffeef2; /* Rosa pastel da Hello Kitty */
            background-image: radial-gradient(#ffb6c1 15%, transparent 16%), radial-gradient(#ffb6c1 15%, transparent 16%);
            background-size: 30px 30px;
            background-position: 0 0, 15px 15px; /* Estampa de bolinhas fofa */
            font-family: 'Quicksand', sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            overflow: hidden;
            color: #4a4a4a;
            text-align: center;
        }

        .container {
            background: rgba(255, 255, 255, 0.9);
            padding: 30px;
            border-radius: 25px;
            box-shadow: 0 10px 20px rgba(255, 182, 193, 0.5);
            border: 4px solid #ff6b8b;
            max-width: 90%;
            width: 350px;
        }

        h1 {
            font-family: 'Fredoka One', cursive;
            color: #ff477e;
            font-size: 1.6rem;
            margin-bottom: 10px;
        }

        .subtitle {
            font-size: 0.9rem;
            color: #777;
            margin-bottom: 25px;
        }

        /* O Coração Principal */
        .heart-box {
            position: relative;
            display: inline-block;
            cursor: pointer;
            user-select: none;
            -webkit-user-select: none;
        }

        .heart {
            font-size: 80px;
            color: #ff477e;
            display: inline-block;
            animation: pulse 1.2s infinite;
            filter: drop-shadow(0 4px 6px rgba(0,0,0,0.1));
        }

        .bow {
            position: absolute;
            top: -10px;
            right: -10px;
            font-size: 35px;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.15); }
            100% { transform: scale(1); }
        }

        /* Modal (Janela que abre com o texto) */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(255, 192, 203, 0.7);
            backdrop-filter: blur(4px);
            justify-content: center;
            align-items: center;
            z-index: 10;
            padding: 20px;
        }

        .modal-content {
            background: white;
            padding: 35px 25px;
            border-radius: 20px;
            border: 4px solid #ff477e;
            width: 100%;
            max-width: 340px;
            box-shadow: 0 8px 16px rgba(0,0,0,0.2);
            position: relative;
            animation: popUp 0.3s ease-out;
        }

        @keyframes popUp {
            from { transform: scale(0.7); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
        }

        .modal-text {
            font-size: 1.05rem;
            line-height: 1.6;
            color: #3d3d3d;
            font-weight: 500;
        }

        .close-btn {
            margin-top: 25px;
            background: #ff477e;
            color: white;
            border: none;
            padding: 10px 24px;
            border-radius: 15px;
            font-family: 'Fredoka One', cursive;
            cursor: pointer;
            box-shadow: 0 4px 0 #d13160;
            transition: 0.1s;
        }

        .close-btn:active {
            transform: translateY(4px);
            box-shadow: none;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Para o Meu Amor 🐱🎀</h1>
        <p class="subtitle">Dê dois toques rápidos no coração abaixo</p>
        
        <div class="heart-box" id="heartButton">
            <span class="heart">❤️</span>
            <span class="bow">🎀</span>
        </div>
    </div>

    <!-- Janela de Declaração -->
    <div class="modal" id="loveModal">
        <div class="modal-content">
            <p class="modal-text" id="loveMessage">Texto romântico aqui!</p>
            <button class="close-btn" onclick="closeModal()">Fechar 🌸</button>
        </div>
    </div>

    <script>
        // Lista de declarações aleatórias com teor mais elaborado e filosófico
        const declaracoes = [
            "Amar você é compreender que o infinito pode caber no espaço de um abraço. Assim como a delicadeza de um laço fofo, nossa conexão é a força sutil que dá sentido e ordem ao caos do meu universo. 🎀✨",
            "Entre todas as infinitas possibilidades do tempo, do espaço e do acaso, meu coração escolheu sintonizar com o seu compasso. Você é a poesia mais bonita e profunda que a existência escreveu na minha história. ❤️⏳",
            "O filósofo Espinosa dizia que a alegria expande a nossa alma. Estar com você é viver nessa expansão constante, onde cada risada boba se torna uma obra de arte e o cotidiano ganha nuances de um eterno entardecer cor-de-rosa. 🌸🌅",
            "Você é a minha tradução mais sincera de lar. Nosso amor tem a leveza das coisas puras e intocadas, mas carrega a profundidade misteriosa dos sentimentos que parecem existir muito antes de nós nascermos. 💖🏛️",
            "Filosofar sobre o amor é redundante quando posso simplesmente deitar no seu colo e sentir a paz do mundo silenciar ao nosso redor. Você transforma a simplicidade de existir em algo absolutamente extraordinário. 🥰💫",
            "Nossos caminhos não se cruzaram por uma mera coincidência geográfica; nós nos encontramos porque nossas almas conversam na mesma melodia fofa, doce e eterna, construindo um refúgio que é só nosso. 🐱💘"
        ];

        const heartButton = document.getElementById('heartButton');
        const loveModal = document.getElementById('loveModal');
        const loveMessage = document.getElementById('loveMessage');

        let lastTap = 0;

        // Função para detectar os dois toques (Double Tap) no celular de forma precisa
        heartButton.addEventListener('touchstart', function (e) {
            let currentTime = new Date().getTime();
            let tapLength = currentTime - lastTap;
            
            if (tapLength < 300 && tapLength > 0) {
                openDeclaration();
                e.preventDefault(); // Evita o zoom automático do navegador ao dar duplo toque
            }
            lastTap = currentTime;
        });

        // Alternativa para desktop/computador
        heartButton.addEventListener('dblclick', function () {
            openDeclaration();
        });

        function openDeclaration() {
            const randomIndex = Math.floor(Math.random() * declaracoes.length);
            loveMessage.innerHTML = declaracoes[randomIndex];
            loveModal.style.display = 'flex';
        }

        function closeModal() {
            loveModal.style.display = 'none';
        }
    </script>
</body>
</html>

atualizado frases
