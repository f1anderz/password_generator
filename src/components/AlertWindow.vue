<script>
export default {
  name: "AlertWindow",
  props: {
    isHidden: {
      type: Boolean,
      required: true
    }
  }
}
</script>

<template>
  <div class="alert" :class="{ hidden: this.isHidden }">
    Password copied to clipboard
  </div>
</template>

<style scoped lang="scss">
@import "@/assets/scss/variables";

.alert {
  position: absolute;
  top: 2rem;
  text-align: center;
  background: $background-color;
  color: $highlight-color;
  width: 22%;
  font-size: 1.5rem;
  padding: .7rem 0;
  border-radius: .3rem;
  opacity: 1;
  transition: opacity .5s ease;
}

.hidden{
  opacity: 0;
}
</style>