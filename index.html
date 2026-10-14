<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pattern Tile Generator</title>
  <style>
    :root {
      --bg: #121316;
      --panel-bg: #1e2025;
      --border: #2e323b;
      --accent: #4f46e5;
      --accent-hover: #4338ca;
      --text: #f3f4f6;
      --text-muted: #9ca3af;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      user-select: none;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
      background: var(--bg);
      color: var(--text);
      display: flex;
      flex-direction: column;
      height: 100vh;
      overflow: hidden;
    }

    header {
      padding: 12px 24px;
      border-bottom: 1px solid var(--border);
      background: var(--panel-bg);
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    header h1 {
      font-size: 1.1rem;
      font-weight: 600;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .main-container {
      display: flex;
      flex: 1;
      height: calc(100vh - 57px);
    }

    /* 左側: エディタ・操作パネル */
    .sidebar {
      width: 380px;
      background: var(--panel-bg);
      border-right: 1px solid var(--border);
      padding: 20px;
      display: flex;
      flex-direction: column;
      gap: 18px;
      overflow-y: auto;
    }

    .section-title {
      font-size: 0.8rem;
      text-transform: uppercase;
      letter-spacing: 0.05em;
      color: var(--text-muted);
      margin-bottom: 8px;
    }

    .control-row {
      display: flex;
      gap: 8px;
      align-items: center;
    }

    .btn {
      background: #2a2d35;
      color: var(--text);
      border: 1px solid var(--border);
      padding: 6px 12px;
      border-radius: 6px;
      cursor: pointer;
      font-size: 0.85rem;
      transition: all 0.15s ease;
    }

    .btn:hover {
      background: #373b45;
    }

    .btn.active {
      background: var(--accent);
      border-color: var(--accent);
      color: #fff;
    }

    .btn-primary {
      background: var(--accent);
      border-color: var(--accent);
      color: #fff;
    }

    .btn-primary:hover {
      background: var(--accent-hover);
    }

    /* グリッドキャンバス */
    .grid-wrapper {
      display: flex;
      justify-content: center;
      align-items: center;
      background: #17181c;
      padding: 16px;
      border-radius: 10px;
      border: 1px solid var(--border);
    }

    #grid {
      display: grid;
      gap: 2px;
      background: #2b2e36;
      padding: 2px;
      border-radius: 6px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.3);
    }

    .cell {
      width: 100%;
      height: 100%;
      background: #ffffff;
      cursor: crosshair;
      border-radius: 2px;
      transition: transform 0.05s ease;
    }

    .cell:hover {
      filter: brightness(0.9);
      transform: scale(0.96);
    }

    /* パレット */
    .color-picker-row {
      display: flex;
      gap: 8px;
      align-items: center;
    }

    .palette {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
    }

    .palette-swatch {
      width: 24px;
      height: 24px;
      border-radius: 4px;
      cursor: pointer;
      border: 2px solid transparent;
      transition: transform 0.1s;
    }

    .palette-swatch:hover {
      transform: scale(1.15);
    }

    .palette-swatch.active {
      border-color: #fff;
      box-shadow: 0 0 0 1px var(--bg);
    }

    /* 右側: プレビューエリア */
    .preview-container {
      flex: 1;
      display: flex;
      flex-direction: column;
      background: #0f1013;
      position: relative;
    }

    .preview-bar {
      padding: 10px 20px;
      background: rgba(30, 32, 37, 0.8);
      backdrop-filter: blur(8px);
      border-bottom: 1px solid var(--border);
      display: flex;
      justify-content: space-between;
      align-items: center;
      z-index: 10;
    }

    .preview-canvas-wrapper {
      flex: 1;
      width: 100%;
      height: 100%;
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    #previewCanvas {
      width: 100%;
      height: 100%;
    }

    input[type="color"] {
      -webkit-appearance: none;
      border: none;
      width: 32px;
      height: 32px;
      border-radius: 6px;
      cursor: pointer;
      background: none;
    }

    input[type="range"] {
      flex: 1;
      accent-color: var(--accent);
    }
  </style>
