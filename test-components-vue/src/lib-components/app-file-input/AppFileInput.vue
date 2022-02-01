<template>
	<div class="input-field">
		<div class="input-label">
			{{ label }} <span v-show="required" style="color: red">*</span>
		</div>
		<q-file dense outlined use-chips multiple>
			<div
				style="color: #636363"
				v-if="files.length === 0"
				class="file-placeholder"
			>
				Select file
			</div>
		</q-file>
	</div>
</template>

<script>
import { ref } from "vue";
export default {
	name: "AppFileInput",
	props: {
		label: {
			type: String,
			default: "",
		},
		required: {
			type: Boolean,
			default: false,
		},
	},
	setup() {
		return {
			files: ref([]),
		};
	},
	computed: {
		inputStyle() {
			return {
				color: "#0B8F99",
				// background: '#0B8F99'
			};
		},
		validationRules() {
			const { required, rules } = this;
			const requredRule = (val) => !!val || "This field is Required";
			return required ? [requredRule, ...rules] : rules;
		},
	},
	mounted() {},
};
</script>

<style scoped>
.file-placeholder {
	display: flex;
	width: 100px;
	align-items: center;
	justify-content: center;
}
</style>
