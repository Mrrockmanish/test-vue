<script lang="ts" setup>
import { rightColClothing } from '../data/data'
import { ref, computed } from 'vue'

const selectedItem = ref<IClothing | null>(null);

const isSelected = (item) => selectedItem.value == item;

const onSelectItem = (item: IClothing) => {
	if (selectedItem.value == item) selectedItem.value = null;
	else selectedItem.value = item;
}

</script>
<template>
	<div class="flex flex-col">
		<div class="flex justify-end">
			<div v-if="selectedItem"
					 class="inline-flex text-3xl border cursor-pointer p-3">
				{{ selectedItem.name }}
			</div>
			<div v-else
					 class="inline-flex text-gray-300 text-3xl border cursor-pointer p-3">
				ничего не выбрано
			</div>

		</div>
		<div class="border flex-grow p-3 mt-3">
			<div class="flex flex-wrap -mx-3">
				<div class="flex-grow px-1.5 w-full md:max-w-6/12 lg:max-w-3/12 mb-3"
						 v-for="item in rightColClothing"
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