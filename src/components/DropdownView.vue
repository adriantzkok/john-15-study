<template>
  <div class="faq-dropdown">
    <div class="faq-item" v-for="(item, index) in faqs" :key="index">
      <div class="faq-question" @click="toggleAnswer(index)">
        <h2 class="studyh2">{{ item.question }}</h2>
        <span class="arrow" :class="{ rotated: isActive(index) }">▼</span>
      </div>
      <transition name="fade">
        <div class="faq-answer" v-if="isActive(index)">
          <p>{{ item.answer }}</p>
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
          answer: 'Vue.js is a progressive JavaScript framework for building user interfaces.'
        },
        {
          question: '2. I am the way, the truth, and the life',
          answer: 'You can install Vue.js via npm, yarn, or by including it in a script tag.'
        },
        {
          question: '3. Physically absent but Spiritually present',
          answer:
            'Components are reusable instances with a name. They can be used in other components.'
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
