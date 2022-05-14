<template>
  <ul class="cards">
    <li v-for="(task, index) in tasks" :key="index">
      <h1 class="titulo">{{ task.subject }}</h1>
      <p>{{ task.description }}</p>
      <div class="btns">
        <button class="editar" @click="edit(index)">Editar</button>
        <!-- Button trigger modal -->
        <button
          type="button"
          class="excluir"
          data-bs-toggle="modal"
          data-bs-target="#exampleModal"
          @click="excluir(task, index)"
        >
          Excluir
        </button>

        <!-- Modal -->
        <div
          ref="modalDele"
          class="modal fade"
          id="exampleModal"
          tabindex="-1"
          aria-labelledby="exampleModalLabel"
          aria-hidden="true"
        >
          <div class="modal-dialog">
            <div class="modal-content">
              <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">
                  Tem certeza que deseja remover essa tarefa ?
                </h5>
                <button
                  type="button"
                  class="btn-close"
                  data-bs-dismiss="modal"
                  aria-label="Close"
                ></button>
              </div>
              <div 
              class="modal-body">
              Ao clicar em Excluir, a opeção não poderá ser revertida.{{taskSelected.subject}}
              </div>
              <div class="modal-footer">
                <button
                  type="button"
                  class="btn btn-secondary"
                  data-bs-dismiss="modal"
                >
                  Cancelar
                </button>
                <button type="button" 
                class="btn btn-secondary color-btn" 
                data-bs-dismiss="modal" 
                @click="comfirDelete(task, index)">
                  Excluir
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </li>
  </ul>
</template>
<script>
export default {
  name: "List",
  data() {
    return {
      tasks: [],
      taskSelected: [],
    };
  },
  methods: {
    edit(index) {
      this.$router.push({ name: "form", params: { index } });
    },

    excluir(task, index){
      this.taskSelected = task;
      this.taskSelected.index = index;
    },

    comfirDelete(){
      this.tasks.splice(this.taskSelected.index, 1);
      localStorage.setItem("tasks", JSON.stringify(this.tasks));

    }
  },
  created() {
    this.tasks = localStorage.getItem("tasks")
      ? JSON.parse(localStorage.getItem("tasks"))
      : [];
  },
};
</script>

<style scoped>
.cards {
  width: 75%;
  margin: 0 auto;
  margin-top: 2em;
  padding: 12px;
}
.color-btn{
  background: rgb(236, 29, 29) !important;
  color: white;
  font-weight: bold;
  border: solid 1px #ccc;
}
ul {
  list-style: none;
}
li {
  border: solid 1px #ccc;
  margin-top: 2em;
  padding: 1.5em;
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

.excluir {
  background: rgb(245, 118, 118);
}
.excluir:hover {
  background: rgb(245, 44, 44);
}
.editar:hover {
  background: #ccc;
}
</style>
