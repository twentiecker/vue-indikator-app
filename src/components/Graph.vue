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
} from "chart.js";
import { Bar, Line } from "vue-chartjs";

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
  name: "App",
  components: {
    Bar,
    Line,
  },
  data() {
    return {
      mainIndikator: "MOBILITAS DAN PARIWISATA",
      indikator: "Jumlah kunjungan wisman",
      month: "Dec",
      year: "2021",
      isShowMainIndikator: false,
      isShowIndikator: false,
      isShowMonth: false,
      isShowYear: false,
      dropdownClassMainIndikator: "dropdown-content main-indikator",
      dropdownClassIndikator: "dropdown-content",
      dropdownClassMonth: "dropdown-content flex-month",
      dropdownClassYear: "dropdown-content flex-year",
      isLine: false,
      dataBar: {
        labels: [
          "Jan",
          "Feb",
          "Mar",
          "Apr",
          "May",
          "Jun",
          "Jul",
          "Agt",
          "Sep",
          "Okt",
          "Nov",
          "Dec",
        ],
        datasets: [
          {
            label: "Nilai",
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
            backgroundColor: ["rgba(128, 0, 32, 1)"],
          },
          {
            label: "m-to-m",
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
            backgroundColor: ["rgba(255, 74, 85, 1)"],
          },
          {
            label: "y-on-y",
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
            backgroundColor: ["rgba(255, 149, 0, 1)"],
          },
          {
            label: "c-to-c",
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
            backgroundColor: ["rgba(29, 199, 234, 0.8)"],
          },
        ],
      },
      dataLine: {
        labels: [
          "Jan",
          "Feb",
          "Mar",
          "Apr",
          "May",
          "Jun",
          "Jul",
          "Agt",
          "Sep",
          "Okt",
          "Nov",
          "Dec",
        ],
        datasets: [
          {
            label: "Nilai",
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
            borderColor: "rgba(128, 0, 32, 1)",
            tension: 0.1,
          },
          {
            label: "m-to-m",
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
            borderColor: "rgba(255, 74, 85, 1)",
            tension: 0.1,
          },
          {
            label: "y-on-y",
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
            borderColor: "rgba(255, 149, 0, 1)",
            tension: 0.1,
          },
          {
            label: "c-to-c",
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
            borderColor: "rgba(29, 199, 234, 1)",
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
    dropdownShowMainIndikator() {
      this.isShowMainIndikator = !this.isShowMainIndikator;
      if (this.isShowMainIndikator) {
        this.dropdownClassMainIndikator =
          "dropdown-content main-indikator show";
      } else {
        this.dropdownClassMainIndikator = "dropdown-content main-indikator";
      }
    },
    dropdownShowIndikator() {
      this.isShowIndikator = !this.isShowIndikator;
      if (this.isShowIndikator) {
        this.dropdownClassIndikator = "dropdown-content show";
      } else {
        this.dropdownClassIndikator = "dropdown-content";
      }
    },
    dropdownShowMonth() {
      this.isShowMonth = !this.isShowMonth;
      if (this.isShowMonth) {
        this.dropdownClassMonth = "dropdown-content flex-month show";
      } else {
        this.dropdownClassMonth = "dropdown-content flex-month";
      }
    },
    dropdownShowYear() {
      this.isShowYear = !this.isShowYear;
      if (this.isShowYear) {
        this.dropdownClassYear = "dropdown-content flex-year show";
      } else {
        this.dropdownClassYear = "dropdown-content flex-year";
      }
    },
    SelectMainIndikator1() {
      this.mainIndikator = "MOBILITAS DAN PARIWISATA";
      this.isShowMainIndikator = false;
      this.dropdownClassMainIndikator = "dropdown-content main-indikator";
    },
    SelectMainIndikator2() {
      this.mainIndikator = "INFLASI";
      this.isShowMainIndikator = false;
      this.dropdownClassMainIndikator = "dropdown-content main-indikator";
    },
    SelectMainIndikator3() {
      this.mainIndikator = "DAYA BELI MASYARAKAT";
      this.isShowMainIndikator = false;
      this.dropdownClassMainIndikator = "dropdown-content main-indikator";
    },
    SelectMainIndikator4() {
      this.mainIndikator = "PERDAGANGAN";
      this.isShowMainIndikator = false;
      this.dropdownClassMainIndikator = "dropdown-content main-indikator";
    },
    SelectMainIndikator5() {
      this.mainIndikator = "MONETER";
      this.isShowMainIndikator = false;
      this.dropdownClassMainIndikator = "dropdown-content main-indikator";
    },
    SelectMainIndikator6() {
      this.mainIndikator = "AKTIVITAS PRODUKSI";
      this.isShowMainIndikator = false;
      this.dropdownClassMainIndikator = "dropdown-content main-indikator";
    },
    SelectMainIndikator7() {
      this.mainIndikator = "HARGA KOMODITAS UNGGULAN";
      this.isShowMainIndikator = false;
      this.dropdownClassMainIndikator = "dropdown-content main-indikator";
    },
    SelectIndikator1() {
      this.indikator = "Jumlah kunjungan wisman";
      this.isShowIndikator = false;
      this.dropdownClassIndikator = "dropdown-content";
    },
    SelectIndikator2() {
      this.indikator = "Jumlah penumpang angkutan udara";
      this.isShowIndikator = false;
      this.dropdownClassIndikator = "dropdown-content";
    },
    SelectIndikator3() {
      this.indikator = "Jumlah penumpang angkutan udara: domestik";
      this.isShowIndikator = false;
      this.dropdownClassIndikator = "dropdown-content";
    },
    SelectIndikator4() {
      this.indikator = "Jumlah penumpang angkutan udara: internasional";
      this.isShowIndikator = false;
      this.dropdownClassIndikator = "dropdown-content";
    },
    SelectIndikator5() {
      this.indikator = "Jumlah penumpang angkutan laut";
      this.isShowIndikator = false;
      this.dropdownClassIndikator = "dropdown-content";
    },
    SelectIndikator6() {
      this.indikator = "Jumlah penumpang angkutan kereta api";
      this.isShowIndikator = false;
      this.dropdownClassIndikator = "dropdown-content";
    },
    SelectMonth1() {
      this.month = "Jan";
      this.isShowMonth = false;
      this.dropdownClassMonth = "dropdown-content flex-month";
    },
    SelectMonth2() {
      this.month = "Feb";
      this.isShowMonth = false;
      this.dropdownClassMonth = "dropdown-content flex-month";
    },
    SelectMonth3() {
      this.month = "Mar";
      this.isShowMonth = false;
      this.dropdownClassMonth = "dropdown-content flex-month";
    },
    SelectMonth4() {
      this.month = "Apr";
      this.isShowMonth = false;
      this.dropdownClassMonth = "dropdown-content flex-month";
    },
    SelectMonth5() {
      this.month = "May";
      this.isShowMonth = false;
      this.dropdownClassMonth = "dropdown-content flex-month";
    },
    SelectMonth6() {
      this.month = "Jun";
      this.isShowMonth = false;
      this.dropdownClassMonth = "dropdown-content flex-month";
    },
    SelectMonth7() {
      this.month = "Jul";
      this.isShowMonth = false;
      this.dropdownClassMonth = "dropdown-content flex-month";
    },
    SelectMonth8() {
      this.month = "Agt";
      this.isShowMonth = false;
      this.dropdownClassMonth = "dropdown-content flex-month";
    },
    SelectMonth9() {
      this.month = "Sep";
      this.isShowMonth = false;
      this.dropdownClassMonth = "dropdown-content flex-month";
    },
    SelectMonth10() {
      this.month = "Okt";
      this.isShowMonth = false;
      this.dropdownClassMonth = "dropdown-content flex-month";
    },
    SelectMonth11() {
      this.month = "Nov";
      this.isShowMonth = false;
      this.dropdownClassMonth = "dropdown-content flex-month";
    },
    SelectMonth12() {
      this.month = "Des";
      this.isShowMonth = false;
      this.dropdownClassMonth = "dropdown-content flex-month";
    },
    SelectYear1() {
      this.year = 2019;
      this.isShowYear = false;
      this.dropdownClassYear = "dropdown-content flex-year";
    },
    SelectYear2() {
      this.year = 2020;
      this.isShowYear = false;
      this.dropdownClassYear = "dropdown-content flex-year";
    },
    SelectYear3() {
      this.year = 2021;
      this.isShowYear = false;
      this.dropdownClassYear = "dropdown-content flex-year";
    },
    SelectYear4() {
      this.year = 2022;
      this.isShowYear = false;
      this.dropdownClassYear = "dropdown-content flex-year";
    },
    SelectYear5() {
      this.year = 2023;
      this.isShowYear = false;
      this.dropdownClassYear = "dropdown-content flex-year";
    },
  },
};
</script>

<template>
  <main>
    <div class="dropdown" style="margin-bottom: 35px;padding-top: 2px;">
      <button
        @click="dropdownShowMainIndikator"
        class="title"
        style="display: flex; align-items: center; border: none; background-color: transparent; cursor: pointer;"
      >
        <h1 class="main-title">
          {{ mainIndikator }}
        </h1>
        <i
          class="bx bxs-down-arrow"
          style="font-size: 15px; color: var(--text-color); margin-left: 5px; margin-top: 5px;"
        ></i>
      </button>
    </div>
    <div :class="dropdownClassMainIndikator">
      <a @click="SelectMainIndikator1" href="#">MOBILITAS DAN PARIWISATA</a>
      <a @click="SelectMainIndikator2" href="#">INFLASI</a>
      <a @click="SelectMainIndikator3" href="#">DAYA BELI MASYARAKAT</a>
      <a @click="SelectMainIndikator4" href="#">PERDAGANGAN</a>
      <a @click="SelectMainIndikator5" href="#">MONETER</a>
      <a @click="SelectMainIndikator6" href="#">AKTIVITAS PRODUKSI</a>
      <a @click="SelectMainIndikator7" class="last-options" href="#"
        >HARGA KOMODITAS UNGGULAN
      </a>
    </div>

    <header>
      <div class="input-info">
        <div class="group-button">
          <div class="dropdown">
            <button @click="dropdownShowIndikator" class="title">
              <h1>
                {{ indikator }}
              </h1>
              <i class="bx bxs-down-arrow"></i>
            </button>
          </div>
          <div :class="dropdownClassIndikator">
            <a @click="SelectIndikator1" href="#">Jumlah kunjungan wisman</a>
            <a @click="SelectIndikator2" href="#"
              >Jumlah penumpang angkutan udara</a
            >
            <a @click="SelectIndikator3" href="#"
              >Jumlah penumpang angkutan udara: domestik</a
            >
            <a @click="SelectIndikator4" href="#"
              >Jumlah penumpang angkutan udara: internasional</a
            >
            <a @click="SelectIndikator5" href="#"
              >Jumlah penumpang angkutan laut</a
            >
            <a @click="SelectIndikator6" class="last-options" href="#"
              >Jumlah penumpang angkutan kereta api</a
            >
          </div>
          <h3>Periode :</h3>
          <div class="date">
            <div class="dropdown">
              <button @click="dropdownShowMonth">
                <h3>{{ month }}</h3>
                <i class="bx bxs-down-arrow"></i>
              </button>
            </div>
            <div :class="dropdownClassMonth">
              <a @click="SelectMonth1" href="#">Jan</a>
              <a @click="SelectMonth2" href="#">Feb</a>
              <a @click="SelectMonth3" href="#">Mar</a>
              <a @click="SelectMonth4" href="#">Apr</a>
              <a @click="SelectMonth5" href="#">May</a>
              <a @click="SelectMonth6" href="#">Jun</a>
              <a @click="SelectMonth7" href="#">Jul</a>
              <a @click="SelectMonth8" href="#">Agt</a>
              <a @click="SelectMonth9" href="#">Sep</a>
              <a @click="SelectMonth10" href="#">Okt</a>
              <a @click="SelectMonth11" href="#">Nov</a>
              <a @click="SelectMonth12" class="last-options" href="#">Dec</a>
            </div>
            <div class="dropdown">
              <button @click="dropdownShowYear">
                <h3>{{ year }}</h3>
                <i class="bx bxs-down-arrow"></i>
              </button>
            </div>
            <div :class="dropdownClassYear">
              <a @click="SelectYear1" href="#">2019</a>
              <a @click="SelectYear2" href="#">2020</a>
              <a @click="SelectYear3" href="#">2021</a>
              <a @click="SelectYear4" href="#">2022</a>
              <a @click="SelectYear5" class="last-options" href="#">2023</a>
            </div>
          </div>
        </div>
        <i class="bx bx-stats"></i>
      </div>
      <div class="card">
        <div class="card-border"></div>
        <div class="card-container">
          <i class="bx bx-transfer-alt"></i>
          <div class="card-content">
            <h4>Nilai (Ribu)</h4>
            <h1>163,62</h1>
            <h5>{{ month }} {{ year }}</h5>
          </div>
        </div>
      </div>
    </header>
    <div class="row-chart">
      <div class="chart-container">
        <div class="button-container">
          <button @click="showLine" :disabled="!isLine">Bar</button>
          <button @click="showLine" :disabled="isLine">Line</button>
        </div>
        <Bar v-if="!isLine" :data="dataBar" :options="options" />
        <Line v-if="isLine" :data="dataLine" :options="options" />
      </div>
      <div class="col-card">
        <div class="card">
          <div class="card-border month"></div>
          <div class="card-container">
            <i class="bx bxs-bar-chart-alt-2 month"></i>
            <div class="card-content">
              <h4>m-to-m (%)</h4>
              <h1>8,66</h1>
              <h5>{{ month }} {{ year }}</h5>
            </div>
          </div>
        </div>
        <div class="card">
          <div class="card-border year"></div>
          <div class="card-container">
            <i class="bx bx-paper-plane year"></i>
            <div class="card-content">
              <h4>y-on-y (%)</h4>
              <h1>-0,28</h1>
              <h5>{{ month }} {{ year }}</h5>
            </div>
          </div>
        </div>
        <div class="card">
          <div class="card-border cumulative"></div>
          <div class="card-container">
            <i class="bx bxs-circle-three-quarter cumulative"></i>
            <div class="card-content">
              <h4>c-to-c (%)</h4>
              <h1>-80,05</h1>
              <h5>{{ month }} {{ year }}</h5>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
/* dropdown */
/* The container <div> - needed to position the dropdown content */
.dropdown {
  position: relative;
  display: inline-block;
}

/* Dropdown Content (Hidden by Default) */
.dropdown-content {
  display: none;
  position: absolute;
  margin-top: 35px;
  background-color: #f1f1f1;
  /* min-width: 160px; */
  width: fit-content;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
  z-index: 1;
  border-radius: 5px;
}

.main-indikator {
  top: 18px;
}

.flex-month {
  top: 165px;
}

.flex-year {
  top: 165px;
  margin-left: 65px;
}

/* Links inside the dropdown */
.dropdown-content a {
  color: var(--text-color);
  padding: 10px 15px 0px 15px;
  text-decoration: none;
  display: block;
}

.dropdown-content a.last-options {
  padding-bottom: 10px;
}

/* Show the dropdown menu (use JS to add this class to the .dropdown-content container when the user clicks on the dropdown button) */
.show {
  display: block;
}

/* header and card */
main {
  padding: 10px 20px 20px 50px;
}

.main-title {
  font-size: 30px;
  font-weight: 500;
  color: var(--text-color);
}

header {
  display: flex;
  margin-bottom: 20px;
}

header .group-button {
  display: flex;
  flex-direction: column;
  justify-content: left;
  align-items: left;
  color: white;
}

header .group-button button {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: transparent;
  border: none;
  width: fit-content;
  color: white;
  cursor: pointer;
}

header .group-button button i {
  font-size: 10px;
  margin-left: 5px;
  padding-top: 5px;
}

header .group-button .date {
  display: flex;
  align-items: center;
}

header .group-button .date button {
  margin-right: 20px;
}

header .group-button button.title {
  margin-bottom: 10px;
}

header .input-info {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 75%;
  margin-right: 90px;
  padding: 5px 20px 5px 20px;
  background-image: url("https://wallpaperaccess.com/full/5437185.jpg");
  border-radius: 10px;
}

header .input-info i {
  font-size: 70px;
  color: white;
}

header .card {
  display: flex;
  justify-content: space-between;
  width: 25%;
  height: 100px;
  margin: 15px;
}

header .card .card-border {
  background-color: #800020;
  border-top-left-radius: 10px;
  border-bottom-left-radius: 10px;
  width: 13px;
  height: 100%;
}

header .card .card-container {
  display: flex;
  width: 90%;
  align-items: center;
  justify-content: space-between;
  text-align: right;
}

header .card-container i {
  font-size: 70px;
  color: #800020;
}

header .card-container .card-content {
  padding-right: 10px;
}

header .card-container .card-content h4 {
  font-size: 18px;
  font-weight: 500;
  margin-bottom: 15px;
  color: var(--text-color);
}

header .card-container .card-content h1 {
  font-size: 35px;
  font-weight: bold;
  color: var(--text-color);
}

/* Chart */
.chart-container {
  margin-left: 10px;
  margin-right: 10px;
  width: 64%;
  padding: 10px;
}

.button-container {
  padding-top: 10px;
}

.button-container button {
  padding: 2px;
  width: 50px;
  background-color: rgb(128, 0, 32);
  border: none;
  color: white;
  border-radius: 20px;
  margin-left: 7px;
  cursor: pointer;
}

.button-container button:disabled {
  opacity: 50%;
}

.row-chart {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.col-card {
  width: 25%;
}

.col-card .card {
  display: flex;
  justify-content: space-between;
  height: 100px;
  margin: 0 15px 35px 15px;
}

.col-card .card .card-border {
  border-top-left-radius: 10px;
  border-bottom-left-radius: 10px;
  width: 13px;
  height: 100%;
}

.card-border.month {
  background-color: rgba(255, 74, 85, 1);
}

.card-border.year {
  background-color: rgba(255, 149, 0, 1);
}

.card-border.cumulative {
  background-color: rgba(29, 199, 234, 1);
}

.col-card .card .card-container {
  display: flex;
  width: 90%;
  align-items: center;
  justify-content: space-between;
  text-align: right;
}

.col-card .card-container i {
  font-size: 70px;
  /* color: #800020; */
}

i.month {
  color: rgba(255, 74, 85, 1);
}

i.year {
  color: rgba(255, 149, 0, 1);
}

i.cumulative {
  color: rgba(29, 199, 234, 1);
}

.col-card .card-container .card-content {
  padding-right: 10px;
}

.col-card .card-container .card-content h4 {
  font-size: 18px;
  font-weight: 500;
  margin-bottom: 15px;
  color: var(--text-color);
}

.col-card .card-container .card-content h1 {
  font-size: 35px;
  font-weight: bold;
  color: var(--text-color);
}
</style>
