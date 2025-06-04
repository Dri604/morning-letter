<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Morning Message</title>
  <style>
    body {
      background-color: #ffffff;
      color: #333;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      height: 100vh;
      margin: 0;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      transition: background-color 1s ease;
      padding: 20px;
    }

    #clickText {
      font-size: 1.2rem;
      color: #ff4d6d;
      margin-bottom: 10px;
      user-select: none;
      cursor: default;
    }

    #heart {
      font-size: 80px;
      color: #ff4d6d;
      cursor: pointer;
      user-select: none;
      transition: transform 0.3s ease;
    }

    #heart:hover {
      transform: scale(1.2);
    }

    .letter {
      max-width: 400px;
      background: white;
      border-radius: 15px;
      padding: 30px 40px;
      box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
      text-align: center;
      color: black;
      font-size: 1rem;
      opacity: 0;
      pointer-events: none;
      transition: opacity 1s ease;
      margin-top: 20px;
    }

    .letter.show {
      opacity: 1;
      pointer-events: auto;
    }

    .letter.hide {
      opacity: 0;
      pointer-events: none;
    }

    .heart-icon {
      font-size: 24px;
      color: #ff4d6d;
      margin-top: 15px;
    }

    @media (max-width: 500px) {
      .letter {
        padding: 20px;
        font-size: 0.95rem;
      }

      #heart {
        font-size: 60px;
      }
    }
  </style>
</head>
<body>

  <div id="clickText">Click or press Enter on the heart</div>
  <div id="heart" tabindex="0" role="button" aria-label="Click to reveal message">❤️</div>

  <div class="letter" id="letter">
    <p>Good morning, love!</p>
    <p>I know things feel heavy right now, but try not to worry about what you can’t control. Take it one step at a time, and remember I’m always here for you.</p>
    <p>Have a peaceful day. I love you! <span class="heart-icon">💖</span></p>
  </div>

  <!-- Sounds -->
  <audio id="heartSound" src="https://cdn.pixabay.com/audio/2023/03/29/audio_770fe5e1f8.mp3"></audio>

  <script>
    const heart = document.getElementById('heart');
    const letter = document.getElementById('letter');
    const clickText = document.getElementById('clickText');
    const body = document.body;
    const heartSound = document.getElementById('heartSound');

    function showLetter() {
      body.style.backgroundColor = '#6a0dad';
      heart.style.display = 'none';
      clickText.style.display = 'none';
      letter.classList.add('show');
      heartSound.play();
    }

    heart.addEventListener('click', showLetter);
    heart.addEventListener('keydown', (e) => {
      if (e.key === 'Enter' || e.key === ' ') {
        e.preventDefault();
        showLetter();
      }
    });
  </script>

</body>
</html>
