<script>
export default {
  name: "GenerateButton"
}
</script>

<template>
  <div class="button">
    Generate
  </div>
</template>

<style scoped lang="scss">
@import "@/assets/scss/variables";

.button {
  width: 50%;
  margin: 0 auto;
  padding: .4rem 0;
  border-radius: .3rem;
  text-align: center;
  font-size: 1.2rem;
  color: #ffffff;
  background: $highlight-color;
}
</style>