<script setup lang="ts">
const props = defineProps<{
	title: string,
	columnId: string
	cards: string[]
}>()
const emit = defineEmits(["update:drop-card", "update:add-task"])
const name = ref("")

const handleSubmit = (data:string) => {
	emit("update:add-task", {task: data, columnId:props.columnId})	
}
</script>

<template>
	<div class=" min-w-[280px] rounded-lg border border-base-300  text-foreground col-span-2 h-screen bg-base-100">
		<div class="flex justify-between items-center border-b border-primary-content p-2">
			<h3>{{ title }} ({{cards.length}})</h3>
			<BoardTaskForm :model-value="name" @update:model-value="handleSubmit">
				<template #trigger><button class="btn btn-primary">New</button></template>
			</BoardTaskForm>
		</div>
		<div :id="columnId" class="h-full bg-base-200 p-2 space-y-4" @dragover.prevent
			@drop.prevent="$emit('update:drop-card', $event)">
			<slot v-for="card in cards" :card />
		</div>
	</div>
</template>
