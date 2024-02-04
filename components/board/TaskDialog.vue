<script setup lang="ts">
import { ref } from "vue"

defineProps<{

}>()

const taskModal = ref()
</script>

<template>
	<button @click="taskModal.showModal()">
		<slot name="trigger" />
	</button>
	<dialog ref="taskModal" class="modal">
		<div class="modal-box">
			<button @click="taskModal.close()" class="btn btn-sm btn-circle btn-ghost absolute right-2 top-2">✕</button>
			<h3 class="font-bold text-lg">Hello!</h3>
			<p class="py-4">Press ESC key or click on ✕ button to close</p>
		</div>
	</dialog>
</template>
