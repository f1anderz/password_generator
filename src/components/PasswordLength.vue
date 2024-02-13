<script>
export default {
  name: "PasswordLength",
  data() {
    return {
      lengthValue: 12
    }
  },
  watch: {
    lengthValue(newValue) {
      this.$emit('updated', newValue)
    }
  }
}
</script>

<template>
  <div class="password-length">
    <div class="password-length-label">Length:</div>
    <div class="password-length-container">
      <input class="password-length-container-input" type="number" v-model="this.lengthValue">
      <div class="password-length-container-arrows">
        <img class="password-length-container-arrows-up" src="../assets/img/arrow.svg" alt="Up"
             @click="this.lengthValue += 1">
        <img class="password-length-container-arrows-down" src="../assets/img/arrow.svg" alt="Down"
             @click="this.lengthValue -= 1">
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import "@/assets/scss/variables";

.password-length {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: .4em;
  width: 25%;

  &-container {
    display: flex;
    flex-direction: row;
    gap: .3em;
    padding: 0 .3em;
    background: #ffffff;
    border: 2px solid $highlight-color;
    border-radius: .3em;

    &-input {
      display: block;
      text-align: center;
      width: 100%;
      border: none;
      -moz-appearance: textfield;
      background: #ffffff;

      &:focus {
        outline: none;
      }

      &::-webkit-inner-spin-button, &::-webkit-outer-spin-button {
        -webkit-appearance: none;
        margin: 0;
      }
    }

    &-arrows {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;

      &-up {
        transform: rotate(180deg);
      }

      &-up, &-down {
        display: block;
        width: .9em;
        height: .9em;

        &:hover {
          cursor: pointer;
        }
      }
    }
  }
}
</style>