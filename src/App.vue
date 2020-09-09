<template>
  <div id="app">
    <Generator />
    <PastPasswords/>
  </div>
</template>

<script>
import Generator from './components/Generator.vue';
import PastPasswords from './components/PastPasswords.vue';

export default {
  name: 'App',
  components: {
    Generator,
    PastPasswords,
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
