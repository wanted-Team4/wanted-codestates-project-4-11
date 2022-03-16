<template>
  <div>
    <MyResult />
    <TabPart :tabs="tabs" :currentTab="currentTab" @changeTab="changeTab" />
  </div>
</template>

<script>
import TabPart from "../components/TabPart.vue";
import MyResult from "../components/MyResult.vue";
export default {
  name: "App",
  components: {
    TabPart,
    MyResult
  },
  data() {
    return {
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
  },
};
</script>

<style></style>
