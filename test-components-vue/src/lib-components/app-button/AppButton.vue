<template>
	<!-- <div style="background: red"> -->
	<q-btn
		class="custom-btn"
		no-caps
		:flat="flat"
		:outline="outline"
		:padding="buttonPadding"
		:unelevated="unelevated"
		:disable="disable || loading"
		:loading="loading"
		:type="buttonType"
		:style="style"
		:color="backgroundColor"
		:round="round"
		@click="onClick"
	>
		<q-icon v-if="icon" :name="icon" :size="iconSize" :color="iconColor" />
		<div v-if="label !== ''" class="label" :style="labelStyle">
			{{ label }}
		</div>
		<q-icon
			v-if="rightIcon"
			:name="rightIcon"
			:size="iconSize"
			:color="iconColor"
		/>
		<q-badge
			v-if="notification"
			:label="notification"
			:color="notificationColor"
			rounded
			floating
		/>
	</q-btn>

	<!-- </div> -->
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
	name: "AppButton",
	props: {
		label: {
			type: String,
			default: "",
		},
		icon: {
			type: String,
			default: "",
		},
		rightIcon: {
			type: String,
			default: "",
		},
		iconSize: {
			type: String,
			default: "14px",
		},
		iconColor: {
			type: String,
			default: "",
		},
		noCustomColor: {
			type: Boolean,
			default: true,
		},
		unelevated: {
			type: Boolean,
			default: false,
		},
		disable: {
			type: Boolean,
			default: false,
		},
		loading: {
			type: Boolean,
			default: false,
		},
		buttonPadding: {
			type: String,
			default: () => "8px 12px",
		},
		buttonType: {
			type: String,
		},
		backgroundColor: {
			type: String,
			default: "",
		},
		color: {
			type: String,
			default: "",
		},
		flat: {
			type: Boolean,
			default: false,
		},
		outline: {
			type: Boolean,
			default: false,
		},
		round: {
			type: Boolean,
			default: false,
		},
		notification: {
			type: String,
			default: null,
		},
		notificationColor: {
			type: String,
			default: "red",
		},
		onClick: {
			type: Function,
		},
	},
	watch: {},
	computed: {
		classes() {
			return {};
		},
		style() {
			return {
				borderRadius: this.round ? "" : "8px",
				backgroundColor: this.flat || this.outline ? "" : this.backgroundColor,
				color: this.flat || this.outline ? this.color : "",
				// padding: this.round ? '' : this.padding
			};
		},
		labelStyle() {
			return {
				marginRight: this.rightIcon ? "5px" : "",
				marginLeft: this.icon ? "10px" : "",
				color: this.color,
			};
		},
	},
});
</script>

<style scoped>
.custom-btn {
	padding: unset;
	padding: 8px 12px;
	color: red;
	font-size: 14px;
}
</style>
