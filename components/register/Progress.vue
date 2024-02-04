<script setup lang="ts">
defineProps<{
	steps: {
		text: string
	}[],
	currentStep: number
}>()

defineEmits(["update:setStep"])
</script>

<template>
	<ul class="steps steps-vertical lg:steps-horizontal mb-12">
		<li v-for="(step, index) in steps" :key="'step-' + step.text + '-' + step.text" @click="$emit('update:setStep', index)"
			:class="['step cursor-pointer', { 'step-primary': currentStep >= index}]">{{ step.text }}</li>
	</ul>
</template>
