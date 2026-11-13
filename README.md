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
            padding: 30px 20px; text-align: center; overflow: hidden; margin: 20px 0;
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
        .open-seal-btn {
            margin-top: 30px; background: linear-gradient(135deg, #ffd700 0%, #d4af37 100%);
            color: #120826; border: none; padding: 12px 25px; font-family: 'Cinzel', serif;
            font-weight: 700; font-size: 0.95rem; border-radius: 30px; cursor: pointer;
            box-shadow: 0 4px 15px rgba(212, 175, 55, 0.4); transition: transform 0.3s ease;
        }
        .open-seal-btn:hover { transform: scale(1.05); }
        .content-screen {
            opacity: 0; transform: scale(0.95); transition: opacity 1s ease, transform 1s ease; pointer-events: none; display: none;
        }
        .content-screen.active { opacity: 1; transform: scale(1); pointer-events: auto; display: block; }
        
        .palace-icon { width: 60px; margin-bottom: 10px; filter: drop-shadow(0 0 10px rgba(255,215,0,0.5)); }
        .header-sub { font-family: 'Cinzel', serif; font-size: 0.8rem; letter-spacing: 2px; color: #d4af37; margin-bottom: 5px; }
        .main-title { font-family: 'Great Vibes', cursive; font-size: 2.8rem; color: #fffdf0; text-shadow: 0 0 15px rgba(255, 215, 0, 0.6); margin-bottom: 5px; }
        .date-badge { font-family: 'Cinzel', serif; font-size: 1.1rem; color: #ffd700; letter-spacing: 2px; margin-bottom: 15px; }
        .quote { font-style: italic; font-size: 0.85rem; color: #e0d5c1; line-height: 1.5; margin-bottom: 20px; border-left: 2px solid #d4af37; border-right: 2px solid #d4af37; padding: 0 10px; }
        
        .countdown-container {
            display: flex; justify-content: space-around; background: rgba(26, 11, 54, 0.6);
            border: 1px solid rgba(212, 175, 55, 0.3); border-radius: 12px; padding: 12px; margin-bottom: 20px;
        }
        .countdown-box { text-align: center; }
        .countdown-number { font-family: 'Cinzel', serif; font-size: 1.2rem; font-weight: bold; color: #ffd700; }
        .countdown-label { font-size: 0.65rem; color: #d4af37; letter-spacing: 1px; }

        .event-card {
            background: rgba(26, 11, 54, 0.6); border: 1px solid rgba(212, 175, 55, 0.3); border-radius: 12px; padding: 15px; margin-bottom: 15px; text-align: center;
        }
        .event-card h3 { font-family: 'Cinzel', serif; font-size: 0.95rem; color: #ffd700; margin-bottom: 8px; }
        .event-card p { font-size: 0.85rem; color: #f3e5ab; margin-bottom: 4px; }
        .map-btn {
            display: inline-block; margin-top: 10px; background: transparent; border: 1px solid #ffd700; color: #ffd700;
            padding: 6px 15px; font-size: 0.75rem; font-family: 'Cinzel', serif; border-radius: 20px; text-decoration: none;
        }
        .wish-box {
            background: rgba(26, 11, 54, 0.6); border: 1px solid rgba(212, 175, 55, 0.3); border-radius: 12px; padding: 15px; margin-bottom: 15px; font-size: 0.85rem; line-height: 1.5; text-align: center;
        }
        .form-group { margin-bottom: 12px; text-align: left; }
        .form-group label { display: block; font-size: 0.75rem; color: #ffd700; font-family: 'Cinzel', serif; margin-bottom: 4px; }
        .form-control {
            width: 100%; background: rgba(18, 8, 38, 0.8); border: 1px solid rgba(212, 175, 55, 0.4);
            border-radius: 8px; padding: 8px 10px; color: #f3e5ab; font-size: 0.8rem; font-family: 'Montserrat', sans-serif;
        }
        .whatsapp-btn {
            display: block; width: 100%; background: linear-gradient(135deg, #25d366 0%, #128c7e 100%);
            color: #fff; text-decoration: none; padding: 10px; font-family: 'Cinzel', serif; font-weight: 600; font-size: 0.85rem; border-radius: 25px; margin-top: 10px; text-align: center;
        }
        .audio-control {
            position: fixed; top: 15px; right: 15px; background: rgba(18, 8, 38, 0.9);
            border: 1px solid #d4af37; border-radius: 20px; padding: 6px 12px;
            display: flex; align-items: center; gap: 6px; cursor: pointer;
            z-index: 100; box-shadow: 0 0 10px rgba(212,175,55,0.3); color: #ffd700; font-size: 0.8rem; font-family: 'Cinzel', serif;
        }
    </style>
</head>
<body>
    <div class="sparkles-bg" id="sparklesContainer"></div>

    <div class="audio-control" id="audioBtn" onclick="toggleAudio()" style="display: none;">
        <span>🎵 Noches de Arabia</span>
    </div>
    <audio id="bgMusic" loop>
        <source src="https://actions.google.com/sounds/v1/ambiences/middle_eastern_market.ogg" type="audio/ogg">
    </audio>

    <div class="invitation-container">
        <div id="envelope-screen">
            <h2 class="envelope-title">Noches de Arabia</h2>
            <div class="lamp-container" onclick="openInvitation()">
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
            <button class="open-seal-btn" onclick="openInvitation()">TOCA PARA ABRIR LA MAGIA</button>
        </div>

        <div class="content-screen" id="contentScreen">
            <svg class="palace-icon" viewBox="0 0 24 24" fill="#ffd700"><path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/></svg>
            <p class="header-sub">MIS XV AÑOS</p>
            <h1 class="main-title">Scarlet Mishell</h1>
            <div class="date-badge">12 • 12 • 2026</div>
            
            <p class="quote">“Como en una noche mágica de Agrabah, comienza una nueva aventura y quiero compartirla contigo en un mundo ideal.”</p>
            
            <div class="countdown-container">
                <div class="countdown-box"><div class="countdown-number" id="days">--</div><div class="countdown-label">DÍAS</div></div>
                <div class="countdown-box"><div class="countdown-number" id="hours">--</div><div class="countdown-label">HORAS</div></div>
                <div class="countdown-box"><div class="countdown-number" id="minutes">--</div><div class="countdown-label">MIN</div></div>
                <div class="countdown-box"><div class="countdown-number" id="seconds">--</div><div class="countdown-label">SEG</div></div>
            </div>

            <div class="event-card">
                <h3>📅 FECHA Y HORA</h3>
                <p><strong>Sábado, 12 de Diciembre de 2026</strong></p>
                <p>8:00 p. m. - Recepción y Gala</p>
            </div>

            <div class="event-card">
                <h3>📍 LUGAR DE RECEPCIÓN</h3>
                <p><strong>Salón de Eventos Medio Ejido</strong></p>
                <p>Av. Enrique Arízaga Toral y Francisco Cisneros, Cuenca, Azuay</p>
                <a href="https://share.google/Ky4QAMwYNoE4yL1te" target="_blank" class="map-btn">VER MAPA 🗺️</a>
            </div>

            <div class="wish-box">
                <h3 style="color: #ffd700; font-family: 'Cinzel', serif; margin-bottom: 5px;">✨ CÓDIGO DE VESTIMENTA</h3>
                <p><strong>Gala / Formal</strong></p>
                <p style="font-size: 0.78rem; color: #e0d5c1; margin-top: 4px;">Tonos sugeridos: Libre, evitando el violeta imperial reservado para la quinceañera.</p>
            </div>

            <div class="wish-box">
                <h3 style="color: #ffd700; font-family: 'Cinzel', serif; margin-bottom: 5px;">🎁 LLUVIA DE SOBRES</h3>
                <p style="font-size: 0.78rem; color: #e0d5c1;">Tu compañía es mi mejor regalo, pero si deseas tener un detalle habrá cofre en recepción.</p>
            </div>

            <div class="wish-box">
                <h3 style="color: #ffd700; font-family: 'Cinzel', serif; margin-bottom: 10px;">💬 CONFIRMAR ASISTENCIA</h3>
                <div class="form-group">
                    <label>NOMBRE DEL INVITADO(S)</label>
                    <input type="text" id="guestName" class="form-control" placeholder="Ej. Familia Pérez / María">
                </div>
                <div class="form-group">
                    <label>ASISTENCIA</label>
                    <select id="guestStatus" class="form-control">
                        <option value="¡Sí, asistiré con mucha emoción!">✨ ¡Sí, asistiré!</option>
                        <option value="Lo siento, no podré asistir">😢 No podré asistir</option>
                    </select>
                </div>
                <a href="javascript:void(0);" onclick="sendWhatsApp()" class="whatsapp-btn">CONFIRMAR POR WHATSAPP 💬</a>
            </div>
        </div>
    </div>

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

        const eventDate = new Date("December 12, 2026 20:00:00").getTime();
        setInterval(() => {
            const now = new Date().getTime();
            const distance = eventDate - now;
            if (distance > 0) {
                document.getElementById("days").innerText = Math.floor(distance / (1000 * 60 * 60 * 24));
                document.getElementById("hours").innerText = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                document.getElementById("minutes").innerText = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
                document.getElementById("seconds").innerText = Math.floor((distance % (1000 * 60)) / 1000);
            }
        }, 1000);

        const music = document.getElementById('bgMusic');
        const audioBtn = document.getElementById('audioBtn');
        let isPlaying = false;

        function openInvitation() {
            const envelope = document.getElementById('envelope-screen');
            const content = document.getElementById('contentScreen');
            envelope.style.opacity = '0';
            envelope.style.transform = 'scale(1.1)';
            setTimeout(() => {
                envelope.style.display = 'none';
                content.classList.add('active');
            }, 800);

            music.play().then(() => {
                isPlaying = true;
                audioBtn.style.display = 'flex';
            }).catch(e => {
                audioBtn.style.display = 'flex';
            });
        }

        function toggleAudio() {
            if (isPlaying) {
                music.pause();
                isPlaying = false;
                audioBtn.innerHTML = '🔇 Silenciado';
            } else {
                music.play();
                isPlaying = true;
                audioBtn.innerHTML = '🎵 Noches de Arabia';
            }
        }

        function sendWhatsApp() {
            const name = document.getElementById('guestName').value.trim();
            const status = document.getElementById('guestStatus').value;
            if (!name) {
                alert('Por favor, escribe tu nombre para confirmar.');
                return;
            }
            const message = `¡Hola! Soy *${name}*. Te escribo para confirmar mi asistencia a los 15 años de Scarlet Mishell:\n\n*Estado:* ${status}`;
            const url = `https://wa.me/?text=${encodeURIComponent(message)}`;
            window.open(url, '_blank');
        }
    </script>
</body>
</html>
