<template>
	<div class="input-field">
		<div class="input-label">
			{{ label }} <span v-show="required" style="color: red">*</span>
		</div>
		<q-input
			:style="inputStyle"
			:loading="loading"
			:outlined="outlined"
			:dense="dense"
			:borderless="borderless"
			:readonly="readonly"
			v-bind="$attrs"
			:type="inputType"
			:rules="validationRules"
			:color="color"
			:bg-color="background"
		>
			<template v-if="prepend" v-slot:prepend>
				<q-icon :name="prepend" />
			</template>
			<template v-slot:append>
				<q-icon
					v-if="inputType === 'search' && text !== ''"
					:name="append"
					@click="text = ''"
					class="cursor-pointer"
				/>
				<q-icon v-if="inputType !== 'search' && append" :name="append" />
				<slot name="append-item" />
			</template>
			<template v-if="hint" v-slot:hint>
				{{ hint }}
			</template>
		</q-input>
	</div>
</template>

<script>
import { ref } from "vue";
export default {
	name: "AppInput",
	props: {
		vModel: {
			type: String,
			default: "text",
		},
		label: {
			type: String,
			default: "",
		},
		password: {
			type: Boolean,
			default: false,
		},
		// search: {
		//   type: Boolean,
		//   default: false,
		// },
		loading: {
			type: Boolean,
			default: false,
		},
		outlined: {
			type: Boolean,
			default: false,
		},
		dense: {
			type: Boolean,
			default: false,
		},
		borderless: {
			type: Boolean,
			default: false,
		},
		styles: {
			type: String,
			default: "",
		},
		readonly: {
			type: Boolean,
			default: false,
		},
		inputType: {
			type: String,
			default: "text",
		},
		required: {
			type: Boolean,
			default: false,
		},
		rules: {
			type: Array,
			default: () => [],
		},
		hint: {
			type: String,
			default: null,
		},
		prepend: {
			type: String,
			default: null,
		},
		append: {
			type: String,
			default: null,
		},
		color: {
			type: String,
			default: "primary",
		},
		background: {
			type: String,
			default: "",
		},
	},
	setup() {
		return {
			text: ref(""),
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
/* @import './AppInput.scss'; */
.input-label {
	font-size: 14px;
	line-height: 18px;
	font-style: normal;
	font-weight: normal;
	color: #000000;
	margin-bottom: 5px;
}
.q-field {
	border-radius: 8px;
}

.text-brand {
	color: #a2aa33 !important;
}
.bg-brand {
	background: #a2aa33 !important;
}
</style>
