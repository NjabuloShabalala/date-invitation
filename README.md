<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Will You Go On a Date?</title>
  <style>
    body {
      font-family: 'Georgia', serif;
      background-color: #1a1a1a;
      color: #ffffff;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      overflow: hidden;
      position: relative;
    }

    .envelope {
      width: 400px;
      height: 250px;
      background: linear-gradient(145deg, #ffffff, #d4d4d4);
      border-radius: 10px;
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
      position: relative;
      perspective: 1000px;
      cursor: pointer;
      text-align: center;
      color: #333;
    }

    .flap {
      width: 100%;
      height: 125px;
      background: linear-gradient(145deg, #e6e6e6, #ffffff);
      position: absolute;
      top: 0;
      left: 0;
      transform-origin: top;
      transform: rotateX(0deg);
      transition: transform 0.8s ease-in-out;
      border-radius: 10px 10px 0 0;
    }

    .instruction {
      position: absolute;
      top: 50px;
      left: 50%;
      transform: translateX(-50%);
      font-size: 16px;
      font-weight: bold;
      color: #444;
    }

    .content {
      width: 100%;
      height: 250px;
      background: #f9f9f9;
      border-radius: 0 0 10px 10px;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 22px;
      color: #333;
      position: absolute;
      top: 125px;
      opacity: 0;
      transition: opacity 0.8s ease-in-out;
    }

    .envelope.open .flap {
      transform: rotateX(-180deg);
    }

    .envelope.open .content {
      opacity: 1;
    }

    .buttons {
      display: none;
      text-align: center;
      margin-top: 10px;
    }

    .buttons button {
      padding: 10px 25px;
      border: none;
      border-radius: 5px;
      margin: 10px;
      cursor: pointer;
      font-size: 16px;
      transition: background 0.3s;
    }

    .yes-button {
      background-color: #4caf50;
      color: #fff;
    }

    .yes-button:hover {
      background-color: #45a049;
    }

    .no-button {
      background-color: #f44336;
      color: #fff;
    }

    .no-button:hover {
      background-color: #d32f2f;
    }

    #emoji-container {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
    }

    .emoji {
      position: absolute;
      font-size: 24px;
      animation: fall 2s linear infinite;
    }

    @keyframes fall {
      0% {
        transform: translateY(-100px) rotate(0deg);
        opacity: 1;
      }
      100% {
        transform: translateY(100vh) rotate(360deg);
        opacity: 0;
      }
    }

    .invitation {
      display: none;
      text-align: center;
      background: #fff;
      color: #333;
      border-radius: 10px;
      padding: 20px;
      width: 80%;
      max-width: 400px;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
      font-family: 'Times New Roman', serif;
      font-size: 18px;
      margin: 20px auto;
      animation: slideDown 0.8s ease-in-out;
    }

    @keyframes slideDown {
      0% {
        transform: translateY(-30px);
        opacity: 0;
      }
      100% {
        transform: translateY(0);
        opacity: 1;
      }
    }
  </style>
</head>
<body>
  <div class="envelope" onclick="openEnvelope()">
    <div class="flap"></div>
    <div class="instruction">Open Me</div>
    <div class="content">Will you go on a date with me?</div>
    <div class="buttons">
      <button class="yes-button" onclick="showDateDetails()">Yes</button>
      <button class="no-button" onclick="showBrokenHearts()">No</button>
    </div>
  </div>

  <div id="emoji-container"></div>

  <div class="invitation">
    <h2>You're Invited!</h2>
    <p>Venue: Vinyl Bar Johannesburg</p>
    <p>Time: 19:30</p>
    <p>Theme: Comfortable</p>
  </div>

  <script>
    function openEnvelope() {
      const envelope = document.querySelector('.envelope');
      envelope.classList.add('open');
      document.querySelector('.buttons').style.display = 'block';
    }

    function createEmoji(emoji) {
      const emojiElement = document.createElement('div');
      emojiElement.textContent = emoji;
      emojiElement.classList.add('emoji');
      emojiElement.style.left = Math.random() * 100 + 'vw';
      emojiElement.style.animationDuration = Math.random() * 1.5 + 2 + 's';
      document.getElementById('emoji-container').appendChild(emojiElement);

      setTimeout(() => {
        emojiElement.remove();
      }, 2000);
    }

    function showDateDetails() {
      document.querySelector('.invitation').style.display = 'block';
      for (let i = 0; i < 50; i++) {
        createEmoji('😊');
        createEmoji('🎉');
        createEmoji('😍');
      }
    }

    function showBrokenHearts() {
      document.body.style.backgroundColor = '#000';
      document.querySelector('.buttons').style.display = 'none';
      document.querySelector('.content').textContent = '';
      document.getElementById('emoji-container').style.display = 'block';
      for (let i = 0; i < 50; i++) {
        createEmoji('💔');
        createEmoji('😢');
      }
    }
  </script>
</body>
</html>
