<template>
	<v-container>
		<v-text-field
			label="Solo"
			placeholder="What is your plan?"
			rounded
			solo
			single-line
			class="mx-auto addtodo"
			v-model="title"
			v-on:keyup.enter="submit"
		>
			<template slot="append">
				<v-icon color="rgb(125, 59, 255)" class="plus" @click="submit">
					far fa-plus
				</v-icon>
			</template>
		</v-text-field>
		<v-snackbar
			color="rgb(125, 59, 255)"
			v-model="snackbar"
			:timeout="2000"
			top
			class="mt-12"
		>
			<v-icon dark> fas fa-exclamation-triangle </v-icon>
			Sorry you can't add empty todo
			<v-btn icon @click="snackbar = false">
				<v-icon color="white"> fal fa-times </v-icon>
			</v-btn>
		</v-snackbar>
	</v-container>
</template>

<script>
	import { v4 as uuidv4 } from "uuid";
	export default {
		name: "addTodo",
		props: ["todos"],
		data() {
			return {
				title: "",
				snackbar: false,
			};
		},
		methods: {
			submit(e) {
				e.preventDefault();
				const newTodo = {
					id: uuidv4(),
					title: this.title,
					details: "",
					completed: false,
				};
				if (this.title == "") {
					this.snackbar = true;
				} else {
					this.$emit("add-todo", newTodo);
					this.title = "";
				}
			},
		},
	};
</script>

<style scoped>
	.addtodo {
		max-width: 700px;
	}
</style>
