<template>
	<v-app>
		<v-content>
			<v-img class="img" :aspect-ratio="16 / 9" src="../assets/home.jpg">
				<template v-slot:placeholder>
					<v-row
						align="center"
						justify="center"
						class="fill-height ma-0 imgholder"
					>
						<v-progress-circular indeterminate color="blue">
						</v-progress-circular>
					</v-row>
				</template>
			</v-img>
			<addTodo class="newtodo" v-on:add-todo="submit" />
			<Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
		</v-content>
	</v-app>
</template>

<script>
	import Todos from "../components/Todos";
	import addTodo from "../components/addTodo";

	export default {
		name: "Home",
		components: {
			Todos,
			addTodo,
		},
		data() {
			return {
				todos: [],
			};
		},
		methods: {
			deleteTodo(id) {
				this.todos = this.todos.filter((todo) => todo.id !== id);
			},
			submit(newTodo) {
				this.todos = [...this.todos, newTodo];
			},
		},
	};
</script>

<style scoped>
	.newtodo {
		margin-top: -100px;
	}
	.imgholder {
		background: #dfe4ed;
	}
	.img {
		max-height: 400px;
	}
</style>
