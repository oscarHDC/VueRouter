<script setup>
  import { RouterView, RouterLink } from 'vue-router';
</script>
<template>
  <main>
    <div class="links">
    <router-link active-class="active" to="/">Home</router-link>
    <router-link active-class="active" to="/about">About</router-link>
  </div>
    <RouterView />
  </main>
</template>

<style scoped>
  .links {
  padding: 20px
}
.links a{
  margin: 0 5px;
  text-decoration: none;
  color: grey;
}

.active{
  font-weight: bold;
  color: green !important;
}

</style>