</head>
<body>

  <header>
    <h1>▦ パターン・タイル・ジェネレーター</h1>
    <div class="control-row">
      <button class="btn btn-primary" id="btnExport">PNG保存</button>
    </div>
  </header>

  <div class="main-container">
    <!-- サイドバー -->
    <div class="sidebar">
      
      <!-- グリッドサイズ -->
      <div>
        <div class="section-title">正方形グリッドサイズ</div>
        <div class="control-row">
          <button class="btn active size-btn" data-size="3">3×3</button>
          <button class="btn size-btn" data-size="4">4×4</button>
          <button class="btn size-btn" data-size="8">8×8</button>
          <button class="btn size-btn" data-size="12">12×12</button>
        </div>
      </div>

      <!-- カラー設定 -->
      <div>
        <div class="section-title">描画カラー</div>
        <div class="color-picker-row">
          <input type="color" id="currentColor" value="#ff4b4b">
          <div class="palette" id="palette"></div>
        </div>
      </div>

      <!-- シンメトリー描画設定 -->
      <div>
        <div class="section-title">対称描画（自動シンメトリー）</div>
        <div class="control-row">
          <button class="btn active sym-btn" data-sym="none">通常</button>
          <button class="btn sym-btn" data-sym="x">左右対称</button>
          <button class="btn sym-btn" data-sym="y">上下対称</button>
          <button class="btn sym-btn" data-sym="quad">万華鏡(4方向)</button>
        </div>
      </div>

      <!-- 編集グリッド -->
      <div class="grid-wrapper">
        <div id="grid"></div>
      </div>

      <!-- 編集アクション -->
      <div class="control-row" style="flex-wrap: wrap;">
        <button class="btn" id="btnRandom">🎲 ランダム生成</button>
        <button class="btn" id="btnRotate">⟳ 90°回転</button>
        <button class="btn" id="btnClear">全消去</button>
      </div>

    </div>

    <!-- プレビュー -->
    <div class="preview-container">
      <div class="preview-bar">
        <span style="font-size: 0.9rem; color: var(--text-muted);">連続パターンのプレビュー</span>
        <div class="control-row">
          <span style="font-size: 0.8rem; color: var(--text-muted);">タイル密度:</span>
          <input type="range" id="scaleSlider" min="20" max="150" value="70">
        </div>
      </div>
      <div class="preview-canvas-wrapper">
        <canvas id="previewCanvas"></canvas>
      </div>
    </div>
  </div>

  <script>
    // デフォルト色プリセット
    const PRESET_COLORS = [
      '#ffffff', '#1e2025', '#ff4b4b', '#ff9f43',
      '#feca57', '#1dd1a1', '#48dbfb', '#5f27cd'
    ];

    let gridSize = 3;
    let symmetryMode = 'none';
    let activeColor = '#ff4b4b';
    let isDrawing = false;
    let gridData = [];

    const gridEl = document.getElementById('grid');
    const colorInput = document.getElementById('currentColor');
    const paletteEl = document.getElementById('palette');
    const previewCanvas = document.getElementById('previewCanvas');
    const ctx = previewCanvas.getContext('2d');
    const scaleSlider = document.getElementById('scaleSlider');

    // 初期化
    function init() {
      setupPalette();
      setupGridData(gridSize);
      renderGridUI();
      resizeCanvas();
      updatePreview();

      window.addEventListener('resize', () => {
        resizeCanvas();
        updatePreview();
      });

      window.addEventListener('mouseup', () => isDrawing = false);
    }

    // パレット生成
    function setupPalette() {
      paletteEl.innerHTML = '';
      PRESET_COLORS.forEach(c => {
        const swatch = document.createElement('div');
        swatch.className = 'palette-swatch';
        swatch.style.background = c;
        if (c === activeColor) swatch.classList.add('active');
        swatch.onclick = () => {
          activeColor = c;
          colorInput.value = c;
          document.querySelectorAll('.palette-swatch').forEach(s => s.classList.remove('active'));
          swatch.classList.add('active');
        };
        paletteEl.appendChild(swatch);
      });

      colorInput.addEventListener('input', (e) => {
        activeColor = e.target.value;
      });
    }

    // データ配列のリセット
    function setupGridData(size) {
      gridSize = size;
      gridData = Array.from({ length: size }, () => Array(size).fill('#ffffff'));
    }

    // 編集用グリッドUIを描画
    function renderGridUI() {
      gridEl.innerHTML = '';
      const cellSize = Math.floor(260 / gridSize);
      gridEl.style.gridTemplateColumns = `repeat(${gridSize}, ${cellSize}px)`;
      gridEl.style.gridTemplateRows = `repeat(${gridSize}, ${cellSize}px)`;

      for (let y = 0; y < gridSize; y++) {
        for (let x = 0; x < gridSize; x++) {
          const cell = document.createElement('div');
          cell.className = 'cell';
          cell.style.background = gridData[y][x];

          cell.addEventListener('mousedown', (e) => {
            isDrawing = true;
            paint(x, y);
          });

          cell.addEventListener('mouseenter', () => {
            if (isDrawing) paint(x, y);
          });

          gridEl.appendChild(cell);
        }
      }
    }

    // セルの色塗り（シンメトリー処理含む）
    function paint(x, y) {
      const targets = [[x, y]];

      if (symmetryMode === 'x' || symmetryMode === 'quad') {
        targets.push([gridSize - 1 - x, y]);
      }
      if (symmetryMode === 'y' || symmetryMode === 'quad') {
        targets.push([x, gridSize - 1 - y]);
      }
      if (symmetryMode === 'quad') {
        targets.push([gridSize - 1 - x, gridSize - 1 - y]);
      }

      targets.forEach(([cx, cy]) => {
        gridData[cy][cx] = activeColor;
        const index = cy * gridSize + cx;
        if (gridEl.children[index]) {
          gridEl.children[index].style.background = activeColor;
        }
      });

      updatePreview();
    }

    // プレビューの描画（Canvas上でリピートタイリング）
    function updatePreview() {
      const w = previewCanvas.width;
      const h = previewCanvas.height;
      ctx.clearRect(0, 0, w, h);

      const tileSize = parseInt(scaleSlider.value, 10);
      const pixelSize = tileSize / gridSize;

      const cols = Math.ceil(w / tileSize) + 1;
      const rows = Math.ceil(h / tileSize) + 1;

      for (let r = 0; r < rows; r++) {
        for (let c = 0; c < cols; c++) {
          const startX = c * tileSize;
          const startY = r * tileSize;

          for (let y = 0; y < gridSize; y++) {
            for (let x = 0; x < gridSize; x++) {
              ctx.fillStyle = gridData[y][x];
              ctx.fillRect(
                startX + x * pixelSize,
                startY + y * pixelSize,
                Math.ceil(pixelSize),
                Math.ceil(pixelSize)
              );
            }
          }
        }
      }
    }

    function resizeCanvas() {
      const rect = previewCanvas.parentElement.getBoundingClientRect();
      previewCanvas.width = rect.width;
      previewCanvas.height = rect.height;
    }

    // ランダム生成
    document.getElementById('btnRandom').onclick = () => {
      const colors = [activeColor, '#ffffff', '#1e2025'];
      for (let y = 0; y < gridSize; y++) {
        for (let x = 0; x < gridSize; x++) {
          gridData[y][x] = colors[Math.floor(Math.random() * colors.length)];
        }
      }
      renderGridUI();
      updatePreview();
    };

    // 90度回転
    document.getElementById('btnRotate').onclick = () => {
      const next = Array.from({ length: gridSize }, () => Array(gridSize).fill('#fff'));
      for (let y = 0; y < gridSize; y++) {
        for (let x = 0; x < gridSize; x++) {
          next[x][gridSize - 1 - y] = gridData[y][x];
        }
      }
      gridData = next;
      renderGridUI();
      updatePreview();
    };

    // 全消去
    document.getElementById('btnClear').onclick = () => {
      setupGridData(gridSize);
      renderGridUI();
      updatePreview();
    };

    // グリッドサイズ切り替えボタン
    document.querySelectorAll('.size-btn').forEach(btn => {
      btn.onclick = () => {
        document.querySelectorAll('.size-btn').forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
        setupGridData(parseInt(btn.dataset.size, 10));
        renderGridUI();
        updatePreview();
      };
    });

    // 対称モード切り替えボタン
    document.querySelectorAll('.sym-btn').forEach(btn => {
      btn.onclick = () => {
        document.querySelectorAll('.sym-btn').forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
        symmetryMode = btn.dataset.sym;
      };
    });

    scaleSlider.addEventListener('input', updatePreview);

    // PNGエクスポート
    document.getElementById('btnExport').onclick = () => {
      const link = document.createElement('a');
      link.download = `pattern_${gridSize}x${gridSize}.png`;
      link.href = previewCanvas.toDataURL('image/png');
      link.click();
    };

    init();
  </script>
</body>
</html>
