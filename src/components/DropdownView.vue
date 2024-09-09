<template>
  <div class="faq-dropdown">
    <div class="faq-item" v-for="(item, index) in faqs" :key="index">
      <div class="faq-question" @click="toggleAnswer(index)">
        <h2 class="studyh2">{{ item.question }}</h2>
        <span class="arrow" :class="{ rotated: isActive(index) }">▼</span>
      </div>
      <transition name="fade">
        <div class="faq-answer" v-if="isActive(index)">
          <p class="faq-answer-text">{{ item.answer }}</p>
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      faqs: [
        {
          question: '1. The Last Supper',
          answer:
            'John 14 and 15 occurs during the last supper, Jesus` final meal with his disciples.'
        },
        {
          question: '2. I am the way, the truth, and the life',
          answer:
            'In the prior chapter, John 14:6, Jesus refers to himself as the way, the truth, and the life.'
        },
        {
          question: '3. Physically absent but Spiritually present',
          answer:
            'Jesus expresses in John 14 that although he is leaving, he will not leave them alone.'
        }
      ],
      activeIndex: null
    }
  },
  methods: {
    toggleAnswer(index) {
      this.activeIndex = this.activeIndex === index ? null : index
    },
    isActive(index) {
      return this.activeIndex === index
    }
  }
}
</script>

<style scoped>
.faq-dropdown {
  width: 100%;
  margin: auto;
}

.faq-item {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 10px; /* Space between FAQ items */
}

.faq-question {
  padding: 15px;
  cursor: pointer;
  background-color: #f9f9f9;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.faq-answer {
  padding: 15px;
  background-color: #fff;
}

.faq-answer-text {
  font-size: 1rem; /* Font size for the answer */
  color: #333; /* Dark text color */
  line-height: 1.5; /* Improved line spacing */
  margin: 0; /* Remove default margin */
  transition: color 0.3s; /* Smooth transition for color changes */
}

.faq-answer-text:hover {
  color: #007bff; /* Change color on hover */
}

.arrow {
  transition: transform 0.3s;
}

.rotated {
  transform: rotate(180deg);
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
