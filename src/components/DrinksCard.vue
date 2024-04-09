<script>
export default {
name: 'DrinksCard',
  props: {
    data: Array, // Debes definir el tipo de la prop data
  },
  computed: {
    sortedData() {
      // Copia y ordena los datos por strDrink
      return this.data.slice().sort((a, b) => {
        if (a.strDrink < b.strDrink) {
          return -1;
        } else if (b.strDrink < a.strDrink) {
          return 1;
        } else {
          return 0;
        }
      });
    },
  },
};
</script>

<template>
  <article>
    <div class="card-container">
      <div
        v-for="info in sortedData"
        :key="info.idDrink"
        class="card"
      >
        <div>
          <img :src="info.strDrinkThumb" alt="" />
        </div>
        <div class="text">
          <h3 class="name">{{ info.strDrink }}</h3>
          <p class="instructions">{{ info.strInstructions }}</p>
        </div>
      </div>
    </div>
  </article>
</template>

<style>
  @import url('../assets/styles/DrinksCard.css');
</style>