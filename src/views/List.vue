<template>
  <div class="card">
    <h1 class="titulo">Titulo</h1>
    <p>descrição</p>
    <div class="btns">
      <button class="editar">Editar</button>
      <button class="excluir">Excluir</button>
    </div>
  </div>
</template>
<script>
export default {};
</script>

<style scoped>
.card {
  width: 75%;
  margin: 0 auto;
  margin-top: 2em;
  padding: 12px;
}

.editar,
.excluir {
  width: 5em;
  margin-left: 1em;
  border: solid 1px;
  background: white;
  font-weight: bold;
  transition: linear 0.1s;
}

.excluir{
  background: rgb(245, 118, 118);
}
.excluir:hover{
  background: rgb(245, 44, 44);
}
.editar:hover{
  background: #ccc;
}
</style>
