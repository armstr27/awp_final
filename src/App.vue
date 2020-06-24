<template>
  <div id="app">
<!--    <div id="nav">-->
<!--      <router-link to="/">Select Grammar Points</router-link>-->
<!--      <router-link to="/practice">Practice Writing</router-link>-->
<!--    </div>-->
    <router-view/>
  </div>
</template>

<script>
  export default {
    
  }
</script>

<style>
body {
    background-color: #C0B7B1;
    background-repeat: repeat-y;
    background-size: 100%;
    background-attachment: fixed;
    background-image: url('./data/background.webp');
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  display: inline-block;
  border: none;
  background: #555555;
  color: white;
  padding: inherit;
  cursor: pointer;
}
</style>
