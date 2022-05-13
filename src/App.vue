<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-dark">
    <div class="container-fluid">
      <div class="collapse navbar-collapse" id="navbarNavDropdown">
        <ul class="navbar-nav">
          <li class="title">ToDo List</li>
          <li class="nav-item item-1">
            <router-link to="/list">Tarefas</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/form">Formulario</router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <router-view />
</template>

<style>
a {
  text-decoration: none;
  color: rgb(255, 255, 255) !important;
  margin-right: 2em;
  font-size: 1.4em;
  transition: linear 0.1s;
}
a:hover {
  color: #ccc !important;
}
.navbar-nav {
  align-items: center;
}
.item-1 {
  margin-left: 7em;
}
.navbar {
  height: 80px;
}
.title {
  font-family: "Arial", cursive;
  font-size: 1.5em;
  color: rgb(255, 255, 255);
  cursor: pointer;

  margin-left: 2em;
}
</style>
