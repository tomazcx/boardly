<script setup lang="ts">
defineProps<{
	title: string,
	columnId: string
	cards: string[]
}>()
defineEmits(["update:drop-card"])

</script>

<template>
	<div class="border min-w-[280px] rounded-lg bg-background text-foreground border-border col-span-2 h-screen">
		<div class="flex justify-between items-center border-b border-border p-2">
			<h3>{{ title }}</h3>
			<Dialog>
				<DialogTrigger>	
				<Button>New</Button>
				</DialogTrigger>
				<DialogContent>
					<DialogHeader>
						<DialogTitle>Add Task</DialogTitle>
						<DialogDescription>Add a new task to this column. Hit save when you're done.</DialogDescription>
					</DialogHeader>

					<DialogFooter>
						<DialogClose>
							<Button variant="outline">Cancel</Button>
						</DialogClose>
						<Button>Save</Button>					
					</DialogFooter>
				</DialogContent>
			</Dialog>
		</div>
		<div :id="columnId" class="h-full p-2 space-y-4" @dragover.prevent
			@drop.prevent="$emit('update:drop-card', $event)">
			<slot v-for="card in cards" :card />
		</div>
	</div>
</template>
