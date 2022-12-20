<script>
import StyledButton from "./StyledButton.vue";
import Modal from "./Modal.vue";
export default {
  name: "CocktailCard",
  props: {
    cocktail: {
      type: Object,
      required: true,
    },
  },
  components: {
    StyledButton,
    Modal,
  },
  data() {
    return {
      showFullDescription: false,
      showModal: false,
    };
  },
  methods: {
    showDescription(description, fullDescription = false, wordCount = 15) {
      if (fullDescription) return description;
      const descriptionSplitted = description.split(" ");
      if (descriptionSplitted.length <= wordCount) return description;
      return descriptionSplitted.splice(0, wordCount).join(" ") + "...";
    },
    openModal() {
      this.showModal = true;
    },
    closeModal() {
      this.showModal = false;
    },
  },
};
</script>

<template>
  <transition name="fade">
    <Modal v-if="showModal" @close="closeModal" :cocktail="cocktail" />
  </transition>
  <div class="cocktail-card">
    <div class="logo">
      <img src="../assets/Logo.png" alt="logo" />
    </div>
    <h3>{{ cocktail.name.toUpperCase() }}</h3>
    <div class="category">{{ cocktail.category }}</div>
    <p @click="showFullDescription = !showFullDescription">
      {{ showDescription(cocktail.instructions, showFullDescription) }}
    </p>
    <StyledButton class="button" @click="openModal"
      >Make It Yourself</StyledButton
    >
    <div class="thumbnail-container">
      <img
        :src="cocktail.imageUrl"
        alt="cocktail thumbnail"
        class="thumbnail-img"
      />
    </div>
  </div>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
.cocktail-card {
  position: relative;
  border: 0.1em solid #fff;
  box-shadow: 0 0 0.2em #fff, 0 0 0.2em #fff, 0 0 2em #601733, 0 0 0.5em #601733,
    0 0 1.5em #601733, inset 0 0 1em #601733;
  padding: 16px;
  padding-top: 46px;
  display: flex;
  flex-direction: column;
  transition: transform 0.4s ease-in-out;
}

.cocktail-card .logo {
  position: absolute;
  width: 80px;
  top: -40px;
  left: 50%;
  transform: translateX(-50%);
  background: rgb(0, 0, 0);
  background: linear-gradient(
    180deg,
    rgba(96, 23, 51, 0.8) 0%,
    rgba(96, 23, 51, 1) 52%,
    rgba(96, 23, 51, 0.1) 100%
  );
  padding: 10px;
  border-radius: 100%;
  transition: all 0.4s ease-in-out;
}

.cocktail-card h3 {
  font-family: "Wire One", sans-serif;
  font-size: 3em;
  text-align: center;
  font-weight: bold;
  color: #eebbb7;
  text-shadow: 0 0 10px #790c09, 0 0 10px #790c09, 0 0 10px #790c09,
    0 0 10px #790c09, 0 0 10px #790c09, 0 0 10px #790c09, 0 0 10px #790c09,
    0 0 10px #790c09;
  transition: all 0.5s ease-in-out;
}

.cocktail-card .category {
  font-family: "Unbounded", cursive;
  font-size: 0.7em;
  font-weight: 300;
  background-color: rgba(238, 187, 183, 0.2);
  width: fit-content;
  border-radius: 12px;
  padding: 8px 12px;
  margin: 10px 0;
  margin-left: auto;
  margin-right: auto;
  transition: all 0.4s ease-in-out;
  box-shadow: 0 0 10px 3px rgba(255, 255, 255, 0.2);
}
.cocktail-card:hover .category {
  box-shadow: 0 0 3px 3px rgba(255, 255, 255, 0.5);
}

.cocktail-card p {
  padding: 16px;
  font-family: "Unbounded", cursive;
  font-weight: 300;
  font-size: 0.85em;
  cursor: pointer;
  white-space: pre-wrap;
}

.cocktail-card .button {
  margin-top: auto;
  margin-bottom: 24px;
}

.thumbnail-container {
  overflow: hidden;
  border-radius: 8px;
}
.thumbnail-img {
  object-fit: cover;
  width: 100%;
  transition: transform 0.4s ease-in-out;
}

.cocktail-card:hover .thumbnail-img {
  transform: scale(1.1);
}

@media (min-width: 1080px) {
  .cocktail-card:hover h3 {
    color: #eebbb7;
    text-shadow: 0 0 20px #8d151f, 0 0 20px #8d151f, 0 0 20px #8d151f,
      0 0 20px #8d151f, 0 0 20px #8d151f, 0 0 20px #8d151f, 0 0 20px #8d151f,
      0 0 20px #8d151f;
  }
}

@media (max-width: 840px) {
  .cocktail-card {
    background-color: rgba(0, 0, 0, 0.2);
  }
}
</style>
