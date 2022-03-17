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

const companyScore = {
  삼성전자: [-10, -9, -9, -5, 7],
  카카오: [-6, -7, -7, -8, 9],
  LG: [-7, -7, -7, -7, -7],
};

export default defineComponent({
  name: "App",
  components: { BarChart },
  props: {
    selectCompany: String,
    currentTab: Number,
  },
  data() {
    return {
      companyScore: companyScore,
    };
  },
  setup() {
    const data = ref([[-8, -10, -10, 7, -6], []]);
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
          data: data.value[0],
          backgroundColor: "#6e3cf9",
          barThickness: 5,
        },
        {
          data: data.value[1],
          backgroundColor: "#ffd966",
          barThickness: 5,
        },
      ],
    }));

    function checkTabOne() {
      data.value[1] = [0];
    }
    function checkTabTwo() {
      data.value[0] = [0];
      if (this.selectCompany === "삼성전자") {
        data.value[1] = this.companyScore.삼성전자;
      } else if (this.selectCompany === "카카오") {
        data.value[1] = this.companyScore.카카오;
      } else {
        data.value[1] = this.companyScore.LG;
      }
    }
    function checkTabThree() {
      data.value[0] = [-8, -10, -10, 7, -6];
      if (this.selectCompany === "삼성전자") {
        data.value[1] = this.companyScore.삼성전자;
      } else if (this.selectCompany === "카카오") {
        data.value[1] = this.companyScore.카카오;
      } else {
        data.value[1] = this.companyScore.LG;
      }
    }
    return { testData, options, checkTabOne, checkTabTwo, checkTabThree };
  },

  beforeUpdate() {
    if (this.currentTab === 1) {
      this.checkTabOne();
    } else if (this.currentTab === 2) {
      this.checkTabTwo();
    } else {
      this.checkTabThree();
    }
  },
});
</script>

<style></style>
