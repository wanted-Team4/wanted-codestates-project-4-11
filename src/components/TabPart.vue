<template>
  <ul class="tabUl">
    <li
      v-for="(tab, i) in tabs"
      v-bind:key="i"
      @click="changeCurrent(i)"
      :class="{ current: currentTab === i }"
    >
      <img :src="tab.icon.src" :alt="tab.icon.alt" />
      <span>{{ tab.name }}</span>
    </li>
  </ul>
</template>

<script>
export default {
  props: ["tabs", "currentTab"],
  data() {
    return {};
  },
  methods: {
    changeCurrent(i) {
      this.$emit("changeTab", i);
    },
  },
};
</script>
e
<style>
.tabUl {
  width: 70%;
  height: 45px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 4px;
  background-color: #f2f2f2;
  padding: 0px;
  margin: auto;
}
.tabUl li {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 33.3%;
  height: 43px;
  background-color: #f2f2f2;
  font-size: 12px;
  border: 1px solid #f2f2f2;
}
.tabUl li.current {
  background: #ffffff;
  width: 33.3%;
  height: 43px;
  border-radius: 4px;
  border: 1px solid #f2f2f2;
  padding: 5px;
}
.tabUl li span {
  position: relative;
  top: 0.4px;
}
.tabUl img {
  position: relative;
  width: 13px;
  height: 13px;
  margin-right: 15px;
}
</style>
