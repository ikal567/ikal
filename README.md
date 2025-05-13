# ikal
ikal lagi gabut
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Be My Girlfriend</title>
  <style>
    body {
      margin: 0;
      font-family: 'Comic Sans MS', cursive, sans-serif;
      background-color: pink;
      overflow: hidden;
    }
    .heart {
      position: absolute;
      width: 20px;
      height: 20px;
      background: red;
      transform: rotate(45deg);
      animation: float 2s infinite;
    }
    .heart::before,
    .heart::after {
      content: '';
      position: absolute;
      width: 20px;
      height: 20px;
      background: red;
      border-radius: 50%;
    }
    .heart::before {
      top: -10px;
      left: 0;
    }
    .heart::after {
      left: -10px;
      top: 0;
    }
    @keyframes float {
      0% {transform: translateY(0) rotate(45deg);}
      100% {transform: translateY(-100px) rotate(45deg); opacity: 0;}
    }
    .page {
      display: none;
      height: 100vh;
      width: 100vw;
      align-items: center;
      justify-content: center;
      flex-direction: column;
    }
    .active {
      display: flex;
    }
    button {
      font-size: 20px;
      margin: 10px;
      padding: 10px 20px;
      border: none;
      border-radius: 10px;
      cursor: pointer;
    }
    #yesBtn {
      background-color: #ff69b4;
      color: white;
    }
    #noBtn {
      position: absolute;
      background-color: #999;
      color: white;
    }
    input, select {
      padding: 10px;
      margin: 10px;
      font-size: 16px;
    }
    .card {
      border: 2px solid white;
      padding: 20px;
      background-color: #fff0f5;
      border-radius: 15px;
      box-shadow: 0 0 10px rgba(0,0,0,0.3);
    }
  </style>
</head>
<body>
  <div class="page active" id="page1">
    <h1>Will you be my girlfriend?</h1>
    <button id="yesBtn" onclick="goToPage(2)">Yes I do</button>
    <button id="noBtn">No, leave me alone</button>
  </div>  <div class="page" id="page2">
    <h1>Let's schedule our first date!</h1>
    <input type="date" id="date">
    <input type="time" id="time">
    <select id="activity">
      <option value="Mobile Legend">Mobile Legend</option>
      <option value="Call">Call</option>
    </select>
    <button onclick="goToPage(3)">Continue</button>
  </div>  <div class="page" id="page3">
    <h1>Our Date Plan</h1>
    <div class="card" id="summary"></div>
  </div>  <script>
    function goToPage(pageNumber) {
      document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
      document.getElementById('page' + pageNumber).classList.add('active');

      if (pageNumber === 3) {
        const date = document.getElementById('date').value;
        const time = document.getElementById('time').value;
        const activity = document.getElementById('activity').value;
        document.getElementById('summary').innerHTML = `
          <p><strong>Date:</strong> ${date}</p>
          <p><strong>Time:</strong> ${time}</p>
          <p><strong>Activity:</strong> ${activity}</p>
        `;
      }
    }

    const noBtn = document.getElementById('noBtn');
    noBtn.addEventListener('mouseover', () => {
      const x = Math.random() * (window.innerWidth - 100);
      const y = Math.random() * (window.innerHeight - 50);
      noBtn.style.left = x + 'px';
      noBtn.style.top = y + 'px';
    });

    // Heart trail animation
    document.addEventListener('mousemove', e => {
      const heart = document.createElement('div');
      heart.className = 'heart';
      heart.style.left = e.pageX + 'px';
      heart.style.top = e.pageY + 'px';
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 2000);
    });
  </script></body>
</html>
