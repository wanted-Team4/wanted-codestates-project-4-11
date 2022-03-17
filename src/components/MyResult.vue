<template>
  <div id="container">
    <div class="title">
      <p class="sub-title">M Y&nbsp;&nbsp;&nbsp;R E S U L T</p>
      <h1>나의 결과는?</h1>
    </div>
    <div class="chartList" v-for="(score, idx) in user" :key="idx">
      <div class="scoreList" :style="selectScoreColor(score)">
        <span class="score">{{ score }}/10</span>
      </div>
      <div class="left" :style="selectTypesColor(score)">
        {{ types[idx][0] }}
      </div>
      <div class="empty"></div>
      <div class="right" :style="selectTypesColor(10 - score)">
        {{ types[idx][1] }}
      </div>
      <div class="scoreList" :style="selectScoreColor(10 - score)">
        <span class="score">{{ 10 - score }}/10</span>
      </div>
    </div>
    <div class="inner">
      <div class="lineOne"></div>
      <div class="lineTwo"></div>
      <div class="lineThree"></div>
      <div class="lineFour"></div>
      <div class="lineFive"></div>
      <div id="col"></div>
      <BarChart :currentTab="currentTab" :selectedCompany="selectedCompany" />
    </div>
  </div>
</template>

<script>
import data from "../Data";
import BarChart from "./BarChart.vue";

const types = [
  ["적극성", "수동성"],
  ["자신감", "신중함"],
  ["책임감", "무심함"],
  ["개인성향", "조직성향"],
  ["수평사고", "위계사고"],
];

export default {
  name: "App",
  data() {
    return {
      user: data.user,
      types: types,
    };
  },
  methods: {
    selectScoreColor(num) {
      let color = "color:#578339";
      if (num < 5) {
        color = "color:#000";
      }
      return color;
    },
    selectTypesColor(num) {
      let color = "color:#25BB6A";
      if (num < 5) {
        color = "color:#000";
      }
      return color;
    },
  },
  components: { BarChart },
  props: {
    currentTab: Number,
    selectedCompany: String,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
#container {
  width: 360px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  margin-bottom: 2rem;
}
.title {
  text-align: center;
}
.sub-title {
  font-weight: 700;
  margin-bottom: 0.5rem;
}
h1 {
  margin-top: 0;
}
.chartList {
  display: flex;
  align-items: center;
  justify-content: space-around;
  font-size: 0.8rem;
  width: 450px;
  height: 35px;
}
.scoreList {
  text-align: center;
  width: 50px;
  font-weight: 700;
  font-size: 0.8rem;
}
.left {
  width: 45px;
}
.right {
  width: 45px;
}
.empty {
  width: 220px;
  height: 55px;
}
.inner {
  width: 165px;
  height: 180px;
  position: absolute;
  top: 110px;
  background-color: #fff;
}
.lineOne {
  width: 165px;
  height: 17px;
  border-bottom: 1px solid #d1d1d1;
  position: absolute;
}
.lineTwo {
  width: 165px;
  height: 50px;
  border-bottom: 1px solid #d1d1d1;
  position: absolute;
}
.lineThree {
  width: 165px;
  height: 83px;
  border-bottom: 1px solid #d1d1d1;
  position: absolute;
}
.lineFour {
  width: 165px;
  height: 116px;
  border-bottom: 1px solid #d1d1d1;
  position: absolute;
}
.lineFive {
  width: 165px;
  height: 149px;
  border-bottom: 1px solid #d1d1d1;
  position: absolute;
}
.rowOne {
  border: 1px solid black;
  width: 165px;
  height: 18px;
  z-index: 999;
}
#col {
  position: absolute;
  width: 83px;
  height: 180px;
  border-right: 1px solid #d1d1d1;
  margin: 0;
}
</style>