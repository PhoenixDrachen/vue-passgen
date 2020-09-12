<template>
  <div id="generator">
<p>{{currentPassword}}</p>
<button @click="updateCurrentPass">click to update state</button>
  </div>
</template>

<script>
import { inject } from 'vue';

export default {
  setup() {
    const currentPassword = inject('password');
    const updateCurrentPass = inject('updatePassword');
    return {
      currentPassword,
      updateCurrentPass,
    };
  },
};
</script>

<style lang="scss" scoped>

</style>
