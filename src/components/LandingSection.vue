<script>
import StyledButton from "./StyledButton.vue";
export default {
  name: "LandingSection",
  components: {
    StyledButton,
  },
};
</script>

<template>
  <section class="landing-section">
    <div class="neon-border"></div>
    <img class="glass" src="../assets/glass.png" alt="cocktail glass" />
    <div class="ticket">
      <div class="ticket-container">
        <img src="../assets/Logo.png" alt="logo" />
        <h1>DRINKLAND</h1>
        <h2>Mix it up with us !</h2>
      </div>
    </div>
    <StyledButton class="explore-button" href="#suggestion"
      >Explore our Suggestions</StyledButton
    >
    <div class="description">
      <h2>THE SMALLEST YET THE BEST COCKTAIL HUB!</h2>
      <p>
        This is an attempt to pass the vue.js test I received from Vade.
        <br />
        You can find details on 3 random cocktails every time you load the page.
        <br />
        The best application to do so which you can find for free on the web !
      </p>
    </div>
  </section>
</template>

<style scoped>
.landing-section {
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 26px;
  align-items: center;
  justify-content: space-between;
  min-height: 100vh;
  width: 100%;
  background-image: url("../assets/background.png");
  background-size: cover;
  padding: 0 70px 80px;
}

.neon-border {
  position: absolute;
  border: 0.2em solid #fff;
  box-shadow: 0 0 0.2em #fff, 0 0 0.2em #fff, 0 0 2em #601733, 0 0 0.8em #601733,
    0 0 2.8em #601733, inset 0 0 1.3em #601733;
  top: 30px;
  bottom: 30px;
  left: 30px;
  right: 30px;
}

.glass {
  position: absolute;
  z-index: 10;
  height: 100vh;
  left: 12%;
  bottom: 0;
}

.ticket {
  z-index: 30;
  height: fit-content;
  width: fit-content;
  background: rgb(0, 0, 0);
  background: linear-gradient(
    180deg,
    rgba(0, 0, 0, 1) 0%,
    rgba(0, 0, 0, 1) 15%,
    rgba(0, 0, 0, 0.2) 100%
  );
  color: white;
  padding: 0 50px;
  padding-top: 70px;
  padding-bottom: 100px;
}

.ticket-container {
  display: flex;
  gap: 30px;
  align-items: center;
  flex-direction: column;
}

.ticket-container img {
  height: 80px;
}

.ticket-container h1 {
  letter-spacing: 5px;
  font-size: 5em;
  font-family: "Wire One", sans-serif;
  color: #721a3c;
  text-shadow: 0 0 7px #fff, 0 0 10px #fff, 0 0 21px #fff, 0 0 42px #f1024d,
    0 0 82px #f1024d, 0 0 92px #f1024d, 0 0 102px #f1024d, 0 0 151px #f1024d;
}

.ticket-container h2 {
  margin: 0;
  padding: 0;
  font-size: 1.5em;
  text-align: center;
  color: #d6cfd0;
  font-family: "Unbounded", cursive;
}

.explore-button {
  font-size: 1.1em;
}

.description {
  z-index: 20;
  align-self: flex-end;
  display: flex;
  flex-direction: column;
  gap: 26px;
  max-width: 60%;
}

.description h2 {
  color: white;
  font-size: 1.2em;
  font-family: "Unbounded", cursive;
}

.description p {
  color: white;
  font-family: "Unbounded", cursive;
  font-size: 0.9em;
  font-weight: 300;
  line-height: 1.5;
  letter-spacing: 1px;
}

@media (max-width: 840px) {
  .landing-section {
    padding: 0 50px 60px;
  }

  .glass {
    display: none;
  }

  .ticket {
    padding: 0 30px;
    padding-top: 35px;
    padding-bottom: 50px;
  }

  .ticket-container h1 {
    letter-spacing: 5px;
    font-size: 5em;
    font-family: "Wire One", sans-serif;
    color: #721a3c;
    text-shadow: 0 0 7px #fff, 0 0 4px #fff, 0 0 4px #f1024d, 0 0 10px #f1024d;
  }

  .description {
    background-color: rgba(254, 216, 249, 0.2);
    padding: 16px;
    max-width: 100%;
  }
}
</style>
