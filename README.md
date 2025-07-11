<!DOCTYPE html><html lang="en"><head><meta http-equiv="Content-Security-Policy" content="default-src 'self' 'unsafe-inline' 'unsafe-eval' data: blob: https://cdnjs.cloudflare.com https://cdn.jsdelivr.net https://code.jquery.com https://unpkg.com https://d3js.org https://threejs.org https://cdn.plot.ly https://stackpath.bootstrapcdn.com https://maps.googleapis.com https://cdn.tailwindcss.com https://ajax.googleapis.com https://kit.fontawesome.com https://cdn.datatables.net https://maxcdn.bootstrapcdn.com https://code.highcharts.com https://tako-static-assets-production.s3.amazonaws.com https://www.youtube.com https://fonts.googleapis.com https://fonts.gstatic.com https://pfst.cf2.poecdn.net https://puc.poecdn.net https://i.imgur.com https://wikimedia.org https://*.icons8.com https://*.giphy.com https://picsum.photos https://images.unsplash.com; frame-src 'self' https://www.youtube.com https://trytako.com; child-src 'self'; manifest-src 'self'; worker-src 'self'; upgrade-insecure-requests; block-all-mixed-content;">
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>HKUAA New Graduate Welcome Party and Alumni Prize Presentation Ceremony - BINGO</title>
  <style>
    body {
      font-family: 'Segoe UI', Arial, sans-serif;
      background: #f4f9fb;
      margin: 0;
      padding: 0;
      color: #222;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    .header {
      text-align: center;
      padding: 2rem 1rem 1rem 1rem;
      background: linear-gradient(90deg, #005daa 0%, #97c1e7 100%);
      color: white;
      width: 100%;
      box-shadow: 0 2px 10px rgba(0,0,0,0.05);
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    .logo {
      max-width: 400px;
      width: 80vw;
      margin-bottom: 0.7rem;
      display: block;
    }
    .main-title {
      margin: 0;
      font-size: 2.1rem;
      letter-spacing: 0.01em;
      font-weight: bold;
      line-height: 1.2;
    }
    .bingo-container {
      background: white;
      border-radius: 20px;
      box-shadow: 0 4px 24px rgba(0,0,0,0.09);
      padding: 1.5rem;
      margin: 2rem 1rem;
      max-width: 750px;
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    .bingo-grid {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 18px;
      width: 100%;
      max-width: 700px;
      margin-bottom: 1.5rem;
    }
    .bingo-cell {
      background: #eaf4fe;
      border-radius: 14px;
      padding: 0.35em;
      min-width: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      cursor: pointer;
      font-size: 0.85rem;
      font-weight: 500;
      user-select: none;
      border: 2px solid transparent;
      transition: background 0.13s, border 0.16s;
      box-sizing: border-box;
      word-break: break-word;
      height: 0;
      padding-bottom: 100%; /* Square cell by default */
      position: relative;
      overflow: hidden;
      line-height: 1.2;
    }
    .bingo-cell > span {
      position: absolute;
      top: 50%;
      left: 50%;
      width: 90%;
      transform: translate(-50%, -50%);
      display: block;
    }
    .bingo-cell.selected, .bingo-cell.free {
      background: linear-gradient(90deg, #68b3e2 0%, #dbf3fa 100%);
      color: #05406b;
      border: 2.5px solid #005daa;
      text-shadow: 0 1px 2px #fff9;
    }
    .bingo-cell.free {
      font-style: italic;
      font-weight: bold;
      background: linear-gradient(90deg, #ffd700 0%, #fdf6c3 100%);
      color: #b48800;
      border: 2.5px solid #e6c200;
      text-shadow: 0 2px 6px #fff8;
    }
    .controls {
      display: flex;
      gap: 1rem;
      margin-bottom: 1rem;
      justify-content: center;
      width: 100%;
    }
    .shuffle-btn, .reset-btn {
      font-size: 1.1rem;
      background: #005daa;
      color: white;
      border: none;
      border-radius: 9px;
      padding: 0.7em 1.6em;
      cursor: pointer;
      transition: background 0.15s;
      font-weight: bold;
      box-shadow: 0 2px 8px #005daa22;
    }
    .shuffle-btn:hover, .reset-btn:hover {
      background: #3579b8;
    }
    .popup {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background: rgba(0,40,80,0.18);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 99999;
      visibility: hidden;
      opacity: 0;
      transition: opacity 0.25s;
    }
    .popup.active {
      visibility: visible;
      opacity: 1;
    }
    .popup-content {
      background: white;
      border-radius: 20px;
      padding: 2rem 2.5rem;
      box-shadow: 0 6px 36px rgba(0,0,0,0.16);
      text-align: center;
      font-size: 2rem;
      color: #005daa;
      font-weight: bold;
      letter-spacing: 0.03em;
      position: relative;
    }
    .close-btn {
      margin-top: 1.2em;
      background: #ffd700;
      color: #b48800;
      border: none;
      border-radius: 7px;
      padding: 0.5em 1.2em;
      font-size: 1.05rem;
      font-weight: bold;
      cursor: pointer;
      box-shadow: 0 2px 8px #ffd70033;
      transition: background 0.15s;
    }
    .close-btn:hover {
      background: #ffe966;
    }
    @media (max-width: 700px) {
      .bingo-container {
        max-width: 99vw;
      }
      .bingo-grid {
        max-width: 99vw;
        gap: 6px;
      }
      .logo {
        max-width: 98vw;
      }
      .main-title {
        font-size: 1.1rem;
      }
      .bingo-cell {
        font-size: 0.73rem;
        padding: 0.18em;
      }
    }
    @media (max-width: 540px) {
      .main-title {
        font-size: 0.97rem;
      }
      .bingo-cell {
        font-size: 0.60rem;
        padding: 0.11em;
      }
      .bingo-grid {
        gap: 4px;
      }
    }
    @media (max-width: 450px) {
      .main-title {
        font-size: 0.82rem;
      }
      .bingo-cell {
        font-size: 0.48rem;
        padding: 0.07em;
      }
      .bingo-grid {
        gap: 2px;
      }
    }
    /* 手机端：格子高度自适应内容 */
    @media (max-width: 700px) {
      .bingo-cell {
        height: auto !important;
        min-height: 56px;
        padding-bottom: 0 !important;
        position: relative;
      }
      .bingo-cell > span {
        position: static;
        top: auto; left: auto;
        width: 100%;
        transform: none;
        display: block;
      }
    }
  </style>
</head>
<body>
  <div class="header">
    <img class="logo" src="https://i.imgur.com/5seuicU.png" alt="HKU Logo">
    <div class="main-title">
      HKUAA New Graduate Welcome Party<br>
      and Alumni Prize Presentation Ceremony
    </div>
  </div>
  <div class="bingo-container">
    <div class="controls">
      <button class="shuffle-btn" type="button">🔀 Shuffle</button>
      <button class="reset-btn" type="button">♻️ Reset</button>
    </div>
    <div class="bingo-grid" id="bingoGrid"></div>
  </div>

  <div class="popup" id="bingoPopup">
    <div class="popup-content">
      🎉 <span>BINGO!</span> 🎉
      <br>
      <button class="close-btn" onclick="hidePopup()">OK</button>
    </div>
  </div>

  <script>
    const bingoCells = [
      "We are/were in the same faculty",
      "We share the same hobby",
      "We all lived in Hall (or not)",
      "We watched a same movie",
      "We took the same transportation here",
      "We love getting up early (or late)",
      "We have the same MBTI",
      "We were born in the same month",
      "We all love coffee (or don’t)",
      "We all tried staying up all night (or not)",
      "We prefer dogs to cats (or vice versa)",
      "FREE SPACE",
      "We’re from the same hometown",
      "We graduated in the same year",
      "We love the same singer",
      "We do the same sports",
      "We speak more than three language (or not)",
      "We have traveled to the same country",
      "We share the same taste in music",
      "We both studied abroad (or not)",
      "We took the same course back in college",
      "We both cook (or not)",
      "We both prefer sweet to savory (or vice versa)",
      "We have the same favorite streaming service",
      "We use the same social media most frequently."
    ];

    let currentGrid = [];
    let selected = [];
    const gridSize = 5;

    function shuffle(array) {
      let arr = array.slice();
      for (let i = arr.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [arr[i], arr[j]] = [arr[j], arr[i]];
      }
      return arr;
    }

    function setupGrid() {
      let shuffled = shuffle(bingoCells);
      currentGrid = shuffled;
      selected = Array(25).fill(false);
      const freeIndex = currentGrid.findIndex(cell => cell === "FREE SPACE");
      if (freeIndex !== -1) selected[freeIndex] = true;
      renderGrid();
    }

    function renderGrid() {
      const grid = document.getElementById('bingoGrid');
      grid.innerHTML = '';
      for (let i = 0; i < 25; i++) {
        const cell = document.createElement('div');
        cell.className = 'bingo-cell';
        if (currentGrid[i] === "FREE SPACE") cell.classList.add('free');
        if (selected[i]) cell.classList.add('selected');
        // 内容用span包裹，保证居中
        const span = document.createElement('span');
        span.textContent = currentGrid[i];
        cell.appendChild(span);
        if (currentGrid[i] !== "FREE SPACE") {
          cell.addEventListener('click', () => {
            selected[i] = !selected[i];
            renderGrid();
            if (checkBingo()) showPopup();
          });
        }
        grid.appendChild(cell);
      }
    }

    function checkBingo() {
      for (let r = 0; r < gridSize; r++) {
        let row = true;
        for (let c = 0; c < gridSize; c++) {
          if (!selected[r * gridSize + c]) { row = false; break; }
        }
        if (row) return true;
        let col = true;
        for (let c = 0; c < gridSize; c++) {
          if (!selected[c * gridSize + r]) { col = false; break; }
        }
        if (col) return true;
      }
      let diag1 = true;
      for (let i = 0; i < gridSize; i++) {
        if (!selected[i * gridSize + i]) { diag1 = false; break; }
      }
      if (diag1) return true;
      let diag2 = true;
      for (let i = 0; i < gridSize; i++) {
        if (!selected[i * gridSize + (gridSize - 1 - i)]) { diag2 = false; break; }
      }
      if (diag2) return true;
      return false;
    }

    function showPopup() {
      document.getElementById('bingoPopup').classList.add('active');
    }
    function hidePopup() {
      document.getElementById('bingoPopup').classList.remove('active');
    }

    document.querySelector('.shuffle-btn').addEventListener('click', () => {
      setupGrid();
    });
    document.querySelector('.reset-btn').addEventListener('click', () => {
      selected = Array(25).fill(false);
      const freeIndex = currentGrid.findIndex(cell => cell === "FREE SPACE");
      if (freeIndex !== -1) selected[freeIndex] = true;
      renderGrid();
    });

    document.addEventListener('keydown', (e) => {
      if (e.key === "Escape") hidePopup();
    });

    setupGrid();
  </script>


</body></html>
