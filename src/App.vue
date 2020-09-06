<template>
  <div class="wrapper">
    <h1>To do list v2</h1>
    <div class="inputs">
      <input v-model="tarea" type="text" autofocus @keyup.13="add" />
      <button @click="add" class="agregar">
        <i class="far fa-plus-square"></i> Agregar tarea
      </button>
    </div>
    <p>{{mensajeVacío}}</p>
    <hr>
    <ul>
      <Tarea
        v-for="(tarea, i) in tareas "
        :tarea="tarea"
        :indice="i"
        :key="i"
        @eliminar="eliminarTarea"
      ></Tarea>
    </ul>
  </div>
</template>

<script>
import Tarea from "./components/Tarea";

export default {
  name: "toDoList",
  data() {
    return {
      tarea: "",
      tareas: [],
      mensajeVacío: "",
    };
  },
  components: {
    Tarea,
  },
  methods: {
    add() {
      if (this.tarea.trim() == "") {
        this.mensajeVacío = "Debes escribir una tarea para poder ingresarla";
      } else {
        this.tareas.push(this.tarea.trim());
        this.tarea = "";
        this.mensajeVacío = "";
      }
    },
    eliminarTarea(indice) {
      let confirmación = confirm("¿Desea eliminar esta tarea?");
      confirmación ? this.tareas.splice(indice, 1) : false;
    },
  },
};
</script>

<style lang="scss">
body {
  min-height: 100vh;
  background: linear-gradient(#eee , #ccc);
  font-family: Helvetica, sans-serif;
  .wrapper {
    margin: 0 auto;
    width: 60%;
  }
}
h1 {
  font-size: 24px;
  text-align: center;
}
p{
  margin: 3px;
}
.inputs {
  display: flex;
  justify-content: center;
  .agregar {
    cursor: pointer;
    color: #fff;
    border: 0;
    background-color: #42cb6f;
    padding: 3px;
    transition: all 0.3s;
    border-radius: 0 5px 5px 0;
    &:hover {
      background-color: #99d468;
    }
    &:active {
      background-color: #47cec0;
    }
  }
}
</style>