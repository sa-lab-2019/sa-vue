<template>
  <div id="app">
    <Form/>
  </div>
</template>

<script>
import Form from './components/Form.vue';
import ApolloClient from 'apollo-boost';
import Vue from 'vue';
import VueApollo from 'vue-apollo';



const apolloClient = new ApolloClient({
  // You should use an absolute URL here
  uri: 'http://localhost:5000/graphiql'
});


Vue.use(VueApollo);

const apolloProvider = new VueApollo({
  defaultClient: apolloClient,
});

new Vue({
  el: '#app',
  // inject apolloProvider here like vue-router or vuex
  apolloProvider,
  render: h => h(this),
});



export default {
  name: 'app',
  components: {
    Form
  }
}
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  height: 100vh;
  background: linear-gradient(#636363, #000000);
}
</style>
