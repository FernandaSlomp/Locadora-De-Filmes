<template>
  <b-container>
    <b-row>
      <h1>{{ title }}</h1>
    </b-row>
    <b-row>
      <p v-if="horas >= 9" id="aberta">ABERTA!</p>
      <p v-else-if="horas >= 17 && horas < 18">PRÓXIMA DE FECHAR</p>
      <p v-else id="fechada">FECHADA!</p>
    </b-row>
    <b-row>
      <HelloWorld msg="Escolha seu filme" />
    </b-row>

	<!-- <b-row>
		<ul>
			<li v-for="filme in filmes" :key="filme">
				{{ filme }}
			</li>
		</ul>
	</b-row> -->
	<!-- aprendendo a usar bootstrap vue -->

	<b-row>
		<div class="cards">
		<b-card v-bind:key="filme.id" v-for="filme in filmes"
		:title="filme.titulo"
		:img-src="filme.imagem"
		:img-alt="filme.titulo"
		img-top
		tag="article"
		style="max-width: 18rem;"
		class="mb-3 text-center"
		>
		<b-card-text>
			{{filme.descricao}}
		</b-card-text>

		<b-card-text>
			{{filme.valor | formatarPreco("RS")}}
		</b-card-text>

    <b-button href="#" variant="dark">ALUGAR</b-button>
  </b-card>
		</div>

	</b-row>
	
	<div>
  
	</div>



  </b-container>
</template>



<script>
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  data() {
    return {
    title: "Locadora de Filme",
	horas:new Date().getHours(),
	filmes: [
        { id: 1, titulo: "Hulk", descricao: "Filme Ruim", valor: 2, imagem: "https://i.imgur.com/0uthCmp.jpg" },
        { id: 2, titulo: "Homem de Ferro", descricao: "Homem de Ferro", valor: 10, imagem: "https://i.imgur.com/OA8pDFM.jpg" },
        { id: 3, titulo: "Thor", descricao: "Bonito ", valor: 20, imagem: "https://i.imgur.com/mt4ZRzw.jpg" },
        { id: 4, titulo: "Capitão América", descricao: "Um filme de capitão", valor: 40, imagem: "https://i.imgur.com/UFmSVtZ.jpg" },
        { id: 5, titulo: "Doutor Estranho", descricao: "Magia", valor: 10, imagem: "https://i.imgur.com/pVEDruM.jpg" },
        { id: 6, titulo: "Pantera Negra", descricao: "Um segundo filme de força", valor: 10, imagem: "https://i.imgur.com/JOSEGKf.jpg" }
      ]
	};
	
  },
  
};
</script>

<style>
.row {
  justify-content: center;
}
.cards {
	display:flex;
	flex-wrap: inherit;
	justify-content: space-around;
}
body {
	background-color: white;
	color: black;
}
.card {
	background-color: white;
	/* border: solid black; */
}
.card:hover {
	transform: scale(1.1);
}
#aberta {
	color: blue;
}
#proxima-fehcar {
	color: orange;
}
#fechada {
	color: red;
}

</style>
