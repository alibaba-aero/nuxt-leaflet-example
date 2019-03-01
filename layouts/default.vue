<template>
  <div class="main">
    <aside class="sidebar">
      <nuxt-link to="/" exact="">
        My Location
      </nuxt-link>
      <nuxt-link to="/draw">
        Draw
      </nuxt-link>
    </aside>

    <nuxt />
  </div>
</template>

<style>
body, html, .main {
  width: 100vw;
  height: 100vh;
  margin: 0;
  display: flex;
  align-items: stretch;
}

.container, .map {
  display: flex;
  flex: 1;
}

.sidebar {
  display: flex;
  flex-direction: column;
  padding: .7em;
  z-index: 999;
  box-shadow: 5px 0 20px 0px #666;
}

.sidebar a {
  text-decoration: none;
  color: white;
  background: grey;
  border-radius: 2em;
  text-align: center;
  margin: .3em 0;
  padding: .3em .6em;
}

.sidebar a.nuxt-link-active {
  background: cadetblue;
}
</style>
