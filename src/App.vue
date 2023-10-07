<script>
import axios from "axios";
import DrinksCard from "./components/DrinksCard.vue";
import Message from "./components/Message.vue";

export default {
  components: {
    Message,
    DrinksCard
  },
  data() {
    return {
      drinksData: [],
      drink: "",
      isLoading: false // Agrega la propiedad isLoading
    };
  },
  mounted() {
    this.searchDrink();
  },
  computed: {
    limitedDrinksData() {
      return this.drinksData.slice(0, 18);
    }
  },
  methods: {
    async searchDrink() {
      try {
        this.isLoading = true;
        console.log('Antes de la solicitud');
        const resp = await axios.get(`https://www.thecocktaildb.com/api/json/v1/1/search.php?s=${this.drink}`);
        console.log('Después de la solicitud');
        console.log('Datos de respuesta:', resp.data);
        this.drinksData = resp.data.drinks || [];
      } catch (err) {
        console.error(err);
      }
       finally {
        this.isLoading = false;
      }
    }
  }
};
</script>

<template>
  <div class="App">
    <div class="input-wrapper">
      <form class="form-input" @submit.prevent="searchDrink">
        <input type="text" class="input-search" placeholder="Buscar bebidas" v-model="drink" />
        <button class="btn">
          <img :src="'/coctel-icon.png'" class="btn-img" alt="Coctel" />
        </button>
      </form>
    </div>
    <div v-if="!isLoading">
      <DrinksCard v-if="limitedDrinksData.length >= 1" :data="limitedDrinksData" />
      <Message v-else />
    </div>
  </div>
</template>

<style>
  @import url('./App.css');
</style>