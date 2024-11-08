<template>
  <div class="dashboard">
    <h1>ONGC News Dashboard</h1>
    
    <!-- Moving Banner with Glitter Effect -->
    <div class="moving-banner">
      <div class="announcement-content">
        <span v-for="(announcement, index) in announcements" :key="index" class="glitter-text">
          {{ announcement }} &nbsp;&nbsp;&nbsp;&nbsp;
        </span>
      </div>
    </div>

    <img src="https://miro.medium.com/v2/resize:fit:1100/format:webp/1*ELMWyWnc0BTwPxZGZFCIaQ.png" alt="welcome" height="200" class="center" />

    <div class="content">
      <div class="events">
        <EventCard v-for="event in events" :key="event.id" :event="event" />
      </div>
      <div class="footer-line"></div>
      <div class="footer">
        <p>Thanks for visiting! Do visit again for more news updates.</p>
        <p>Contact us:</p>
        <p>Email: <a href="mailto:namit752@gmail.com">namit752@gmail.com</a></p>
        <p>Mobile: <a href="tel:+917678605936">7678605936</a></p>
      </div>
    </div>
  </div>
</template>

<script>
import EventCard from "@/components/EventCard.vue";
import EventService from "@/services/EventService.js";

export default {
  name: "Dashboard",
  components: {
    EventCard
  },
  data() {
    return {
      events: [],
      announcements: [
        "Internship openings available for Summer 2024!",
        "Annual employee event happening soon!",
        "Join our monthly webinar series on energy advancements."
      ]
    };
  },
  created() {
    EventService.getEvents()
      .then(response => {
        this.events = response.data;
      })
      .catch(error => {
        console.log(error);
      });
  }
};
</script>

<style scoped>
.dashboard {
  padding: 20px;
  background: linear-gradient(135deg, #e0f7fa, #006064);
  color: #fff;
  font-family: 'Arial', sans-serif;
  min-height: 100vh;
}

.dashboard h1 {
  font-size: 3rem;
  font-weight: bold;
  margin-bottom: 20px;
  color: #004d40;
  text-align: center;
  text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
}

.center {
  margin: 20px auto;
  display: block;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
}

.moving-banner {
  overflow: hidden;
  background-color: #004d40;
  color: #fff;
  font-size: 1.2rem;
  padding: 10px;
  border: 3px solid #006064;
  border-radius: 10px;
  margin-bottom: 20px;
  width: 100%;
  white-space: nowrap;
  position: relative;
}

.announcement-content {
  display: inline-block;
  padding-left: 100%; /* Starts the text off-screen to the right */
  animation: scroll-left 15s linear infinite; /* Infinite scrolling effect */
}

@keyframes scroll-left {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-100%);
  }
}

/* Glitter/Shimmer Effect */
.glitter-text {
  display: inline-block;
  background: linear-gradient(90deg, #ffffff, #ffd700, #ffffff); /* Gradient with gold shimmer */
  background-size: 200% 100%;
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
  animation: shimmer 2s linear infinite; /* Infinite shimmer effect */
}

@keyframes shimmer {
  0% {
    background-position: -200% 0;
  }
  100% {
    background-position: 200% 0;
  }
}

.content {
  padding: 20px;
  border-radius: 10px;
  background: #ffffff;
  color: #333;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

.events {
  display: flex;
  justify-content: space-around;
  align-items: stretch;
  padding: 20px;
  gap: 20px;
}

.EventCard {
  flex: 1;
  max-width: 300px;
  min-width: 250px;
  height: 450px;
  background: #ffffff;
  border: 4px solid #004d40;
  border-radius: 15px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  padding: 20px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.EventCard img {
  width: 100%;
  height: auto;
  border-radius: 10px;
}

.EventCard h3 {
  font-size: 1.2rem;
  color: #333;
  text-align: center;
  margin-top: 10px;
}

.EventCard p {
  font-size: 1rem;
  color: #555;
  text-align: center;
}

.EventCard:hover {
  transform: translateY(-10px);
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.3);
}

.footer-line {
  margin-top: 40px;
  border-top: 2px solid #004d40;
  opacity: 0.8;
}

.footer {
  margin-top: 20px;
  padding: 20px;
  background: linear-gradient(135deg, #004d40, #00796b);
  color: #ffffff;
  text-align: center;
  border-radius: 0 0 10px 10px;
  box-shadow: 0 -4px 10px rgba(0, 0, 0, 0.2);
}

.footer p {
  margin-bottom: 8px;
}

.footer a {
  color: #b2dfdb;
  text-decoration: none;
}

.footer a:hover {
  color: #e0f7fa;
  text-decoration: underline;
}

@media (max-width: 600px) {
  .dashboard h1 {
    font-size: 2rem;
  }
  .content {
    padding: 15px;
  }
  .footer {
    padding: 15px;
  }
}
</style>
