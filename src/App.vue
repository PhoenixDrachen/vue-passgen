<template>
  <div id="app">
    <Generator />
    <PastPasswords/>
    <input type="text" id="clipboardProxy" v-model="passToCopy" />
    <transition name="slide-fade">
      <div class="transitionWrapper" v-if="alertActive">
        <div id="copyAlertWrapper" :class="[alertType]">
          <span id="copyAlert">{{copyAlert}}</span>
        </div>
      </div>

    </transition>
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
    const passToCopy = ref('');
    const alertActive = ref(false);
    const copyAlert = ref('');
    const alertType = ref('');

    let t;
    const copy = async (textToCopy) => {
      clearTimeout(t);
      if (navigator.clipboard) {
        try {
          await navigator.clipboard.writeText(textToCopy);
          copyAlert.value = 'Copied to Clipboard';
          alertActive.value = true;
          alertType.value = 'success';
          t = setTimeout(() => {
            copyAlert.value = '';
            alertActive.value = false;
          }, 2000);
        } catch (e) {
          copyAlert.value = 'Failed to Copy to Clipboard';
          alertActive.value = true;
          alertType.value = 'failed';
          t = setTimeout(() => {
            copyAlert.value = '';
            alertActive.value = false;
          }, 2000);
        }
      } else {
        passToCopy.value = textToCopy;
        setTimeout(() => {
          document.querySelector('#clipboardProxy').select();
          document.execCommand('copy');
          copyAlert.value = 'Copied to Clipboard';
          alertActive.value = true;
          alertType.value = 'success';
          t = setTimeout(() => {
            copyAlert.value = '';
            alertActive.value = false;
          }, 2000);
        }, 500);
      }
    };

    const updatePassword = (newPass) => {
      if (password.value !== '') {
        passwords.value = [password.value, ...passwords.value];
      }
      password.value = newPass;
    };

    provide('passwords', readonly(passwords));
    provide('password', readonly(password));
    provide('copy', copy);
    provide('updatePassword', updatePassword);

    return {
      passToCopy,
      alertActive,
      copyAlert,
      alertType,
    };
  },
};
</script>

<style lang="scss">
@import url('./css/reset.scss');

body{
  background-color: #ffffff;

}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #333333;
  margin-top: 30px;
  height:100vh;
}

#clipboardProxy{
  position:absolute;
  top:-99999px;
  left:-99999px
}
.transitionWrapper{
  position:absolute;
  display:flex;
  align-items: center;
  justify-content: center;
  font-size:18px;
  bottom:50px;
  left: calc(50% - 250px);
}
#copyAlertWrapper{
  display:flex;
  align-items: center;
  justify-content: center;
  width:500px;
  height:50px;
  color:white;
  box-shadow: 6px 6px 0 #454545;
  transform:skewX(-15deg);
  &.success{
    background-color:#48e98a;
  }
  &.failed{
    background-color:#fe4551;
  }
  #copyAlert{
    transform:skewX(15deg);
  }
}
.slide-fade-enter-active {
  transition: all 0.5s ease-in;
}

.slide-fade-leave-active {
  transition: all .5s ease-out;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateY(20px);
  opacity: 0;
}

</style>
