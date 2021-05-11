<template>
	<Titulo :texto="header" />
	<div id="padre">
		<div id="right">
			<img class="shadow image" src="../assets/men.png" alt="user" />
			<h1 class="tit shadow"> Autor: Usuario {{ articulo.id }}</h1>
		</div>
		<div id="article">
			<Titulo class="tit shadow" :texto="titulo" />
			<h3>{{ articulo.body }}</h3>
		</div>
	</div>
</template>

<script>
	import Titulo from "../components/Titulo";
	export default {
		name: "Articulo",
		created() {
			this.consumirApi();
		},
		components: {
			Titulo,
		},
		data() {
			return {
				header: `Artículo N°${this.$route.params.id} del blog`,
				articulo: {},
				titulo: "",
			};
		},
		methods: {
			async consumirApi() {
				try {
					const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`);
					const dataJson = await data.json();
					this.articulo = dataJson;
					this.titulo = this.articulo.title.toUpperCase();
					console.log(this.articulo);
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
		flex-direction: row;
		flex-wrap: wrap;
		width: 70vw;
		margin: 0 auto;
		border-radius: 80px;
		background-image: linear-gradient(135deg, #90f7ec 10%, #32ccbc 100%);
	}
	#right {
		padding: 20px;
		border-right: 8px solid #ffffff;
	}
	#article {
		text-align: center;
		padding-left: 40px;
		padding-right: 50px;
		width: 40vw;
	}
	.tit {
		color: #ffffff;
	}
	.shadow {
		-webkit-filter: drop-shadow(15px 15px 15px #222);
		filter: drop-shadow(15px 15px 15px #222);
	}
	/* PORTRAIT RESPONSIVE DESIGN */
	@media screen and (min-width: 0px) and (max-width: 374px) and (orientation: portrait) {
		#padre {
			width: 70vw;
			height: 70vh;
		}
		#right {
			padding: 20px;
			border-right: 0;
			border-bottom: 8px solid #ffffff;
			width: 100%;
			height: 20vh;
		}
		#article {
			padding-bottom: 10px;
			width: 100%;
			height: 55vh;
			padding-left: 10px;
			padding-right: 10px;
		}
		.image {
			width: 80px;
			height: 80px;
		}
		.tit {
			font-size: 15px;
		}
		h3 {
			font-size: 12px;
		}
	}
	@media screen and (min-width: 375px) and (max-width: 700px) and (orientation: portrait) {
		#padre {
			width: 70vw;
			height: 70vh;
		}
		#right {
			padding: 20px;
			border-right: 0;
			border-bottom: 8px solid #ffffff;
			width: 100%;
			height: 20vh;
		}
		#article {
			width: 100%;
			height: 80vh;
			padding: 10px;
		}
		.image {
			width: 100px;
			height: 100px;
		}
		.tit {
			font-size: 18px;
		}
		h3 {
			font-size: 14px;
		}
	}
	@media screen and (min-width: 701px) and (max-width: 1023px) and (orientation: portrait) {
		#padre {
			width: 70vw;
			height: 70vh;
		}
		#right {
			padding: 20px;
			border-right: 0;
			border-bottom: 8px solid #ffffff;
			width: 100%;
			height: 20vh;
		}
		#article {
			width: 100%;
			height: 80vh;
			padding: 10px;
		}
		.image {
			width: 120px;
			height: 120px;
		}
		.tit {
			font-size: 25px;
		}
		h3 {
			font-size: 20px;
		}
	}
	@media screen and (min-width: 1024px) and (max-width: 1200px) and (orientation: portrait) {
		#padre {
			width: 60vw;
			height: 70vh;
		}
		#right {
			padding: 20px;
			border-right: 0;
			border-bottom: 8px solid #ffffff;
			width: 100%;
			height: 20vh;
		}
		#article {
			width: 100%;
			height: 80vh;
			padding: 10px;
		}
		.image {
			width: 200px;
			height: 200px;
		}
		.tit {
			font-size: 30px;
		}
		h3 {
			font-size: 27px;
		}
	}
	@media screen and (min-width: 977px) and (max-width: 1459px){
		#padre {
			width: 60vw;
			height: 80vh;
		}
		#right {
			padding: 20px;
			border-right: 0;
			border-bottom: 8px solid #ffffff;
			width: 100%;
			height: 30vh;
		}
		#article {
			width: 100%;
			height: 70vh;
			padding: 10px;
		}
		.image {
			width: 200px;
			height: 200px;
		}
		.tit {
			font-size: 30px;
		}
		h3 {
			font-size: 27px;
		}
	}
	/* LANDSCAPE RESPONSIVE DESIGN */
	@media screen and (min-width: 0px) and (max-width: 639px) and (orientation: landscape) {
		#padre {
			width: 90vw;
			height: 60vh;
		}
		#right {
			padding: 20px;
			width: 15%;
			height: 100%;
		}
		#article {
			width: 70%;
			height: 100%;
			padding: 10px;
		}
		.image {
			width: 80px;
			height: 80px;
		}
		.tit {
			font-size: 15px;
		}
		h3 {
			font-size: 12px;
		}
	}
	@media screen and (min-width: 640px) and (max-width: 850px) and (orientation: landscape) {
		#padre {
			width: 90vw;
			height: 50vh;
		}
		#right {
			padding: 20px;
			width: 15%;
			height: 100%;
		}
		#article {
			width: 70%;
			height: 100%;
			padding: 10px;
		}
		.image {
			width: 80px;
			height: 80px;
		}
		.tit {
			font-size: 15px;
		}
		h3 {
			font-size: 12px;
		}
	}
	@media screen and (min-width: 851px) and (max-width: 1200px) and (orientation: landscape) {
		#padre {
			width: 60vw;
			height: 30vh;
		}
		#right {
			padding: 0px;
			padding-left: 20px;
			padding-right: 20px;
			width: 15%;
			height: 100%;
			border-bottom: 0;
			border-right: 8px solid #ffffff;
		}
		#article {
			width: 70%;
			height: 100%;
			padding: 10px;
		}
		.image {
			width: 80px;
			height: 80px;
			padding-top: 20px;
		}
		.tit {
			font-size: 15px;
		}
		h3 {
			font-size: 12px;
		}
	}
	@media screen and (min-width: 1201px) and (max-width: 1400px) and (orientation: landscape) {
		#padre {
			width: 70vw;
			height: 25vh;
		}
		#right {
			padding: 0px;
			padding-left: 20px;
			padding-right: 20px;
			width: 15%;
			height: 100%;
			border-bottom: 0;
			border-right: 8px solid #ffffff;
		}
		#article {
			width: 70%;
			height: 100%;
			padding: 20px;
		}
		.image {
			width: 80px;
			height: 80px;
			padding-top: 30px;
		}
		.tit {
			font-size: 25px;
		}
		h3 {
			font-size: 18px;
		}
	}
</style>
