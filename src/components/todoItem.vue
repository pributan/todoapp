<template>
	<v-card class="my-2 mx-auto cardwidth rounded-card" :elevation="1" centered>
		<v-list-item>
			<div v-if="todo.completed == true">
				<v-list-item-action>
					<v-checkbox
						color="green"
						v-model="checked"
						@change="isCompleted"
						:on-icon="onIcon"
						:off-icon="offIcon"
					>
					</v-checkbox>
				</v-list-item-action>
			</div>
			<div v-else>
				<v-list-item-action>
					<v-checkbox
						v-model="unchecked"
						@change="isCompleted"
						:on-icon="onIcon"
						:off-icon="offIcon"
					>
					</v-checkbox>
				</v-list-item-action>
			</div>

			<v-list-item-content v-bind:class="{ complete: todo.completed }">
				<v-list-item-title class="txtcolor" @click.stop="dialog = true">
					{{ todo.title }}
				</v-list-item-title>
				<v-row justify="center">
					<v-dialog v-model="dialog" max-width="500">
						<v-card class="rounded-card txtcolor">
							<v-card-title class="headline">
								{{ todo.title }}
								<v-spacer></v-spacer>
								<v-btn
									color="red"
									icon
									@click="
										[
											$emit('del-todo', todo.id),
											(dialog = false),
										]
									"
								>
									<v-icon> fas fa-trash </v-icon>
								</v-btn>
							</v-card-title>

							<v-card-text>
								{{ todo.details }}
							</v-card-text>

							<v-card-actions>
								<v-spacer></v-spacer>
								<v-btn
									color="blue darken-1"
									text
									@click="dialog = false"
								>
									Edit
								</v-btn>
								<v-btn
									color="green darken-1"
									text
									@click="dialog = false"
								>
									Close
								</v-btn>
							</v-card-actions>
						</v-card>
					</v-dialog>
				</v-row>
			</v-list-item-content>
		</v-list-item>
	</v-card>
</template>

<script>
	export default {
		name: "todoItem",
		props: ["todo"],
		data: function() {
			return {
				dialog: false,
				checked: true,
				unchecked: false,
				offIcon: "fal fa-circle",
				onIcon: "fal fa-check-circle",
			};
		},
		methods: {
			isCompleted() {
				var todo = this.todo;
				setTimeout(function() {
					todo.completed = !todo.completed;
				}, 1000);
			},
		},
	};
</script>

<style scoped>
	.complete {
		font-style: italic;
		text-decoration: line-through;
		color: gray;
	}
	.cardwidth {
		max-width: 700px;
	}
	.rounded-card {
		border-radius: 15px !important;
	}
	.txtcolor {
		color: #455169 !important;
	}
</style>
