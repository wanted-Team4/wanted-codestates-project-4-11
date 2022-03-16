<template>
  <div>
    <h1>Hello! last project!!</h1>
    <TabPart :tabs="tabs" :currentTab="currentTab" @changeTab="changeTab" />
  </div>
</template>

<script>
import TabPart from "../components/TabPart.vue";
export default {
  name: "App",
  components: {
    TabPart,
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
