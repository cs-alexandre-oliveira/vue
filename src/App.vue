<template>
  <div>
    <h1>{{ titulo }}</h1>
    <img v-bind:src="foto.url" :alt="foto.titulo">
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
      foto: {
        url: 'https://thumb.lovemondays.com.br/image/096106d41e8d443e964f45fae4a30cb7/logos/93e6a6/concrete-solutions.gif',
        titulo: 'Concrete Soluction'
      }

    }
  }
}
</script>

<style>

</style>
