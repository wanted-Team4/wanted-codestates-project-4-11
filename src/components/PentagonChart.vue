<template>
  <RadarChart :chartData="data" :options="options" />
</template>

<script>
import { defineComponent } from "vue";
import { RadarChart } from "vue-chart-3";
import { Chart, registerables } from "chart.js";

Chart.register(...registerables);

export default defineComponent({
  name: "APP",
  components: { RadarChart },
  setup() {
    const data = {
      labels: ["적극적인", "자신있는", "책임감있는", "개인주의", "수평적인"],
      datasets: [
        {
          label: "본인",
          data: [8, 10, 10, 3, 6],
          backgroundColor: "rgba(110, 60, 249, 0.32)",
          borderColor: "#6E3CF9",
        },
        {
          label: "회사",
          data: [8, 10, 20, 3, 6],
          background: "rgba(255, 193, 74, 0.32)",
          borderColor: "#FFD335",
        },
      ],
    };
    const options = {};
    return { data, options };
  },
  methods: {
    show(idx) {
      this.matchData.datasets[idx].fill = true;
      this.matchData.datasets[idx].showLine = true;
    },
    hide(idx) {
      this.matchData.datasets[idx].fill = false;
      this.matchData.datasets[idx].showLine = false;
    },
  },
  beforeMount() {
    const { scale } = Chart.defaults;
    // plugins.legend.display = false;
    // plugins.tooltip.enabled = false;
    scale.ticks = {
      count: 5,
      stepSize: 2,
      display: false,
    };
    scale.grid.borderDash = [5];
  },
});
</script>
