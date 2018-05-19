<template>
  <div id="app">
    <h1>Twoj e-mail to {{ email }}</h1>
    <input type="email" v-model="email">
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'test@gmail.com'
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
