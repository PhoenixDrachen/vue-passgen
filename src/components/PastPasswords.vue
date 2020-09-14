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
    display:grid;
    width:90%;
    grid-template-columns: repeat(3, 1fr);
    grid-auto-rows: 80px;
    // align-items: center;
    margin:0 auto;
  }
</style>
