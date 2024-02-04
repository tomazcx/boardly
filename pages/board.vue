<script setup lang="ts">
import { ref } from "vue"

definePageMeta({
	layout: "dashboard"
})

const currentDraggingCard = ref<{ el: HTMLElement, prevTarget: string } | null>(null)
const states = ref<{ [key: string]: { id: string; title: string; cards: string[]; } }>({
	new: {
		id: "new",
		title: "New",
		cards: [],
	},
	readyToStart: {
		id: "readyToStart",
		title: "Ready To Start",
		cards: [],
	},
	development: {
		id: "development",
		title: "Development",
		cards: [],
	},
	blocked: {
		id: "blocked",
		title: "Blocked",
		cards: [],
	},
	toBeTested: {
		id: "toBeTested",
		title: "To Be Tested",
		cards: [],
	},
	closed: {
		id: "closed",
		title: "Closed",
		cards: [],
	}
})

const arrStates = computed(() => {
	return Object.keys(states.value).map(state => {
		return {
			id: states.value[state].id,
			title: states.value[state].title,
			cards: states.value[state].cards
		}
	});
})

const startDragCard = (event: any) => {
	currentDraggingCard.value = { el: event.target, prevTarget: event.target.parentElement.id };
}

const endDragCard = () => {
	currentDraggingCard.value = null;
}

const dropCard = (event: any) => {
	states.value[event.target.id].cards.push(currentDraggingCard.value?.el.id!)

	const cardIndex = states.value[currentDraggingCard.value?.prevTarget!]?.cards.indexOf(currentDraggingCard.value?.el.id!);
	if (cardIndex !== -1) {
		states.value[currentDraggingCard.value?.prevTarget!].cards.splice(cardIndex, 1);
	}
}

const addTask = (data: { columnId: string; task: string }) => {
	const cardIndex = states.value[data.columnId]?.cards.indexOf(data.task);
	const taskId = (Math.random() * 10000).toFixed(0);
	const taskLabel = taskId.toString() + " - " + data.task;
	if (cardIndex === -1) {
		states.value[data.columnId].cards.push(taskLabel)
	}
}
</script>

<template>
	<h2 class="text-2xl mb-4">Board</h2>
	<div class="flex gap-4 h-[80vh] overflow-auto">
		<BoardStateColumn @update:add-task="addTask" v-for="state in arrStates" :column-id="state.id" v-slot="scope"
			@update:drop-card="dropCard" :title="state.title" :cards="state.cards">
			<BoardTaskCard :current-state="state.title" :label="scope.card"
				:key="'card-' + state.id + '-' + scope.card" @dragstart="startDragCard"
				@dragend="endDragCard" />
		</BoardStateColumn>
	</div>
</template>

