<script setup lang="ts">
</script>

<template>
  <nav>
    <router-link to="/">Home</router-link>
    <router-link to="/about">About</router-link>
  </nav>
  <router-view/>
</template>

<style>
body {
  background-color: #799c7d;
  color: #2d2a32;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  margin: auto;
}
nav {
  background-color: #2d2a32;
  font-size: large;
  font-weight: bold;
  display: flex;
  gap: 20px;
  align-items: start;
  justify-content: center;
  padding: 12px;
}
nav .router-link-active {
  border-bottom: 1px solid #799c7d;
  color: #eee;
  padding: 2px 4px;
}
nav a {
  text-decoration: none;
  color: #eee;
  padding: 2px 4px;
}
nav a:hover, nav a:active {
  color: #799c7d;
}
</style>
