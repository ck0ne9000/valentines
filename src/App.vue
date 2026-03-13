<script setup>
import { ref } from "vue";

// Reactive variable to track if the user has accepted
const valentineAccepted = ref(false);

// Ref for the "No" button to move it on hover
const noButton = ref(null);

// Method to handle clicking the "Yes" button
const acceptValentine = () => {
  valentineAccepted.value = true;
};

// Method to handle clicking the "No" button (optional, you can add custom behavior here)
const declineValentine = () => {
  // Custom logic when clicking "No" (if needed)
};

// Method to move the "No" button to a random location when hovered
const moveNoButton = () => {
  if (noButton.value) {
    const randomX =
      Math.random() * (window.innerWidth - noButton.value.offsetWidth);
    const randomY =
      Math.random() * (window.innerHeight - noButton.value.offsetHeight);

    noButton.value.style.position = "absolute";
    noButton.value.style.left = `${randomX}px`;
    noButton.value.style.top = `${randomY}px`;
  }
};
</script>
<template>
  <div class="app-container">
    <div class="postcard">
      <div class="bear-container">
        <p v-if="!valentineAccepted" class="message">
          Will you be my Valentine?!
        </p>
        <div v-else>
          <img
            src="https://media.tenor.com/gUiu1zyxfzYAAAAi/bear-kiss-bear-kisses.gif"
            alt="Cute bear"
            class="bear"
          />
          <p class="message">I love you!</p>
        </div>
      </div>

      <div class="buttons">
        <button
          class="yes-button"
          v-if="!valentineAccepted"
          @click="acceptValentine"
        >
          Yes
        </button>
        <button
          class="no-button"
          v-if="!valentineAccepted"
          @mouseenter="moveNoButton"
          @click="declineValentine"
          ref="noButton"
        >
          No
        </button>
      </div>
    </div>
  </div>
</template>
<style scoped>
.app-container {
  text-align: center;
}

.bear-container {
  display: inline-block;
}

.bear {
  width: 300px;
  height: auto;
}

.message {
  font-size: 5rem;
  text-align: left;
  color: #e74b3c;
  font-weight: 800;
  padding: 40px;
}

.buttons {
  margin-top: 30px;
}

button {
  font-size: 1.5rem;
  padding: 15px 30px;
  margin: 10px;
  cursor: pointer;
  border-radius: 12px;
  border: none;
}

.yes-button {
  background-color: #e74b3c;
  color: white;
}

.no-button {
  background-color: #fdf4fd;
  color: #e74b3c;
}

.no-button:hover {
  transition: transform 0.3s;
}

.no-button:active {
  background-color: #ff3366;
}

.postcard {
  background-color: white;
  border-radius: 6px;
  height: 700px;
  width: 600px;
  background-color: #ffcccc;
}
</style>
