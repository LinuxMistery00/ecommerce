<template>
  <div class="Main">
    <NuxtLogo></NuxtLogo>
    <h1 class="Title">Nuxt E-Commerce</h1>
    <NuxtLink to="products"><button class="StartBuyBTN">Get Start</button></NuxtLink>
  </div>
</template>

<style scoped>
  .Main {
    display: flex;
    justify-content: center;
    flex-direction: column;
    gap: 1vh;
    align-items: center;
    margin-top: 30vh;
  }

  .Title {
    font-size: 5vh;
  }

  .StartBuyBTN {
    background-color: #212223;
    color: #f1f2f3;
    border-radius: 1.5vh;
    width: 30vh;
    height: 4.5vh;
  }

  .StartBuyBTN:hover {
    background-color: #d1d1d1;
    color: #212223;
  }
</style>

<style>
  * {
    margin: 0;
    padding: 0;
    transition: 0.4s;
    box-sizing: border-box;
    font-family: Arial, Helvetica, sans-serif;
  }

  body {
    color: #212223;
  }
</style>

<script lang="ts">
import Vue from 'vue'
import NuxtLogo from '~/components/NuxtLogo.vue';

export default Vue.extend({
    name: "IndexPage",
    components: { NuxtLogo }
})
</script>
