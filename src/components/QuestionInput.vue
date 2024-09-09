<template>
  <div class="responsequestion1">
    <div class="container">
      <h2 class="studyh2">Question</h2>
      <p class="studyp">{{ question }}</p>
      <form @submit.prevent="submitForm">
        <textarea
          v-model="userInput"
          rows="10"
          placeholder="Enter your thoughts here..."
        ></textarea>
        <button class="submitbutton">Submit</button>
      </form>
    </div>
    <div class="container">
      <h2>Responses</h2>
      <div class="responsescontainer">
        <template v-if="data.length === 0">
          <p>No responses yet.</p>
        </template>
        <template v-else>
          <div v-for="(response, index) in data" :key="index">
            <p>{{ Object.values(response)[0] }}</p>
          </div>
        </template>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  props: {
    question: {
      type: String,
      required: true
    },
    link: {
      type: String,
      required: false
    }
  },
  data() {
    return {
      userInput: '', // Store textarea input
      data: [] // Initialize as an empty array
    }
  },
  methods: {
    submitForm() {
      axios
        .post(this.link, JSON.stringify({ question: this.userInput }))
        .then((response) => {
          console.log(response)
          this.userInput = '' // Clear the textarea after successful submission
          this.getData() // Fetch updated data after submission
        })
        .catch((error) => {
          console.error(error) // Log the error
        })
    },
    getData() {
      axios
        .get(this.link)
        .then((response) => {
          this.data = response.data // Store the response data
          console.log(this.data) // Log the response
        })
        .catch((error) => console.log(error))
    }
  },
  mounted() {
    this.getData() // Fetch data when the component is mounted
  }
}
</script>

<style scoped>
.container {
  display: flex;
  max-width: 50%;
  flex-direction: column;
  gap: 1rem;
  height: 100%;
  width: 100%;
  margin: 0 auto; /* Center the container */
  padding: 20px; /* Add padding */
  border: 1px solid #ddd; /* Add border */
  border-radius: 8px; /* Rounded corners */
  background-color: #fff; /* White background */
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1); /* Subtle shadow */
}

.studyh2 {
  font-size: 1.5rem;
  color: #333; /* Darker text color */
  margin-bottom: 10px; /* Space below the heading */
}

.studyp {
  font-size: 1rem;
  color: #555; /* Gray text color */
  line-height: 1.5; /* Better line spacing */
}

textarea {
  width: 100%;
  padding: 10px; /* Padding inside the textarea */
  border: 1px solid #ccc; /* Light border */
  border-radius: 4px; /* Rounded corners */
  resize: none; /* Disable resizing */
  font-size: 1rem; /* Font size */
  color: #333; /* Text color */
  background-color: #f9f9f9; /* Light background */
  transition: border-color 0.3s; /* Smooth transition */
}

textarea:focus {
  border-color: #007bff; /* Blue border on focus */
  outline: none; /* Remove outline */
}

.submitbutton {
  padding: 10px 20px; /* Button padding */
  border: none; /* Remove border */
  border-radius: 4px; /* Rounded corners */
  background-color: #007bff; /* Blue background */
  color: white; /* White text */
  font-size: 1rem; /* Font size */
  cursor: pointer; /* Pointer cursor */
  transition: background-color 0.3s; /* Smooth transition */
}

.submitbutton:hover {
  background-color: #0056b3; /* Darker blue on hover */
}

.responsescontainer {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  height: 100%;
  width: 100%;
  background-color: rgb(235, 240, 245);
  padding: 10px; /* Padding inside the responses container */
  border-radius: 4px; /* Rounded corners */
  border: 1px solid #ccc; /* Light border */
}

.responsescontainer p {
  background-color: #fff; /* White background for each response */
  padding: 15px; /* Padding inside each response */
  border-radius: 4px; /* Rounded corners */
  box-shadow: 0 1px 5px rgba(0, 0, 0, 0.1); /* Subtle shadow */
  margin: 0; /* Remove default margin */
  font-size: 1rem; /* Font size for responses */
  color: #333; /* Text color */
  line-height: 1.4; /* Better line spacing */
  transition: transform 0.2s; /* Smooth transition for hover effect */
}

.responsescontainer p:hover {
  transform: scale(1.02); /* Slightly enlarge on hover */
  background-color: #f1f1f1; /* Light gray background on hover */
}
</style>
