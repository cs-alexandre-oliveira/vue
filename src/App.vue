<template>
  <div>
    <h1>{{ titulo }}</h1>
    
    <ul v-for="foto of images">
      <li><img v-bind:src="foto.url" :alt="foto.titulo"></li>
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


</style>
