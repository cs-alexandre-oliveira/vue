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
      images: [
      {
        url: 'https://thumb.lovemondays.com.br/image/096106d41e8d443e964f45fae4a30cb7/logos/93e6a6/concrete-solutions.gif',
        titulo: 'Concrete Soluction'
      },
      {
        url: 'https://codesui.com/app/uploads/2016/12/vuejs-logo.png',
        titulo: 'Vue da Massa'
      }
      ]
    }
  }
}
</script>

<style>
img {
  width:100px;
  height:50px;
}

</style>
