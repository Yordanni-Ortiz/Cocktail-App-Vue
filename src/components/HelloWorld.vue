<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>














<script>
import axios from "axios";
import DrinksCard from "./components/DrinksCard.vue";
import Message from "./components/Message.vue";


export default {
  components: {
    Message, DrinksCard
  },
  data() {
    return {
      drinksData: [],
      drink: ""
    };
  },
   mounted() {
    this.searchDrink();
  },
  methods: {
    async searchDrink() {
      try {
        console.log('Antes de la solicitud');
        const resp = await axios.get(`https://www.thecocktaildb.com/api/json/v1/1/search.php?s=${this.drink}`);
        console.log('Después de la solicitud');
        console.log('Datos de respuesta:', resp.data);this.drinksData = resp.data.drinks;
      } catch (err) {
        console.error(err);
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
    <div v-if="drinksData">
      <DrinksCard :data="drinksData" />
    </div>
    <div v-else>
      <Message />
    </div>
  </div>
</template>
