<template>
	<span :style="badgeStyle" class="badge-class">
		<span>
			{{ label }}
		</span>
		<span v-if="title" class="badge-title">
			{{ title }}
		</span>
	</span>
</template>

<script>
export default {
	name: "AppCircularProgressBar",
	props: {
		label: {
			type: String,
			default: "",
		},
		title: {
			type: String,
			default: "",
		},
		bgColor: {
			type: String,
			default: "",
		},
		color: {
			type: String,
			default: "#00CC66",
		},
	},
	computed: {
		badgeStyle() {
			return {
				border: this.title !== "" ? "1px solid #C4C4C4" : "0px",
				padding: "4px 8px",
				background: this.bgColor,
				color: this.color,
				borderRadius: "20px",
				fontWeight: "500",
			};
		},
	},
};
</script>

<style scoped>
/* @import './AppBadge.scss'; */
.badge-title {
	margin-left: 5px;
	color: black;
}
</style>
