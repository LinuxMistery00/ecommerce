<template>
  <div>
    <Scrollbar></Scrollbar>
    <div class="FilterContainer">
      <div class="FinalPrice">Preço Total: R$ {{ finalPrice.toFixed(2) }}</div>
      <label class="Filter" for="category">Filtrar por Categoria:</label>
      <select class="Filter" v-model="selectedCategory" id="category">
        <option value="">Todas as categorias</option>
        <option v-for="category in uniqueCategories" :key="category">{{ category }}</option>
      </select>
      <NuxtLink to="/final"><button class="FinalBTN">Finalize Purchase</button></NuxtLink>
    </div>
    <div class="Products">
      <ul class="ProductList">
        <li class="Product" v-for="product in filteredProducts" :key="product.id">
          <div class="Card">
            <img :src="product.image" alt="Product Image" width="100" height="100">
            <h1 class="Title">{{ product.title }}</h1>
            <p class="Price">Preço: R$ {{ product.price.toFixed(2) }}</p>
            <button @click="buyProduct(product)" class="BuyBTN">Buy</button>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
  .FinalBTN {
    width: 20vh;
    height: 3vh;
    background-color: #212223;
    color: #f1f2f3;
    border-radius: 1.5vh;
  }

  .FinalBTN:hover {
    background-color: #d1d2d3;
    color: #212223;
  }

  .FilterContainer {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .Title {
    font-size: 3vh;
    text-align: center;
  }

  .BuyBTN {
    background-color: #212223;
    color: #f1f2f3;
    border-radius: 1.5vh;
    width: 5vh;
    height: 2vh;
  }

  .BuyBTN:hover {
    background-color: #d1d2d3;
    color: #212223;
  }

  img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 20vh;
  }

  .Price {
    text-align: center;
  }

  .Card {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 50vh;
    height: 30vh;
  }

  .Products {
    display: flex;
    justify-content: center;
  }

  .ProductList {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    row-gap: 45vh;
  }

  .Product {
    flex: 1;
    margin: 0 1vh;
  }

  .FinalPrice {
    text-align: center;
    font-size: 2vh;
    margin-top: 5vh;
  }
</style>

<script>
import axios from 'axios';
import Scrollbar from '~/components/scrollbar.vue';

export default {
  components: {
    Scrollbar,
  },
  data() {
    return {
      products: [],
      selectedCategory: '',
      finalPrice: 0, // Variável para armazenar o preço final
    };
  },
  computed: {
    uniqueCategories() {
      const categories = new Set();
      this.products.forEach(product => {
        categories.add(product.category);
      });
      return Array.from(categories);
    },
    filteredProducts() {
      if (this.selectedCategory === '') {
        return this.products;
      }
      return this.products.filter(product => product.category === this.selectedCategory);
    },
  },
  methods: {
    buyProduct(product) {
      this.finalPrice += product.price; // Adiciona o preço do produto ao preço final
      console.log('Preço Total: R$ ' + this.finalPrice);
    },
  },
  created() {
    axios.get('https://fakestoreapi.com/products')
      .then(response => {
        this.products = response.data;
      })
      .catch(error => {
        console.error('Erro ao buscar produtos:', error);
      });
  },
};
</script>
