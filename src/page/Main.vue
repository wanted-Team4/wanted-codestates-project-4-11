<template>
  <div class="container">
    <NavBar />
    <Search :selectedCompany="selectedCompany" @changeSelect="changeSelect" />
    <PentagonChart />
    <TabPart :tabs="tabs" :currentTab="currentTab" @changeTab="changeTab" />
    <MyResult :currentTab="currentTab" />
  </div>
</template>

<script>
import PentagonChart from "../components/PentagonChart.vue";
import TabPart from "../components/TabPart.vue";
import MyResult from "../components/MyResult.vue";
import Search from "../components/Search.vue";
import NavBar from "../components/NavBar.vue";

export default {
  name: "App",
  components: {
    NavBar,
    Search,
    PentagonChart,
    TabPart,
    MyResult,
  },
  data() {
    return {
      selectedCompany: "", 
      currentTab: 0,
      tabs: [
        {
          name: "모두",
          icon: {
            src: require("../assets/tab1.png"),
            alt: "companyMe",
          },
        },
        {
          name: "본인",
          icon: {
            src: require("../assets/tab2.png"),
            alt: "Me",
          },
        },
        {
          name: "회사",
          icon: {
            src: require("../assets/tab3.png"),
            alt: "company",
          },
        },
      ],
    };
  },
  methods: {
    changeTab(i) {
      this.currentTab = i;
    },
    changeSelect(company) {
      this.selectedCompany = company;
    }
  },
};
</script>
<style>
.container {
  width: 60%;
  margin: auto;
}
</style>