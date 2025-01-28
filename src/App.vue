<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <RouterLink to="/books">Books</RouterLink>
    </nav>
  </header>

  <RouterView />

  <footer>
    <h3>bookKeeper</h3>
  </footer>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300..700&display=swap');
* {
  font-family: 'Space Grotesk', sans-serif;
}

a {
  text-decoration: none;
  color: darkslategray;
}

header {
  width: 100%;
}

nav {
  height: 60px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 10px;
  background-color: darkkhaki;
  border-radius: 5px;
  font-size: 25px;
  font-weight: bold;
}

footer {
  position: relative;
  width: 100%;
  height: 20px;
  padding: 10px;
  border-radius: 5px;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: darkslategray;
  font-size: 20px;
  font-weight: bold;
}
</style>
