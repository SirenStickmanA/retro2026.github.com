<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>ROBLOX.com - Online Building Toy</title>
    
    <style>
        body { background-color: #E1E1E1; font-family: Verdana, sans-serif; margin: 0; padding: 0; }
        .top-header { background-color: #000080; color: white; padding: 5px 10px; display: flex; justify-content: space-between; align-items: center; border-bottom: 2px solid #ff0000; }
        .nav-bar { background-color: #EEE; border-bottom: 1px solid #999; padding: 5px 10px; display: flex; gap: 15px; font-weight: bold; font-size: 13px; }
        .nav-bar a { color: black; text-decoration: none; }
        .main-layout { display: flex; padding: 15px; gap: 15px; }
        .sidebar { width: 160px; background: #f0f0f0; border: 1px solid #999; padding: 10px; font-size: 12px; }
        .content { flex: 1; }
        .game-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 10px; }
        .game-card { background: white; border: 1px solid #999; padding: 10px; text-align: center; }
        .game-card img { width: 100%; border: 1px solid #ccc; margin-bottom: 5px; }
        .play-btn { background: url('PlayButton_Green.png') no-repeat; background-size: contain; width: 100px; height: 30px; border: none; cursor: pointer; color: transparent; }
    </style>
</head>
<body>

    <div class="top-header">
        <img src="logo.png" height="35" alt="Roblox">
        <span><a href="Login/index.html" style="color: white; text-decoration: none;">Login</a> | Register | Help</span>
    </div>

    <div class="nav-bar">
        <a href="index.html">Home</a>
        <a href="MP/index.html">My Page</a>
        <a href="maintenance.html">Games</a>
        <a href="Install/index.html">Install</a>
    </div>

    <div class="main-layout">
        <div class="sidebar">
            <b>My ROBLOX</b><br><br>
            <a href="Login/index.html">Login</a><br>
            <a href="#">Character</a><br>
            <a href="#">Forum</a><br>
            <hr>
            <!-- O ID "online-counter" permite a atualização via Script -->
            <p>Users Online: <span id="online-counter" style="font-weight: bold;">42</span></p>
        </div>

        <div class="content">
            <h2 style="margin-top:0;">Featured Games</h2>
            <div class="game-grid">
                <div class="game-card">
                    <img src="ChaosCanyonSmall2.png" alt="Chaos Canyon">
                    <b>Chaos Canyon</b><br>
                    <button class="play-btn" onclick="playOof()">Play</button>
                </div>
                <div class="game-card">
                    <img src="screen1.png" alt="Building Room">
                    <b>Building Room</b><br>
                    <button class="play-btn" onclick="playOof()">Play</button>
                </div>
            </div>
        </div>
    </div>

    <script src="wombat.js"></script>
    <script>
        function playOof() {
            var audio = new Audio('Oof.mp3');
            audio.play();
            alert('Conectando ao Client de 2006... Aguarde.');
        }

        // Função do contador dinâmico em tempo real
        function updateOnlineCounter() {
            const date = new Date();
            const hour = date.getHours();
            let baseUsers;

            // Define tráfego dinâmico dependendo da hora do dia
            if (hour >= 0 && hour < 6) {
                baseUsers = 35; // Madrugada menos acessos
            } else if (hour >= 18 && hour < 23) {
                baseUsers = 110; // Pico a noite
            } else {
                baseUsers = 65; // Dia comercial
            }

            // Gera uma variação aleatória de +/- 12 usuários
            const fluctuation = Math.floor(Math.random() * 25) - 12;
            const finalCount = baseUsers + fluctuation;

            // Aplica o valor na tela
            document.getElementById('online-counter').innerText = finalCount;
        }

        // Roda ao carregar a página
        updateOnlineCounter();

        // Altera o número organicamente a cada 7 segundos sem recarregar
        setInterval(updateOnlineCounter, 7000);
    </script>
</body>
</html>
</div>

        <div class="content">
            <h2 style="margin-top:0;">Featured Games</h2>
            <div class="game-grid">
                <!-- Mapa 1: Chaos Canyon -->
                <div class="game-card">
                    <img src="images/ChaosCanyonLarge.png" alt="Chaos Canyon">
                    <b>Chaos Canyon</b><br>
                    <button class="play-btn" onclick="playOof()">Play</button>
                </div>
                <!-- Mapa 2: Building Room -->
                <div class="game-card">
                    <img src="images/BuildingRoomLarge.png" alt="Building Room">
                    <b>Building Room</b><br>
                    <button class="play-btn" onclick="playOof()">Play</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Scripts do seu projeto -->
    <script src="js/wombat.js"></script>
    <script>
        function playOof() {
            var audio = new Audio('Oof.mp3');
            audio.play();
            alert('Conectando ao Client de 2006... Aguarde.');
        }
    </script>
</body>
</html>

