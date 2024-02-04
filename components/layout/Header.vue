<script setup lang="ts">
import { useDark, useToggle } from '#imports';

const isDark = useDark({
	attribute:"data-theme",
	valueDark: "dark",
	valueLight: "light"
})
const toggleTheme = useToggle(isDark)
</script>

<template>
	<header class="px-8 py-4 flex items-center justify-between border-b border-base-300">
		<h1>Boardly</h1>
		<details class="dropdown dropdown-end">
			<summary class="m-1">
				<Icon name="ph:user-bold" size="24" />
			</summary>
			<ul class="p-2 shadow menu dropdown-content z-[1] bg-base-100 rounded-box w-52">
				<li>
					<button @click="toggleTheme()">
						<Icon :name="isDark ? 'ph:sun-bold' : 'ph:moon-bold'" /> <span>Toggle
							Theme</span>
					</button>
				</li>
			</ul>
		</details>
	</header>
</template>
