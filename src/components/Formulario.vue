<template>
  <div class="formulario">
    <p><u>Crear Post</u></p>
    <input name="titulo" class="form-control" v-model="titulo" />
    <textarea
      name="contenido"
      class="form-control"
      v-model="contenido"
    ></textarea>
    <button @click="createPost">Crear</button>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      titulo: "",
      contenido: "",
    };
  },
  methods: {
    createPost() {
      axios
        .post("https://jsonplaceholder.typicode.com/posts", {
          title: this.titulo,
          body: this.contenido,
        })
        .then(() => {
          alert("Post creado");
          this.$store.dispatch("getData");
          this.titulo = "";
          this.contenido = "";
        });
    },
  },
};
</script>
<style>
p {
  font-weight: bold;
  font-size: 20px;
}
.formulario {
  width: 100%;
  max-width: 500px;
  display: block;
  margin: 50px auto;
  padding: 20px;
}
input,
textarea {
  width: 100%;
  padding: 5px;
  margin-bottom: 20px;
}

button {
  border: 2px solid #909e90;
}
.loader {
  margin-top: 6rem;
  font-size: 30px;
}
</style>