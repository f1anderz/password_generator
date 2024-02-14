<script>
import PasswordInput from "@/components/PasswordInput.vue";
import PasswordLength from "@/components/PasswordLength.vue";
import Options from "@/components/Options.vue";
import Algorithm from "@/components/Algorithm.vue";
import AlertWindow from "@/components/AlertWindow.vue";
import GenerateButton from "@/components/GenerateButton.vue";

export default {
  name: "App",
  components: {GenerateButton, AlertWindow, Algorithm, Options, PasswordLength, PasswordInput},
  data() {
    return {
      messageHidden: true,
      passwordLength: 12,
      generator: false,
      options: {
        "Capital": true,
        "Numbers": true,
        "Special": false
      },
      algorithm: "Normal"
    }
  },
  methods: {
    showAlert() {
      this.messageHidden = false;
      setTimeout(() => {
        this.messageHidden = true;
      }, 750);
    },
    async generatePassword(){
      this.generator = true;
      await this.showAlert();
      this.generator = false;
    },
    setPasswordLength(value) {
      this.passwordLength = value;
    },
    setOptions(value) {
      switch (value) {
        case "Use capital letters":
          this.options["Capital"] = !this.options["Capital"];
          break;
        case "Use numbers":
          this.options["Numbers"] = !this.options["Numbers"];
          break;
        case "Use special symbols":
          this.options["Special"] = !this.options["Special"];
          break;
      }
    },
    setAlgorithm(value) {
      this.algorithm = value;
    }
  }
}
</script>

<template>
  <div class="wrapper">
    <div class="wrapper-container">
      <div class="wrapper-container-title">
        Password<span class="wrapper-container-title-highlighted">Generator</span>
      </div>
      <div class="wrapper-container-row">
        <password-input :generator="this.generator" :password-length="this.passwordLength" :options="this.options"
                        :algorithm="this.algorithm" @copyPass="this.showAlert"/>
        <password-length @updated="this.setPasswordLength"/>
      </div>
      <div class="wrapper-container-row">
        <options @selected="this.setOptions"/>
        <algorithm @selected="this.setAlgorithm"/>
      </div>
      <generate-button @generated="this.generatePassword"/>
    </div>
    <alert-window :is-hidden="this.messageHidden"/>
  </div>
</template>

<style lang="scss">
@use '@/assets/scss/global';
@import "@/assets/scss/variables";

.wrapper {
  overflow: hidden;
  width: 100%;
  height: 100vh;
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 1rem;

  &-container {
    width: 40%;
    margin: 0 auto;
    padding: 2vh 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 1em;
    background: $background-color;
    border-radius: 1em;

    &-title {
      display: flex;
      font-size: 2rem;
      gap: .8rem;
      font-weight: bold;

      &-highlighted {
        color: $highlight-color;
      }
    }

    &-row {
      width: 80%;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
    }
  }
}
</style>
