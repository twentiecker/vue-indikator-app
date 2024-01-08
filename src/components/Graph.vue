<script>
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
} from 'chart.js';
import { Bar, Line } from 'vue-chartjs';

ChartJS.register(
  CategoryScale,
  LinearScale,
  BarElement,
  PointElement,
  LineElement,
  Title,
  Tooltip,
  Legend
);

export default {
  name: 'App',
  components: {
    Bar,
    Line,
  },
  data() {
    return {
      isLine: false,
      dataBar: {
        labels: [
          'Januari',
          'Februari',
          'Maret',
          'April',
          'Mei',
          'Juni',
          'Juli',
          'Agustus',
          'September',
          'Oktober',
          'November',
          'Desember',
        ],
        datasets: [
          {
            label: 'Nilai',
            data: [
              126.52,
              105.79,
              119.98,
              112.76,
              139.43,
              126.84,
              127.25,
              118.53,
              120.1,
              146.14,
              150.58,
              163.62,
            ],
            backgroundColor: ['rgba(0, 0, 0, 0.8)'],
          },
          {
            label: 'm-to-m',
            data: [
              -22.89,
              -16.38,
              13.41,
              -6.02,
              23.66,
              -9.03,
              0.32,
              -6.85,
              1.32,
              21.68,
              3.04,
              8.66,
            ],
            backgroundColor: ['rgba(255, 74, 85, 0.8)'],
          },
          {
            label: 'y-on-y',
            data: [
              -90.2,
              -87.88,
              -75.32,
              -28.67,
              -13.85,
              -18.98,
              -18.3,
              -26.63,
              -19.39,
              -4.04,
              4.22,
              -0.28,
            ],
            backgroundColor: ['rgba(255, 149, 0, 0.8)'],
          },
          {
            label: 'c-to-c',
            data: [
              -90.2,
              -89.26,
              -86.13,
              -83.48,
              -81.69,
              -82.49,
              -82.45,
              -83.12,
              -82.87,
              -81.1,
              -80.69,
              -80.05,
            ],
            backgroundColor: ['rgba(29, 199, 234, 0.8)'],
          },
        ],
      },
      dataLine: {
        labels: [
          'Januari',
          'Februari',
          'Maret',
          'April',
          'Mei',
          'Juni',
          'Juli',
          'Agustus',
          'September',
          'Oktober',
          'November',
          'Desember',
        ],
        datasets: [
          {
            label: 'Nilai',
            data: [
              126.52,
              105.79,
              119.98,
              112.76,
              139.43,
              126.84,
              127.25,
              118.53,
              120.1,
              146.14,
              150.58,
              163.62,
            ],
            fill: false,
            borderColor: 'rgba(0, 0, 0, 0.8)',
            tension: 0.1,
          },
          {
            label: 'm-to-m',
            data: [
              -22.89,
              -16.38,
              13.41,
              -6.02,
              23.66,
              -9.03,
              0.32,
              -6.85,
              1.32,
              21.68,
              3.04,
              8.66,
            ],
            fill: false,
            borderColor: 'rgba(255, 74, 85, 0.8)',
            tension: 0.1,
          },
          {
            label: 'y-on-y',
            data: [
              -90.2,
              -87.88,
              -75.32,
              -28.67,
              -13.85,
              -18.98,
              -18.3,
              -26.63,
              -19.39,
              -4.04,
              4.22,
              -0.28,
            ],
            fill: false,
            borderColor: 'rgba(255, 149, 0, 0.8)',
            tension: 0.1,
          },
          {
            label: 'c-to-c',
            data: [
              -90.2,
              -89.26,
              -86.13,
              -83.48,
              -81.69,
              -82.49,
              -82.45,
              -83.12,
              -82.87,
              -81.1,
              -80.69,
              -80.05,
            ],
            fill: false,
            borderColor: 'rgba(29, 199, 234, 0.8)',
            tension: 0.1,
          },
        ],
      },
      options: {
        responsive: true,
      },
    };
  },
  methods: {
    showLine() {
      return (this.isLine = !this.isLine);
    },
  },
};
</script>

<template>
  <main>
    <header>
      <div class="card" style="padding: 10px;">
        <h4>Jumlah Kunjungan Wisman (Ribu)</h4>
        <div
          style="display: flex; justify-content: space-between; align-items: center;padding: 0px 10px 0px 10px;"
        >
          <i>
            Icon
          </i>
          <div>
            <h2>163,62</h2>
            <h6>Des 2021</h6>
          </div>
        </div>
      </div>
      <div class="card"></div>
      <div class="card"></div>
      <div class="card"></div>
    </header>
    <div class="chart-container">
      <div class="button-container">
        <button @click="showLine" :disabled="!isLine">Bar</button>
        <button @click="showLine" :disabled="isLine">Line</button>
      </div>
      <Bar v-if="!isLine" :data="dataBar" :options="options" />
      <Line v-if="isLine" :data="dataLine" :options="options" />
    </div>
  </main>
</template>

<style scoped>
main {
  padding: 20px;
}

header {
  display: flex;
  margin-bottom: 20px;
}

.card {
  width: 25%;
  height: 150px;
  margin: 10px;
  border-style: solid;
  border-color: rgb(0, 0, 0, 0.1);
}

button {
  padding: 2px;
  width: 50px;
  background-color: rgb(128, 0, 32);
  border: none;
  color: white;
  border-radius: 20px;
  margin-left: 7px;
  cursor: pointer;
}

button:disabled {
  opacity: 50%;
}

.chart-container {
  margin-left: 10px;
  margin-right: 10px;
  width: 50%;
  padding: 10px;
  border-style: solid;
  border-color: rgb(0, 0, 0, 0.1);
}

.button-container {
  padding-top: 10px;
}
</style>
