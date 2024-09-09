<template>
  <hero-image @toggle-get-started="toggleSection"></hero-image>
  <verse-section v-if="Section && type === 'Verse'" @toggle-study="selectSection"></verse-section>
  <study-section v-if="Section && type === 'Study'"></study-section>
</template>

<script>
import HeroImage from './components/HeroImage.vue'
import StudySection from './components/StudySection.vue'
import VerseSection from './components/VerseSection.vue'

export default {
  components: { HeroImage, VerseSection, StudySection },
  data() {
    return {
      type: 'Verse',
      Section: false
    }
  },
  methods: {
    toggleSection() {
      this.Section = true
    },
    selectSection(sectiontype) {
      this.type = sectiontype
      window.scrollTo({ top: 0, behavior: 'smooth' })
    }
  }
}
</script>

<style>
h1 {
  font-weight: 600;
  margin: 0;
  font-size: 5rem;
}

h2 {
  font-size: 2rem;
}

p {
  font-size: 2rem;
}

.herotext {
  margin: 0;
  color: white;
}

.button {
  width: 12rem;
  height: 3rem;
  margin-top: 4rem;
  border: 2px solid rgba(217, 212, 212, 0.3); /* Make border less visible */
  border-radius: 0.3rem;
  background-color: rgba(0, 0, 0, 0.2);
  color: white; /* Change text color to white */
  font-size: 1rem; /* Adjust font size */
  cursor: pointer; /* Pointer cursor */
}

hr.solid {
  border-top: 3px solid #bbb;
  margin-top: 1rem;
  margin-bottom: 1rem;
}
</style>
