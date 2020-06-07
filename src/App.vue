<template>
	<v-app>
		<v-app-bar class="navbar" dense app>
			<v-row class="d-flex mx-auto navbarcontent align-center">
				<v-icon color="white"> fas fa-check </v-icon>
				<h3 class="ml-3">Todo App</h3>
				<v-spacer></v-spacer>
				<h4 class="mr-3">Menu</h4>
				<v-menu
					v-model="menu"
					:close-on-content-click="true"
					transition="slide-y-transition"
					bottom
					content-class="my-menu"
					nudge-left="80"
					nudge-bottom="10"
				>
					<template v-slot:activator="{ on }">
						<v-btn icon dark v-on="on">
							<v-icon size="22">
								{{
									menu
										? "fal fa-chevron-up"
										: "fal fa-chevron-down"
								}}
							</v-icon>
						</v-btn>
					</template>
					<floatingMenu />
				</v-menu>
			</v-row>
		</v-app-bar>
		<router-view />
		<v-footer dark class="footer">
			<v-container text-center>
				<h6>
					Created with
					<v-icon size="12" class="mug d-inline"> fas fa-mug </v-icon>
					by Kusuma.
				</h6>
				<h6>Todo App v{{ version }}. Licensed under MIT.</h6>
			</v-container>
		</v-footer>
	</v-app>
</template>

<script>
	import floatingMenu from "./components/floatingMenu";

	export default {
		components: {
			floatingMenu,
		},
		data() {
			return {
				menu: false,
				version: process.env.VUE_APP_VERSION,
			};
		},
	};
</script>

<style scoped>
	.navbar {
		color: white;
		background: rgb(125, 59, 255);
		background: linear-gradient(
			90deg,
			rgba(125, 59, 255, 1) 0%,
			rgba(74, 181, 255, 1) 100%
		);
	}
	.navbarcontent {
		max-width: 1000px;
	}
	.footer {
		background: rgb(26, 0, 96);
		background: linear-gradient(
			90deg,
			rgba(26, 0, 96, 1) 0%,
			rgba(61, 0, 96, 1) 100%
		);
	}
	.my-menu {
		margin-top: 40px;
		overflow: visible;
		border-radius: 15px;
		width: 200px;
	}
	.mug {
		background: rgb(255, 46, 125);
		background: linear-gradient(
			90deg,
			rgba(255, 46, 125, 1) 0%,
			rgba(255, 192, 86, 1) 100%
		);
		color: transparent !important;
		background-clip: text !important;
	}
</style>
