<script setup lang="ts">
import { ref } from "vue"
import PersonalInfoForm from '../components/register/PersonalInfoForm.vue';
import PasswordForm from '../components/register/PasswordForm.vue';
import ProfilePictureForm from '../components/register/ProfilePictureForm.vue';
import ProjectForm from '../components/register/ProjectForm.vue';

const currentStep = ref(0)
const steps = [
	{
		text: "Personal Info",
		component: PersonalInfoForm
	},
	{
		text: "Create Password",
		component: PasswordForm
	},
	{
		text: "Profile Image",
		component: ProfilePictureForm 
	},
	{
		text: "Your First Project",
		component: ProjectForm 
	}
];

const setStep = (step: number) => {
	currentStep.value = step;
}

</script>

<template>
	<div class="bg-base-300 min-h-screen flex flex-col gap-4 justify-center items-center">
		<RegisterProgress @update:set-step="setStep($event as number)" :current-step="currentStep" :steps="steps" />
		<component @update:step="setStep($event as number)" :is="steps[currentStep].component" />
	</div>
</template>
