<template>
  <div class="about">
    <h1>This is an about page</h1>
    <router-link :to="{ name: 'Home' }">Home</router-link> <br />
    <router-link :to="{ name: 'About' }">About</router-link>
  </div>
</template>
