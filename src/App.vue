<template>
  <div id="app">
    <div id="nav">
      <div id="brand">
        <router-link to="/">
          <img src="./assets/logo.png" />
        </router-link>
      </div>
      <div id="side">
        <router-link to="/transactions">Transactions</router-link>
        <router-link to="/budget">Budget</router-link>
      </div>
    </div>
    <router-view/>
  </div>
</template>

<style>

body {
  font-family: 'Lato', sans-serif;
  font-weight: 400;
  background-color: #f8f9fa;
  color: #484e61;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

#nav {
  display: flex;
  align-items: center;
  padding: 10px 40px;
}

#side {
  padding-right: 30px;
  padding-bottom: 10px;
}

#side a {
  text-decoration: none;
  font-size: 18px;
  color: #484e61;
  padding: 0px 20px;
}

#side a:hover {
  color: #e02800;
}

#brand {
  margin-right: auto;
}
</style>
