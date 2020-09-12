<template>
  <div id="pastPasswords">
    <span v-for="pass in pastPasswords" :key="pass">{{pass}}</span>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const pastPasswords = ref(['lfdafjlks', 'klfjdasljfdsjlka', 'fldasjlfksa']);
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
