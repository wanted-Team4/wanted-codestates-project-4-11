<template>
  <BarChart
    :chartData="testData"
    :options="options"
    :style="{
      width: '165px',
      alignItems: 'center',
    }"
  />
</template>

<script>
import { Chart, registerables } from "chart.js";
import { BarChart } from "vue-chart-3";
import { computed, defineComponent, ref } from "vue";
Chart.register(...registerables);

export default defineComponent({
  name: "Home",
  components: { BarChart },
  props: {
    userScore: Number,
    companyScore: Number,
    selectCompany: String,
    currentTab: Number,
  },
  data() {
    return {
      currentUserScore: this.userScore,
      currentCompanyScore: this.companyScore,
      matchData: 6,
    };
  },
  methods: {
    test() {
      console.log(this.userScore, this.companyScore, this.currentData);
    },
  },
  setup() {
    const data = ref([0, 0]);

    const options = ref({
      responsive: true,
      plugins: {
        legend: false,
      },
      indexAxis: "y",
      scales: {
        y: {
          display: false,
          grid: {
            display: false,
          },
        },
        x: {
          display: false,
          grid: {
            display: false,
          },
          ticks: {
            display: true,
            stepSize: 2,
          },
          min: -10,
          max: 10,
        },
      },
    });
    const testData = computed(() => ({
      labels: ["적극적인", "자신있는", "책임있는", "개인주의", "수평적인"],
      datasets: [
        {
          data: [-8, -10, -10, 7, -6],
          backgroundColor: "#6e3cf9",
          barThickness: 5,
        },
        {
          // 삼성전자
          data: [-10, -9, -9, -5, 7],
          backgroundColor: "#ffd966",
          barThickness: 5,
        },
      ],
    }));
    return { testData, options };
  },

  // beforeUpdate() {
  //   if (this.currentTab === 2) {
  //     this.testData.datasets[0].data[0] = 0;
  //   } else {
  //     this.testData.datasets[0].data[0] =
  //       this.userScore > 5 ? this.userScore * -1 : this.userScore;
  //   }
  //   if (!this.selectCompany || this.currentTab === 1) {
  //     this.testData.datasets[0].data[1] = 0;
  //   } else {
  //     this.testData.datasets[0].data[1] =
  //       this.companyScore > 5 ? this.companyScore * -1 : this.companyScore;
  //   }
  // },
  // beforeMount() {
  //   this.testData.datasets[0].data[0] =
  //     this.userScore > 5 ? this.userScore * -1 : this.userScore;
  // },
});
</script>

<style>
</style>