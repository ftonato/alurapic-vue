<template>
  <div>
    <h1 class="text-center">{{ titulo }}</h1>

    <input v-on:input="filtro = $event.target.value" type="search" class="filter" placeholder="filtre pelo título da foto">

    <ul class="list-images">
      <li class="list-images-item" v-for="foto of fotosComFiltro">
        <meu-painel :titulo="foto.titulo">
          <imagem-responsiva :url="foto.url" :titulo="foto.titulo"/>
        </meu-painel>
      </li>
      </li>
    </ul>
  </div>
</template>

<script>
import Painel from '../shared/painel/Painel.vue';
import ImagemResponsiva from '../shared/imagem-responsiva/ImagemResponsiva.vue';

export default {
  components: {
    'meu-painel': Painel,
    'imagem-responsiva': ImagemResponsiva,
  },
  name: 'app',
  data () {
    return {
      titulo: 'Alurapic - Vue',
      fotos: [],
      filtro: ''
    }
  },
  computed: {
    fotosComFiltro() {
      if (this.filtro) {
        let exp = new RegExp(this.filtro.trim(), 'i');
        return this.fotos.filter(foto => exp.test(foto.titulo));
      } else {
        // se o campo estiver vazio, não filtramos, retornamos a lista
        return this.fotos;
      }
    }
  },
  created () {
    this.$http.get('http://localhost:3000/v1/fotos')
      .then(res => res.json())
      .then(fotos => this.fotos = fotos, err => console.log(err));
  }
}
</script>

<style>
.text-center {
  text-align: center;
}

.list-images {
  list-style: none;
}

.list-images .list-images-item {
  display: inline-block;
}

.filter {
  display: block;
  width: 100%;
}
</style>
