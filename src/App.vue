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
}
</script>

<template>
  <div class="wrapper">
    <div class="wrapper-container">
      <div class="wrapper-container-title">
        Password<span class="wrapper-container-title-highlighted">Generator</span>
      </div>
      <div class="wrapper-container-row">
        <password-input @passCopy=""/>
        <password-length/>
      </div>
      <div class="wrapper-container-row">
        <options/>
        <algorithm/>
      </div>
      <generate-button/>
    </div>
    <alert-window class="wrapper-message"/>
  </div>
</template>

<style lang="scss">
@use '@/assets/scss/global';
@import "@/assets/scss/variables";

.wrapper {
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

  &-message {
    position: absolute;
    display: none;
  }
}
</style>
