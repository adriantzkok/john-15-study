<template>
  <div class="versecontainer">
    <div v-if="!error">
      <div class="controlbar">
        <h2 class="header">{{ title }}</h2>
        <h3 class="guidebutton" @click="toggleGuideStatus">Turn {{ guideStatus.text }} Guide</h3>
      </div>
      <hr class="solid" />
      <div v-for="verse in verses" :key="verse.verse" class="verses">
        <span class="versenumber">{{ verse.verse }} </span>
        <mark v-if="verse?.notes && guideStatus.status" class="mark">
          <span class="verses">{{ verse.text.replace(/\n/g, ' ') }}</span>
        </mark>
        <span v-else class="verses">{{ verse.text.replace(/\n/g, ' ') }}</span>
        <p class="notes" v-if="guideStatus.status && verse?.notes">
          {{ verse.verse }}: {{ verse?.notes }}
        </p>
      </div>
      <div class="sectionfooter">
        <button class="studybutton" @click="toggleStudy">Start Studying</button>
      </div>
    </div>
    <div v-else>
      <p>{{ error }}</p>
    </div>
  </div>
</template>

<script>
import john15verse from '@/assets/data/john15'

export default {
  data() {
    return {
      title: john15verse.reference,
      verses: john15verse.verses,
      guideStatus: { status: false, text: 'On' }
    }
  },
  methods: {
    toggleGuideStatus() {
      this.guideStatus.status = !this.guideStatus.status

      if (this.guideStatus.status) {
        this.guideStatus.text = 'Off'
      } else {
        this.guideStatus.text = 'On'
      }
    },
    toggleStudy() {
      this.$emit('toggle-study', 'Study')
    }
  }
}
</script>

<style scoped>
.versecontainer {
  padding: 2rem;
}

.controlbar {
  display: flex;
  gap: 2rem;
  justify-content: space-between;
  align-items: center;
}

.guidebutton {
  cursor: pointer;
}

.guidebutton:hover {
  color: #bbb;
}

.verses {
  font-size: 1rem;
  display: inline;
  line-height: 1.6;
  word-spacing: 0.1rem;
  position: relative;
}

.verses .notes {
  position: absolute;
  font-size: 0.9rem; /* Slightly smaller font size */
  font-family: 'Arial', sans-serif; /* Change to a more readable font */
  color: #555; /* Softer text color for supplementary notes */
  background-color: rgba(244, 244, 244, 0.95); /* Slightly transparent background */
  padding: 8px; /* Increased padding for better spacing */
  display: none; /* Initially hide the notes */
  z-index: 10; /* Ensure the notes appear above other content */
}

mark {
  background-color: yellow;
}

.verses:hover .notes {
  display: block;
}

.versenumber {
  font-size: 0.7rem;
  vertical-align: super;
}

.sectionfooter {
  text-align: right; /* Right align the footer content */
  margin-top: 1rem; /* Add space above */
}

.studybutton {
  display: inline-block; /* Inline-block for better control */
  padding: 0.5rem 1rem; /* Padding for the button */
  background-color: white; /* Example background color */
  color: white; /* Button text color */
  border-radius: 4px; /* Rounded corners */
  border-color: black;
  border-style: solid;
  cursor: pointer; /* Pointer cursor on hover */
  color: black;
}

.studybutton:hover {
  background-color: rgb(232, 232, 232);
}
</style>
