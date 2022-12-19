<script setup>
import LandingSection from "./components/LandingSection.vue";
</script>

<template>
  <LandingSection />
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
  font-family: "Poppins", sans-serif;
  text-decoration: none;
  list-style: none;
  scroll-behavior: smooth;
}

body {
  color: white;
}

img,
picture,
svg,
video {
  display: block;
  max-width: 100%;
}

@media (max-width: 840px) {
  * {
    font-size: 13px;
  }
}
</style>
