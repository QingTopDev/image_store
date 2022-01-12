<template>
  <div id="app">
    <div id="nav">
      <button><router-link to="/">Accueil</router-link></button>
      <button><router-link to="/videos">Nos vidéos</router-link></button>
      <button><router-link to="/contact">Contact</router-link></button>
    </div>
    <div class="router_part">
      <router-view />
    </div>
  </div>
</template>

<style lang="scss">
#app {
  font-family: Montserrat, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #ddd;
}

#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #ffffff;
    text-decoration: none;

    &.router-link-exact-active {
      color: #ffffff;
      font-size: 30px;
    }
  }
}

.tag {
  color: rgb(255, 255, 255);
  background: orange;
  padding: 10px 20px;
  margin: 5px 10px;
  max-width: 50%;
  margin-left: auto;
  margin-right: auto;
}

h1,
h2 {
  border-bottom: 1px solid #aaa;
}
</style>
