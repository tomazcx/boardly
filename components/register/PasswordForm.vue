<template>
	<form @submit.prevent class="bg-base-100 w-10/12 max-w-[500px] flex flex-col gap-4 rounded-lg shadow">
		<div class="border-b border-base-300 px-8 pt-8 pb-4">
			<span>Register account</span>
			<h2 class="text-2xl font-medium">Create your password</h2>
		</div>
		<div class="px-8 py-4 space-y-2">
			<FormInput label="Password" id="password" type="password" />
			<FormInput label="Confirm Password" id="confirmPassword" type="password" />
		</div>
		<div class="pt-4 px-8 pb-8 flex flex-col gap-4 items-center">
			<button @click="$emit('update:step', 1)" class="btn btn-primary w-full">Next</button>
		</div>
	</form>
</template>
