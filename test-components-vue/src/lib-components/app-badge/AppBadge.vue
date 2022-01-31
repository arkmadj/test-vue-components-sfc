<template>
  <span :style="badgeStyle" class="badge-class">
    <span>
    {{label}}
    </span>
    <span v-if="title" class="badge-title">
    {{title}}
    </span>
  </span>
</template>

<script>
export default {
  name: 'Badge',
  props: {
    label: {
      type: String,
      default: '',
    },
    title: {
      type: String,
      default: '',
    },
    bgColor: {
      type: String,
      default: 'rgba(0, 204, 102, 0.1)'
    },
    color: {
      type: String,
      default: '#00CC66'
    },
  },
  computed:{
    badgeStyle() {
      return {
        border: this.title !== '' ? '1px solid #C4C4C4' : '0px',
        padding: '4px 8px',
        background: this.bgColor,
        color: this.color,
        borderRadius: '20px',
        fontWeight: '500',
      }
    }
  }
}
</script>

<style scoped>
@import './AppBadge.scss';
</style>
