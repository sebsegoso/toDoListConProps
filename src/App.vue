<template>
  <div>
    <input v-model="tarea" type="text" autofocus @keyup.13="add" />
    <button @click="add">Agregar tarea</button>
    <Tarea
      v-for="(tarea, i) in tareas "
      :tarea="tarea"
      :indice="i"
      :key="i"
      @eliminar="eliminarTarea"
    ></Tarea>
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
    };
  },
  components: {
    Tarea,
  },
  methods: {
    add() {
      this.tareas.push(this.tarea);
      this.tarea = "";
    },
    eliminarTarea(indice) {
      this.tareas.splice(indice, 1);
    },
  },
};
</script>

<style lang="scss">

</style>