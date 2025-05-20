<script lang="ts" setup>
import { leftColClothing } from '../data/data'
import { ref, computed } from 'vue'


const selectedItems = ref<IClothing[]>([]);
const maxCountSelected = ref(6);

const isSelected = (item) => selectedItems.value.includes(item);

const onSelectItem = (item: IClothing) => {
	if (!selectedItems.value.includes(item) && selectedItems.value.length < maxCountSelected.value) {
		selectedItems.value.push(item);
		return;
	}
	const index = selectedItems.value.indexOf(item);
	if (index > -1) {
		selectedItems.value.splice(index, 1)
	}
}

</script>
<template>
	<div class="flex flex-col">
		<div class="border p-3">
			<div class="flex flex-wrap -mx-3">
				<div class="flex-grow px-1.5 w-full md:max-w-6/12 lg:max-w-3/12 mb-3"
						 v-for="item in selectedItems"
						 :key="item.id">
					<div class="border cursor-pointer p-2">
						{{ item.name }}
					</div>
				</div>
			</div>
			<div :class="{ 'text-red-600': selectedItems.length == maxCountSelected }"
					 class="mt-3">
				selected: {{ selectedItems.length }}/{{ maxCountSelected }}
			</div>
		</div>
		<div class="border flex-grow p-3 mt-3">
			<div class="flex flex-wrap -mx-3">
				<div class="flex-grow px-1.5 w-full md:max-w-6/12 lg:max-w-3/12 mb-3"
						 v-for="item in leftColClothing"
						 :key="item.id">
					<div @click="onSelectItem(item)"
							 :class="{ 'bg-green-600 text-white': isSelected(item) }"
							 class="border cursor-pointer p-2">
						{{ item.name }}
					</div>
				</div>
			</div>
		</div>
	</div>
</template>