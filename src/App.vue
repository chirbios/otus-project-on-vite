<script setup lang="ts">
import { ref } from 'vue'

const listShow = ref(true)
const showAge = ref(true)

const hover = ref({
	color: 'fuchsia'
})

const persons = ref(
	[
		{
			name: 'Саша',
			year: 30,
		},
		{
			name: 'Лиза',
			year: 29,
		},
		{
			name: 'Ваня',
			year: 28,
		},
		{
			name: 'Надя',
			year: 22,
		},
		{
			name: 'Вова',
			year: 16
		},
	]
)
</script>

<template>
	<button class="close-list" @click="listShow = !listShow">{{ listShow ? 'Скрыть список' : 'Показать список' }}</button>
	<button class="toggle-age" @click="showAge = !showAge">
			{{ showAge ? 'Скрыть возраст' : 'Показать возраст' }}
	</button>
	<ul v-if="listShow">
		<li 
			v-for="(person, index) in persons" 
			:key="index"
			class="element"
		>
			{{ person.name }}
			 <span v-if="showAge"> - {{ person.year }} лет</span>
		</li>
	</ul>
</template>

<style scoped>
ul {
	list-style-type: none;
	padding-left: 0px;
}

li, .close-list {
	cursor: pointer;
}

.element:hover {
	color: v-bind('hover.color');
}
</style>
