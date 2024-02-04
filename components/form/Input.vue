<script setup lang="ts">
const model = defineModel()
defineOptions({
	inheritAttrs:false
})
defineProps<{
	label?:string
}>()
</script>

<template>
	<div class="w-full">
		<label v-if="label" :for="$attrs.id as string" class="label" >{{label}}</label>
		<input v-model="model" v-bind="$attrs" class="input input-bordered w-full" />
	</div>
</template>
