<script>
import JobsListComponent from "./components/JobsListComponent.vue";
import jsonData from "./data/data.json";
export default {
  components: {
    JobsListComponent,
  },
  setup() {
    const data = jsonData;

    return { data };
  },
};
</script>
>

<template>
  <header class="header"></header>
  <main><JobsListComponent :jobs="data" /></main>
</template>

<style scoped>
.header {
  background: url("./assets/images/bg-header-mobile.svg") no-repeat;
  background-color: hsl(180, 29%, 50%);
  height: 23vh;
  width: 100%;
}
</style>
