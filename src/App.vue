<script>
import PasswordInput from "@/components/PasswordInput.vue";
import PasswordLength from "@/components/PasswordLength.vue";
import Options from "@/components/Options.vue";
import Algorithm from "@/components/Algorithm.vue";
import AlertWindow from "@/components/AlertWindow.vue";

export default {
  name: "App",
  components: {AlertWindow, Algorithm, Options, PasswordLength, PasswordInput},
}
</script>

<template>
  <div class="wrapper">
    <div class="wrapper-container">
      <password-input @passCopy=""/>
      <password-length/>
      <options/>
      <algorithm/>
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
  flex-direction: row;
  justify-content: center;
  align-items: center;

  &-container {
    width: 40%;
    margin: 0 auto;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 1em;
    background: $background-color;
    border-radius: 1em;
    padding: 5vh 0;
  }

  &-message {
    position: absolute;
    display: none;
  }
}
</style>
