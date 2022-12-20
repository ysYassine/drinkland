<script setup>
import LandingSection from "./components/LandingSection.vue";
import CocktailsList from "./components/CocktailsList.vue";
</script>

<template>
  <LandingSection />
  <CocktailsList />
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Unbounded:wght@200;300;400&family=Wire+One&display=swap");

*,
*::before,
*::after {
  box-sizing: border-box;
}

* {
  margin: 0;
  padding: 0;
  font-family: "Unbounded", cursive;
  text-decoration: none;
  list-style: none;
  scroll-behavior: smooth;
}

body {
  color: #d6cfd0;
}

img,
picture,
svg,
video {
  display: block;
  max-width: 100%;
}

::-webkit-scrollbar {
  width: 0.6rem;
  background-color: #601733;
}

::-webkit-scrollbar-thumb {
  background-color: #ad295b;
  border-radius: 0.5rem;
}

::-webkit-scrollbar-thumb:hover {
  background-color: #c58fb1;
}

@media (max-width: 840px) {
  * {
    font-size: 15px;
  }
}
</style>
