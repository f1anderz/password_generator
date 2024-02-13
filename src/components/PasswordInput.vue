<script>
export default {
  name: "PasswordInput",
  data() {
    return {
      password: "",
      generatorString: "",
      charset: [
        {
          name: "letters", value: "abcdefghijklmnopqrstuvwxyz"
        },
        {
          name: "Capital", value: "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
        },
        {
          name: "Numbers", value: "0123456789"
        },
        {
          name: "Special", value: "~`!@#$%^&*()_-+={[}]|\\:;\"'<,>.?/"
        }
      ]
    }
  },
  props: {
    generator: {
      type: Boolean,
      required: true
    },
    passwordLength: {
      type: Number,
      required: true
    },
    options: {
      type: Object,
      required: true
    },
    algorithm: {
      type: String,
      required: true
    }
  },
  methods: {
    async copyPassword() {
      await navigator.clipboard.writeText(this.password);
      this.$emit('copyPass');
    },
    generatePassword() {
      let newPassword = "";
      this.generatorString = this.charset[0].value;
      this.charset.forEach((chars) => {
        if (this.options[chars.name]) {
          this.generatorString += chars.value;
        }
      })
      for (let i = 0; i < this.passwordLength; i++) {
        newPassword += this.generatorString[Math.floor(Math.random() * this.generatorString.length)];
      }
      this.password = newPassword;
      this.copyPassword();
    }
  }, watch: {
    generator(newGenerator) {
      if (newGenerator) {
        this.generatePassword();
      }
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