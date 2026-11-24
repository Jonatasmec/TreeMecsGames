<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TreeMecsGames | Loja & Arcade</title>
    <!-- Fontes retrô / pixel -->
    <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=VT323&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-dark: #0d0818;
            --purple-main: #6a0dad;
            --purple-bright: #9d4edd;
            --purple-neon: #c77dff;
            --blue-retro: #240046;
            --window-border: #b583ff;
            --window-header: linear-gradient(90deg, #3c096c, #7b2cbf);
            --text-light: #f8f9fa;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background-color: var(--bg-dark);
            background-image: linear-gradient(rgba(13, 8, 24, 0.75), rgba(13, 8, 24, 0.9)), url('assets/bg.png');
            background-size: cover;
            background-attachment: fixed;
            background-position: center;
            color: var(--text-light);
            font-family: 'VT323', monospace;
            font-size: 1.3rem;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        /* Estilo Janela Vaporwave Retrô (Baseado na sua moldura) */
        .retro-window {
            background: rgba(20, 11, 41, 0.92);
            border: 4px solid var(--window-border);
            box-shadow: 6px 6px 0px #000000, inset 0 0 15px rgba(157, 78, 221, 0.3);
            border-radius: 4px;
            overflow: hidden;
        }

        .window-bar {
            background: var(--window-header);
            padding: 6px 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 4px solid var(--window-border);
            font-family: 'Press Start 2P', cursive;
            font-size: 0.7rem;
            letter-spacing: 1px;
        }

        .window-close {
            background: #e0aaff;
            color: #10002b;
            border: 2px solid #000;
            width: 22px;
            height: 22px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-family: sans-serif;
            cursor: default;
            user-select: none;
        }

        /* Cabeçalho & Navegação */
        header {
            background: rgba(16, 0, 43, 0.95);
            border-bottom: 4px solid var(--purple-bright);
            padding: 15px 5%;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            gap: 15px;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .brand {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .brand img {
            height: 55px;
            filter: drop-shadow(0 0 8px var(--purple-neon));
        }

        .brand h1 {
            font-family: 'Press Start 2P', cursive;
            font-size: 1.2rem;
            color: #fff;
            text-shadow: 3px 3px 0px var(--purple-main);
        }

        .brand span {
            color: var(--purple-neon);
        }

        nav {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .nav-btn {
            background: #240046;
            color: #fff;
            border: 3px solid var(--purple-neon);
            padding: 8px 16px;
            font-family: 'Press Start 2P', cursive;
            font-size: 0.7rem;
            cursor: pointer;
            transition: 0.15s;
            box-shadow: 3px 3px 0px #000;
        }

        .nav-btn:hover, .nav-btn.active {
            background: var(--purple-bright);
            transform: translate(-2px, -2px);
            box-shadow: 5px 5px 0px #000;
        }

        /* Hero Banner com Mascotes */
        .hero {
            max-width: 1200px;
            margin: 30px auto 10px;
            padding: 0 20px;
            width: 100%;
        }

        .hero-content {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 25px;
            gap: 20px;
            flex-wrap: wrap;
        }

        .hero-text {
            flex: 1;
            min-width: 280px;
        }

        .hero-text h2 {
            font-family: 'Press Start 2P', cursive;
            font-size: 1.3rem;
            color: var(--purple-neon);
            margin-bottom: 15px;
            line-height: 1.5;
        }

        .hero-mascots {
            display: flex;
            align-items: flex-end;
            gap: 10px;
        }

        .hero-mascots img {
            height: 140px;
            object-fit: contain;
            filter: drop-shadow(0 5px 10px rgba(0,0,0,0.8));
            transition: transform 0.3s;
        }

        .hero-mascots img:hover {
            transform: translateY(-8px) scale(1.05);
        }

        /* Container Principal */
        main {
            max-width: 1200px;
            margin: 20px auto;
            padding: 0 20px;
            width: 100%;
            flex: 1;
        }

        .tab-section {
            display: none;
        }

        .tab-section.active {
            display: block;
            animation: fadeIn 0.3s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Barra de Pesquisa */
        .search-container {
            margin-bottom: 25px;
            display: flex;
            gap: 10px;
        }

        .search-input {
            width: 100%;
            padding: 12px 18px;
            background: #10002b;
            border: 3px solid var(--purple-neon);
            color: #fff;
            font-family: 'VT323', monospace;
            font-size: 1.5rem;
            outline: none;
            box-shadow: 4px 4px 0px #000;
        }

        .search-input::placeholder {
            color: #9d4edd;
        }

        /* Grid de Jogos (Loja) */
        .games-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(330px, 1fr));
            gap: 25px;
        }

        .game-card {
            display: flex;
            flex-direction: column;
            transition: transform 0.2s;
        }

        .game-card:hover {
            transform: translateY(-5px);
        }

        /* Área de Live Preview (Roda o jogo sem controles) */
        .game-preview-wrapper {
            position: relative;
            width: 100%;
            height: 220px;
            background: #000;
            overflow: hidden;
            cursor: pointer;
            border-bottom: 4px solid var(--window-border);
        }

        /* Escala o iframe para caber como miniatura e bloqueia cliques/teclado */
        .game-preview-wrapper iframe {
            width: 200%;
            height: 200%;
            border: none;
            transform: scale(0.5);
            transform-origin: 0 0;
            pointer-events: none; /* Impede de controlar na capa */
        }

        /* Camada invisível clicável sobre o iframe */
        .preview-overlay {
            position: absolute;
            inset: 0;
            background: rgba(16, 0, 43, 0.25);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: background 0.2s;
        }

        .game-preview-wrapper:hover .preview-overlay {
            background: rgba(106, 13, 173, 0.45);
        }

        .play-badge {
            background: #10002b;
            border: 3px solid #fff;
            color: #fff;
            padding: 10px 18px;
            font-family: 'Press Start 2P', cursive;
            font-size: 0.75rem;
            box-shadow: 4px 4px 0px #000;
            opacity: 0.9;
            transition: transform 0.2s;
        }

        .game-preview-wrapper:hover .play-badge {
            transform: scale(1.1);
            background: var(--purple-bright);
        }

        .game-info {
            padding: 18px;
            display: flex;
            flex-direction: column;
            gap: 10px;
            flex: 1;
            justify-content: space-between;
        }

        .game-title {
            font-family: 'Press Start 2P', cursive;
            font-size: 0.95rem;
            color: var(--purple-neon);
        }

        .game-desc {
            color: #e0aaff;
            line-height: 1.3;
        }

        .btn-play-full {
            background: var(--purple-bright);
            color: #fff;
            border: 3px solid #fff;
            padding: 10px;
            font-family: 'Press Start 2P', cursive;
            font-size: 0.75rem;
            cursor: pointer;
            text-align: center;
            box-shadow: 3px 3px 0px #000;
            margin-top: 8px;
        }

        .btn-play-full:hover {
            background: #7b2cbf;
        }

        /* Aba Sugestões */
        .suggestions-box {
            max-width: 650px;
            margin: 0 auto;
        }

        .form-group {
            padding: 20px;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .form-group label {
            font-family: 'Press Start 2P', cursive;
            font-size: 0.75rem;
            color: var(--purple-neon);
        }

        .form-group input, .form-group textarea {
            background: #10002b;
            border: 3px solid var(--purple-neon);
            color: #fff;
            padding: 12px;
            font-family: 'VT323', monospace;
            font-size: 1.4rem;
            outline: none;
        }

        .form-group textarea {
            min-height: 140px;
            resize: vertical;
        }

        /* Modal onde o jogo abre de verdade */
        #game-modal {
            display: none;
            position: fixed;
            inset: 0;
            background: rgba(0, 0, 0, 0.88);
            z-index: 999;
            padding: 20px;
            align-items: center;
            justify-content: center;
        }

        #game-modal.open {
            display: flex;
        }

        .modal-window {
            width: 100%;
            max-width: 1100px;
            height: 85vh;
            display: flex;
            flex-direction: column;
        }

        .modal-controls {
            display: flex;
            gap: 10px;
        }

        .modal-btn {
            background: #e0aaff;
            color: #10002b;
            border: 2px solid #000;
            padding: 2px 8px;
            font-family: 'Press Start 2P', cursive;
            font-size: 0.65rem;
            cursor: pointer;
        }

        .modal-btn.close-red {
            background: #ff4d6d;
            color: #fff;
        }

        #active-game-frame {
            width: 100%;
            height: 100%;
            border: none;
            background: #000;
            flex: 1;
        }

        /* Rodapé com os ADMs */
        footer {
            background: rgba(16, 0, 43, 0.96);
            border-top: 4px solid var(--purple-bright);
            padding: 25px 5%;
            margin-top: 50px;
            text-align: center;
        }

        .adm-list {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 15px;
            margin: 15px 0;
        }

        .adm-badge {
            background: #240046;
            border: 2px solid var(--purple-neon);
            padding: 6px 14px;
            font-family: 'Press Start 2P', cursive;
            font-size: 0.65rem;
            color: #e0aaff;
            box-shadow: 3px 3px 0px #000;
        }

        .copyright {
            font-size: 1.1rem;
            color: #9d4edd;
            margin-top: 10px;
        }
    </style>
</head>
<body>

    <!-- Cabeçalho -->
    <header>
        <div class="brand">
            <img src="assets/logo.png" alt="TreeMecs Studios Mascote" onerror="this.style.display='none'">
            <h1>TreeMecs<span>Games</span></h1>
        </div>
        <nav>
            <button class="nav-btn active" onclick="switchTab('loja', this)">🕹️ LOJA / JOGOS</button>
            <button class="nav-btn" onclick="switchTab('sugestoes', this)">✉️ SUGESTÕES</button>
        </nav>
    </header>

    <!-- Banner do Estúdio -->
    <section class="hero">
        <div class="retro-window">
            <div class="window-bar">
                <span>TreeMecs_OS.exe - Bem-vindo</span>
                <div class="window-close">X</div>
            </div>
            <div class="hero-content">
                <div class="hero-text">
                    <h2>JOGUE DIRETO NO NAVEGADOR!</h2>
                    <p>Explore os jogos criados pela equipe <strong>TreeMecsGames</strong>. Passe o mouse ou clique em qualquer janela abaixo para entrar no jogo em tela cheia.</p>
                </div>
                <div class="hero-mascots">
                    <img src="assets/robo-arvore.png" alt="Mascote Robô Árvore" onerror="this.style.display='none'">
                    <img src="assets/robo-tv.png" alt="Mascote Monitor" onerror="this.style.display='none'">
                    <img src="assets/monstro.png" alt="Monstro Telecom" onerror="this.style.display='none'">
                </div>
            </div>
        </div>
    </section>

    <main>
        <!-- ABA 1: LOJA DE JOGOS -->
        <section id="tab-loja" class="tab-section active">
            <!-- Aba de Pesquisa -->
            <div class="search-container">
                <input type="text" id="searchInput" class="search-input" placeholder="🔍 Pesquisar jogos na TreeMecsGames..." onkeyup="filterGames()">
            </div>

            <div class="games-grid" id="gamesGrid">
                
                <!-- JOGO 1: Orb Rush -->
                <div class="retro-window game-card" data-name="orb rush">
                    <div class="window-bar">
                        <span>Orb_Rush.html</span>
                        <div class="window-close">X</div>
                    </div>
                    <!-- Preview ao vivo do jogo sem controles -->
                    <div class="game-preview-wrapper" onclick="openGame('Orb Rush', 'Jogos em Html/Orb Rush/index.html')">
                        <iframe src="Jogos em Html/Orb Rush/index.html" scrolling="no" tabindex="-1"></iframe>
                        <div class="preview-overlay">
                            <span class="play-badge">▶ JOGAR AGORA</span>
                        </div>
                    </div>
                    <div class="game-info">
                        <div>
                            <h3 class="game-title">Orb Rush</h3>
                            <p class="game-desc">Desvie dos obstáculos em alta velocidade neste desafio arcade frenético!</p>
                        </div>
                        <button class="btn-play-full" onclick="openGame('Orb Rush', 'Jogos em Html/Orb Rush/index.html')">ABRIR JOGO</button>
                    </div>
                </div>

                <!-- JOGO 2: Padaria e Patos -->
                <div class="retro-window game-card" data-name="padaria e patos">
                    <div class="window-bar">
                        <span>Padaria_e_Patos.html</span>
                        <div class="window-close">X</div>
                    </div>
                    <div class="game-preview-wrapper" onclick="openGame('Padaria e Patos', 'Jogos em Html/Padaria e Patos/index.html')">
                        <iframe src="Jogos em Html/Padaria e Patos/index.html" scrolling="no" tabindex="-1"></iframe>
                        <div class="preview-overlay">
                            <span class="play-badge">▶ JOGAR AGORA</span>
                        </div>
                    </div>
                    <div class="game-info">
                        <div>
                            <h3 class="game-title">Padaria e Patos</h3>
                            <p class="game-desc">Gerencie os pães e atenda os patos mais exigentes da cidade.</p>
                        </div>
                        <button class="btn-play-full" onclick="openGame('Padaria e Patos', 'Jogos em Html/Padaria e Patos/index.html')">ABRIR JOGO</button>
                    </div>
                </div>

                <!-- JOGO 3: patos no lago -->
                <div class="retro-window game-card" data-name="patos no lago">
                    <div class="window-bar">
                        <span>patos_no_lago.html</span>
                        <div class="window-close">X</div>
                    </div>
                    <div class="game-preview-wrapper" onclick="openGame('Patos no Lago', 'Jogos em Html/patos no lago/index.html')">
                        <iframe src="Jogos em Html/patos no lago/index.html" scrolling="no" tabindex="-1"></iframe>
                        <div class="preview-overlay">
                            <span class="play-badge">▶ JOGAR AGORA</span>
                        </div>
                    </div>
                    <div class="game-info">
                        <div>
                            <h3 class="game-title">Patos no Lago</h3>
                            <p class="game-desc">Relaxe ou encare aventuras aquáticas controlando patos no lago.</p>
                        </div>
                        <button class="btn-play-full" onclick="openGame('Patos no Lago', 'Jogos em Html/patos no lago/index.html')">ABRIR JOGO</button>
                    </div>
                </div>

            </div>
        </section>

        <!-- ABA 2: SUGESTÕES (Envia sem expor o e-mail visualmente na tela) -->
        <section id="tab-sugestoes" class="tab-section">
            <div class="retro-window suggestions-box">
                <div class="window-bar">
                    <span>Enviar_Sugestao.exe</span>
                    <div class="window-close">X</div>
                </div>
                <!-- Utiliza FormSubmit para enviar direto para sua caixa de entrada sem exibir seu endereço -->
                <form class="form-group" action="https://formsubmit.co/Jonatassouzapaiva632@gmail.com" method="POST">
                    <!-- Configurações ocultas do formulário -->
                    <input type="hidden" name="_subject" value="Nova Sugestão - TreeMecsGames!">
                    <input type="hidden" name="_captcha" value="false">

                    <p>Tem alguma ideia de jogo novo, encontrou algum bug ou quer mandar um salve pra equipe? Escreva abaixo!</p>

                    <label for="playerName">Seu Nome / Nick:</label>
                    <input type="text" id="playerName" name="Nome" placeholder="Ex: Player123" required>

                    <label for="gameTopic">Assunto ou Jogo:</label>
                    <input type="text" id="gameTopic" name="Assunto" placeholder="Ex: Ideia para Orb Rush" required>

                    <label for="message">Sua Mensagem:</label>
                    <textarea id="message" name="Mensagem" placeholder="Digite sua sugestão aqui..." required></textarea>

                    <button type="submit" class="btn-play-full">🚀 ENVIAR SUGESTÃO</button>
                </form>
            </div>
        </section>
    </main>

    <!-- Modal para jogar de verdade -->
    <div id="game-modal">
        <div class="retro-window modal-window">
            <div class="window-bar">
                <span id="modal-game-title">Jogando...</span>
                <div class="modal-controls">
                    <button class="modal-btn" onclick="toggleFullscreen()">[ TELA CHEIA ]</button>
                    <button class="modal-btn close-red" onclick="closeGame()">X</button>
                </div>
            </div>
            <iframe id="active-game-frame" src=""></iframe>
        </div>
    </div>

    <!-- Rodapé com a equipe de ADMs -->
    <footer>
        <p style="font-family: 'Press Start 2P', cursive; font-size: 0.75rem; color: #fff;">EQUIPE TREEMECSGAMES</p>
        <div class="adm-list">
            <span class="adm-badge">👑 Adm Jonatas</span>
            <span class="adm-badge">🛡️ Adm Guilherme</span>
            <span class="adm-badge">🛡️ Adm Diogo</span>
            <span class="adm-badge">🛡️ Adm Carlos</span>
        </div>
        <p class="copyright">© 2026 TreeMecsGames Studio - Todos os direitos reservados.</p>
    </footer>

    <script>
        // Alternar entre as abas Loja e Sugestões
        function switchTab(tabName, btnElement) {
            document.querySelectorAll('.tab-section').forEach(sec => sec.classList.remove('active'));
            document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
            
            document.getElementById('tab-' + tabName).classList.add('active');
            btnElement.classList.add('active');
        }

        // Filtro de pesquisa em tempo real
        function filterGames() {
            const query = document.getElementById('searchInput').value.toLowerCase();
            const cards = document.querySelectorAll('.game-card');

            cards.forEach(card => {
                const name = card.getAttribute('data-name');
                if (name.includes(query)) {
                    card.style.display = 'flex';
                } else {
                    card.style.display = 'none';
                }
            });
        }

        // Abrir o jogo jogável no modal
        function openGame(title, path) {
            const modal = document.getElementById('game-modal');
            const frame = document.getElementById('active-game-frame');
            const titleEl = document.getElementById('modal-game-title');

            titleEl.textContent = "TreeMecsGames - " + title;
            frame.src = path;
            modal.classList.add('open');
        }

        // Fechar o jogo e parar o som/execução
        function closeGame() {
            const modal = document.getElementById('game-modal');
            const frame = document.getElementById('active-game-frame');

            frame.src = "";
            modal.classList.remove('open');
        }

        // Botão de Tela Cheia dentro do jogo
        function toggleFullscreen() {
            const frame = document.getElementById('active-game-frame');
            if (frame.requestFullscreen) {
                frame.requestFullscreen();
            } else if (frame.webkitRequestFullscreen) {
                frame.webkitRequestFullscreen();
            }
        }
    </script>
</body>
</html>
