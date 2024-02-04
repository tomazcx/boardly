<script setup lang="ts">
import { ref } from "vue"
defineOptions({
	inheritAttrs: false
})

const input = ref<HTMLInputElement>()
</script>

<template>
	<div class="flex flex-col items-center gap-4">
		<div @click="input.click()"
			class="w-48 cursor-pointer hover:opacity-75 transition-opacity relative h-48 rounded-full bg-base-300">
			<div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 flex flex-col items-center gap-2">
				<Icon name="ph:image" size="24" />
				<span class="text-center">Choose a
					image</span>
			</div>
		</div>
		<input type="file" ref="input" v-bind="$attrs" class="file-input file-input-bordered w-full" />
	</div>
</template>
