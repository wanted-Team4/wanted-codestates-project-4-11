<template>
  <RadarChart :chartData="resultData" />
</template>

<script>
import { defineComponent } from "vue";
import { RadarChart } from "vue-chart-3";
import { Chart, registerables } from "chart.js";
import Data from "../Data";

Chart.register(...registerables);

export default defineComponent({
  name: "APP",
  components: { RadarChart },
  setup() {
    const setData = {
      labels: ["적극적인", "자신있는", "책임감있는", "개인주의", "수평적인"],
      datasets: [
        {
          label: "본인",
          data: Data.user,
          backgroundColor: "rgba(110, 60, 249, 0.32)",
          borderColor: "#6E3CF9",
        },
        {
          label: "회사",
          // data: Data.company,
          background: "rgba(255, 193, 74, 0.32)",
          borderColor: "#FFD335",
        },
        {
          label: "외곽선",
          data: [10, 10, 10, 10, 10],
          backgroundColor: "rgba(248, 248, 248, 0.32)",
          borderColor: " #B2B2B2",
          pointRadius: 13,
          borderWidth: 1,
          pointBackgroundColor: [
            "rgba(235, 133, 108, 0.7)",
            "rgba(108, 135, 245, 0.5)",
            "rgba(64, 171, 199, 0.5)",
            "rgba(229, 115, 160, 0.5)",
            "rgba(101, 184, 81, 0.5)",
          ],
          pointBorderColor: [
            "rgba(235, 133, 108, 0.7)",
            "rgba(108, 135, 245, 0.5)",
            "rgba(64, 171, 199, 0.5)",
            "rgba(229, 115, 160, 0.5)",
            "rgba(101, 184, 81, 0.5)",
          ],
          pointBorderWidth: 1,
          pointHoverRadius: 1,
        },
      ],
    };
    return { setData };
  },
  beforeMount() {
    const { scale, plugins } = Chart.defaults;
    scale.ticks = {
      stepSize: 2,
      display: false,
    };
    scale.grid.borderDash = [5];
    plugins.legend.display = false;
    plugins.tooltip.enabled = false;
  },
  data() {
    return { resultData: this.setData };
  },
  props: {
    company: String,
    currentTab: Number,
  },
  methods: {
    show(idx) {
      this.resultData.datasets[idx].fill = true;
      this.resultData.datasets[idx].showLine = true;
    },
    hide(idx) {
      this.resultData.datasets[idx].fill = false;
      this.resultData.datasets[idx].showLine = false;
    },
  },
  beforeUpdate() {
    const tabConvert = {
      tab: {
        //모두
        0: (searchCompany) => {
          this.resultData.datasets[0].data = [...Data["user"]];
          this.resultData.datasets[1].data = [...Data[searchCompany]];
          this.show(0);
          this.show(1);
        },
        //유저
        1: () => {
          this.resultData.datasets[0].data = [...Data["user"]];
          this.show(0);
          this.hide(1);
        },
        //회사
        2: (searchCompany) => {
          this.resultData.datasets[1].data = [...Data[searchCompany]];
          this.hide(0);
          this.show(1);
        },
      },
      convert(tabNum, searchCompany) {
        searchCompany ? this.tab[tabNum] : this.tab[1]();
      },
    };
    try {
      tabConvert.convert(this.currentTab, this.company);
    } catch (e) {
      console.log(e);
    }
  },
});
</script>
