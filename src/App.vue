<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import RightColumn from './components/RightColumn.vue'
import LeftColumn from './components/LeftColumn.vue'
</script>

<template>
	<div class="container mx-auto py-5 px-4">
		<div class="page-grid">
			<LeftColumn></LeftColumn>
			<RightColumn></RightColumn>
		</div>
	</div>
</template>

<style scoped>
.page-grid {
	display: grid;
	grid-template-columns: 1fr 1fr;
	gap: 1rem;
}
</style>
