<template>
  <div id="generator">
    <div id ="params">
      <div class="lengthWrapper">
          <input v-model="passLength" @keyup="validateOnKeyup"
          @blur="validateOnBlur" :class="{ valid : validNumber }" />
          <h2>Length?</h2>
      </div>
      <div v-if="error" class="errorsWrapper" >
        <div class="errors">
          {{error}}
        </div>
      </div>
      <div class="checkWrapper" >
          <h2 class="checkLabel">
              Uppercase?
          </h2>
          <div>
              <input type="checkbox" id="capsToggle" v-model="useUpper" />
              <label htmlFor="capsToggle" class="toggleWrapper">
                  <div class="toggle"></div>
              </label>
          </div>
      </div>
      <div class="checkWrapper" >
          <h2 class="checkLabel">
              Numbers?
          </h2>
          <div>
              <input type="checkbox" id="numToggle" v-model="useNum" />
              <label htmlFor="numToggle" class="toggleWrapper">
                  <div class="toggle"></div>
              </label>
          </div>
      </div>
      <div class="checkWrapper" >
          <h2 class="checkLabel">
              Symbols?
          </h2>
          <div>
              <input type="checkbox" id="symToggle" v-model="useSym" />
              <label htmlFor="symToggle" class="toggleWrapper">
                  <div class="toggle"></div>
              </label>
          </div>
      </div>
    </div>
    <div id="output">
      <div id="currentPassWrapper">
        <h1 @click="copy(currentPassword)">{{currentPassword}}</h1>
      </div>
      <button @click="generate" class="cta" :disabled="!validNumber" ><span>Generate</span>
    <span>
      <svg width="33px" height="21px" viewBox="0 0 33 21" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
        <g id="arrow" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
          <path class="one"
          d="M40.1543933,3.89485454 L43.9763149,0.139296592 C44.1708311,-0.0518420739 44.4826329,
          -0.0518571125 44.6771675,0.139262789 L65.6916134,20.7848311 C66.0855801,
          21.1718824 66.0911863,21.8050225 65.704135,22.1989893 C65.7000188,
          22.2031791 65.6958657,22.2073326 65.6916762,22.2114492 L44.677098,
          42.8607841 C44.4825957,43.0519059 44.1708242,43.0519358 43.9762853,
          42.8608513 L40.1545186,39.1069479 C39.9575152,38.9134427 39.9546793,
          38.5968729 40.1481845,38.3998695 C40.1502893,38.3977268 40.1524132,
          38.395603 40.1545562,38.3934985 L56.9937789,21.8567812 C57.1908028,
          21.6632968 57.193672,21.3467273 57.0001876,21.1497035 C56.9980647,
          21.1475418 56.9959223,21.1453995 56.9937605,21.1432767 L40.1545208,
          4.60825197 C39.9574869,4.41477773 39.9546013,4.09820839 40.1480756,
          3.90117456 C40.1501626,3.89904911 40.1522686,3.89694235 40.1543933,
          3.89485454 Z" fill="#FFFFFF"></path>
          <path class="two" d="M20.1543933,3.89485454 L23.9763149,
          0.139296592 C24.1708311,
          -0.0518420739 24.4826329,-0.0518571125 24.6771675,
          0.139262789 L45.6916134,20.7848311 C46.0855801,
          21.1718824 46.0911863,21.8050225 45.704135,22.1989893 C45.7000188,22.2031791 45.6958657,
          22.2073326 45.6916762,22.2114492 L24.677098,42.8607841 C24.4825957,
          43.0519059 24.1708242,43.0519358 23.9762853,42.8608513 L20.1545186,39.1069479 C19.9575152,
          38.9134427 19.9546793,38.5968729 20.1481845,38.3998695 C20.1502893,38.3977268 20.1524132,
          38.395603 20.1545562,38.3934985 L36.9937789,21.8567812 C37.1908028,21.6632968 37.193672,
          21.3467273 37.0001876,21.1497035 C36.9980647,21.1475418 36.9959223,21.1453995 36.9937605,
          21.1432767 L20.1545208,4.60825197 C19.9574869,4.41477773 19.9546013,4.09820839 20.1480756,
          3.90117456 C20.1501626,3.89904911 20.1522686,
          3.89694235 20.1543933,3.89485454 Z" fill="#FFFFFF"></path>
          <path class="three" d="M0.154393339,3.89485454 L3.97631488,0.139296592 C4.17083111,
          -0.0518420739 4.48263286,-0.0518571125 4.67716753,0.139262789 L25.6916134,
          20.7848311 C26.0855801,21.1718824 26.0911863,21.8050225 25.704135,
          22.1989893 C25.7000188,22.2031791 25.6958657,22.2073326 25.6916762,
          22.2114492 L4.67709797,42.8607841 C4.48259567,43.0519059 4.17082418,
          43.0519358 3.97628526,42.8608513 L0.154518591,39.1069479 C-0.0424848215,
          38.9134427 -0.0453206733,38.5968729 0.148184538,38.3998695 C0.150289256,
          38.3977268 0.152413239,38.395603 0.154556228,38.3934985 L16.9937789,
          21.8567812 C17.1908028,21.6632968 17.193672,21.3467273 17.0001876,
          21.1497035 C16.9980647,21.1475418 16.9959223,21.1453995 16.9937605,
          21.1432767 L0.15452076,4.60825197 C-0.0425130651,4.41477773 -0.0453986756,
          4.09820839 0.148075568,3.90117456 C0.150162624,3.89904911 0.152268631,
          3.89694235 0.154393339,3.89485454 Z" fill="#FFFFFF"></path>
        </g>
      </svg>
    </span> </button>
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

    const copy = inject('copy');

    // Local State Variables
    const useUpper = ref(false);
    const useSym = ref(false);
    const useNum = ref(false);
    const passLength = ref('');
    const validNumber = ref(false);
    const error = ref('');

    // Object to pull random letters/symbols/numbers from
    const passObject = {
      letters: 'abcdefghijklmnopqrstuvwxyz',
      numbers: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
      symbols: ['!', '@', '#', '$', '_', '+', '?'],
    };

    // Generates a new password and passes it to the updateCurrentPass method
    const generate = () => {
      let generatedPass = '';
      let pick = '';
      for (let i = 0; i < passLength.value; i += 1) {
        const rand = Math.floor(Math.random() * 6);
        if (useUpper.value && rand === 0) {
          pick = Math.floor(Math.random() * 26);
          generatedPass += passObject.letters[pick].toUpperCase();
        } else if (useNum.value && rand === 1) {
          pick = Math.floor(Math.random() * 10);
          generatedPass += passObject.numbers[pick].toString();
        } else if (useSym.value && rand === 2) {
          pick = Math.floor(Math.random() * 7);
          generatedPass += passObject.symbols[pick];
        } else {
          pick = Math.floor(Math.random() * 26);
          generatedPass += passObject.letters[pick];
        }
      }
      updateCurrentPass(generatedPass);
    };

    const validateOnKeyup = (e) => {
      const numToValidate = Number(e.target.value);
      if (Number.isNaN(numToValidate)) {
        validNumber.value = false;
        error.value = 'Length must be a number.';
      } else if (numToValidate === 0) {
        validNumber.value = false;
        error.value = 'Length must not be empty.';
      } else if (numToValidate >= 12 && numToValidate <= 25) {
        validNumber.value = true;
        error.value = '';
      } else {
        validNumber.value = false;
        error.value = 'Length must be between 12 and 25.';
      }
    };

    const validateOnBlur = (e) => {
      const numToValidate = Number(e.target.value);
      if (!validNumber.value) {
        if (numToValidate === 0) {
          error.value = 'Length must not be empty.';
        }
        passLength.value = '';
      }
    };

    return {
      currentPassword,
      updateCurrentPass,
      generate,
      useUpper,
      useSym,
      useNum,
      passLength,
      validNumber,
      error,
      validateOnKeyup,
      validateOnBlur,
      copy,
    };
  },
};
</script>

