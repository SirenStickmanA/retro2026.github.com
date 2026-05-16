<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <link rel="icon" type="image/png" href="icon.png">
    <title>ROBLOX.com - Online Building Toy</title>
    
    <style>
        body { background-color: #E1E1E1; font-family: Verdana, sans-serif; margin: 0; padding: 0; }
        .top-header { background-color: #000000; color: #FFF; padding: 4px 10px; display: flex; justify-content: space-between; align-items: center; font-size: 11px; }
        .top-header a { color: #FFF; text-decoration: none; }
        .top-header a:hover { text-decoration: underline; }
        .main-banner { background-color: #000080; padding: 10px; display: flex; align-items: center; border-bottom: 3px solid #E1E1E1; }
        .nav-bar { background-color: #ECECEC; border-top: 1px solid #FFF; border-bottom: 1px solid #A0A0A0; padding: 6px 15px; display: flex; gap: 20px; font-weight: bold; font-size: 13px; }
        .nav-bar a { color: #002E62; text-decoration: none; }
        .nav-bar a:hover { text-decoration: underline; }
        .main-layout { display: flex; padding: 15px; gap: 15px; background-color: #FFF; margin: 10px; border: 1px solid #A0A0A0; min-height: 500px; }
        .sidebar { width: 160px; background: #EFEFEF; border: 1px solid #A0A0A0; padding: 8px; font-size: 12px; }
        .sidebar b { color: #222; font-size: 13px; display: block; margin-bottom: 5px; }
        .sidebar a { color: #002E62; text-decoration: none; display: block; margin: 4px 0; }
        .sidebar a:hover { text-decoration: underline; }
        .sidebar hr { border: 0; border-top: 1px dashed #A0A0A0; margin: 10px 0; }
        .content { flex: 1; }
        .content h2 { font-size: 18px; color: #002E62; margin-top: 0; margin-bottom: 15px; border-bottom: 1px solid #A0A0A0; padding-bottom: 5px; }
        .game-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 15px; }
        .game-card { background: white; border: 1px solid #A0A0A0; padding: 8px; text-align: center; font-size: 12px; }
        .game-card b { color: #002E62; display: block; margin-bottom: 5px; }
        .game-card img { width: 100%; max-width: 180px; height: auto; border: 1px solid #A0A0A0; margin-bottom: 5px; display: inline-block; }
        .play-btn { display: block; margin: 5px auto 0 auto; background: url('PlayButton_Green.png') no-repeat center; background-size: contain; width: 64px; height: 64px; border: none; cursor: pointer; color: transparent; overflow: hidden; }
        .footer { text-align: center; font-size: 10px; color: #555; padding: 20px 0; border-top: 1px solid #A0A0A0; margin: 10px; }
        .footer a { color: #002E62; text-decoration: none; }
        .footer a:hover { text-decoration: underline; }

        /* --- INTERFACE INTEGRADA CABLOX + BUILDERFOUND V1.08 --- */
        .cablox-overlay { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0, 0, 0, 0.85); z-index: 9999; align-items: center; justify-content: center; }
        .cablox-modal { background: #E1E1E1; border: 3px double #FF0000; width: 420px; padding: 15px; font-family: Courier New, monospace; font-size: 11px; box-shadow: 5px 5px 0px #000; }
        .cablox-header { background: #000080; color: white; padding: 4px; font-weight: bold; font-size: 12px; text-align: center; margin-bottom: 10px; }
        .ia-box { background: #F0F0F0; border: 1px solid #A0A0A0; padding: 8px; margin-bottom: 8px; }
        .ia-title { font-weight: bold; color: #000080; border-bottom: 1px dashed #A0A0A0; margin-bottom: 4px; }
        .cablox-captcha-box { background: #FFF; border: 1px dashed #000; padding: 8px; text-align: center; font-size: 20px; font-weight: bold; letter-spacing: 5px; color: #FF0000; user-select: none; font-style: italic; background-image: linear-gradient(45deg, #ccc 25%, transparent 25%), linear-gradient(-45deg, #ccc 25%, transparent 25%); background-size: 10px 10px; margin: 8px 0; }
        .cablox-input { width: 92%; padding: 4px; border: 1px solid #A0A0A0; font-family: Courier New; font-weight: bold; margin-bottom: 8px; text-align: center; }
        .cablox-btn { background: #ECECEC; border: 1px solid #A0A0A0; padding: 6px 15px; font-weight: bold; cursor: pointer; display: block; width: 100%; font-family: Courier New; }
        .cablox-logs { background: #000; color: #00FF00; padding: 6px; font-size: 10px; height: 70px; overflow-y: auto; margin-top: 8px; text-align: left; }
    </style>
</head>
<body>

    <div id="cablox-screen" class="cablox-overlay">
        <div class="cablox-modal">
            <div class="cablox-header">🛡️ ROBLOX DOUBLE VERIFICATION MATRIX</div>
            
            <div class="ia-box">
                <div class="ia-title">🤖 [1] CaBlox AI Core v1.08</div>
                <div id="cablox-scan-details">Scanning browser software...</div>
            </div>

            <div class="ia-box">
                <div class="ia-title">🧱 [2] BuilderFound Behavior Scan</div>
                <div id="builderfound-scan-details">Analyzing physical device hardware...</div>
            </div>
            
            <div class="cablox-captcha-box" id="captcha-display">----</div>
            <input type="text" id="captcha-input" class="cablox-input" placeholder="Type Verification Code" autocomplete="off">
            
            <button class="cablox-btn" onclick="verificarCablox()">EXECUTE SECURITY APPROVAL</button>
            <div class="cablox-logs" id="cablox-log-box"></div>
        </div>
    </div>

    <div class="top-header">
        <span></span>
        <span id="header-auth-links">
            <a href="login.html">Login</a> | <a href="login.html">Register</a> | <a href="#">Help</a>
        </span>
    </div>

    <div class="main-banner"><img src="logo.png" height="40" alt="Roblox"></div>

    <div class="nav-bar">
        <a href="index.html">Home</a><a href="mypage.html">My Page</a><a href="maintenance.html">Games</a><a href="install.html">Install</a>
    </div>

    <div class="main-layout">
        <div class="sidebar" id="main-sidebar">
            <b>My ROBLOX</b><a href="login.html">Login</a><a href="login.html">Register</a><a href="character.html">Character</a><a href="forum.html">Forum</a>
            <hr>
            <p style="margin:0;">Users Online: <span id="online-counter" style="font-weight: bold;">--</span></p>
        </div>

        <div class="content">
            <h2>Featured Games</h2>
            <div class="game-grid">
                <div class="game-card">
                    <img src="ChaosCanyonSmall2.png" alt="Chaos Canyon"><b>Chaos Canyon</b>
                    <button class="play-btn" onclick="playOof('Chaos Canyon')">Play</button>
                </div>
                <div class="game-card">
                    <img src="screen1.png" alt="Building Room"><b>Building Room</b>
                    <button class="play-btn" onclick="playOof('Building Room')">Play</button>
                </div>
            </div>
        </div>
    </div>

    <div class="footer">ROBLOX, "Online Building Toy", characters, logos and trading dress are trademarks of ROBLOX Corporation.</div>

    <script src="wombat.js"></script>
    <script>
        let captchaGerado = "";
        let inputTouchDetectado = "Mouse Pointer"; 

        // Monitora fisicamente se o usuário encostou o dedo na tela para calibrar o BuilderFound
        window.addEventListener('touchstart', function dectetarDedo() {
            inputTouchDetectado = "Finger Touchscreen";
            window.removeEventListener('touchstart', dectetarDedo);
        });

        function playOof(nomeDoJogo) {
            var audio = new Audio('Oof.mp3');
            audio.play().catch(function(e) {});
            alert('Conectando ao Client de 2006... Aguarde.');
            window.location.href = "play.html?game=" + encodeURIComponent(nomeDoJogo);
        }

        function rodarVerificacoesDuplas() {
            const screen = document.getElementById('cablox-screen');
            if (sessionStorage.getItem('cablox_verified') === 'true') {
                screen.style.display = "none";
                inicializarSite();
                return;
            }
            screen.style.display = "flex";

            const ua = navigator.userAgent;

            // --- 1. SCANNER CABLOX AI v1.08 (Navegador e Dispositivo) ---
            let dispositivo = "PC";
            if (/Mobi|Android|iPhone/i.test(ua)) dispositivo = "Celular";
            else if (/Tablet|iPad/i.test(ua)) dispositivo = "Tablet";
            else if (/Macintosh|Windows/i.test(ua) && window.screen.width < 1100) dispositivo = "Notebook";

            let navegador = "Internet Explorer";
            if (ua.includes("Firefox") && !ua.includes("Seamonkey")) navegador = "Firefox";
            else if (ua.includes("MiBrowser")) navegador = "Mi Browser";
            else if (ua.includes("Opr/") || ua.includes("OPR") || ua.includes("Opera")) navegador = "Opera";
            else if (ua.includes("Edg/")) navegador = "Edge";
            else if (ua.includes("Chrome") && !ua.includes("Chromium")) navegador = "Chrome";
            else if (ua.includes("Safari") && !ua.includes("Chrome") && !ua.includes("Edg")) navegador = "Safari";

            document.getElementById('cablox-scan-details').innerHTML = `Browser: ${navegador} | Environment: ${dispositivo}`;

            // --- 2. SCANNER BUILDERFOUND AI (Análise Física Comportamental) ---
            // A. Detecção de Sistema Operacional Exato
            let so = "Unknown OS";
            if (ua.includes("Windows")) so = "Windows";
            else if (ua.includes("Android")) so = "Android";
            else if (/iPhone|iPad|iPod/.test(ua)) so = "iOS";
            else if (ua.includes("Macintosh")) so = "macOS";
            else if (ua.includes("Linux")) so = "Linux";

            // B. Detecção de Layout e Tamanhos de Botão recomendados
            let layoutLayout = (dispositivo === "Celular" || dispositivo === "Tablet") ? "Mobile UI Layout (Big Buttons)" : "Desktop UI Layout (Compact)";
            
            // C. Dedução de Teclado com base no SO
            let tecladoProvavel = "Standard PC Keyboard";
            if (so === "Android") tecladoProvavel = "Google Gboard Keyboard";
            else if (so === "iOS") tecladoProvavel = "Apple Virtual Keyboard";

            document.getElementById('builderfound-scan-details').innerHTML = `
                OS: ${so}<br>
                Layout Mode: ${layoutLayout}<br>
                Pointer Input: ${inputTouchDetectado}<br>
                Estimated Input: ${tecladoProvavel}
            `;

            // Lógica Heurística Atualizada (Opera é suspeito!)
            let suspeito = "Não";
            if (navegador === "Opera") suspeito = "Sim (ALERTA: Usuário de Opera!)";
            else if (dispositivo === "Celular") suspeito = "Sim (Acesso Mobile Remoto)";

            // Guardando tudo na caixinha (localStorage) dentro da chave Lock
            const fullReport = {
                timestamp: new Date().toLocaleString(),
                cablox: { browser: navegador, type: dispositivo },
                builderfound: { os: so, layout: layoutLayout, input: inputTouchDetectado, keyboard: tecladoProvavel },
                is_suspicious: suspeito
            };
            localStorage.setItem('Lock_cablox_scan', JSON.stringify(fullReport));

            // CAPTCHA
            const caracteres = "ABCDEFGHJKLMNOPQRSTUVWXYZ23456789";
            captchaGerado = "";
            for (let i = 0; i < 4; i++) {
                captchaGerado += caracteres.charAt(Math.floor(Math.random() * caracteres.length));
            }
            document.getElementById('captcha-display').innerText = captchaGerado;

            document.getElementById('cablox-log-box').innerHTML = `[INFO] CaBlox Engine V1.08 Online.<br>[INFO] BuilderFound Hardware Matcher Online.<br>[LOCK] Full tracking frame dispatched to localStorage://Lock.`;
        }

        function verificarCablox() {
            const input = document.getElementById('captcha-input').value.trim().toUpperCase();
            const logBox = document.getElementById('cablox-log-box');

            if (input === captchaGerado) {
                logBox.innerHTML += `<br><span style="color:#00FF00">[OK] BuilderFound e CaBlox Aprovaram o Dispositivo.</span>`;
                sessionStorage.setItem('cablox_verified', 'true');
                setTimeout(() => {
                    document.getElementById('cablox-screen').style.display = "none";
                    inicializarSite();
                }, 1000);
            } else {
                logBox.innerHTML += `<br><span style="color:#FF0000">[FAIL] Quebra de Matriz de Segurança. Recalibrando sensores...</span>`;
                setTimeout(() => rodarVerificacoesDuplas(), 1200);
            }
        }

        function inicializarSite() {
            let visitorId = localStorage.getItem('visitor_id') || Math.floor(Math.random() * 10000) + 1;
            localStorage.setItem('visitor_id', visitorId);

            const estaLogado = localStorage.getItem('is_logged_in') === 'true';
            const dadosUsuario = localStorage.getItem('roblox_user');
            const areaSidebar = document.getElementById('main-sidebar');
            const linksHeader = document.getElementById('header-auth-links');
            
            if (estaLogado && dadosUsuario) {
                const conta = JSON.parse(dadosUsuario);
                linksHeader.innerHTML = `Logged in as: <b>${conta.username}</b> | <a href="#" onclick="efetuarLogout()">Logout</a> | <a href="#">Help</a>`;
                areaSidebar.innerHTML = `
                    <b>My ROBLOX</b>
                    <p style="margin:5px 0; color:#002E62; font-weight:bold;">Hello, ${conta.username}!</p>
                    <span style="font-size:10px; color:#666; display:block; margin-bottom:5px;">Account ID: #${conta.id}</span>
                    <hr>
                    <a href="character.html">Character</a><a href="forum.html">Forum</a><a href="#" onclick="efetuarLogout()">Logout</a>
                    <hr>
                    <p style="margin:0;">Users Online: <span id="online-counter" style="font-weight: bold;">--</span></p>
                `;
            } else {
                linksHeader.innerHTML = `<a href="login.html">Login</a> | <a href="login.html">Register</a> | <a href="#">Help</a>`;
            }

            function gerenciarContadorOnline() {
                const horaAtual = new Date().getHours();
                let baseDeUsuarios = (horaAtual >= 0 && horaAtual < 6) ? 45 : (horaAtual >= 18 && horaAtual < 23) ? 135 : 80;
                const variacao = Math.floor(Math.random() * 21) - 10; 
                if (document.getElementById('online-counter')) document.getElementById('online-counter').innerText = baseDeUsuarios + variacao;
            }
            gerenciarContadorOnline();
            setInterval(gerenciarContadorOnline, 7000);
        }

        function efetuarLogout() {
            localStorage.removeItem('is_logged_in');
            window.location.reload();
        }

        window.onload = rodarVerificacoesDuplas;
    </script>
</body>
</html>
