<script>
import axios from "axios";
import CocktailCard from "./CocktailCard.vue";

export default {
  name: "CocktailsList",
  components: {
    CocktailCard,
  },
  data() {
    return {
      cocktails: [],
    };
  },

  methods: {
    async getRandomCocktail(maxIngredients = 15) {
      try {
        const response = await axios.get(
          "https://www.thecocktaildb.com/api/json/v1/1/random.php"
        );
        const cocktail = response.data.drinks[0];
        const ingredientsList = [];
        for (let i = 1; i <= maxIngredients; i++) {
          const ingredient = cocktail[`strIngredient${i}`];
          const measure = cocktail[`strMeasure${i}`];
          if (ingredient) {
            ingredientsList.push({
              ingredient: ingredient,
              measure: measure,
            });
          } else {
            break;
          }
        }
        return {
          id: cocktail["idDrink"],
          name: cocktail["strDrink"],
          imageUrl: cocktail["strDrinkThumb"],
          category: cocktail["strCategory"],
          instructions: cocktail["strInstructions"],
          ingredientsList,
        };
      } catch (error) {
        console.error(error);
      }
    },
    async refreshListWithRandomCocktails(number, maxRequests = 25) {
      let attempsThreshHold = 0;
      this.cocktails.splice(0);

      while (
        this.cocktails.length < number &&
        attempsThreshHold < maxRequests
      ) {
        attempsThreshHold++;
        const res = await this.getRandomCocktail();
        if (this.cocktails.some((cocktail) => res.id === cocktail.id)) {
          continue;
        }
        this.cocktails.push(res);
      }
      this.cocktails.sort(
        (a, b) => b.instructions.length - a.instructions.length
      );
      // Just for better UI reasons:
      this.cocktails.sort(function (a, b) {
        return b.instructions.length - a.instructions.length;
      });
    },
  },

  mounted() {
    this.refreshListWithRandomCocktails(3);
  },
};
</script>

<template>
  <section class="cocktails-section" id="suggestion">
    <CocktailCard
      v-for="cocktail in cocktails"
      :cocktail="cocktail"
      :key="cocktail.id"
    />
  </section>
</template>

<style scoped>
.cocktails-section {
  background-image: url("../assets/secondary-background.png");
  background-size: cover;
  padding: 120px 8% 8%;
  display: grid;
  width: 100%;
  grid-template-columns: repeat(auto-fit, minmax(300px, auto));
  align-items: stretch;
  gap: 2.5em;
  row-gap: 60px;
}
</style>
