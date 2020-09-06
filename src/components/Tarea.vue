<template>
  <div>
    <li>
        <button @click="vaciar" class="eliminar">
          <i class="far fa-minus-square"></i>
        </button>
        {{tarea}}
    </li>
  </div>
</template>

<script>
export default {
  name: "Tarea",
  props: {
    tarea: String,
    indice: Number,
  },
  methods: {
    vaciar() {
      this.$emit("eliminar", this.indice);
    },
  },
};
</script>

<style lang="scss" scoped>
.eliminar {
  cursor: pointer;
  background-color: #ed5564;
  color: #fff;
  border-radius: 5px;
  border: 0;
  padding: 3px;
  transition: all 0.3s;
  width: 20px;
  height: 20px;
  &:hover {
    background-color: #d34855;
  }
  &:active {
    background-color: #f3f5f5;
  }
}

li{
    padding: 5px 0;
    list-style-type: none;
}
</style>