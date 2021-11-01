<template>
  <div id="pastPasswords">
    <div v-for="pass in pastPasswords" class="passwordWrapper" :key="pass" @click="copy(pass)">
        <span class="password">
            {{pass}}
        </span>
    </div>
  </div>
</template>

<script>
import { inject } from 'vue';

export default {
  setup() {
    // Injected readonly State Variable
    const pastPasswords = inject('passwords');

    const copy = inject('copy');

    return {
      pastPasswords,
      copy,
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
  grid-gap:25px 25px;
  align-items: center;
  margin:50px auto 0;
  .passwordWrapper{
    color:#ffffff;
    background-color:#333333;
    height:100%;
    box-shadow: 6px 6px 0 #454545;
    transform: skewX(-15deg);
    display:flex;
    align-items:center;
    justify-content: center;
    transition:.5s;
    cursor: pointer;
    .password{
      transform: skewX(15deg);
      font-size:18px;
    }
    &:nth-of-type(2n){
      background-color: #696969;
    }
    &:hover{
      box-shadow: 8px 8px 0 #696969;
      transition: .5s;
    }
    &:active{
      box-shadow: 4px 4px 0 #333333;
      transition: .2s ease-in-out;
    }
  }
}
</style>
