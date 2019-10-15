<template>
  <div class="content">
    <div class="title">
      <h1>REGISTRO</h1>
    </div>
    <div class="form-data">
      <input ref="firstNameField" type="text" placeholder="Nombre">
      <input ref="lastNameField" type="text" placeholder="Apellido">
      <input ref="usernameField" type="text" placeholder="Nombre de usuario">
      <input ref="passwordField" type="password" placeholder="Contraseña">
    </div>
    <div class="buttons">
      <button v-on:click="sendRest">Crear con REST</button>
      <button v-on:click="sendGraphQl">Crear con GraphQL</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import { gql } from "apollo-boost";

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted(){
    console.log("Hello world!");
     },
  methods:{
    sendRest: function (params) {
      console.log("Rest");
      let url = "http://localhost:4000/sa-auth-ms/resources/users/";
      //firstName, lastName, username, password 3308 /users
      let firstName = this.$refs.firstNameField.value;
      let lastName = this.$refs.lastNameField.value;
      let username = this.$refs.usernameField.value;
      let password = this.$refs.passwordField.value;
      console.log(firstName,lastName,username,password);
  
      axios.post(url,{firstName: firstName,lastName: lastName,username:username,password:password })
      .then(Response =>{
        alert("Usuario creado satisfactoriamente desde Microservicio: "+Response+"");
      })
      .catch(e =>{

      });
      
    },
    sendGraphQl: function (params){
      console.log("Ql");
      let url = "http://localhost:5000/graphiql";
      let firstName = this.$refs.firstNameField.value;
      let lastName = this.$refs.lastNameField.value;
      let username = this.$refs.usernameField.value;
      let password = this.$refs.passwordField.value;
      let user = {
        firstName: firstName,
        lastName: lastName,
        username: username,
        password: password
      };
     //mutation
       async  () => {
      // Call to the graphql mutation
      const result = await this.$apollo.mutate({
        // Query
        mutation: gql`mutation {
          createUser(user:$user)}`,
        // Parameters
        variables: {
          user: this.user,
        },
      }).then(Response => {
        alert("Usuario creado satisfactoriamente desde Microservicio: "+Response+"");
      }); 
      }
    
    }
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
