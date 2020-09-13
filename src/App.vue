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
    const password = ref('');
    const passwords = ref([]);

    const updatePassword = (newPass) => {
      if (password.value !== '') {
        passwords.value.push(password.value);
      }
      password.value = newPass;
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