<style lang="scss" scoped>
#output{
  display:flex;
  align-items: center;
  width:700px;
  justify-content: space-between;
  margin:0 auto;
  button{
    border:none;
  }
  #currentPassWrapper{
    transform: skewX(-15deg);
    background-color:#fff;
    border: 2px solid #333;
    box-shadow: 6px 6px 0 #454545;
    flex-basis:60%;
    padding:10px;
    min-height:50px;
    transition: .5s ease-in-out;
    cursor:pointer;
    &:hover{
      transition: .5s ease-in-out;
      box-shadow: 8px 8px 0 #696969;
    }
    &:active{
      transition: .3s ease-in-out;
      box-shadow: 4px 4px 0 #333;
    }
    h1{
      font-size:28px;
      font-weight:bold;
      transform: skewX(15deg);
    }
  }
}
#params{
  width:700px;
  margin:0 auto;
  .lengthWrapper{
    margin-bottom:25px;
    position: relative;
    box-shadow: 6px 6px 0 #454545;
    transform: skewX(-15deg);
    border: 2px solid #333;
    input{
      width:100%;
      height:50px;
      font-size:18px;
      font-weight:800;
      padding: 15px 0;
      color: #333;
      border: none;
      outline: none;
      background: transparent;
      transform: skewX(15deg);
      padding-left:10px;
      -moz-appearance: textfield;
      &::-webkit-outer-spin-button{
        -webkit-appearance: none;
        margin: 0;
      }
      &::-webkit-inner-spin-button{
        -webkit-appearance: none;
        margin: 0;
      }
      &:focus ~ h2{
        top: -30px;
        left: 0;
        color: #555555;
        font-size: 16px;
      }
      &.valid ~ h2{
        top: -30px;
        left: 0;
        color: #555555;
        font-size: 16px;
      }
    }
    h2{
      // padding-left:25px;
      text-align:left;
      font-size:22px;
      font-weight:800;
      position: absolute;
      top:5px;
      left: 5px;
      padding: 10px 0;
      color: #333;
      pointer-events: none;
      transition: .5s;
      transform: skewX(15deg)
    }
  }
  .errorsWrapper{
    color:#ffffff;
    background-color:#ff0000;
    box-shadow: 6px 6px 0 #660000;
    height:50px;
    margin-bottom: 15px;
    display:flex;
    align-items:center;
    justify-content: center;
    font-size:18px;
    font-weight:bold;
    transform: skewX(-15deg);
    .errors{
      transform: skewX(15deg);
    }
  }
}
// Begin Toggle Styles
.checkWrapper{
  display:flex;
  grid-gap:30px;
  grid-template-columns: 1fr 1fr;
  align-items:center;
  justify-content: space-between;
  padding-bottom:10px;
  margin-bottom:25px;
  h2{
    // padding-left:25px;
    text-align:left;
    font-size:22px;
    font-weight:800;
  }
}

