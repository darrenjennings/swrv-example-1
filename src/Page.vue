<template>
  <div>Page Data: {{ data }}</div>
</template>

<script>
import { defineComponent, onUnmounted } from "@vue/composition-api";
import useSWRV from "swrv";

function fetcher(url) {
  console.log("revalidation fired " + url);
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve({ id: `${url}` });
    }, 500);
  });
}

export default defineComponent({
  props: {
    page: {
      type: Number,
      default: 0,
    },
  },
  setup(props) {
    onUnmounted(() => {
      console.log("oh noooo");
    });
    const { data } = useSWRV(() => props.page, fetcher, {
      dedupingInterval: Infinity,
    });

    return {
      data,
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
