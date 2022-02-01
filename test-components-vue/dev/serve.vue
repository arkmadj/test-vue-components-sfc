<script>
import { defineComponent } from "vue";
import AppBadge from "../src/lib-components/app-badge/AppBadge.vue";
import AppLineChart from "../src/lib-components/app-line-chart/AppLineChart.vue";
import GraphCard from "../src/lib-components/app-graph-card/GraphCard.vue";
// Uncomment import and local "components" registration if library is not registered globally.
// import { TestComponentsVueSample } from '@/entry.esm';

export default defineComponent({
	components: { AppBadge, AppLineChart, GraphCard },
	name: "ServeDev",
	setup() {
		return {
			data: {
				Jan: 15,
				Feb: 35,
				Mar: 30,
				Apr: 50,
				Jun: 35,
				Jul: 35,
				Aug: 70,
				Sep: 60,
				Oct: 35,
				Nov: 80,
				Dec: 95,
			},
		};
	},
});
</script>

<template>
	<div id="app">
		<!-- <test-components-vue-sample /> -->
		<app-badge label="$15,000,000" title="Account Balance"/>
		<graph-card>
			<template v-slot:icon>
				<div
					class="header-icon-container"
					style="
						background: rgba(0, 204, 102, 0.25);
						margin-top: 3px;
						width: 35px;
						height: 35px;
						border-radius: 50%;
						margin-right: 12px;
						display: flex;
						align-items: center;
						justify-content: center;
					"
				>
					<img
						src="https://www.arsenal.com/themes/custom/arsenal_main/logo.svg"
					/>
				</div>
			</template>
			<template v-slot:body>
				<!-- <AppAreaChart :data="chartData" /> -->
				<app-line-chart lineColor="#ffcc00" :data="data" />
			</template>
		</graph-card>
		<app-line-chart lineColor="#ffcc00" :data="data" />
	</div>
</template>
