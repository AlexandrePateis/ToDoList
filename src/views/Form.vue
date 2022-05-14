<template>
  <div class="main">
    <form action="">
      <div class="task-title">
        <label for="subject" class="title-label">Titulo</label>
        <input
          type="text"
          autocomplete="off"
          placeholder="Ex: estudar"
          required
          class="form-control"
          v-model="form.subject"
        />
      </div>
      <div class="task-desc">
        <label for="" class="title-label">Descrição</label>
        <textarea
          type="text"
          class="form-control"
          aria-label="With textarea"
          placeholder="Ex: eu preciso estudar"
          id="desciption"
          required
          autocomplete="off"
          v-model="form.description"
        >
        </textarea>
        <input class="btn btn-primary" type="submit" value="Salvar" @click="saveTask"/>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "Form",

  data() {
    return {
      form: {
        subject: "",
        description: "",
      },
      methodSave: 'new'
    };
  },
  methods:{
    saveTask(){
      if(this.methodSave == "update"){
        let tasks = JSON.parse(localStorage.getItem("tasks"));
        tasks[this.$route.params.index] = this.form;
        localStorage.setItem("tasks", JSON.stringify(tasks))
        this.$router.push({name: "list"})
        return;
      }
      var tasks = (localStorage.getItem("tasks")) ? JSON.parse(localStorage.getItem("tasks")) : [];
      tasks.push(this.form)
      localStorage.setItem("tasks", JSON.stringify(tasks))
      this.$router.push({name: "list"})
    }
  },
  created(){
    if(this.$route.params.index === 0 || this.$route.params.index !== undefined){
      this.methodSave = "update";
      let tasks = JSON.parse(localStorage.getItem("tasks"));
      this.form = tasks[this.$route.params.index];
    }
  }
};
</script>

<style>
.main {
  width: 75%;
  margin: 0 auto;
  margin-top: 2em;
  height: 13em;
}
.task-title,
.task-desc {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.task-desc {
  margin-top: 2em;
}
#desciption {
  height: 5em;
}
.btn-primary {
  margin-top: 1em;
  width: 5em;
}
.title-label {
  font-size: 1.2em;
  font-weight: bold;
}
</style>
