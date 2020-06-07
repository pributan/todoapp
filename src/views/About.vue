<template>
	<v-app>
		<v-content>
			<v-img class="img" :aspect-ratio="16 / 9" src="../assets/about.jpg">
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
			<v-container text-center>
				<v-card class="cardabout mx-auto rounded-card">
					<v-card-subtitle> Hello, it's me Kusuma </v-card-subtitle>
					<div class="gradient-border-wrap">
						<v-avatar size="80">
							<img
								src="https://avatars2.githubusercontent.com/u/47457477?s=460&u=9f6a825bfd49176a78cbb1a0cfa87669ad134b41&v=4"
								alt="Kusuma"
								class="profile"
							/>
						</v-avatar>
					</div>
					<v-card-text class="mt-5">
						<span v-for="(social, i) in socials" :key="i">
							<a :href="social.link">
								<v-icon size="28" :class="style">
									{{ social.icon }}
								</v-icon>
							</a>
						</span>
					</v-card-text>
				</v-card>
				<h3 class="mt-12 txtcolor">About Todo App</h3>
				<div class="mx-auto center my-5 txtcolor">
					<p>
						This app can do some basic stuff such as add, delete,
						and check the completed todo. But it's very good start
						to learn Vue by the way 😅. Currently this app is
						optimized for mobile view. If you found some code that
						is not normal, please don't hesitate to correct me.
						Thanks 😬.
					</p>
					<p>
						Features to add : Edit todo's details, Communicate with
						API, Note app. ☕️
					</p>
					<v-btn class="source my-5 pa-2" rounded>
						<a href="https://github.com/djykus/todoapp">
							<v-icon size="20" class="mr-2">
								{{ socials[1].icon }}
							</v-icon>
							Source Code
						</a>
					</v-btn>
				</div>
			</v-container>
		</v-content>
	</v-app>
</template>

<script>
	export default {
		data() {
			return {
				socials: [
					{
						link: "https://instagram.com/kusuma.jy",
						icon: "fab fa-instagram",
					},
					{
						link: "https://github.com/djykus",
						icon: "fab fa-github",
					},
					{
						link: "https://dribbble.com/djykus",
						icon: "fab fa-dribbble",
					},
				],
				style: "mx-3 warna d-inline pa-2",
			};
		},
	};
</script>

<style scoped>
	.cardabout {
		margin-top: -100px;
		max-width: 250px;
	}
	.img {
		max-height: 400px;
	}
	a {
		text-decoration: none !important;
	}
	.warna {
		background: rgb(125, 59, 255);
		background: linear-gradient(
			90deg,
			rgba(125, 59, 255, 1) 0%,
			rgba(74, 181, 255, 1) 100%
		) !important;
		color: transparent !important;
		background-clip: text !important;
	}
	.source {
		background: rgb(125, 59, 255);
		background: linear-gradient(
			90deg,
			rgba(125, 59, 255, 1) 0%,
			rgba(74, 181, 255, 1) 100%
		);
		text-transform: none !important;
	}
	.source a {
		color: white !important;
	}
	.rounded-card {
		border-radius: 15px !important;
	}
	.center {
		max-width: 1000px;
	}
	.txtcolor {
		color: #455169 !important;
	}

	.gradient-border-wrap {
		background: linear-gradient(
			to right bottom,
			yellow 0%,
			orange 20%,
			red 60%,
			purple 100%
		);
		padding: 3px;
		border-radius: 50px;
		max-width: 86px;
		margin: auto;
	}
	.profile {
		background-color: white;
		padding: 5px;
	}
</style>
