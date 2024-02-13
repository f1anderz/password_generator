<script>
import OptionsCheckbox from "@/components/OptionsCheckbox.vue";

export default {
  name: "Options",
  components: {OptionsCheckbox},
  data() {
    return {
      options: [
        {
          id: 1,
          value: "Use capital letters",
          checked: true
        },
        {
          id: 2,
          value: "Use numbers",
          checked: true
        },
        {
          id: 3,
          value: "Use special symbols",
          checked: false
        }
      ]
    }
  }
}
</script>

<template>
  <div class="options">
    <span class="options-title">Options:</span>
    <transition-group name="options">
      <options-checkbox v-for="option in this.options" :option="option.value" :key="option.id"
                        :checked="option.checked" @selected="(value)=>{this.$emit('selected', value)}"/>
    </transition-group>
  </div>
</template>

<style scoped lang="scss">
.options {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  gap: .6em;
}
</style>