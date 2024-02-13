<script>
export default {
  name: "OptionsCheckbox",
  props: {
    option: {
      type: String,
      required: true
    },
    checked: {
      type: Boolean,
      required: true
    }
  }
}
</script>

<template>
  <label class="checkbox">
    {{ this.option }}
    <input type="checkbox" :checked="this.checked" @click="this.$emit('selected', this.option)">
    <span class="checkbox-checkmark"></span>
  </label>
</template>

<style scoped lang="scss">
@import "@/assets/scss/variables";

.checkbox {
  position: relative;
  display: flex;
  flex-direction: row;
  cursor: pointer;
  user-select: none;
  padding-left: 2.1em;
  padding-top: .2em;

  & input {
    position: absolute;
    height: 0;
    width: 0;
    opacity: 0;
    cursor: pointer;
  }

  & input:checked ~ &-checkmark {
    background: $highlight-color;
  }

  & &-checkmark:after {
    left: .6em;
    top: .3em;
    width: .3em;
    height: .6em;
    border: solid #ffffff;
    border-width: 0 .2em .2em 0;
    transform: rotate(45deg);
  }

  & input:checked ~ &-checkmark:after {
    display: block;
  }

  &-checkmark {
    position: absolute;
    top: 0;
    left: 0;
    height: 1.6em;
    width: 1.6em;
    border-radius: .3em;
    background-color: #ffffff;

    &:after {
      content: "";
      position: absolute;
      display: none;
    }
  }
}
</style>