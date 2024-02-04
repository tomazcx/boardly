<script setup lang="ts">
defineProps<{
	label: string
	currentState: string
}>()
</script>

<template>
	<div :id="label" draggable="true"
		class="w-full flex flex-col gap-2 bg-base-100 h-32 shadow p-2 rounded-lg border-rounded border border-base-300 border-input">
		<div class="flex gap-4 items-center">
			<BoardTaskDialog>
				<template #trigger>
					<Icon name="material-symbols:task" /> <span class="hover:underline cursor-pointer">{{
						label
					}}</span>
				</template>
			</BoardTaskDialog>
		</div>
		<div class="badge badge-secondary">{{ currentState }}</div>
	</div>
</template>
