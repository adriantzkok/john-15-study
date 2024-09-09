<template>
  <div class="heroimage">
    <div class="container">
      <h1 class="herotext">I AM THE TRUE VINE</h1>
      <p class="herotext">John 15</p>
      <button class="button" @click="toggleGetStarted">Get Started</button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    toggleGetStarted() {
      this.$emit('toggle-get-started')
    }
  }
}
</script>

<style scoped>
.heroimage {
  width: 100%;
  height: 90vh;
  background-image: linear-gradient(to bottom right, rgba(19, 16, 16, 0.9), rgba(43, 34, 6, 0.9)),
    url(/public/images/hero.png);
  background-size: cover;
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%; /* Ensure full height for centering */
  padding: 10px; /* Add some padding for smaller screens */
}

h1 {
  letter-spacing: 0.6rem;
  margin: 0; /* Remove default margin */
}

.herotext {
  margin: 10px 0; /* Add margin for spacing */
}

.button {
  margin-top: 20px; /* Space above button */
  padding: 10px 20px; /* Button padding */
  font-size: 1.2rem; /* Increase font size for visibility */
}
</style>
