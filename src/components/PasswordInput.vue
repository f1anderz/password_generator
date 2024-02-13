<script>
export default {
  name: "PasswordInput",
  data() {
    return {
      password: "",
    }
  }, methods: {
    async copyPassword() {
      await navigator.clipboard.writeText(this.password);
      this.$emit('passCopy');
    }
  }
}
</script>

<template>
  <div class="password-container">
    <input class="password-container-input" v-model="this.password" type="text" placeholder="Your Password...">
    <img class="password-container-copy" src="@/assets/img/copy.svg" alt="Copy"
         @click="this.copyPassword">
  </div>
</template>

<style scoped lang="scss">
@import "@/assets/scss/variables";

.password-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 50%;
  background: #ffffff;
  border: 2px solid $highlight-color;
  border-radius: .5em;
  padding: .2em;

  &-input {
    display: block;
    width: 95%;
    padding: .1em .3em;
    font-size: 110%;
    border: none;

    &:focus {
      outline: none;
    }
  }

  &-copy {
    width: 1.6em;
    height: 1.6em;

    &:hover {
      cursor: pointer;
    }
  }
}
</style>