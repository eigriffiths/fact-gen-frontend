<template>
 <div>
  <FactsHome></FactsHome>
 </div>
</template>

<script>
import FactsHome from './components/FactsHome.vue';
export default {
  name: 'App',
  components: {
    FactsHome
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
