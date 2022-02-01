<template>
  <div :class="`circle ${getStatus(percentage, showStatus)}`">
    <div class="number">{{ growingValue > 0 ? `${growingValue}%` : '--' }}</div>
    <div class="svg">
      <svg xmlns="http://www.w3.org/2000/svg" version="1.1">
        <circle class="svg-circle1" cx="80" cy="80" r="70" stroke-linecap="round" />
        <circle
          class="svg-circle2"
          :stroke-dashoffset="getStopPoint(percentage)"
          cx="80"
          cy="80"
          r="70"
          stroke-linecap="round"
        />
      </svg>
    </div>
  </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'AppCircularProgressBar',
  props: {
    percentage: {
      type: Number,
    },
    showStatus: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      growingValue: 0,
    }
  },
  mounted() {
    this.incrementValue()
  },
  //   computed() {
  //       },
  methods: {
    getStatus(percentage, showStatus) {
      return showStatus ? (percentage < 40 ? 'low' : percentage < 75 ? 'medium' : null) : null
    },
    getStopPoint(percentage) {
      return 440 - 440 * (percentage / 100)
    },
    incrementValue() {
      let counter = 0
      this.growingValue = 0
      const myInterval = setInterval(() => {
        if (counter >= this.percentage) {
          clearInterval(myInterval)
        } else {
          counter += 1
          this.growingValue = counter
        }
      }, 10)
    },
  },
  watch: {
    percentage() {
      this.incrementValue()
    },
  },
})
</script>

<style scoped>
/* @import './AppCircularProgressBar.scss'; */
.circle {
	width: 160px;
	height: 160px;
	position: relative;
}

.number {
	width: 100%;
	height: 100%;
	display: flex;
	justify-content: center;
	align-items: center;
	font-weight: 500;
	font-size: 40px;
	line-height: 48px;
	color: #0b8f99;
}

.svg-circle1 {
	fill: none;
	stroke: rgba(11, 143, 153, 0.1);
	stroke-width: 20px;
	stroke-dasharray: 440;
	stroke-linecap: butt;
}

.svg-circle2 {
	fill: none;
	stroke: #0b8f99;
	stroke-width: 20px;
	stroke-dasharray: 440;
	stroke-linecap: butt;
	animation: anim 1s linear alternate;
}

.svg {
	position: absolute;
	top: -4px;
	left: 4px;
	transform: rotate(-90deg);
}

.svg > svg {
	height: 160px;
	width: 160px;
}

@keyframes anim {
	0% {
		stroke-dashoffset: 440;
	}
}
</style>
