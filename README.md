<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Durjoy Ghosh</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@700;400&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Poppins', sans-serif;
            color: #fff;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: hidden;
            background: linear-gradient(-45deg, #1C2526, #4b0082, #00ff88, #ffcc00);
            background-size: 400% 400%;
            animation: gradient 15s ease infinite;
            position: relative;
        }
        @keyframes gradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        .anime-character {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 300px;
            height: 300px;
            background: url('https://cdn.pixabay.com/photo/2023/06/12/00/30/anime-8057068_1280.jpg') no-repeat center center/cover;
            opacity: 0.3; /* Semi-transparent to blend with gradient */
            z-index: 0;
            animation: scaleAnime 10s ease infinite;
        }
        @keyframes scaleAnime {
            0% { transform: translate(-50%, -50%) scale(1); }
            50% { transform: translate(-50%, -50%) scale(1.05); }
            100% { transform: translate(-50%, -50%) scale(1); }
        }
        .container {
            text-align: center;
            z-index: 1;
            opacity: 0;
            animation: fadeIn 1s ease forwards;
        }
        .name {
            font-size: 4em;
            font-weight: 700;
            background: linear-gradient(to right, #00ff88, #ffcc00);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 20px;
            text-shadow: 0 0 5px rgba(255, 255, 255, 0.5);
            opacity: 0;
            animation: fadeIn 1s ease 0.5s forwards;
        }
        .typing {
            font-size: 1.8em;
            font-weight: 400;
            color: #fff;
            margin-bottom: 20px;
            white-space: nowrap;
            overflow: hidden;
            border-right: 3px solid #00ff88;
            width: 0;
            animation: typing 4s steps(40, end) forwards, blink 0.75s infinite, fadeIn 1s ease 1s forwards;
        }
        @keyframes typing {
            from { width: 0; }
            to { width: 100%; }
        }
        @keyframes blink {
            50% { border-color: transparent; }
        }
        @keyframes fadeIn {
            to { opacity: 1; }
        }
        .about {
            font-size: 1.6em; /* Larger as requested */
            font-weight: 400;
            color: #ccc;
            margin-bottom: 20px;
            opacity: 0;
            animation: fadeIn 1s ease 1.5s forwards;
        }
        .discord a {
            font-size: 1.3em;
            color: #fff;
            text-decoration: none;
            transition: transform 0.3s, color 0.3s;
            opacity: 0;
            animation: fadeIn 1s ease 2s forwards;
        }
        .discord a:hover {
            color: #00ff88;
            transform: scale(1.1); /* Hover scale animation */
        }
        .audio-player {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(0, 0, 0, 0.8);
            padding: 12px 20px;
            border-radius: 8px;
            z-index: 1000;
            display: flex;
            gap: 10px;
            opacity: 0;
            animation: fadeIn 1s ease 2.5s forwards;
        }
        .audio-player button {
            background: linear-gradient(to right, #00ff88, #ffcc00);
            border: none;
            padding: 10px 20px;
            color: #1C2526;
            cursor: pointer;
            border-radius: 5px;
            font-size: 1em;
            font-family: 'Poppins', sans-serif;
            font-weight: 400;
            animation: pulse 2s ease infinite;
        }
        .audio-player button:hover {
            background: #fff;
        }
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        .audio-fallback {
            font-size: 0.8em;
            color: #ccc;
            margin-top: 10px;
            text-align: center;
        }
        @media (max-width: 600px) {
            .name {
                font-size: 2.5em;
            }
            .typing {
                font-size: 1.2em;
            }
            .about {
                font-size: 1.1em;
            }
            .discord a {
                font-size: 1em;
            }
            .audio-player button {
                padding: 8px 15px;
                font-size: 0.9em;
            }
            .anime-character {
                width: 200px;
                height: 200px;
            }
        }
    </style>
</head>
<body>
    <div class="anime-character"></div>
    <div class="container">
        <h1 class="name">Durjoy Ghosh</h1>
        <div class="typing">Web Enthusiast | Creative Mind</div>
        <div class="about">I love to play chess and am passionate about coding.</div>
        <div class="discord">
            <a href="https://discord.gg/rdXczhha" target="_blank">Join me on Discord</a>
        </div>
    </div>
    <div class="audio-player">
        <audio id="background-audio" loop>
            <source src="https://cdn.pixabay.com/audio/2024/08/08/audio_5e6a4e7a31.mp3" type="audio/mp3">
            Your browser does not support the audio element.
        </audio>
        <button onclick="playAudio()">Play BGM</button>
        <button onclick="pauseAudio()">Pause BGM</button>
        <div class="audio-fallback">Click "Play BGM" to hear "Golden Brown".</div>
    </div>
    <script>
        const audio = document.getElementById('background-audio');
        audio.muted = false;

        function playAudio() {
            audio.play().catch(err => {
                console.log("Autoplay prevented:", err);
                document.querySelector('.audio-fallback').textContent = 'Autoplay blocked. Click "Play BGM" to start.';
            });
            document.querySelector('.audio-player').style.opacity = '1';
        }

        function pauseAudio() {
            audio.pause();
            document.querySelector('.audio-player').style.opacity = '1';
        }

        // Attempt to play audio on page load
        window.addEventListener('load', () => {
            audio.play().catch(err => {
                console.log("Autoplay prevented:", err);
                document.querySelector('.audio-fallback').textContent = 'Click "Play BGM" to hear "Golden Brown".';
            });
        });
    </script>
</body>
</html>
