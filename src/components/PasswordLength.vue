<script>
export default {
  name: "PasswordLength",
  data() {
    return {
      lengthValue: 12,
      upShadow: false,
      downShadow: false
    }
  },
  methods: {
    resetShadows() {
      this.upShadow = false;
      this.downShadow = false;
    },
    increaseLength() {
      this.resetShadows();
      if (this.lengthValue < 32) {
        this.lengthValue++;
      }
      this.upShadow = this.lengthValue === 32;
    },
    decreaseLength() {
      this.resetShadows();
      if (this.lengthValue > 4) {
        this.lengthValue--;
      }
      this.downShadow = this.lengthValue === 4;
    },
    validateInput() {
      this.resetShadows();
      if (this.lengthValue < 4) {
        this.lengthValue = 4;
        this.downShadow = true;
      } else if (this.lengthValue > 32) {
        this.lengthValue = 32;
        this.upShadow = true;
      }
    }
  },
  watch: {
    lengthValue(newLengthValue) {
      this.$emit('updated', newLengthValue);
    }
  }
}
</script>

<template>
  <div class="password-length">
    <div class="password-length-label">Length:</div>
    <div class="password-length-container">
      <input class="password-length-container-input" type="number" v-model="this.lengthValue"
             @blur="this.validateInput">
      <div class="password-length-container-arrows">
        <img class="password-length-container-arrows-up" src="../assets/img/arrow.svg" alt="Up"
             @click="this.increaseLength" :class="{shadow: upShadow}">
        <img class="password-length-container-arrows-down" src="../assets/img/arrow.svg" alt="Down"
             @click="this.decreaseLength" :class="{shadow: downShadow}">
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import "@/assets/scss/variables";
@import "@/assets/scss/mixins";

.password-length {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: .4em;

  @include breakpoint(xs) {
    width: 50%;
  }

  @include breakpoint(s) {
    width: 35%;
  }

  @include breakpoint(m) {
    width: 35%;
  }

  @include breakpoint(l) {
    width: 24%;
  }

  @include breakpoint(xl) {
    width: 25%;
  }

  @include breakpoint(xxl) {
    width: 25%;
  }

  @include breakpoint(xxxl) {
    width: 25%;
  }

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

.shadow {
  opacity: .5;

  &:hover {
    cursor: default;
  }
}
</style>