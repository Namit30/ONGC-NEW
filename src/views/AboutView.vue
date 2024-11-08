<template>
  <div class="about">
    <!-- Content -->
    <div class="content">
      <h1>Welcome to the ONGC News Portal</h1>
      <p>We are dedicated to bringing you the latest news and updates from ONGC (Oil and Natural Gas Corporation Limited). Our mission is to provide accurate, reliable, and timely information to our readers.</p>
      <p>Explore our portal to stay informed about the latest developments, innovations, and events in the world of energy and beyond.</p>
      <p>Join our community of enthusiasts, professionals, and industry experts as we embark on a journey to explore the future of energy together.</p>
    </div>
    <!-- Image -->
    <div class="image-container">
      <img src="https://media.assettype.com/psuwatch%2Fimport%2Fwp-content%2Fuploads%2F2022%2F02%2Fwebp.net-compress-image-27-611108cd1e2a2-3.jpg?w=1200&auto=format%2Ccompress&fit=max" alt="ONGC Image" class="ongc-image">
    </div>
    <!-- Suggestion Box -->
    <div class="suggestion-box">
      <h2>Have any suggestions or feedback?</h2>
      <form @submit.prevent="submitSuggestion">
        <textarea v-model="suggestion" placeholder="Enter your suggestion or feedback"></textarea>
        <button type="submit">Submit</button>
      </form>
    </div>
    <!-- Feedback Success Modal -->
    <div v-if="showModal" class="modal" @click.self="closeModal">
      <div class="modal-content">
        <span class="close" @click="closeModal">&times;</span>
        <h2>Thank you for your feedback!</h2>
        <p>We appreciate your input. Your feedback has been submitted successfully.</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      suggestion: '',
      showModal: false
    };
  },
  methods: {
    submitSuggestion() {
      // Here, you can implement the logic to send the suggestion to your backend or perform any other action
      console.log('Suggestion submitted:', this.suggestion);
      // You can also clear the suggestion textarea after submission
      this.suggestion = '';
      // Show the feedback success modal
      this.showModal = true;
    },
    closeModal() {
      // Close the feedback success modal
      this.showModal = false;
    }
  }
};
</script>

<style scoped>
/* Styles for the about page */
/* Styles for the about page */
.about {
  padding: 20px;
  text-align: center;
  background: linear-gradient(135deg, #1a1a1a, #333333);
  color: #f5f5f5;
  font-family: 'Roboto', sans-serif;
}

.content {
  margin-bottom: 40px;
}

.about h1 {
  font-size: 3rem;
  font-weight: bold;
  margin-bottom: 20px;
  color: #ffdd57;
}

.about p {
  font-size: 1.2rem;
  line-height: 1.8;
  color: #d4d4d4;
  margin-bottom: 15px;
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
}

/* Image container and hover effect */
.image-container {
  position: relative;
  overflow: hidden;
  max-width: 100%;
  display: flex;
  justify-content: center;
}

.ongc-image {
  width: 100%;
  max-width: 600px;
  transition: transform 0.5s ease, border-color 0.5s ease;
  border: 5px solid transparent;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
}

.ongc-image:hover {
  transform: scale(1.1);
  border-color: #ffdd57;
}

/* Suggestion Box */
.suggestion-box {
  margin-top: 40px;
}

.suggestion-box h2 {
  font-size: 1.8rem;
  margin-bottom: 15px;
  color: #ffdd57;
}

textarea {
  width: 100%;
  height: 100px;
  resize: vertical;
  padding: 10px;
  margin-bottom: 15px;
  border-radius: 5px;
  border: 1px solid #ccc;
}

button {
  background-color: #ffdd57;
  color: #333;
  padding: 12px 25px;
  border: none;
  border-radius: 25px;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
}

button:hover {
  background-color: #ffc107;
  transform: scale(1.05);
}

/* Feedback success modal styles */
.modal {
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.6);
  z-index: 999;
  animation: fadeIn 0.5s ease;
}

.modal-content {
  background-color: #fff;
  padding: 25px;
  border-radius: 15px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
  position: relative;
  max-width: 500px;
  text-align: center;
  animation: scaleIn 0.3s ease;
}

.close {
  position: absolute;
  top: 10px;
  right: 10px;
  cursor: pointer;
  font-size: 1.5rem;
  color: #666;
}

.close:hover {
  color: #333;
}

/* Keyframes for animations */
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes scaleIn {
  from {
    transform: scale(0.8);
  }
  to {
    transform: scale(1);
  }
}

</style>
