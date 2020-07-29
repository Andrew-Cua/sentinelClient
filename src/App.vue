<template>
  <div id="app">
    <div id="nav"><router-link to="/">Home</router-link></div>
    <router-view />
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: whitesmoke;
    margin: 10px;
    text-decoration: none;
  }

  border: #fff, 1px, solid;
  height: 5%;
  backdrop-filter: blur(20px);
  background-color: rgba(255, 255, 255, 0.1);
  box-shadow: 2px 3px 18px #333;
  border-radius: 50px;
  margin-top: 20px;
  align-self: center;
  align-content: center;
}

body {
  background: #0f2027;
  background: -webkit-linear-gradient(147deg, #2c5364, #203a43, #0f2027);
  background: linear-gradient(147deg, #2c5364, #203a43, #0f2027);
  background-attachment: fixed;
}
</style>
