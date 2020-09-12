<template>
  <div id="app">
    <Generator />
    <PastPasswords/>
  </div>
</template>

<script>
import { ref, provide, readonly } from 'vue';
import Generator from './components/Generator.vue';
import PastPasswords from './components/PastPasswords.vue';

export default {
  name: 'App',
  components: {
    Generator,
    PastPasswords,
  },
  setup() {
    const password = ref('This is state from App');
    const passwords = ref(['lfdafjlks', 'klfjdasljfdsjlka', 'fldasjlfksa']);
    let count = 1;
    const generateNewPass = () => {
      const newPass = `item #${count}`;
      count += 1;
      return newPass;
    };
    const updatePassword = () => {
      passwords.value.push(password.value);
      password.value = generateNewPass();
    };

    provide('passwords', readonly(passwords));
    provide('password', readonly(password));
    provide('updatePassword', updatePassword);
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
