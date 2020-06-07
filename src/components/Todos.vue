<template>
	<div>
		<v-container>
			<div class="mt-2 mb-12">
				<div v-if="exist">
					<div :key="todo.id" v-for="todo in uncomplete">
						<todoItem
							v-bind:todo="todo"
							v-on:del-todo="$emit('del-todo', todo.id)"
						/>
					</div>
				</div>
				<div v-else>
					<h5 class="txt text-center">
						You don't have any todo yet!
					</h5>
				</div>
			</div>
		</v-container>

		<v-divider></v-divider>

		<v-container>
			<h4 class="text-center uncompl" @change="counted">
				Completed Todos ({{ counted }})
				<v-btn icon @click="show = !show">
					<v-icon size="22" color="blue">
						{{ show ? "fal fa-chevron-up" : "fal fa-chevron-down" }}
					</v-icon>
				</v-btn>
			</h4>
			<v-expand-transition>
				<div v-show="show">
					<div :key="todo.id" v-for="todo in complete">
						<todoItem
							v-bind:todo="todo"
							v-on:del-todo="$emit('del-todo', todo.id)"
						/>
					</div>
				</div>
			</v-expand-transition>
		</v-container>
	</div>
</template>

<script>
	import todoItem from "./todoItem";

	export default {
		name: "Todos",
		components: {
			todoItem,
		},
		props: ["todos"],
		data: () => ({
			show: false,
		}),

		computed: {
			uncomplete() {
				var uncmp = this.todos.filter(
					(todo) => todo.completed == false
				);
				return uncmp.reverse(this.todos.id);
			},
			complete() {
				var cmp = this.todos.filter((todo) => todo.completed == true);
				return cmp;
			},
			counted() {
				var count = this.todos.filter((todo) => todo.completed == true);
				return count.length;
			},
			exist() {
				var count = this.todos.filter(
					(todo) => todo.completed == false
				);
				return count.length;
			},
		},
	};
</script>

<style scoped>
	.txt {
		color: #b1bbcc;
	}

	.uncompl {
		color: #455169;
	}
</style>
