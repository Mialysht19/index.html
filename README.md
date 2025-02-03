# index.html <!DOCTYPE html>
<html>
<head>
    <title>To:maaboyAimal  Do you love me?</title>
    <style>
        body {
            text-align: center;
            font-family: Arial, sans-serif;
            background-color: pink;
            margin-top: 100px;
        }
        .btn {
            font-size: 20px;
            padding: 15px 25px;
            cursor: pointer;
            margin: 10px;
            border-radius: 10px;
            font-weight: bold;
        }
        #yes {
            background-color: #4CAF50;
            color: white;
            border: none;
        }
        #no {
            background-color: red;
            color: white;
            border: none;
            position: absolute;
            transition: 0.3s;
        }
        h2 {
            font-size: 28px;
            color: #fff;
        }
        img {
            width: 150px;
        }
        #confetti {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 9999;
        }
    </style>
</head>
<body>

    <img src="https://media.tenor.com/0V2P1IwANsMAAAAi/cute-love.gif">
    <h2>Will you be my Valentine? 💕</h2>

    <button class="btn" id="yes">Yes 💖</button>
    <button class="btn" id="no">No 😢</button>

    <canvas id="confetti"></canvas>

    <audio id="loveSong" loop>
        <source src="https://www.bensound.com/bensound-music/bensound-love.mp3" type="audio/mp3">
    </audio>

    <script>
        let noButton = document.getElementById("no");
        let yesButton = document.getElementById("yes");
        let confettiCanvas = document.getElementById("confetti");
        let ctx = confettiCanvas.getContext("2d");
        let loveSong = document.getElementById("loveSong");

        noButton.addEventListener("mouseover", function() {
            let x = Math.random() * window.innerWidth - 100;
            let y = Math.random() * window.innerHeight - 50;
            noButton.style.left = ${x}px;
            noButton.style.top = ${y}px;
            noButton.style.fontSize = ${parseInt(noButton.style.fontSize || 20) - 2}px;
        });

        yesButton.addEventListener("click", function() {
            alert("Yay! Love you too Seng Muah! ❤️");
            startConfetti();
            loveSong.play();
        });

        function startConfetti() {
            confettiCanvas.width = window.innerWidth;
            confettiCanvas.height = window.innerHeight;
            let particles = [];

            for (let i = 0; i < 200; i++) {
                particles.push({
                    x: Math.random() * confettiCanvas.width,
                    y: Math.random() * confettiCanvas.height,
                    r: Math.random() * 5 + 2,
                    d: Math.random() * 5 + 2,
                    color: hsl(${Math.random() * 360}, 100%, 50%)
                });
            }

            function drawConfetti() {
                ctx.clearRect(0, 0, confettiCanvas.width, confettiCanvas.height);
                particles.forEach(p => {
                    ctx.beginPath();
                    ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2, false);
                    ctx.fillStyle = p.color;
                    ctx.fill();
                    p.y += p.d;

                    if (p.y > confettiCanvas.height) {
                        p.y = 0;
                        p.x = Math.random() * confettiCanvas.width;
                    }
                });
                requestAnimationFrame(drawConfetti);
            }

            drawConfetti();
        }
    </script>
</body>
</html>
