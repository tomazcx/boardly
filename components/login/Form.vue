<template>
	<form class="bg-base-100 w-10/12 max-w-[500px] flex flex-col items-center gap-4 rounded-lg shadow p-8">
		<h1 class="text-xl font-medium">Login</h1>
		<span class="text-center">Login with your credentials to access Boardly, or registed if you don't have an account.</span>
		<FormInput label="Name" id="name" type="text" />
		<FormInput label="Password" id="password" type="password" />
		<button class="btn btn-primary w-full">Submit</button>
		<span>Don't have an account? <a class="link" href="/register">Register here</a></span>
	</form>
</template>
