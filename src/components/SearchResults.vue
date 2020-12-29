<template>
	<div class='root'>
		<p> Showing {{ filteredTitles.length }} results for "{{ query }}" </p>
		<ul>
			<li v-for='title in filteredTitles' :key='title'>
				{{ title }}
			</li>
		</ul>
	</div>
</template>
<script>
import { ref, computed } from 'vue'

const titles = ['Creating Your First Vue3 Project', 'A Complete Guide to Vue Lifecycle Hooks in Vue3']
export default {
	props: {
		query: String
	},
	setup (props, context) {
		const filteredTitles = computed(() => {
			return titles.filter(s => s.toLowerCase().includes(props.query.toLowerCase()))
		})

		return {
			filteredTitles
		}
	}
}
</script>

<style scoped>

	.root {
		width: 400px;
		margin: 0 auto;
	}

	.root p {
		text-align: right;
		font-size: 0.7em;
		margin: 0;
	}

	ul {
		list-style:  none;
		width: 50px 0;
		padding: 0;
		background-color: #fafafa;
		border-radius: 5px;
		border: 1px solid #ddd;
	}

	li {
		text-align: left;
		padding: 20px;
		border-bottom: 1px solid #ddd;
	}

	li:nth-last-of-type(1) {
		border-bottom: none;
	}
</style>