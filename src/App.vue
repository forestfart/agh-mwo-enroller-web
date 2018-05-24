<template>
  <div id="app">
    <h1>Witaj w systemie zapisów na zajęcia</h1>
      <div v-if="!authenticatedEmail">
        <login-form @login="logMeIn($event)" :button-label=buttonLabelToDisplay></login-form>
      </div>
      <div id="app-status" v-else>
        <app-status @login="logOut($event)" :username=authenticatedEmail :button-label=buttonLabelToDisplay></app-status>
        <meetings-page :username="authenticatedEmail"></meetings-page>
      </div>
  </div>
</template>


<script>
import "milligram";
import LoginForm from "./LoginForm";
import AppStatus from "./AppStatus";
import MeetingsPage from "./meetings/MeetingsPage";

export default {
  name: 'app',
  components: {LoginForm, AppStatus, MeetingsPage},
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
  margin-left: 100px;
  margin-right: 100px;
}

#app-status {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}

#warning {
  color: #ff0000;
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
