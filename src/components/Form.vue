<template>
  <div class="content">
    <div class="title">
      <h1>REGISTRO</h1>
    </div>
    <div class="form-data">
      <input type="text" placeholder="Nombre">
      <input type="text" placeholder="Apellido">
      <input type="text" placeholder="Nombre de usuario">
      <input type="text" placeholder="Contraseña">
    </div>
    <div class="buttons">
      <button>Crear con REST</button>
      <button>Crear con GraphQL</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.content {
  height: 100%;
  width: 100%;
  background-image: url('../assets/planets.svg');
  display: flex;
  justify-content: space-around;
  flex-direction: column;
  align-items: center;
}
.title {
  background-color: rgba(128, 0, 128, 0.8);
  padding: 5px 20px;
  border-radius: 25px;
}
.form-data {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  width: 40%;
  height: 25%;
}
input {
  border: none;
  border-radius: 25px;
  padding: 10px;
  min-width: 45%;
  font-size: 16px;
}
.buttons {
  display: flex;
  justify-content: space-between;
  width: 40%;
  max-width: 400px;
  height: 15%;
}
button {
  border-radius: 25px;
  padding: 10px;
  border: none;
  min-width: 170px;
  font-weight: bold;
  font-size: 16px;
  cursor: pointer;
  height: 50px;
}
</style>
