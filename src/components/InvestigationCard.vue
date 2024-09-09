<template>
  <div class="grid-item" @click="toggleanswer">
    <p v-if="!answershown">{{ item }}</p>
    <p v-else>{{ answer }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      answershown: false
    }
  },
  methods: {
    toggleanswer() {
      this.answershown = !this.answershown
    }
  },
  props: {
    item: { type: String },
    answer: { type: String }
  }
}
</script>

<style scoped>
.grid-item {
  height: 30vh; /* Height for grid items */
  width: 100%;
  background-color: #f9f9f9; /* Example background color */
  display: flex; /* Centering content in the grid item */
  justify-content: center;
  align-items: center;
  border: 1px solid #ccc; /* Example border */
  padding: 1.5rem;
}
</style>
