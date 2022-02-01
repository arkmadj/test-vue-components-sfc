<template>
  <q-toggle
    :label="showLabel ? `${value}` : ''"
    :true-value="trueValue"
    :false-value="falseValue"
    :left-label="leftLabel"
    :disable="disabled"
  />
</template>

<script>
import { ref } from 'vue'
export default {
  name: 'AppToggle',
  props: {
    trueValue: {
      type: String,
      default: 'True',
    },
    falseValue: {
      type: String,
      default: 'false',
    },
    leftLabel: {
      type: Boolean,
      default: true,
    },
    showLabel: {
      type: Boolean,
      default: false,
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  setup() {
    return {
      value: ref(false),
    }
  },
  methods: {
    // setValue() {
    //   this.value = this.falseValue
    // },
  },
  mounted() {
    // this.setValue()
  },
}
</script>

<style scoped>
</style>
