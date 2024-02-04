<script setup lang="ts">
import { ref } from "vue"
defineOptions({
	inheritAttrs: false
})

const input = ref<HTMLInputElement>()
const file = ref<string>()

const setFile = (e: Event) => {
	const parsedImage = URL.createObjectURL((e.target as HTMLInputElement)!.files![0])
	file.value = parsedImage
}
</script>

<template>
	<div class="flex flex-col items-center gap-4">
		<div @click="input!.click()" v-if="!file"
			class="w-48 cursor-pointer hover:opacity-75 transition-opacity relative h-48 rounded-full bg-base-300">
			<div
				class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 flex flex-col items-center gap-2">
				<Icon name="ph:image" size="24" />
				<span class="text-center">Choose a
					image</span>
			</div>
		</div>
		<div v-else class="w-48 h-48 rounded-full overflow-hidden bg-base-300 flex items-center justify-center">
			<img :src="file" class="w-full object-cover" />
		</div>
		<input @change="setFile" type="file" ref="input" v-bind="$attrs"
			class="file-input file-input-bordered w-full" />
	</div>
</template>
