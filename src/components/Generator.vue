<template>
  <div id="generator">
    <div id="Output">
      <div id ="params">
        <label><strong>Password Length:</strong></label>
        <input type="text" v-model="passLength" /><br/>
        <label><strong>Use Uppercase:</strong></label>
        <input type="checkbox" v-model="useUpper" /><br/>
        <label><strong>Use Numbers:</strong></label>
        <input type="checkbox" v-model="useNum" /><br/>
        <label><strong>Use Symbols:</strong></label>
        <input type="checkbox" v-model="useSym" />
      </div>
      <h1>{{currentPassword}}</h1>
      <button @click="generate">click to update state</button>
    </div>

  </div>
</template>

<script>
import { inject, ref } from 'vue';

export default {
  setup() {
    // Injected State Variables -- readonly
    const currentPassword = inject('password');

    // Injected Method to update readonly state variable
    const updateCurrentPass = inject('updatePassword');

    // Local State Variables
    const useUpper = ref(false);
    const useSym = ref(false);
    const useNum = ref(false);
    const passLength = ref(15);

    // Generates a new password and passes it to the updateCurrentPass method
    const generate = () => {
      let generatedPass = '';
      console.log(useUpper.value);
      for (let i = 0; i < passLength.value; i += 1) {
        const rand = Math.floor(Math.random() * 6);
        if (useUpper.value && rand === 0) {
          generatedPass += 'A';
        } else if (useNum.value && rand === 1) {
          generatedPass += '1';
        } else if (useSym.value && rand === 2) {
          generatedPass += '!';
        } else {
          generatedPass += 'a';
        }
      }
      updateCurrentPass(generatedPass);
    };

    return {
      currentPassword,
      updateCurrentPass,
      generate,
      useUpper,
      useSym,
      useNum,
      passLength,
    };
  },
};
</script>

<style lang="scss" scoped>

</style>
