<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mis 15 Años - Scarlet Mishell</title>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700&family=Great+Vibes&family=Montserrat:wght@300;400;500&display=swap" rel="stylesheet">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            background-color: #05020a;
            color: #f3e5ab;
            font-family: 'Montserrat', sans-serif;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            position: relative;
        }
        .sparkles-bg {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; z-index: 2; overflow: hidden;
        }
        .sparkle {
            position: absolute;
            background: radial-gradient(circle, #fffdf0 0%, #ffd700 60%, rgba(212,175,55,0) 100%);
            border-radius: 50%;
            animation: fall linear infinite;
        }
        @keyframes fall {
            0% { transform: translateY(-20px) scale(0.3); opacity: 0; }
            50% { opacity: 0.8; }
            100% { transform: translateY(105vh) scale(1); opacity: 0; }
        }
        .invitation-container {
            position: relative; z-index: 20; width: 90%; max-width: 420px;
            background: linear-gradient(135deg, #120826 0%, #0d0518 100%);
            border: 2px solid #d4af37; border-radius: 20px;
            box-shadow: 0 0 30px rgba(212, 175, 55, 0.4), inset 0 0 20px rgba(212, 175, 55, 0.15);
            padding: 30px 20px; text-align: center; overflow: hidden;
        }
        #envelope-screen {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            background: linear-gradient(145deg, #1a0b36 0%, #0a0314 100%);
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            z-index: 30; transition: opacity 0.8s ease, transform 0.8s ease; padding: 20px;
        }
        .envelope-title {
            font-family: 'Cinzel', serif; font-size: 1.4rem; color: #ffd700; margin-bottom: 25px;
            text-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
        }
        .lamp-container {
            position: relative; cursor: pointer; animation: floatLamp 3s ease-in-out infinite;
        }
        @keyframes floatLamp {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        .magic-lamp {
            width: 120px; filter: drop-shadow(0 0 15px rgba(255, 215, 0, 0.6));
        }
        .smoke-plume {
            position: absolute; top: -45px; left: 75px; width: 30px; height: 60px;
            background: radial-gradient(circle, rgba(255,255,255,0.7) 0%, rgba(212,175,55,0.3) 50%, rgba(0,0,0,0) 80%);
            border-radius: 50%; filter: blur(8px); opacity: 0; animation: riseSmoke 2.5s infinite ease-in-out;
        }
        @keyframes riseSmoke {
            0% { transform: translateY(10px) scale(0.5); opacity: 0; }
            50% { opacity: 0.8; }
            100% { transform: translateY(-40px) scale(1.8); opacity: 0; }
        }
        .open-seal-btn {
            margin-top: 30px; background: linear-gradient(135deg, #ffd700 0%, #d4af37 100%);
            color: #120826; border: none; padding: 12px 25px; font-family: 'Cinzel', serif;
            font-weight: 700; font-size: 0.95rem; border-radius: 30px; cursor: pointer;
            box-shadow: 0 4px 15px rgba(212, 175, 55, 0.4); transition: transform 0.3s ease;
        }
        .open-seal-btn:hover { transform: scale(1.05); }
        .content-screen {
            opacity: 0; transform: scale(0.95); transition: opacity 1s ease, transform 1s ease; pointer-events: none;
        }
        .content-screen.active { opacity: 1; transform: scale(1); pointer-events: auto; }
        .header-sub { font-family: 'Cinzel', serif; font-size: 0.85rem; letter-spacing: 3px; color: #d4af37; margin-bottom: 5px; }
        .main-title { font-family: 'Great Vibes', cursive; font-size: 2.8rem; color: #fffdf0; text-shadow: 0 0 15px rgba(255, 215, 0, 0.6); margin-bottom: 15px; }
        .name {
            font-family: 'Cinzel', serif; font-size: 1.6rem; font-weight: 700; color: #ffd700; letter-spacing: 2px;
            margin-bottom: 20px; border-bottom: 1px solid rgba(212, 175, 55, 0.4); border-top: 1px solid rgba(212, 175, 55, 0.4); padding: 10px 0;
        }
        .message { font-size: 0.9rem; line-height: 1.6; color: #e0d5c1; margin-bottom: 20px; }
        .event-details {
            background: rgba(26, 11, 54, 0.6); border: 1px solid rgba(212, 175, 55, 0.3); border-radius: 12px; padding: 15px; margin-bottom: 20px;
        }
        .event-details h3 { font-family: 'Cinzel', serif; font-size: 1rem; color: #ffd700; margin-bottom: 8px; }
        .event-details p { font-size: 0.85rem; color: #f3e5ab; margin-bottom: 5px; }
        .map-btn {
            display: inline-block; margin-top: 8px; background: transparent; border: 1px solid #ffd700; color: #ffd700;
            padding: 6px 15px; font-size: 0.75rem; font-family: 'Cinzel', serif; border-radius: 20px; text-decoration: none;
        }
        .whatsapp-btn {
            display: block; width: 100%; background: linear-gradient(135deg, #25d366 0%, #128c7e 100%);
            color: #fff; text-decoration: none; padding: 12px; font-family: 'Cinzel', serif; font-weight: 600; font-size: 0.9rem; border-radius: 25px;
        }
        /* Contenedor oculto para el reproductor de YouTube */
        #youtube-audio-container {
            position: absolute;
            width: 0;
            height: 0;
            overflow: hidden;
            opacity: 0;
            pointer-events: none;
        }
    </style>
</head>
<body>
    <div class="sparkles-bg" id="sparklesContainer"></div>

    <!-- Reproductor oculto de YouTube con la música -->
    <div id="youtube-audio-container">
        <div id="player"></div>
    </div>

    <div class="invitation-container">
        <div id="envelope-screen">
            <h2 class="envelope-title">Una Noche Mágica</h2>
            <div class="lamp-container" onclick="openInvitation()">
                <div class="smoke-plume"></div>
                <svg class="magic-lamp" viewBox="0 0 200 120" xmlns="http://www.w3.org/2000/svg">
                    <path d="M20 90 C50 90, 70 100, 100 100 C130 100, 150 90, 180 90 C185 90, 190 95, 185 105 C170 115, 30 115, 15 105 C10 95, 15 90, 20 90 Z" fill="#ffd700"/>
                    <path d="M50 90 C50 60, 80 40, 100 40 C120 40, 150 60, 150 90 Z" fill="url(#lampGrad)" stroke="#ffd700" stroke-width="2"/>
                    <path d="M90 40 C90 25, 95 15, 100 10 C105 15, 110 25, 110 40 Z" fill="#ffd700"/>
                    <path d="M150 75 Q180 75, 175 50 Q170 30, 155 35" fill="none" stroke="#ffd700" stroke-width="6" stroke-linecap="round"/>
                    <defs>
                        <linearGradient id="lampGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                            <stop offset="0%" stop-color="#ffdf73"/>
                            <stop offset="100%" stop-color="#b8860b"/>
                        </linearGradient>
                    </defs>
                </svg>
            </div>
            <button class="open-seal-btn" onclick="openInvitation()">Abrir Invitación ✨</button>
        </div>

        <div class="content-screen" id="contentScreen">
            <p class="header-sub">MIS XV AÑOS</p>
            <h1 class="main-title">Scarlet Mishell</h1>
            <div class="name">Noches de Arabia</div>
            <p class="message">Hay momentos en la vida que son inolvidables, y compartirlos con las personas que amamos los hace eternos. Te invito a celebrar conmigo esta mágica noche.</p>
            <div class="event-details">
                <h3>📅 Fecha y Hora</h3>
                <p>12 de Diciembre • 8:00 P.M.</p>
            </div>
            <div class="event-details">
                <h3>📍 Lugar</h3>
                <p><strong>Salón de Eventos Medio Ejido</strong></p>
                <p>Av. Enrique Arízaga Toral y Francisco Cisneros, Cuenca</p>
                <a href="https://share.google/Ky4QAMwYNoE4yL1te" target="_blank" class="map-btn">Ver en Google Maps 🗺️</a>
            </div>
            <a href="https://wa.me/?text=¡Hola!%20Confirmo%20mi%20asistencia%20a%20los%2015%20años%20de%20Scarlet%20Mishell." target="_blank" class="whatsapp-btn">Confirmar Asistencia 💬</a>
        </div>
    </div>

    <!-- Script oficial de YouTube para asegurar la reproducción -->
    <script src="https://www.youtube.com/iframe_api"></script>
    <script>
        const container = document.getElementById('sparklesContainer');
        for (let i = 0; i < 25; i++) {
            const sparkle = document.createElement('div');
            sparkle.classList.add('sparkle');
            sparkle.style.left = `${Math.random() * 100}vw`;
            sparkle.style.top = `${Math.random() * -100}px`;
            const size = Math.random() * 5 + 2;
            sparkle.style.width = `${size}px`;
            sparkle.style.height = `${size}px`;
            sparkle.style.animationDuration = `${Math.random() * 5 + 4}s`;
            sparkle.style.animationDelay = `${Math.random() * 5}s`;
            container.appendChild(sparkle);
        }

        let player;
        function onYouTubeIframeAPIReady() {
            player = new YT.Player('player', {
                height: '0',
                width: '0',
                videoId: 'sX8B1c9xL20', // ID de música ambiental compatible
                playerVars: { 'autoplay': 0, 'loop': 1, 'playlist': 'sX8B1c9xL20' }
            });
        }

        function openInvitation() {
            const envelope = document.getElementById('envelope-screen');
            const content = document.getElementById('contentScreen');
            envelope.style.opacity = '0';
            envelope.style.transform = 'scale(1.1)';
            setTimeout(() => {
                envelope.style.display = 'none';
                content.classList.add('active');
            }, 800);

            if (player && typeof player.playVideo === 'function') {
                player.playVideo();
            }
        }
    </script>
</body>
</html>
