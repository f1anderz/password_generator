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
    <input type="radio" :name="this.group" :checked="this.checked" @click="this.$emit('selected', this.option)">
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
  padding-left: 2.1rem;

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
    left: .48rem;
    top: .25rem;
    width: .25rem;
    height: .5rem;
    border: solid #ffffff;
    border-width: 0 .2rem .2rem 0;
    transform: rotate(45deg);
  }

  & input:checked ~ &-checkmark:after {
    display: block;
  }

  &-checkmark {
    position: absolute;
    top: 0;
    left: 0;
    height: 1.4rem;
    width: 1.4rem;
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