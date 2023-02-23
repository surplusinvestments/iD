# iD

<head>
  <script src="https://unpkg.com/lightweight-charts@3.3.0/dist/lightweight-charts.standalone.production.js"></script>
</head>

<body>
  <div id="chart"></div>
</body>

const chart = LightweightCharts.createChart(document.getElementById('chart'), {
  width: 600,
  height: 300,
});

const candlestickSeries = chart.addCandlestickSeries();

fetch('https://api.polygon.io/v2/aggs/ticker/AAPL/range/1/day/2020-01-01/2020-12-31?apiKey=<YOUR_API_KEY>')
  .then(response => response.json())
  .then(data => {
    const formattedData = data.results.map(d => ({
      time: d.t / 1000,
      open: d.o,
      high: d.h,
      low: d.l,
      close: d.c,
    }));

    candlestickSeries.setData(formattedData);
  });
