<template>
  <div id="app">
    <Page :page="page" />
    <k-button @click="previous">< previos</k-button>
    <k-button @click="next">next ></k-button>
  </div>
</template>

<script>
import { defineComponent, ref } from "@vue/composition-api";
import KButton from "@kongponents/kbutton";
import Page from "./Page";

export default defineComponent({
  components: { Page, KButton },
  setup() {
    const page = ref(1);

    function next() {
      page.value += 1;
    }

    function previous() {
      page.value -= 1;
    }

    return {
      page,
      previous,
      next,
    };
  },
});
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
