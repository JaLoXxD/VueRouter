<template>
	<button id="buttonApi" @click="consumirApi"><span>Consumir API</span></button>
	<div id="padre">
		<div v-for="(post, i) in posts" :key="i" id="contenedor">
			<div id="photo">
				<h3 id="titPost"
					>Post hecho por: Usuario <span>{{ post.id }}</span></h3
				>
				<img id="userPh" src="../assets/men.png" alt="" />
			</div>
			<div id="contenido">
				<div id="tit">
					<router-link :to="`/blog/${post.id}`"><Titulo id="tit" :texto="post.title"/></router-link>
				</div>
				<div id="post">
					<PostBlog :texto="post.body" />
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	import Titulo from "../components/Titulo";
	import PostBlog from "../components/PostBlog";

	export default {
		name: "Blog",
		created() {
			this.consumirApi();
		},
		components: {
			Titulo,
			PostBlog,
		},
		data() {
			return {
				titulo: "Entrada de blog",
				posts: [],
			};
		},
		methods: {
			async consumirApi() {
				try {
					const data = await fetch("https://jsonplaceholder.typicode.com/posts");
					const array = await data.json();
					this.posts = array;
				} catch (error) {
					console.log(error);
				}
			},
		},
	};
</script>

<style scoped>
	#padre {
		display: flex;
		justify-content: center;
		flex-wrap: wrap;
		align-items: center;
	}
	#contenedor {
		display: flex;
		justify-content: center;
		flex-wrap: wrap;
		flex-direction: row;
		width: 30vw;
		height: 60vh;
		margin: 0 auto;
		border-radius: 15px;
		margin-top: 30px;
		background: #f3efdb;
	}
	#titPost {
		padding: 0px;
	}
	#photo {
		width: 100%;
		height: 35%;
		border-radius: 15px 15px 20% 20%;
		display: flex;
		justify-content: center;
		flex-direction: column;
		background-color: #40b883;
		box-shadow: 10px 10px 42px 0 rgba(36, 35, 35, 0.75);
	}
	#userPh {
		width: 100px;
		height: 100px;
		margin: 5px;
		margin: 0 auto;
	}
	#contenido {
		display: flex;
		width: 100%;
		height: 100%;
		flex-direction: column;
		justify-content: center;
	}
	#tit {
		margin-top: 20px;
		height: 20%;
		font-size: 25px;
		color: #40b883;
		align-content: center;
	}
	#post {
		margin-top: 10px;
		height: 80%;
	}
	#buttonApi {
		border-radius: 4px;
		background-color: #40b883;
		border: none;
		color: #ffffff;
		text-align: center;
		font-size: 20px;
		padding: 5px;
		transition: all 0.5s;
		cursor: pointer;
		margin: 5px;
		width: 170px;
		margin: 0 auto;
		margin-bottom: 5px;
	}

	#buttonApi span {
		cursor: pointer;
		display: inline-block;
		position: relative;
		transition: 0.5s;
	}

	#buttonApi span:after {
		content: "\00bb";
		position: absolute;
		opacity: 0;
		top: 0;
		right: -20px;
		transition: 0.5s;
	}

	#buttonApi:hover span {
		padding-right: 25px;
	}

	#buttonApi:hover span:after {
		opacity: 1;
		right: 0;
	}
	a {
		color: #40b883;
	}
	/* PORTRAIT RESPONSIVE DESIGN */
	@media screen and (min-width: 300px) and (max-width: 374px) and (orientation: portrait) {
		#contenedor {
			width: 85vw;
			height: 75vh;
		}
		#tit {
			font-size: 16px;
		}
		#post {
			font-size: 13px;
		}
		#contenido {
			margin: 10px;
		}
		#titPost {
			font-size: 18px;
		}
		#userPh {
			width: 70px;
			height: 70px;
		}
	}
	@media screen and (min-width: 375px) and (max-width: 500px) and (orientation: portrait) {
		#padre {
			width: 95vw;
		}
		#photo {
			border-right: 0px;
			border-bottom: 6px solid #40b883;
			margin: 0 auto;
			border-right: 0px;
			height: 25vh;
		}
		#contenido {
			width: 70vw;
			height: 75vh;
		}
		#contenedor {
			margin-bottom: 10px;
			width: 80vw;
			height: 75vh;
		}
		#tit {
			font-size: 22px;
		}
		#post {
			margin-top: 20px;
			font-size: 15px;
		}
	}
	@media screen and (min-width: 501px) and (max-width: 700px) and (orientation: portrait) {
		#contenedor {
			width: 60vw;
			height: 75vh;
		}
		#tit {
			font-size: 20px;
		}
		#post {
			font-size: 15px;
		}
		#contenido {
			margin: 10px;
		}
	}
	@media screen and (min-width: 701px) and (max-width: 1023px) and (orientation: portrait) {
		#contenedor {
			width: 40vw;
		}
		#contenido {
			margin: 10px;
		}
		#tit {
			font-size: 20px;
		}
		#post {
			margin-top: 17px;
			font-size: 15px;
			margin: 5px;
		}
	}
	@media screen and (min-width: 1024px) and (max-width: 1200px) and (orientation: portrait) {
		#contenedor {
			width: 30vw;
			height: 38vh;
		}
		#contenido {
			margin: 10px;
		}
		#tit {
			font-size: 20px;
		}
		#post {
			margin-top: 17px;
			font-size: 15px;
			margin: 5px;
		}
	}
	/* LANDSCAPE RESPONSIVE DESIGN */
	@media screen and (min-width: 0px) and (max-width: 639px) and (orientation: landscape) {
		#contenedor {
			width: 40vw;
			height: 130vh;
		}
		#tit {
			font-size: 16px;
		}
		#post {
			margin-top: 17px;
			font-size: 13px;
			margin: 5px;
		}
		#titPost {
			font-size: 16px;
		}
		#userPh {
			width: 50px;
			height: 50px;
		}
	}
	@media screen and (min-width: 640px) and (max-width: 850px) and (orientation: landscape) {
		#contenedor {
			width: 40vw;
			height: 120vh;
		}
		#tit {
			font-size: 18px;
		}
		#post {
			margin-top: 17px;
			font-size: 14px;
			margin: 5px;
		}
		#titPost {
			font-size: 18px;
		}
		#userPh {
			width: 70px;
			height: 70px;
		}
	}
	@media screen and (min-width: 851px) and (max-width: 1200px) and (orientation: landscape) {
		#contenedor {
			width: 40vw;
			height: 120vh;
		}
		#tit {
			font-size: 18px;
		}
		#post {
			margin-top: 17px;
			font-size: 14px;
			margin: 5px;
		}
		#titPost {
			font-size: 18px;
		}
		#userPh {
			width: 70px;
			height: 70px;
		}
	}
	@media screen and (min-width: 1201px) and (max-width: 1400px) and (orientation: landscape) {
		#contenedor {
			width: 40vw;
			height: 120vh;
		}
		#tit {
			font-size: 18px;
		}
		#post {
			margin-top: 17px;
			font-size: 14px;
			margin: 5px;
		}
		#titPost {
			font-size: 18px;
		}
		#userPh {
			width: 70px;
			height: 70px;
		}
	}
	@media screen and (min-width: 1401px) and (max-width: 1600px) and (orientation: landscape) {
		#contenedor {
			width: 40vw;
			height: 120vh;
		}
		#tit {
			font-size: 18px;
		}
		#post {
			margin-top: 17px;
			font-size: 14px;
			margin: 5px;
		}
		#titPost {
			font-size: 18px;
		}
		#userPh {
			width: 70px;
			height: 70px;
		}
	}
</style>