input[type="checkbox"] {
  display: none;
}

.toggleWrapper {
  z-index: 3;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all .2s;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-color: #fe4551;
  box-shadow: 5px 5px 0 #454545;
  &:active {
    box-shadow: 3px 3px 0 #333333;
    .toggle {
      height: 7px;
      width: 7px;
    }
  }

  .toggle {
    transition: all 0.2s ease-in-out;
    height: 20px;
    width: 20px;
    background-color: transparent;
    border: 5px solid #fff;
    border-radius: 50%;
    cursor: pointer;

    // animation: red .7s linear forwards;
  }
}

input[type="checkbox"]:checked {
  & ~ .background {
    background-color: #f9faf7;
  }
  & + .toggleWrapper {
    background-color: #48e98a;
    // box-shadow: 5px 5px 10px 0 rgba(#333333, 0.3);

    // &:active {
    //   box-shadow: 5px 5px 5px 0 rgba(#333333, 0.5);
    // }

    .toggle {
      width: 0;
      background-color: #fff;
      border-color: transparent;
      border-radius: 30px;
      // animation: green .7s linear forwards !important;
    }
  }
}

// End Toggle Styles

// Start Button Styles
.cta {
    display: flex;
    padding: 10px 25px;
    text-decoration: none;
    font-family: 'Poppins', sans-serif;
    font-size: 20px;
    color: white;
    background: #333333;
    transition: 1s;
    box-shadow: 6px 6px 0 #454545;
    transform: skewX(-15deg);
    cursor:pointer;
    &:disabled{
      pointer-events:none;
    }
    &:focus {
      outline: none;
    }
    &:hover{
      box-shadow: 8px 8px 0 #696969;
      transition: .5s
    }
    &:active{
      box-shadow: 4px 4px 0 #333333;
      transition: .3s ease-in-out;
    }
    span {
      text-transform:uppercase;
      transform: skewX(15deg)
    }
    span:nth-child(2) {
      width: 20px;
      margin-left: 30px;
      position: relative;
      top: 12%;
    }
    span:nth-child(2) {
      transition: 0.5s;
      margin-right: 0px;
    }
    &:hover  span:nth-child(2) {
      transition: 0.5s;
      margin-right: 10px;
    }
    path.one {
      transition: 0.4s;
      transform: translateX(-60%) scale(.5);
    }
    path.two {
      transition: 0.5s;
      transform: translateX(-30%) scale(.5);
    }
    path.three{
      transform: scale(.5);
    }
    &:hover path.three {
      animation: color_anim 1s infinite 0.2s;
    }
    &:hover path.one {
      transform: translateX(0%) scale(.5);
      animation: color_anim 1s infinite 0.6s;
    }
    &:hover path.two {
      transform: translateX(0%) scale(.5);
      animation: color_anim 1s infinite 0.4s;
    }
}

/* SVG animations */

@keyframes color_anim {
    0% {
        fill: white;
    }
    50% {
        fill: #FBC638;
    }
    100% {
        fill: white;
    }
}
// End Button Styles
</style>
