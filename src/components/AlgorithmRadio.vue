<script>
export default {
  name: "AlgorithmRadio",
  props: {
    option: {
      type: String,
      required: true
    },
    checked: {
      type: Boolean,
      required: true
    },
    group: {
      type: String,
      required: true
    }
  }
}
</script>

<template>
  <label class="radio">
    {{ this.option }}
    <input type="radio" :name="this.group" :checked="this.checked">
    <span class="radio-checkmark"></span>
  </label>
</template>

<style scoped lang="scss">
@import "@/assets/scss/variables";

.radio {
  position: relative;
  display: flex;
  flex-direction: row;
  cursor: pointer;
  user-select: none;
  padding-left: 2.1em;
  padding-top: .3em;

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
    left: .58em;
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
    border-radius: 50%;
    background-color: #ffffff;

    &:after {
      content: "";
      position: absolute;
      display: none;
    }
  }
}
</style>