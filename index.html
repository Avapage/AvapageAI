import { useState, useEffect } from 'react';
import Head from 'next/head';
import { Line } from 'react-chartjs-2';
import Chart from 'chart.js/auto';

const API_URL = 'https://api.coingecko.com/api/v3';

export default function Home() {
  const [coins, setCoins] = useState([]);
  const [selectedCoin, setSelectedCoin] = useState({});  // Default to an empty object instead of null
  const [chartData, setChartData] = useState({}); // Initialize as empty object
  const [darkMode, setDarkMode] = useState(true);

  useEffect(() => {
    const fetchCoins = async () => {
      try {
        const res = await fetch(`${API_URL}/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&sparkline=false&price_change_percentage=1h`);
        if (!res.ok) throw new Error('Failed to fetch coins');
        const data = await res.json();
        setCoins(data);
      } catch (error) {
        console.error('Error fetching coins:', error);
      }
    };
    fetchCoins();
  }, []);

  useEffect(() => {
    const fetchChart = async () => {
      if (!selectedCoin.id) return;  // Ensure selectedCoin is properly selected before fetching chart data
      
      try {
        const res = await fetch(`${API_URL}/coins/${selectedCoin.id}/market_chart?vs_currency=usd&days=7`);
        if (!res.ok) throw new Error('Failed to fetch chart data');
        const data = await res.json();
        setChartData({
          labels: data.prices.map(price => new Date(price[0]).toLocaleDateString()),
          datasets: [{
            label: `${selectedCoin.name} Price (USD)`,
            data: data.prices.map(price => price[1]),
            fill: false,
            borderColor: 'rgb(75, 192, 192)',
            tension: 0.1
          }]
        });
      } catch (error) {
        console.error('Error fetching chart data:', error);
      }
    };
    if (selectedCoin.id) fetchChart();
  }, [selectedCoin]);

  const getRsiColor = (change) => {
    if (change > 7) return 'bg-red-500';
    if (change < -7) return 'bg-blue-500';
    return 'bg-gray-400';
  };

  return (
    <div className={`${darkMode ? "bg-black text-white" : "bg-white text-black"} min-h-screen transition-all`}>
      <Head>
        <title>Vanguard Crypto</title>
      </Head>

      <header className="flex justify-between items-center p-4 shadow">
        <h1 className="text-2xl font-bold">Vanguard Cryptocurrency</h1>
        <button
          onClick={() => setDarkMode(!darkMode)}
          className="text-sm px-3 py-1 border rounded shadow"
        >
          {darkMode ? "☀️ Light Mode" : "🌙 Dark Mode"}
        </button>
      </header>

      <main className="p-4 grid grid-cols-2 md:grid-cols-4 lg:grid-cols-5 gap-4">
        {coins.map((coin) => (
          <div
            key={coin.id}
            onClick={() => setSelectedCoin(coin)}
            className="cursor-pointer border rounded-xl p-3 shadow-md hover:shadow-xl transition-all"
          >
            <div className="flex items-center space-x-2">
              <img src={coin.image} alt={coin.name} className="w-6 h-6" />
              <span className="font-medium">{coin.name}</span>
            </div>
            <p className="text-sm">${coin.current_price.toLocaleString()}</p>
            <div className={`w-full h-2 mt-2 rounded ${getRsiColor(coin.price_change_percentage_1h_in_currency)}`}></div>
            <p className="text-xs mt-1">1H: {coin.price_change_percentage_1h_in_currency?.toFixed(2)}%</p>
          </div>
        ))}
      </main>

      {selectedCoin.id && chartData.datasets && (
        <section className="p-6">
          <h2 className="text-xl font-semibold mb-4">{selectedCoin.name} - 7 Day Price Chart</h2>
          <Line data={chartData} />
        </section>
      )}
    </div>
  );
}
