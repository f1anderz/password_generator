<script>
import AlgorithmRadio from "@/components/AlgorithmRadio.vue";

export default {
  name: "Algorithm",
  components: {AlgorithmRadio},
  data() {
    return {
      radioGroup: "algorithm",
      algorithms: [
        {
          id: 1,
          value: "Normal",
          checked: true
        },
        {
          id: 2,
          value: "Enhanced",
          checked: false
        }
      ]
    }
  },
  methods: {
    radioSelected(value) {
      this.$emit('selected', value)
    }
  }
}
</script>

<template>
  <div class="algorithm">
    <span class="algorithm-title">Algorithm:</span>
    <transition-group name="algorithm">
      <algorithm-radio v-for="algorithm in this.algorithms" :key="algorithm.id" :option="algorithm.value"
                       :checked="algorithm.checked" :group="this.radioGroup"
                       @selected="this.radioSelected"/>
    </transition-group>
  </div>
</template>

<style scoped lang="scss">
.algorithm {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  gap: .4em;
}
</style>