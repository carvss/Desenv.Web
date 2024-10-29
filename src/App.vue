<template>
  <div id="app">
    <h1>Gerenciador de Séries</h1>
    <Series />
  </div>
</template>

<script>
import Series from './components/Series.vue';

export default {
  name: 'App',
  components: {
    Series
  }
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  margin-top: 20px;
}
h1 {
  color: #333;
}
</style>
