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
    async generatePassword() {
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
@import "@/assets/scss/mixins";

.wrapper {
  overflow: hidden;
  width: 100%;
  height: 100vh;
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  &-container {
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    background: $background-color;
    border-radius: 1rem;

    @include breakpoint(xs) {
      width: 90%;
      padding: 1vh 0;
      gap: .5rem;
    }

    @include breakpoint(s) {
      width: 60%;
      padding: 3vh 0;
      gap: .5rem;
    }

    @include breakpoint(m) {
      width: 60%;
      padding: 3vh 0;
      gap: .5rem;
    }

    @include breakpoint(l) {
      width: 65%;
      padding: 3vh 0;
      gap: .8rem;
    }

    @include breakpoint(xl) {
      width: 50%;
      padding: 3vh 0;
      gap: .8rem;
    }

    @include breakpoint(xxl) {
      width: 40%;
      padding: 2vh 0;
      gap: 1rem;
    }

    @include breakpoint(xxxl) {
      width: 40%;
      padding: 2vh 0;
      gap: 2rem;
    }

    &-title {
      display: flex;
      font-weight: bold;

      @include breakpoint(xs) {
        font-size: 1.8rem;
        gap: .5rem;
      }

      @include breakpoint(s) {
        font-size: 1.6rem;
        gap: .5rem;
      }

      @include breakpoint(m) {
        font-size: 1.8rem;
        gap: .5rem;
      }

      @include breakpoint(l) {
        font-size: 2rem;
        gap: .7rem;
      }

      @include breakpoint(xl) {
        font-size: 2rem;
        gap: .7rem;
      }

      @include breakpoint(xxl) {
        font-size: 2rem;
        gap: .8rem;
      }

      @include breakpoint(xxxl) {
        font-size: 4rem;
        gap: 1.6rem;
      }

      &-highlighted {
        color: $highlight-color;
      }
    }

    &-row {
      width: 80%;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      align-items: flex-start;
      flex-wrap: wrap;

      @include breakpoint(xs) {
        gap: .5rem;
      }

      @include breakpoint(s) {
        gap: .5rem;
      }

      @include breakpoint(m) {
        gap: .8rem;
      }

      @include breakpoint(l) {
        gap: .8rem;
      }

      @include breakpoint(xl) {
        gap: .8rem;
      }

      @include breakpoint(xxl) {
        gap: 1rem;
      }

      @include breakpoint(xxxl) {
        gap: 2rem;
      }
    }
  }
}
</style>
