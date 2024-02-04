<template>
	<LayoutHeader />
	<main class="grid grid-cols-12">
		<LayoutAside />
		<section class="col-span-10 bg-primary-content  p-4">
			<slot />
		</section>
	</main>
</template>
