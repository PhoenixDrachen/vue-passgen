<template>
  <div id="pastPasswords">
    <span v-for="pass in pastPasswords" :key="pass">{{pass}}</span>
  </div>
</template>

<script>
import { inject } from 'vue';

export default {
  setup() {
    // Injected readonly State Variable
    const pastPasswords = inject('passwords');
    return {
      pastPasswords,
    };
  },
};
</script>

<style lang="scss" scoped>
  #pastPasswords{
    // display:grid;
    width:90%;
    display:flex;
    justify-content: space-between;
    margin:0 auto;
  }
</style>
