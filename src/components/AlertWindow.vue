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
@import "@/assets/scss/mixins";

.alert {
  position: absolute;
  text-align: center;
  background: $background-color;
  color: $highlight-color;
  border-radius: .3rem;
  opacity: 1;
  transition: opacity .5s ease;

  @include breakpoint(xs) {
    top: 1.5rem;
    width: 80%;
    font-size: 1.2rem;
    padding: .5rem 0;
  }

  @include breakpoint(s) {
    top: .5rem;
    width: 40%;
    font-size: 1.2rem;
    padding: .3rem 0;
  }

  @include breakpoint(m) {
    top: 2rem;
    width: 50%;
    font-size: 1.5rem;
    padding: .3rem 0;
  }

  @include breakpoint(l) {
    top: 2rem;
    width: 40%;
    font-size: 1.5rem;
    padding: .3rem 0;
  }

  @include breakpoint(xl) {
    top: 2rem;
    width: 35%;
    font-size: 1.7rem;
    padding: .3rem 0;
  }

  @include breakpoint(xxl) {
    top: 2rem;
    width: 22%;
    font-size: 1.5rem;
    padding: .7rem 0;
  }

  @include breakpoint(xxxl) {
    top: 4rem;
    width: 22%;
    font-size: 3rem;
    padding: 1.4rem 0;
  }
}

.hidden{
  opacity: 0;
}
</style>