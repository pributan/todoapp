<template>
	<v-card class="mn">
		<v-subheader>
			Menu
		</v-subheader>
		<v-divider></v-divider>
		<v-list shaped class="py-3">
			<v-list-item-group color="primary">
				<v-list-item v-for="(item, i) in items" :key="i">
					<v-list-item-icon>
						<v-icon :class="item.color" class="d-inline">
							{{ item.icon }}
						</v-icon>
					</v-list-item-icon>
					<v-list-item-content>
						<router-link :to="item.path">
							<v-list-item-title v-text="item.text" class="link">
							</v-list-item-title>
						</router-link>
					</v-list-item-content>
				</v-list-item>
			</v-list-item-group>
		</v-list>
	</v-card>
</template>

<script>
	export default {
		name: "floatingMenu",
		data() {
			return {
				menu: false,
				items: [
					{
						text: "Home",
						icon: "fas fa-home",
						color: "biru",
						path: "/",
					},
					{
						text: "About",
						icon: "fas fa-rocket",
						color: "hijau",
						path: "/About",
					},
				],
			};
		},
	};
</script>

<style scoped>
	a {
		text-decoration: none !important;
		color: #2c3e50 !important;
	}
	a:focus,
	a:hover {
		color: dodgerblue !important;
	}
	.biru {
		background: rgb(30, 57, 255);
		background: linear-gradient(
			90deg,
			rgba(30, 57, 255, 1) 0%,
			rgba(0, 212, 255, 1) 100%
		);
		color: transparent !important;
		background-clip: text !important;
	}
	.hijau {
		background: rgba(0, 218, 98, 1);
		background: linear-gradient(
			90deg,
			rgba(0, 218, 98, 1) 0%,
			rgba(113, 252, 255, 1) 100%
		);
		background-clip: text !important;
		color: transparent !important;
	}
	.mn {
		border-radius: 15px !important;
	}
</style>
