<template>
  <div>
    <h1 class="centralizado">{{ titulo }}</h1>
    
    <input type="search" class="filtro" v-on:input="filtro = $event.target.value" placeholder="Encontre sua imagem por título!">
    {{ filtro }}
    <ul class="lista-fotos" v-for="foto of imagensComfiltro">
      <li class="lista-fotos-item">
        <meu-painel :titulo="foto.titulo">
          <imagem-responsiva :url="foto.url" :titulo="foto.titulo"/>
          <meu-botao tipo="button" rotulo="Remover" @botaoAtivado="remove(foto)" :confirmacao="true" estilo="padrao"></meu-botao>
          </imagem-responsiva>
        </meu-painel>  
      </li>
    </ul>
    
    <form>
      <select>
        <option value="QA">QA</option>
        <option value="JavaScript">JavaScript</option>
      </select>
      <br><br>
      <select>
        <option value="talks">Talks</option>
        <option value="onboarding">Onboarding</option>
      </select>
      <br><br>
      Assunto:<br>
      <input type=""/>
      <br><br>
      Descrição:<br>
      <textarea name="descricao" >
      </textarea>
      <br>
      <button type="button" onclick="alert('Clickaduh!!!')">Incluir</button>
    </form>
  </div>
</template>

<script>
import Painel from '../shared/painel/Painel.vue';
import ImagemResponsiva from '../shared/imagem-responsiva/ImagemResponsiva.vue';
import Botao from '../shared/botao/Botao.vue';

export default { 
  
  components: {
    'meu-painel' : Painel,
    'imagem-responsiva' : ImagemResponsiva,
    'meu-botao' : Botao
  },
  data() {

    return {
      titulo: 'Onboard Cadastro',
      images: [],
      filtro: ''
    }
  },
  computed: {
    imagensComfiltro() {
      if(this.filtro) {
        let exp = new RegExp(this.filtro.trim(), 'i');
        return this.images.filter(foto => exp.test(foto.titulo));
      } else {
        return this.images;
      }
    } 
  },
  methods: {
    remove(foto) {
        alert('Remover a foto! ' + foto.titulo);
    }
  },
  created() {
    let promise = this.$http.get('http://localhost:3000/v1/fotos');
    promise
      .then(res => res.json())
      .then(fotos => this.images = fotos, err => console.log(err));
  }
}
</script>

<style>
  .centralizado {
    text-align: center;
  }
  .lista-fotos {
    list-style: none;
  }
  .lista-fotos, .lista-fotos-item {
    display: inline-block;
  }
  .filtro {
    display: block;
    width: 100%;
  }
</style>
