<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Valentine</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    body {
      margin: 0;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      font-family: Arial, sans-serif;
    }

    .card {
      background: white;
      padding: 30px 20px;
      border-radius: 20px;
      width: 90%;
      max-width: 420px;
      text-align: center;
      box-shadow: 0 20px 40px rgba(0,0,0,0.2);
      position: relative;
      overflow: hidden;
    }

    h1 {
      font-size: 1.6rem;
      margin-bottom: 25px;
      letter-spacing: 1px;
    }

    .buttons {
      display: flex;
      justify-content: center;
      gap: 15px;
    }

    button {
      border: none;
      padding: 14px 22px;
      font-size: 1rem;
      border-radius: 999px;
      cursor: pointer;
      transition: 0.2s;
    }

    #yesBtn {
      background: #ff4d6d;
      color: white;
    }

    #noBtn {
      background: #eeeeee;
      color: #444;
    }

    .yes-page {
      display: none;
      animation: fadeIn 0.5s ease forwards;
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    .heart {
      position: absolute;
      width: 14px;
      height: 14px;
      background: #ff4d6d;
      transform: rotate(45deg);
      animation: float 6s linear infinite;
      opacity: 0.6;
    }

    .heart::before,
    .heart::after {
      content: "";
      position: absolute;
      width: 14px;
      height: 14px;
      background: #ff4d6d;
      border-radius: 50%;
    }

    .heart::before { top: -7px; left: 0; }
    .heart::after { left: -7px; top: 0; }

    @keyframes float {
      from { transform: translateY(110%) rotate(45deg); }
      to { transform: translateY(-120%) rotate(45deg); }
    }
  </style>
</head>

<body>
  <div class="card">
    <h1 id="question">NOVERA, WILL YOU BE MY VALENTINE?</h1>

    <div class="buttons" id="buttons">
      <button id="yesBtn">Yes</button>
      <button id="noBtn">No</button>
    </div>

    <div class="yes-page" id="yesPage">
      <h1>YAY! YOU JUST MADE MY DAY ❤️<br>HAPPY VALENTINE’S 💖</h1>
    </div>
  </div>

  <script>
    const noTexts = [
      "Are you sure?",
      "Think again 😳",
      "Please?",
      "Don’t break my heart 💔",
      "Last chance…"
    ];

    let count = 0;

    const yesBtn = document.getElementById("yesBtn");
    const noBtn = document.getElementById("noBtn");
    const buttons = document.getElementById("buttons");
    const yesPage = document.getElementById("yesPage");

    noBtn.onclick = () => {
      count++;
      noBtn.textContent = noTexts[Math.min(count, noTexts.length - 1)];
      yesBtn.style.transform = `scale(${1 + count * 0.15})`;
    };

    yesBtn.onclick = () => {
      buttons.style.display = "none";
      yesPage.style.display = "block";
      spawnHearts();
    };

    function spawnHearts() {
      for (let i = 0; i < 20; i++) {
        const heart = document.createElement("div");
        heart.className = "heart";
        heart.style.left = Math.random() * 100 + "%";
        heart.style.animationDelay = Math.random() * 4 + "s";
        document.body.appendChild(heart);
      }
    }
  </script>
</body>
</html>
