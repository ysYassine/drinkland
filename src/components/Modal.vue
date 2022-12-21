<script>
export default {
  name: "Modal",
  props: {
    cocktail: {
      type: Object,
      required: true,
    },
  },
  methods: {
    closeModal() {
      this.$emit("close");
    },
  },
};
</script>

<template>
  <div class="modal" @click.self="closeModal">
    <div class="modal-content">
      <div class="modal-header">
        <div class="title-container">
          <h3>{{ cocktail.name.toUpperCase() }}</h3>
          <div class="category">{{ cocktail.category }}</div>
        </div>
        <button class="close-button" @click="closeModal">&times;</button>
      </div>
      <div class="modal-header-divider"></div>
      <div class="modal-body">
        <div class="body-text">
          <div>Make sure you have following ingredients:</div>
          <ul>
            <li v-for="ingredient in cocktail.ingredientsList">
              <span class="ingredient-name"
                >&#8680;
                {{ ingredient.ingredient }}
              </span>
              <span v-if="ingredient.measure">
                :
                <span>
                  {{ ingredient.measure }}
                </span>
              </span>
            </li>
          </ul>
          <br />
          <div>Then:</div>
          <div class="description">{{ cocktail.instructions }}</div>
        </div>
        <img
          :src="cocktail.imageUrl"
          alt="cocktail thumbnail"
          class="thumbnail-img"
        />
      </div>
    </div>
  </div>
</template>

<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 999;
  animation: fadeIn 0.6s;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.modal-content {
  display: flex;
  flex-direction: column;
  width: 70%;
  height: 80%;
  background-image: url("../assets/secondary-background.png");
  border-radius: 5px;
  padding-bottom: 16px;
  border: 0.1em solid #fff;
  box-shadow: 0 0 0.2em #fff, 0 0 0.2em #fff, 0 0 2em #601733, 0 0 0.5em #601733,
    0 0 1.5em #601733, inset 0 0 1em #601733;
}

.modal-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 12px 20px;
}

.title-container {
  width: fit-content;
  display: flex;
  flex-wrap: wrap;
  row-gap: 8px;
  column-gap: 30px;
  align-items: center;
  justify-content: center;
}

h3 {
  font-family: "Wire One", sans-serif;
  font-size: 3em;
  text-align: center;
  font-weight: bold;
  color: #eebbb7;
  text-shadow: 0 0 20px #8d151f, 0 0 20px #8d151f, 0 0 20px #8d151f,
    0 0 20px #8d151f, 0 0 20px #8d151f, 0 0 20px #8d151f, 0 0 20px #8d151f,
    0 0 20px #8d151f;
}

.category {
  font-family: "Unbounded", cursive;
  width: fit-content;
  display: flex;
  text-align: center;
  align-items: center;
  justify-content: center;
  font-size: 0.6em;
  font-weight: 300;
  background-color: rgba(238, 187, 183, 0.2);
  border-radius: 12px;
  padding: 8px 12px;
  margin: 10px 0;
  margin-left: auto;
  margin-right: auto;
  box-shadow: 0 0 5px 5px rgba(255, 255, 255, 0.5);
}

.close-button {
  margin: 0;
  border: none;
  padding: 8px;
  height: fit-content;
  width: fit-content;
  color: white;
  font-size: 2.5em;
  font-weight: bold;
  background-color: transparent;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
}

.close-button:hover {
  transform: scale(1.15);
  color: #831143;
}

.modal-header-divider {
  background-color: rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  width: 98%;
  height: 3px;
  margin: auto;
}

.modal-body {
  color: inherit;
  padding: 18px;
  display: flex;
  gap: 28px;
  flex-direction: row;
  overflow-x: hidden;
  overflow-y: auto;
  max-height: 100%;
}

.body-text {
  font-size: 0.95em;
  line-height: 2;
  flex-grow: 1;
  white-space: pre-wrap;
  padding-bottom: 20px;
}

li {
  font-size: 0.85em;
  padding-left: 20px;
  font-weight: 200;
}

.ingredient-name {
  font-weight: 400;
}

.description {
  font-size: 0.85em;
  padding-left: 20px;
  font-weight: 300;
}

.thumbnail-img {
  width: fit-content;
  height: fit-content;
  border-radius: 12px;
  max-height: 100%;
  max-width: 45%;
  object-fit: contain;
}

@media (max-width: 840px) {
  .modal-content {
    width: 90%;
  }

  .modal-body {
    flex-direction: column;
    gap: 12px;
  }
  .thumbnail-img {
    margin: auto;
    max-width: 100%;
  }
}
</style>
