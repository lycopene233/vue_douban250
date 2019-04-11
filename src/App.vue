<template>
  <div id="app">
    <h1 class="title" v-text="title"></h1>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      title: '豆瓣电影250'
    }
  }
}
</script>

<style scoped>
.title {
  background-color: #edf4ec;
  color: #2e963d;
  font-size: 1.2rem;
  line-height: 2.5;
  margin: 0;
}
</style>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-size: 16px;
}
body {
  margin: 0;
}
p, ul {
  margin: 0;
  padding: 0;
}
a {
  text-decoration: none;
}
</style>
