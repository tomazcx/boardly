<script setup lang="ts">
defineEmits(["update:step"])
</script>

<template>
	<form @submit.prevent class="bg-base-100 w-10/12 max-w-[500px] flex flex-col gap-4 rounded-lg shadow">
		<div class="border-b border-base-300 px-8 pt-8 pb-4">
			<span>Register account</span>
			<h2 class="text-2xl font-medium">Personal information</h2>
		</div>
		<div class="px-8 py-4 space-y-4">
			<FormInput label="First name" id="firstName" type="text" />
			<FormInput label="Surname" id="surname" type="text" />
			<FormInput label="Email" id="email" type="email" />
		</div>
		<div class="pt-4 px-8 pb-8 flex flex-col gap-4 items-center">
			<button @click="$emit('update:step', 1)" class="btn btn-primary w-full">Next</button>
			<span>Already have an account? <a class="link" href="/login">Login here</a></span>
		</div>
	</form>
</template>
