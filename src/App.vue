<template>
  <div id="app">
    <h1>Witaj w systemie zapisów na zajęcia</h1>
      <div v-if="!authenticatedEmail">
        <login-form @login="logMeIn($event)"></login-form>
      </div>
      <div v-else>
        Witaj {{ authenticatedEmail }}<button @click="logOut()">Wyloguj</button>
    </div>
  </div>
</template>


<script>
import "milligram";
import LoginForm from "./LoginForm";

export default {
  name: 'app',
  components: {LoginForm},
  data () {
    return {
      email: '',
      authenticatedEmail: ''
    }
  },
  methods: {
    logMeIn(email) {
      this.authenticatedEmail = email;
    },
    logOut(){
      this.authenticatedEmail = '';
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
