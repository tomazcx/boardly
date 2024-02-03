<script setup lang="ts">
defineProps<{
	label: string
	currentState: string
}>()

</script>

<template>
	<div :id="label" draggable="true" class="w-full h-32 shadow p-2 rounded-lg border-rounded border border-input">
		<div class="flex gap-4 items-center">
			<Icon name="material-symbols:task" /> <span>{{ label }}</span>
		</div>
		<Badge>{{currentState}}</Badge>
	</div>
</template>
