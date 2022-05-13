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
        v-model="subject"
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
        v-model="description"
        >
        </textarea>
        <input class="btn btn-primary" type="submit" value="Salvar">
      </div>
    </form>
  </div>
</template>

<script>
export default {
 name: "Form",

 data(){
   return{
     subject: "",
     desciption:""
   }
 }
}
</script>


<style>
.main{
  width: 75%;
  margin: 0 auto;
  margin-top: 2em;
  height: 13em;
}
.task-title, 
.task-desc{
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.task-desc{
  margin-top: 2em;
}
#desciption{
  height: 5em;
}
.btn-primary{
  margin-top: 1em;
  width: 5em;
}
.title-label{
  font-size: 1.2em;
  font-weight: bold;
}
</style>
