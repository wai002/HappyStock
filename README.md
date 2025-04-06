# HappyStock<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>恒生科技指數儀表板</title>
  <style>
    body {
      font-family: "Segoe UI", sans-serif;
      margin: 0;
      padding: 0;
      background: #f9f9f9;
      text-align: center;
    }
    header {
      background-color: #222;
      color: white;
      padding: 1rem;
      font-size: 1.5rem;
    }
    .container {
      max-width: 960px;
      margin: 2rem auto;
      padding: 1rem;
    }
    input {
      padding: 0.5rem;
      font-size: 1rem;
      width: 60%;
      max-width: 300px;
    }
    button {
      padding: 0.5rem 1rem;
      font-size: 1rem;
      margin-left: 0.5rem;
      background-color: #007bff;
      color: white;
      border: none;
      cursor: pointer;
    }
    iframe {
      width: 100%;
      height: 600px;
      border: none;
      margin-top: 2rem;
    }
    @media (max-width: 600px) {
      iframe {
        height: 400px;
      }
    }
  </style>
</head>
<body>
  <header>
    📈 恒生科技指數儀表板
  </header>
  <div class="container">
    <p>
      輸入股票代碼（例如：<code>INDEX:HSTECH</code>、<code>HKEX:700</code>、<code>NASDAQ:AAPL</code>）
    </p>
    <input type="text" id="symbol" placeholder="輸入 TradingView 代碼" value="INDEX:HSTECH" />
    <button onclick="loadChart()">載入圖表</button>

    <iframe
      id="tv-widget"
      src="https://www.tradingview.com/embed-widget/advanced-chart/?symbol=INDEX%3AHSTECH&interval=15&theme=light&style=1&timezone=Asia%2FTaipei&hide_side_toolbar=false&save_image=true&studies=[]&locale=zh_TW"
      allowfullscreen>
    </iframe>
  </div>

  <script>
    function loadChart() {
      const symbol = document.getElementById("symbol").value.trim();
      if (!symbol) return alert("請輸入股票代碼");
      const encodedSymbol = encodeURIComponent(symbol);
      const chartSrc = `https://www.tradingview.com/embed-widget/advanced-chart/?symbol=${encodedSymbol}&interval=15&theme=light&style=1&timezone=Asia%2FTaipei&hide_side_toolbar=false&save_image=true&studies=[]&locale=zh_TW`;
      document.getElementById("tv-widget").src = chartSrc;
    }
  </script>
</body>
</html>
