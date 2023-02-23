# iD

<head>
  <script src="https://unpkg.com/lightweight-charts@3.3.0/dist/lightweight-charts.standalone.production.js"></script>
</head>

<body>
  <div id="chart"></div>
</body>

const chart = LightweightCharts.createChart(document.getElementById('chart'), {
    width: 600,
    height: 400,
    timeScale: {
        timeVisible: true,
        secondsVisible: false,
        tickMarkFormatter: (time, tickIndex, ticks) => {
            const date = new Date(time * 1000);
            return date.toLocaleDateString();
        },
    },
});

const series = chart.addCandlestickSeries({
    upColor: '#00ff00',
    downColor: '#ff0000',
    borderUpColor: '#00ff00',
    borderDownColor: '#ff0000',
    wickUpColor: '#00ff00',
    wickDownColor: '#ff0000',
    priceScale: {
        mode: LightweightCharts.PriceScaleMode.Normal,
        borderColor: '#D9D9D9',
    },
    scaleMargins: {
        top: 0.2,
        bottom: 0.2,
    },
});

fetch('https://api.polygon.io/v2/aggs/ticker/XOM/range/1/day/2020-01-01/2020-12-31?apiKey=<YOUR_API_KEY>')
    .then((response) => response.json())
    .then((data) => {
        const formattedData = data.results.map((d) => ({
            time: d.t / 1000,
            open: d.o,
            high: d.h,
            low: d.l,
            close: d.c,
        }));
        series.setData(formattedData);
    });


const lineSeries = chart.addLineSeries({
    priceLineVisible: false,
    color: '#00ff00',
    lineWidth: 2,
    crosshairMarkerVisible: false
