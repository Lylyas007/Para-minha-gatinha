<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Para Minha Garota Hello Kitty 🎀</title>
    <!-- Fontes fofas e elegantes do Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Fredoka+One&family=Quicksand:wght@500;700&display=swap" rel="stylesheet">
    
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background-color: #ffeef2; /* Cor de fundo caso a imagem demore a carregar */
            background-image: url('fundo.jpg'); /* Sua foto da Hello Kitty aqui */
            background-repeat: repeat; /* Faz o padrão se repetir lindamente */
            background-size: 220px; /* Ajusta o tamanho dos desenhos na tela */
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
            background: rgba(255, 255, 255, 0.92); /* Fundo branco com leve transparência para destacar */
            padding: 35px 25px;
            border-radius: 25px;
            box-shadow: 0 10px 25px rgba(255, 182, 193, 0.6);
            border: 4px solid #ff6b8b;
            max-width: 90%;
            width: 350px;
            backdrop-filter: blur(2px); /* Efeito charmoso de vidro no fundo do card */
        }

        h1 {
            font-family: 'Fredoka One', cursive;
            color: #ff477e;
            font-size: 1.6rem;
            margin-bottom: 10px;
            letter-spacing: 0.5px;
        }

        .subtitle {
            font-size: 0.9rem;
            color: #666;
            margin-bottom: 30px;
            line-height: 1.4;
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
            font-size: 85px;
            color: #ff477e;
            display: inline-block;
            animation: pulse 1.4s infinite ease-in-out;
            filter: drop-shadow(0 4px 6px rgba(0,0,0,0.1));
        }

        .bow {
            position: absolute;
            top: -8px;
            right: -8px;
            font-size: 38px;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.12); }
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
            background: rgba(255, 192, 203, 0.75);
            backdrop-filter: blur(5px);
            -webkit-backdrop-filter: blur(5px);
            justify-content: center;
            align-items: center;
            z-index: 10;
            padding: 20px;
        }

        .modal-content {
            background: white;
            padding: 35px 25px;
            border-radius: 24px;
            border: 4px solid #ff477e;
            width: 100%;
            max-width: 330px;
            box-shadow: 0 12px 24px rgba(0,0,0,0.15);
            position: relative;
            animation: popUp 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        @keyframes popUp {
            from { transform: scale(0.7); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
        }

        .modal-text {
            font-size: 1.05rem;
            line-height: 1.6;
            color: #4a4a4a;
            font-weight: 700;
            text-align: left;
        }

        .close-btn {
            margin-top: 25px;
            background: #ff477e;
            color: white;
            border: none;
            padding: 10px 25px;
            border-radius: 18px;
            font-family: 'Fredoka One', cursive;
            font-size: 0.9rem;
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
        <p class="subtitle">Dê dois toques rápidos no coração para abrir um pensamento meu sobre nós</p>
        
        <div class="heart-box" id="heartButton">
            <span class="heart">❤️</span>
            <span class="bow">🎀</span>
        </div>
    </div>

    <!-- Janela de Declaração -->
    <div class="modal" id="loveModal">
        <div class="modal-content">
            <p class="modal-text" id="loveMessage">Texto romântico aqui!</p>
            <button class="close-btn" onclick="closeModal()">Guardar no coração 🌸</button>
        </div>
    </div>

    <script>
        const declaracoes = [
            "Nosso amor transcende a efemeridade do tempo. Como o laço característico que une os detalhes mais bonitos, nossas almas se entrelaçam em uma sinfonia discreta de afeto, respeito e profunda cumplicidade. Te amo além das palavras vazias. 🎀✨",
            "Amar você é encontrar poesia e ordem no caos do mundo. É perceber que, entre tantas órbitas aleatórias e acasos do destino, a nossa conexão é a constante mais bonita, terna e significativa do meu universo. 🌌❤️",
            "Dizia um antigo pensamento que o amor verdadeiro é composto por uma única alma que escolhe habitar dois corpos. Em cada detalhe da sua existência, encontro a delicadeza e a força que dão um sentido inteiramente novo à minha. 🌸🍂",
            "Você tem o dom raro de transformar a simplicidade dos dias comuns em momentos eternos. O laço que nos une não é apenas um adorno do acaso, mas a própria essência de tudo aquilo que escolho cuidar, proteger e amar todos os dias. 🐱💝",
            "Entre a imensidão incompreensível do tempo e o infinito do espaço, a minha maior certeza e o meu porto seguro é o privilégio de compartilhar a vida com você. Você é o meu recomeço mais bonito e o meu capítulo favorito. 📖💞",
            "O amor não reside apenas nos grandes cenários, mas na beleza das pequenas constâncias. Estar com você é compreender que os sentimentos mais profundos se manifestam nos sorrisos sinceros e na doçura de saber que pertencemos um ao outro. 💌🌹"
        ];

        const heartButton = document.getElementById('heartButton');
        const loveModal = document.getElementById('loveModal');
        const loveMessage = document.getElementById('loveMessage');

        let lastTap = 0;

        heartButton.addEventListener('touchstart', function (e) {
            let currentTime = new Date().getTime();
            let tapLength = currentTime - lastTap;
            
            if (tapLength < 300 && tapLength > 0) {
                openDeclaration();
                e.preventDefault(); 
            }
            lastTap = currentTime;
        });

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
