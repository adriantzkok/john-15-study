<template>
  <div class="grid-item" @click="toggleanswer">
    <p v-if="!answershown" class="item-text">{{ item }}</p>
    <p v-else class="answer-text">{{ answer }}</p>
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
    item: { type: String, required: true },
    answer: { type: String, required: true }
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
  border-radius: 8px; /* Rounded corners */
  padding: 1.5rem;
  transition:
    background-color 0.3s,
    box-shadow 0.3s,
    transform 0.3s; /* Smooth transitions */
  text-align: center; /* Center text */
  box-sizing: border-box; /* Include padding and border in the element's total width and height */
}

.grid-item:hover {
  cursor: pointer;
  background-color: #e0e7ff; /* Change background color on hover */
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2); /* Add shadow on hover */
  transform: scale(1.05); /* Slightly scale up on hover */
}

.item-text {
  font-size: 1.2rem; /* Size for the item text */
  font-weight: bold; /* Bold for emphasis */
  color: #333; /* Color for the item text */
}

.answer-text {
  font-size: 1.2rem; /* Size for the answer text */
  font-weight: bold; /* Bold for emphasis */
  color: #000000; /* Color for the answer text */
  transition: color 0.3s; /* Smooth color transition */
}

.grid-item:hover .answer-text {
  color: #003d80; /* Darker color for the answer text on hover */
}
</style>
