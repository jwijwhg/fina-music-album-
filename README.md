# fina-music-album-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cute Character Music Player</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Montserrat', sans-serif;
        }

        body {
            background-color: #f0f0f0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
        }

        .player-container {
            width: 320px;
            height: 580px;
            background: linear-gradient(135deg, #121212, #1e1e1e);
            border-radius: 30px;
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
            overflow: hidden;
            position: relative;
            border: 8px solid #333;
        }

        .notch {
            position: absolute;
            width: 150px;
            height: 25px;
            background-color: #333;
            top: 0;
            left: 50%;
            transform: translateX(-50%);
            border-bottom-left-radius: 15px;
            border-bottom-right-radius: 15px;
            z-index: 10;
        }

        .screen {
            width: 100%;
            height: 100%;
            overflow: hidden;
            position: relative;
        }

        .background {
            position: absolute;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, #0f0c29, #302b63, #24243e);
            z-index: 1;
            overflow: hidden;
        }

        /* Stars */
        .stars {
            position: absolute;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        .star {
            position: absolute;
            background-color: white;
            border-radius: 50%;
            animation: twinkle var(--duration) infinite ease-in-out;
            opacity: var(--opacity);
        }

        @keyframes twinkle {
            0%, 100% { opacity: var(--opacity); transform: scale(1); }
            50% { opacity: 0.2; transform: scale(0.8); }
        }

        .character-container {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 3;
            width: 200px;
            height: 200px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .character {
            position: relative;
            width: 120px;
            height: 140px;
            animation: float 4s infinite ease-in-out;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .head {
            position: absolute;
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, #FFD3E0, #FF9EC4);
            border-radius: 50%;
            top: 0;
            left: 20px;
            box-shadow: 0 5px 15px rgba(255, 158, 196, 0.3);
            overflow: hidden;
        }

        .ear {
            position: absolute;
            width: 25px;
            height: 40px;
            background: linear-gradient(135deg, #FF9EC4, #FFD3E0);
            border-radius: 50% 50% 0 0;
        }

        .ear-left {
            top: -15px;
            left: 10px;
            transform: rotate(-30deg);
        }

        .ear-right {
            top: -15px;
            right: 10px;
            transform: rotate(30deg);
        }

        .inner-ear {
            position: absolute;
            width: 15px;
            height: 25px;
            background: #FFEAF1;
            border-radius: 50% 50% 0 0;
            top: 5px;
            left: 5px;
        }

        .eye {
            position: absolute;
            width: 15px;
            height: 20px;
            background: #333;
            border-radius: 50%;
            top: 30px;
        }

        .eye-left {
            left: 25px;
        }

        .eye-right {
            right: 25px;
        }

        .pupil {
            position: absolute;
            width: 7px;
            height: 12px;
            background: #fff;
            border-radius: 50%;
            top: 3px;
            left: 4px;
        }

        .nose {
            position: absolute;
            width: 12px;
            height: 8px;
            background: #FF9EC4;
            border-radius: 50%;
            top: 50px;
            left: 34px;
        }

        .mouth {
            position: absolute;
            width: 20px;
            height: 10px;
            border-radius: 0 0 10px 10px;
            border-bottom: 2px solid #333;
            top: 60px;
            left: 30px;
        }

        .body {
            position: absolute;
            width: 100px;
            height: 80px;
            background: linear-gradient(135deg, #FF9EC4, #FFD3E0);
            border-radius: 50% 50% 40% 40%;
            top: 70px;
            left: 10px;
            box-shadow: 0 5px 15px rgba(255, 158, 196, 0.3);
        }

        .arm {
            position: absolute;
            width: 20px;
            height: 50px;
            background: linear-gradient(135deg, #FFD3E0, #FF9EC4);
            border-radius: 10px;
        }

        .arm-left {
            top: 80px;
            left: -5px;
            transform: rotate(20deg);
        }

        .arm-right {
            top: 80px;
            right: -5px;
            transform: rotate(-20deg);
        }

        .hand {
            position: absolute;
            width: 15px;
            height: 15px;
            background: #FFEAF1;
            border-radius: 50%;
            bottom: -5px;
        }

        .tail {
            position: absolute;
            width: 60px;
            height: 15px;
            background: linear-gradient(135deg, #FFD3E0, #FF9EC4);
            border-radius: 10px;
            bottom: 10px;
            right: -30px;
            transform-origin: left center;
            animation: wag 3s infinite ease-in-out;
        }

        @keyframes wag {
            0%, 100% { transform: rotate(0deg); }
            25% { transform: rotate(15deg); }
            75% { transform: rotate(-15deg); }
        }

        .info-container {
            position: absolute;
            top: 180px;
            width: 100%;
            text-align: center;
            z-index: 3;
            color: #fff;
        }

        .song-title {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 5px;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
        }

        .album-title {
            font-size: 14px;
            font-weight: 300;
            opacity: 0.8;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
        }

        .gradient-text {
            background: linear-gradient(90deg, #FFD3E0, #FF9EC4);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .controls {
            position: absolute;
            bottom: 40px;
            width: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 3;
        }

        .control-btn {
            background: rgba(255, 255, 255, 0.2);
            border: none;
            width: 45px;
            height: 45px;
            border-radius: 50%;
            margin: 0 15px;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            transition: all 0.3s ease;
            color: #fff;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
        }

        .control-btn:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-3px);
        }

        .play-btn {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #FFD3E0, #FF9EC4);
            color: #fff;
            font-size: 20px;
            box-shadow: 0 5px 15px rgba(255, 158, 196, 0.3);
        }

        .play-btn:hover {
            background: linear-gradient(135deg, #FF9EC4, #FFD3E0);
            transform: translateY(-3px);
        }

        .progress-container {
            position: absolute;
            bottom: 100px;
            width: 80%;
            height: 4px;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 2px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 3;
        }

        .progress-bar {
            height: 100%;
            background: linear-gradient(90deg, #FFD3E0, #FF9EC4);
            border-radius: 2px;
            width: 0%;
            transition: width 0.1s linear;
        }

        .time {
            position: absolute;
            bottom: 70px;
            width: 80%;
            display: flex;
            justify-content: space-between;
            font-size: 12px;
            color: #fff;
            left: 50%;
            transform: translateX(-50%);
            z-index: 3;
        }

        .visualizer {
            position: absolute;
            bottom: 10px;
            width: 80%;
            height: 30px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            justify-content: space-between;
            align-items: flex-end;
            z-index: 2;
        }

        .visualizer-bar {
            width: 8px;
            height: 5px;
            background: linear-gradient(to top, #FFD3E0, #FF9EC4);
            border-radius: 4px;
            transition: height 0.2s ease;
        }

        .playlist-btn {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(255, 255, 255, 0.2);
            border: none;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            color: #fff;
            font-size: 18px;
            transition: all 0.3s ease;
            z-index: 3;
        }

        .playlist-btn:hover {
            background: rgba(255, 255, 255, 0.3);
        }

        .search-container {
            position: absolute;
            top: 20px;
            left: 20px;
            z-index: 3;
        }

        .search-input {
            background: rgba(255, 255, 255, 0.1);
            border: none;
            border-radius: 20px;
            padding: 8px 15px;
            color: #fff;
            width: 150px;
            font-size: 12px;
        }

        .search-input::placeholder {
            color: rgba(255, 255, 255, 0.6);
        }

        .search-input:focus {
            outline: none;
            background: rgba(255, 255, 255, 0.15);
        }

        .gradient-animation {
            position: absolute;
            width: 200px;
            height: 200px;
            border-radius: 50%;
            background: linear-gradient(45deg, #FFD3E0, #FF9EC4, #FFD3E0);
            filter: blur(40px);
            opacity: 0.3;
            z-index: 2;
            animation: gradientMove 8s infinite alternate;
        }

        @keyframes gradientMove {
            0% { transform: translate(-50%, -50%) scale(1); background-position: 0% 50%; }
            50% { transform: translate(-50%, -50%) scale(1.2); background-position: 100% 50%; }
            100% { transform: translate(-50%, -50%) scale(1); background-position: 0% 50%; }
        }
    </style>
</head>
<body>
    <div class="player-container">
        <div class="notch"></div>
        <div class="screen">
            <div class="background">
                <div class="stars" id="stars"></div>
            </div>
            
            <div class="gradient-animation"></div>
            
            <div class="search-container">
                <input type="text" class="search-input" placeholder="Search music...">
            </div>
            
            <button class="playlist-btn">
                <i class="fas fa-ellipsis-h"></i>
            </button>
            
            <div class="character-container">
                <div class="character">
                    <div class="ear ear-left">
                        <div class="inner-ear"></div>
                    </div>
                    <div class="ear ear-right">
                        <div class="inner-ear"></div>
                    </div>
                    <div class="head">
                        <div class="eye eye-left">
                            <div class="pupil"></div>
                        </div>
                        <div class="eye eye-right">
                            <div class="pupil"></div>
                        </div>
                        <div class="nose"></div>
                        <div class="mouth"></div>
                    </div>
                    <div class="body"></div>
                    <div class="arm arm-left">
                        <div class="hand"></div>
                    </div>
                    <div class="arm arm-right">
                        <div class="hand"></div>
                    </div>
                    <div class="tail"></div>
                </div>
            </div>
            
            <div class="info-container">
                <div class="song-title gradient-text">Nebula Nap</div>
                <div class="album-title">Cosmic Cuddle</div>
            </div>
            
            <div class="progress-container">
                <div class="progress-bar"></div>
            </div>
            
            <div class="time">
                <span class="current-time">0:00</span>
                <span class="total-time">3:45</span>
            </div>
            
            <div class="visualizer" id="visualizer">
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
                <div class="visualizer-bar"></div>
            </div>
            
            <div class="controls">
                <button class="control-btn prev-btn">
                    <i class="fas fa-backward"></i>
                </button>
                <button class="control-btn play-btn">
                    <i class="fas fa-play"></i>
                </button>
                <button class="control-btn next-btn">
                    <i class="fas fa-forward"></i>
                </button>
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Create stars
            const starsContainer = document.getElementById('stars');
            const starCount = 100;
            
            for (let i = 0; i < starCount; i++) {
                const star = document.createElement('div');
                star.classList.add('star');
                
                // Random size between 1px and 3px
                const size = Math.random() * 2 + 1;
                star.style.width = `${size}px`;
                star.style.height = `${size}px`;
                
                // Random position
                const posX = Math.random() * 100;
                const posY = Math.random() * 100;
                star.style.left = `${posX}%`;
                star.style.top = `${posY}%`;
                
                // Random twinkle animation duration
                const duration = Math.random() * 3 + 2;
                star.style.setProperty('--duration', `${duration}s`);
                
                // Random opacity
                const opacity = Math.random() * 0.5 + 0.3;
                star.style.setProperty('--opacity', opacity);
                
                starsContainer.appendChild(star);
            }
            
            // player functionality
            const playBtn = document.querySelector('.play-btn');
            const prevBtn = document.querySelector('.prev-btn');
            const nextBtn = document.querySelector('.next-btn');
            const progressBar = document.querySelector('.progress-bar');
            const currentTimeEl = document.querySelector('.current-time');
            const totalTimeEl = document.querySelector('.total-time');
            const visualizerBars = document.querySelectorAll('.visualizer-bar');
            
            let isPlaying = false;
            let progress = 0;
            let progressInterval;
            const totalDuration = 225; // 3:45 in seconds
            
            // Toggle play/pause
            playBtn.addEventListener('click', function() {
                if (isPlaying) {
                    pauseSong();
                } else {
                    playSong();
                }
            });
            
            // Previous button
            prevBtn.addEventListener('click', function() {
                resetProgress();
                if (isPlaying) {
                    playSong();
                }
            });
            
            // Next button
            nextBtn.addEventListener('click', function() {
                resetProgress();
                if (isPlaying) {
                    playSong();
                }
            });
            
            function playSong() {
                isPlaying = true;
                playBtn.innerHTML = '<i class="fas fa-pause"></i>';
                
                // Simulate progress
                progressInterval = setInterval(function() {
                    progress += 0.5;
                    if (progress >= totalDuration) {
                        resetProgress();
                    } else {
                        updateProgress();
                    }
                }, 500);
                
                // Animate visualizer
                animateVisualizer();
            }
            
            function pauseSong() {
                isPlaying = false;
                playBtn.innerHTML = '<i class="fas fa-play"></i>';
                clearInterval(progressInterval);
                stopVisualizer();
            }
            
            function resetProgress() {
                progress = 0;
                updateProgress();
            }
            
            function updateProgress() {
                const percent = (progress / totalDuration) * 100;
                progressBar.style.width = percent + '%';
                
                // Update time display
                const currentMinutes = Math.floor(progress / 60);
                const currentSeconds = Math.floor(progress % 60);
                currentTimeEl.textContent = `${currentMinutes}:${currentSeconds < 10 ? '0' : ''}${currentSeconds}`;
            }
            
            function animateVisualizer() {
    
