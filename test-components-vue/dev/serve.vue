<script>
import { defineComponent } from 'vue';
import AppBadge from '../src/lib-components/app-badge/AppBadge.vue';
// Uncomment import and local "components" registration if library is not registered globally.
// import { TestComponentsVueSample } from '@/entry.esm';

export default defineComponent({
	components: { AppBadge },
  name: 'ServeDev',
  // components: {
  //  TestComponentsVueSample,
  // }
});
</script>

<template>
  <div id="app">
    <!-- <test-components-vue-sample /> -->
    <app-badge label="Approved"/>
  </div>
</template>
