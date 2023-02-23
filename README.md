# iD

<head>
    <meta charset="UTF-8">
    <title>TradingView Lightweight Charts Example</title>
    <script src="https://unpkg.com/lightweight-charts@3.3.0/dist/lightweight-charts.standalone.production.js"></script>
</head>



<body>
    <div id="chart"></div>
    <script>
        const chart = LightweightCharts.createChart(document.getElementById('chart'), {
            width: 600,
            height: 400,
            layout: {
                backgroundColor: '#ffffff',
                textColor: '#333333',
            },
            grid: {
                vertLines: {
                    visible: false,
                },
                horzLines: {
                    color: '#eee',
                },
            },
            crosshair: {
                mode: LightweightCharts.CrosshairMode.Normal,
            },
            rightPriceScale: {
                borderColor: '#000',
            },
            timeScale: {
                borderColor: '#000',
            },
        });
        
        const lineSeries = chart.addLineSeries();
        lineSeries.setData([
            { time: '2018-10-19', value: 50.1 },
            { time: '2018-10-22', value: 50.2 },
            { time: '2018-10-23', value: 50.3 },
            { time: '2018-10-24', value: 50.4 },
            { time: '2018-10-25', value: 50.5 },
            { time: '2018-10-26', value: 50.6 },
            { time: '2018-10-29', value: 50.7 },
            { time: '2018-10-30', value: 50.8 },
            { time: '2018-10-31', value: 50.9 },
            { time: '2018-11-01', value: 51.0 },
            { time: '2018-11-02', value: 51.1 },
            { time: '2018-11-05', value: 51.2 },
            { time: '2018-11-06', value: 51.3 },
            { time: '2018-11-07', value: 51.4 },
            { time: '2018-11-08', value: 51.5 },
            { time: '2018-11-09', value: 51.6 },
            { time: '2018-11-12', value: 51.7 },
            { time: '2018-11-13', value: 51.8 },
            { time: '2018-11-14', value: 51.9 },
            { time: '2018-11-15', value: 52.0 },
            { time: '2018-11-16', value: 52.1 },
        ]);
    </script>
</body>
