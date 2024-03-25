<template>
  <div>
    <canvas id="statistik"></canvas>
  </div>
</template>

<script setup>
import Chart from 'chart.js/auto'

const labels = [
    'January',
    'February',
    'March',
    'April',
    'May',
    'June',
  ];

  const data = {
    labels: labels,
    datasets: [{
      label: 'Pengunjung',
      backgroundColor: 'rgb(255, 99, 132)',
      borderColor: 'rgb(255, 99, 132)',
      data: [30, 40, 50, 40, 20, 50],
    }]
  };

  const config = {
    type: 'bar',
    data: data,
    options: {}
  };


onMounted(() => {
  const myChart = new Chart(
    document.getElementById('statistik'),
    config
  );
})
</script>