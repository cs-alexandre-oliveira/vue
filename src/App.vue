<template>
  <div class="corpo">
    <h1 class="centralizado">{{ titulo }}</h1>
    
    <ul class="lista-fotos" v-for="foto of images">
      <li class="lista-fotos-item">
        <div class="painel">
          <h2 class="painel-titulo">{{ foto.titulo }}</h2>
          <div class="painel-conteudo">
            <img class="imagem-responsiva" v-bind:src="foto.url" :alt="foto.titulo">
          </div>
        </div>
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
export default { 
  data() {

    return {
      titulo: 'Onboard Cadastro',
      images: []
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
  .corpo {
    font-family: Helvetica;
    width: 96%;
    margin: 0 auto;
  }
  .centralizado {
    text-align: center;
  }
  .lista-fotos {
    list-style: none;
  }
  .lista-fotos, .lista-fotos-item {
    display: inline-block;
  }
  .imagem-responsiva {
    width: 100%;
  }
  .painel {
    padding: 0 auto;
    border: solid 2px grey;
    display: inline-block;
    margin: 5px;
    box-shadow: 5px 5px 10px grey;
    width: 200px;
    height: 100%;
    vertical-align: top;
    text-align: center;
  }

  .painel .painel-titulo {
    text-align: center;
    border: solid 2px;
    background: lightgreen;
    margin: 0 0 15px 0;
    padding: 10px;
    text-transform: uppercase;
  }
</style>
