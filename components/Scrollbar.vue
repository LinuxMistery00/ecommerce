<template>
    <div>
      <div class="scrollbar">
        <NuxtLogoMini></NuxtLogoMini>
        <h1 class="Title">Nuxt E-Commerce</h1>
        <div class="Options">
            <NuxtLink to="/"><h1 class="OptionsTitle">Back</h1></NuxtLink>
            <h1 class="OptionsTitle">View Products</h1>
        </div>
      </div>
    </div>
</template>

<script>
import NuxtLogoMini from './NuxtLogoMini.vue';

export default {
    components: { 
        NuxtLogoMini 
    }
}
</script>
  
<style scoped>
.scrollbar {
    display: flex;
    background-color: #111213;
    width: auto;
    height: 8vh;
    justify-content: space-between;
}

.Options {
    display: flex;
    gap: 2vh;
    margin-top: 3vh;
    font-size: 3vh;
}


.OptionsTitle {
    color: #f1f2f3;
}

.OptionsTitle {
  color: #f1f2f3;
  position: relative;
  text-decoration: none;
}

.OptionsTitle::before {
  content: '';
  position: absolute;
  width: 100%;
  height: 4px;
  border-radius: 4px;
  background-color: #111213;
  bottom: 0;
  left: 0;
  transform-origin: right;
  transform: scaleX(0);
  transition: transform .3s ease-in-out;
}

.OptionsTitle:hover::before {
  transform-origin: left;
  transform: scaleX(1);
}

.Title {
    color: #f1f2f3;
    font-size: 5vh;
}
</style>
  