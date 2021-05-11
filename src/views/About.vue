<template>
	<div class="about">
		<Titulo :texto="titulo" />
	</div>
</template>

<script>
	import Titulo from "../components/Titulo";

	export default {
		name: "About",
		components: {
			Titulo,
		},
		data() {
			return {
				titulo: "Página about",
			};
		},
	};
</script>

<style></style>
