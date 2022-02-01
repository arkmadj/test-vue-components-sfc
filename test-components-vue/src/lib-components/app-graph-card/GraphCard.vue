<template>
  <div class="graph-card">
    <div class="header">
      <div class="header-left">
        <slot name="icon" />
        <div class="title-container">
          <div class="title">{{ title }}</div>
          <div v-if="subTitle" class="sub-title">{{ subTitle }}</div>
        </div>
      </div>
      <div class="header-right">
        <div v-for="(item, key) in legend" :key="key" class="legend-item-container">
          <div key class="legend-item-color" :style="`background: ${item.color};`" />
          <div class="legend-item-text">{{ item.name }}</div>
        </div>
      </div>
    </div>
    <slot name="body" />
  </div>
</template>

<script>
export default {
  name: 'GraphCard',
  props: {
    title: {
      type: String,
    },
    legend: {
      type: Array,
    },
    subTitle: {
      type: String,
    },
  },
}
</script>

<style scoped>
/* @import './GraphCard.scss'; */
.graph-card {
	border: 2px solid #eeeeee;
	border-radius: 8px;
	padding: 24px;
	height: 100%;
}

.header {
	display: flex;
	justify-content: space-between;
}

.header-left {
  display: flex;
  margin-bottom: 40px;
}

.title {
  color: #808080;
  font-weight: 600;
  font-size: 16px;
  line-height: 19px;
}

.sub-title {
  color: #000;
  font-weight: 500;
  font-size: 24px;
  line-height: 29px;
}

.header-right {
  display: flex;
}

.legend-item-container {
  display: flex;
  margin-left: 25px;
}

.legend-item-color {
  border-radius: 2px;
  width: 12px;
  height: 12px;
  margin-right: 9px;
}

.legend-item-text {
  font-size: 14px;
  line-height: 17px;
  color: #63666f;
}
</style>
