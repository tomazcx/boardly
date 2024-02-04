<script setup lang="ts">
import { ref } from "vue"

const props = defineProps<{ modelValue: string }>()
const emit = defineEmits(["update:model-value"])

const name = ref(props.modelValue)
const taskModal = ref<HTMLDialogElement>()

const handleSubmit = () => {
	emit("update:model-value", name.value)
	taskModal.value.close();
}

</script>

<template>
	<button @click="taskModal!.showModal()">
		<slot name="trigger" />
	</button>
	<dialog ref="taskModal" id="taskModal" class="modal">
		<form v-bind="$attrs" @submit.prevent="handleSubmit" class="modal-box">
			<h3 class="font-bold text-lg">New Task</h3>
			<p class="py-4">Add a new task to the current state. Hit save when you are done.</p>
			<div class="flex flex-col">
				<label for="name" class="label">Name</label>
				<input v-model="name" class="input input-bordered" />
			</div>
			<div class="modal-action">
				<button @click="taskModal!.close()" type="button" class="btn">Close</button>
				<button class="btn btn-primary">Save</button>
			</div>
		</form>
	</dialog>
</template>
