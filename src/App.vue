<template>
  <div id="app">
    <FilterForm>Filters</FilterForm>
    <MyTable>Movies</MyTable>
  </div>
</template>

<script>
import MyTable from "@/components/MyTable";
import FilterForm from "./components/FilterForm";
import Vue from 'vue';
import underscore from 'vue-underscore';

Vue.use(underscore);

export default {
  name: 'app',
  components: {
    FilterForm,
    MyTable
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 50%;
  margin: auto;
}
</style>
