<template>
  <div class="StudySection">
    <div>
      <investigation-section heading="Preface">
        <dropdown-view></dropdown-view>
      </investigation-section>
    </div>
    <question-area header="Question 1"
      ><question-input
        question="What are your initial thoughts of this passage?"
        :link="question_link_1"
      >
      </question-input
    ></question-area>
    <question-area header="Question 2"
      ><question-input
        question="Do you have any questions regarding this passage?"
        :link="question_link_2"
      >
      </question-input
    ></question-area>

    <div>
      <investigation-section heading="Investigation #1">
        <blockquote>
          <div v-for="verse in verses.slice(0, 7)" :key="verse.verse" class="verses">
            <span class="versenumber">{{ verse.verse }} </span>
            <span class="verses">{{ verse.text.replace(/\n/g, ' ') }}</span>
          </div>
        </blockquote>
        <div class="grid-container">
          <investigation-card
            item="1. What is the significance of the Vine and the Vinedresser?"
            answer="Vine: Refer to Psalm 80:8-9 and Isaiah 5:4"
          ></investigation-card>
          <investigation-card
            item="2. What is meant by Fruit and Pruning the Fruit in this context?"
            answer="The Fruit can refer to love or the fruit of the sprit. God prunes the branches (us) so that we can be even more fruitful."
          ></investigation-card>
          <investigation-card
            item="3. What exactly does Jesus mean by remaining in him?"
            answer="By following the Holy Spirit. Refer to John 14:26"
          ></investigation-card>
        </div>
      </investigation-section>
    </div>
    <div>
      <investigation-section heading="Investigation #2">
        <blockquote>
          <div v-for="verse in verses.slice(8, 15)" :key="verse.verse" class="verses">
            <span class="versenumber">{{ verse.verse }} </span>
            <span class="verses">{{ verse.text.replace(/\n/g, ' ') }}</span>
          </div>
        </blockquote>
        <div class="grid-container">
          <investigation-card
            item="1. What does it mean to love in this section's context?"
            answer="Love is divine (v9), mutual (v12), and sacrificial (v13)"
          ></investigation-card>
          <investigation-card
            item="2. What is the significance of Jesus calling him his friends?"
            answer="Our relationship through God is built through a connection."
          ></investigation-card>
          <investigation-card
            item="3. How can we become Jesus' friend?"
            answer="By obeying v14"
          ></investigation-card>
        </div>
      </investigation-section>
    </div>
    <div>
      <question-area header="Question 3"
        ><question-input
          question="Refer to verse 16. Do you think we are chosen by God?"
          :link="question_link_3"
        >
        </question-input
      ></question-area>
    </div>
  </div>
</template>

<script>
import john15verse from '@/assets/data/john15'
import QuestionArea from './QuestionArea.vue'
import QuestionInput from './QuestionInput.vue'
import InvestigationSection from './InvestigationSection.vue'
import InvestigationCard from './InvestigationCard.vue'
import DropdownView from './DropdownView.vue'
export default {
  components: {
    QuestionArea,
    QuestionInput,
    InvestigationSection,
    InvestigationCard,
    DropdownView
  },
  data() {
    return {
      InvestigationSection: john15verse.reference,
      verses: john15verse.verses,
      question_link_1: `${import.meta.env.VITE_FIREBASE_DATABASE}question1.json`,
      question_link_2: `${import.meta.env.VITE_FIREBASE_DATABASE}question2.json`,
      question_link_3: `${import.meta.env.VITE_FIREBASE_DATABASE}question3.json`
    }
  }
}
</script>

<style>
.StudySection {
  width: 100%;
  min-height: 65vh;
  padding: 2rem;
}

.verses {
  font-size: 1rem;
  display: inline;
  line-height: 1.6;
  word-spacing: 0.1rem;
  position: relative;
}

.versenumber {
  font-size: 0.7rem;
  vertical-align: super;
}

.controlbar {
  display: flex;
  gap: 2rem;
  justify-content: space-between;
  align-items: center;
}

.responsequestion1 {
  display: flex;
  gap: 4rem;
  align-items: flex-start;
  width: 100%;
  min-height: 55vh;
}

.investigation {
  display: flex;
  flex-direction: column;
  gap: 4rem;
  align-items: flex-start;
  width: 100%;
  margin-bottom: 4rem;
}

.investigation .grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* Creates three equal columns */
  row-gap: 50px; /* Vertical gap between rows */
  column-gap: 20px; /* Optional: Horizontal gap between columns */
  width: 100%;
}

.container {
  display: flex;
  max-width: 50%;
  flex-direction: column;
  gap: 1rem;
  height: 100%;
}

.submitbutton {
  padding: 0.5rem;
  margin-top: 1rem;
}

form {
  height: 100%;
}

textarea {
  width: 100%;
}

blockquote {
  border-left: 8px solid black;
  padding-left: 15px;
}

.studyp {
  font-size: 1rem;
}

.studyh1 {
  font-size: 3rem;
  font-weight: 700;
}

.studyh2 {
  font-size: 1.5rem;
  font-weight: 600;
}

/* Media Queries for Mobile Layout */
@media (max-width: 768px) {
  .responsequestion1 {
    flex-direction: column; /* Stack items vertically */
    gap: 2rem; /* Reduce gap for mobile */
  }

  .investigation .grid-container {
    grid-template-columns: 1fr; /* Single column layout */
  }

  .controlbar {
    flex-direction: column; /* Stack control bar items */
  }

  .container {
    max-width: 100%; /* Full width on mobile */
  }
}
</style>
