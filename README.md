<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>С Днём Рождения, Папа! ❤️</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            user-select: none;
        }

        body {
            background: linear-gradient(145deg, #2b1a0f 0%, #1f130a 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Segoe UI', 'Arial', sans-serif;
            padding: 10px;
        }

        /* СТАРТОВОЕ ОКНО */
        .start-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.85);
            backdrop-filter: blur(8px);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            transition: opacity 0.5s;
        }

        .start-card {
            background: #fff9f0;
            max-width: 500px;
            width: 90%;
            padding: 40px 30px;
            border-radius: 60px 20px 60px 20px;
            text-align: center;
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
            border: 3px solid #ffb347;
            animation: gentlePop 0.6s ease-out;
        }

        @keyframes gentlePop {
            0% { transform: scale(0.8); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        .start-card h1 {
            font-size: 42px;
            margin-bottom: 20px;
            color: #c44b1e;
        }

        .start-card p {
            font-size: 20px;
            line-height: 1.5;
            color: #3d2a1a;
            margin-bottom: 30px;
        }

        .ok-btn {
            background: #ff8a5c;
            border: none;
            color: white;
            font-size: 28px;
            font-weight: bold;
            padding: 15px 50px;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 5px 0 #b34e2a;
            transition: 0.1s;
            border: 2px solid #ffd29b;
        }

        .ok-btn:active {
            transform: translateY(5px);
            box-shadow: none;
        }

        /* ОСНОВНОЙ ЭКРАН (новелла) */
        .story-screen {
            width: 100%;
            max-width: 1000px;
            margin: 0 auto;
            position: relative;
            display: none;
        }

        .story-image-container {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            width: 100%;
            border-radius: 30px;
            box-shadow: 0 15px 30px rgba(0,0,0,0.5);
            border: 3px solid #ffc285;
            cursor: pointer;
            overflow: visible;
        }

        .story-image {
            width: 100%;
            height: auto;
            display: block;
            transition: transform 0.3s;
            border-radius: 27px 27px 0 0; /* чтобы рамка красиво обтекала */
        }

        .story-image:active {
            transform: scale(1.02);
        }

        /* Стрелка назад */
        .back-arrow {
            margin: 15px 0 15px 15px;
            width: 55px;
            height: 55px;
            background: rgba(255, 240, 210, 0.9);
            backdrop-filter: blur(5px);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 35px;
            cursor: pointer;
            border: 3px solid #ff9966;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            transition: 0.2s;
        }

        .back-arrow:active {
            transform: scale(0.9);
            background: #ffe4b5;
        }

        /* Контейнер для сердечек */
        .hearts-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 100;
        }

        .heart {
            position: absolute;
            font-size: 30px;
            animation: floatUp 3s ease-out forwards;
            filter: drop-shadow(0 5px 5px rgba(0,0,0,0.2));
        }

        @keyframes floatUp {
            0% {
                opacity: 1;
                transform: translateY(0) rotate(0deg);
            }
            100% {
                opacity: 0;
                transform: translateY(-200px) rotate(20deg);
            }
        }

        /* ФИНАЛЬНОЕ ПОЗДРАВЛЕНИЕ (большое) */
        .final-message-big {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 150;
            background: rgba(0,0,0,0.2);
            backdrop-filter: blur(3px);
        }

        .big-card {
            background: #fff9f0;
            max-width: 600px;
            width: 90%;
            padding: 40px 30px;
            border-radius: 80px 30px 80px 30px;
            text-align: center;
            box-shadow: 0 25px 50px rgba(0,0,0,0.3);
            border: 5px solid #ff9966;
            animation: bigPop 0.8s ease-out;
            position: relative;
            z-index: 151;
        }

        @keyframes bigPop {
            0% { transform: scale(0.5); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        .big-card p {
            font-size: 20px;
            line-height: 1.6;
            color: #3d2a1a;
            white-space: pre-line;
            text-align: left;
            margin: 20px 0;
            font-weight: 500;
        }

        .continue-btn {
            background: #ff8a5c;
            border: none;
            color: white;
            font-size: 22px;
            font-weight: bold;
            padding: 12px 40px;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 4px 0 #b34e2a;
            transition: 0.1s;
            border: 2px solid #ffd29b;
            margin-top: 20px;
        }

        .continue-btn:active {
            transform: translateY(4px);
            box-shadow: none;
        }

        /* ПРЫГАЮЩИЕ КОТО-ОКОШКИ В КОНЦЕ */
        .final-message {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 200;
            display: none;
        }

        .jumping-message {
            position: absolute;
            background: #fff2d7;
            padding: 18px 25px;
            border-radius: 60px 60px 60px 20px;
            font-size: 20px;
            box-shadow: 0 15px 25px rgba(0,0,0,0.2);
            border: 3px solid #ff8a5c;
            max-width: 250px;
            text-align: center;
            animation: jumpAround 5s infinite alternate;
            pointer-events: none;
            font-weight: 600;
            color: #4a2e1a;
            font-family: 'Comic Sans MS', 'Arial', cursive;
        }

        /* Треугольные ушки */
        .jumping-message::before,
        .jumping-message::after {
            content: '';
            position: absolute;
            top: -15px;
            width: 0;
            height: 0;
            border-left: 12px solid transparent;
            border-right: 12px solid transparent;
            border-bottom: 20px solid #ff8a5c;
        }

        .jumping-message::before {
            left: 15px;
            transform: rotate(-8deg);
        }

        .jumping-message::after {
            left: 45px;
            transform: rotate(8deg);
        }

        @keyframes jumpAround {
            0% { transform: translate(0, 0) rotate(-3deg); }
            25% { transform: translate(30px, 40px) rotate(4deg); }
            50% { transform: translate(-20px, 90px) rotate(-4deg); }
            75% { transform: translate(40px, 140px) rotate(6deg); }
            100% { transform: translate(0, 180px) rotate(0deg); }
        }

        /* Для телефонов в перевёрнутом положении */
        @media (orientation: landscape) {
            .story-image-container {
                max-height: 90vh;
                align-items: center;
            }
            .story-image {
                width: auto;
                height: 80vh;
                margin: 0 auto;
            }
            .back-arrow {
                align-self: flex-start;
                margin-left: 10px;
            }
        }
    </style>
</head>
<body>

<!-- СТАРТОВОЕ ОКНО -->
<div class="start-screen" id="startScreen">
    <div class="start-card">
        <h1>🐱 Привет, Димуль!</h1>
        <p>Надеюсь, у тебя всё хорошо и вы классно проводите время ✨</p>
        <p>Это моё маленькое личное поздравление с днём рождения.<br>Пожалуйста, пройди его целиком ❤️</p>
        <p style="font-size: 18px; color: #b1624b;">Оно будет совсем коротеньким, но очень душевным...</p>
        <button class="ok-btn" id="startBtn">Ок👌</button>
    </div>
</div>

<!-- ОСНОВНАЯ ЧАСТЬ (НОВЕЛЛА) -->
<div class="story-screen" id="storyScreen">
    <div class="story-image-container" onclick="nextSlide()">
        <img src="images/1.jpg" alt="История" class="story-image" id="storyImage">
        <div class="back-arrow" onclick="prevSlide(event)">←</div>
    </div>
</div>

<!-- КОНТЕЙНЕР ДЛЯ СЕРДЕЧЕК -->
<div class="hearts-container" id="heartsContainer"></div>

<!-- БОЛЬШОЕ ФИНАЛЬНОЕ ПОЗДРАВЛЕНИЕ  -->
<div class="final-message-big" id="finalMessageBig">
    <div class="big-card">
        <p>
И я присоединяюсь к словам Томика!

С днём рождения тебя, мой дорогой папа! ❤️

Я тебя очень сильно люблю и ценю каждый момент, что был у меня с тобой в этой жизни. Каждое наше дурачество, каждый разговор, каждое молчание рядом.

Надеюсь, ты хорошо проведёшь этот день — с теплотой в душе и счастьем на сердце. Ты этого заслуживаешь.

Обнимаю тебя крепко-крепко. Твоя Сашуля 💖
        </p>
        <button class="continue-btn" id="continueBtn">Дальше</button>
    </div>
</div>

<!-- ПРЫГАЮЩИЕ КОТО-ПОЗДРАВЛЕНИЯ -->
<div class="final-message" id="finalMessage">
    <div class="jumping-message" style="top: 5%; left: 5%;">Папочка, ты мой герой! 🦸‍♂️</div>
    <div class="jumping-message" style="top: 15%; left: 60%;">Спасибо, что ты у меня есть! 💖</div>
    <div class="jumping-message" style="top: 30%; left: 15%;">Ты самый лучший на свете! 🌎</div>
    <div class="jumping-message" style="top: 45%; left: 70%;">Люблю тебя бесконечно! ∞</div>
    <div class="jumping-message" style="top: 60%; left: 25%;">Обнимаю крепко!</div>
    <div class="jumping-message" style="top: 75%; left: 50%;">С днём рождения, пап! 🎂</div>
    <div class="jumping-message" style="top: 85%; left: 10%;">Ты — мой космос! 🚀</div>
    <div class="jumping-message" style="top: 20%; left: 80%;">Самый лучший папа 👑</div>
    <div class="jumping-message" style="top: 50%; left: 85%;">Мур-мур-мур! 🐱</div>
    <div class="jumping-message" style="top: 70%; left: 75%;">Томас тебя любит! 😺</div>
    <div class="jumping-message" style="top: 40%; left: 5%;">Твоя доча ❤️</div>
    <div class="jumping-message" style="top: 90%; left: 65%;">Счастья, здоровья! ✨</div>
</div>

<script>
    // ===== картинки =====
    const slides = [
        'images/1.jpg', 'images/2.jpg', 'images/3.jpg', 'images/4.jpg', 'images/5.jpg',
        'images/6.jpg', 'images/7.jpg', 'images/8.jpg', 'images/9.jpg', 'images/10.jpg',
        'images/11.jpg', 'images/12.jpg', 'images/13.jpg', 'images/14.jpg', 'images/15.jpg',
        'images/16.jpg', 'images/17.jpg', 'images/18.jpg', 'images/19.jpg', 'images/20.jpg',
        'images/21.jpg', 'images/22.jpg', 'images/23.jpg', 'images/24.jpg', 'images/25.jpg',
        'images/26.jpg', 'images/27.jpg', 'images/28.jpg', 'images/29.jpg', 'images/30.jpg',
        'images/31.jpg', 'images/32.jpg', 'images/33.jpg', 'images/34.jpg', 'images/35.jpg'
    ];

    let currentSlide = 0;
    const storyScreen = document.getElementById('storyScreen');
    const startScreen = document.getElementById('startScreen');
    const storyImage = document.getElementById('storyImage');
    const heartsContainer = document.getElementById('heartsContainer');
    const finalMessageBig = document.getElementById('finalMessageBig');
    const finalMessage = document.getElementById('finalMessage');

    // Функция для создания сердечек (постоянно)
    function startFloatingHearts() {
        setInterval(() => {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.innerHTML = ['❤️', '🧡', '💛', '💚', '💙', '💜'][Math.floor(Math.random() * 6)];
            heart.style.left = Math.random() * 100 + '%';
            heart.style.top = 100 + '%';
            heart.style.fontSize = (20 + Math.random() * 30) + 'px';
            heart.style.animationDuration = (2 + Math.random() * 3) + 's';
            heartsContainer.appendChild(heart);
            
            setTimeout(() => heart.remove(), 5000);
        }, 400);
    }

    function explodeHearts(count = 15) {
        for (let i = 0; i < count; i++) {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.innerHTML = ['❤️', '🧡', '💛', '💚', '💙', '💜'][Math.floor(Math.random() * 6)];
            heart.style.left = Math.random() * 100 + '%';
            heart.style.top = Math.random() * 100 + '%';
            heart.style.fontSize = (20 + Math.random() * 30) + 'px';
            heart.style.animationDuration = (1.5 + Math.random() * 2) + 's';
            heartsContainer.appendChild(heart);
            
            setTimeout(() => heart.remove(), 3000);
        }
    }

    function updateSlide() {
        storyImage.src = slides[currentSlide];
    }

    window.nextSlide = function() {
        if (currentSlide < slides.length - 1) {
            currentSlide++;
            updateSlide();
            explodeHearts(8);
        } else if (currentSlide === slides.length - 1) {
            storyScreen.style.display = 'none';
            finalMessageBig.style.display = 'flex';
            explodeHearts(25);
        }
    };

    window.prevSlide = function(event) {
        event.stopPropagation();
        if (currentSlide > 0) {
            currentSlide--;
            updateSlide();
            finalMessageBig.style.display = 'none';
            finalMessage.style.display = 'none';
            storyScreen.style.display = 'block';
            explodeHearts(8);
        }
    };

    document.getElementById('continueBtn').addEventListener('click', () => {
        finalMessageBig.style.display = 'none';
        finalMessage.style.display = 'block';
        explodeHearts(30);
    });

    document.getElementById('startBtn').addEventListener('click', () => {
        startScreen.style.opacity = '0';
        setTimeout(() => {
            startScreen.style.display = 'none';
            storyScreen.style.display = 'block';
            currentSlide = 0;
            updateSlide();
            explodeHearts(20);
            startFloatingHearts();
        }, 500);
    });

    document.addEventListener('click', function(e) {
        if (!e.target.classList.contains('back-arrow') && 
            !e.target.classList.contains('continue-btn') &&
            storyScreen.style.display === 'block') {
            if (Math.random() > 0.5) {
                explodeHearts(5);
            }
        }
    });
</script>
</body>
</html>
