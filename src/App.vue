<template>
  <div id="app">
    <nav :class="{ 'black-nav': isAboutPage }">
      <router-link to="/">News</router-link> |
      <router-link to="/about">About</router-link>
    </nav>

    <router-view />
  </div>
</template>

<script>
export default {
  data() {
    return {
      isAboutPage: false,
    };
  },
  watch: {
    $route(to) {
      // Check if the route is "about" and set isAboutPage accordingly
      this.isAboutPage = to.path === "/about";
    }
  },
  mounted() {
    // Set the initial state when the component mounts
    this.isAboutPage = this.$route.path === "/about";
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: linear-gradient(45deg, #f3f5f9, #dde1e7);
  min-height: 100vh;
  padding: 20px;
  position: relative;
  overflow: hidden;
}

#app::before,
#app::after {
  content: "";
  position: absolute;
  width: 500px;
  height: 500px;
  background: rgba(255, 255, 255, 0.15);
  border-radius: 50%;
  pointer-events: none;
  animation: float 8s ease-in-out infinite;
}

#app::before {
  top: -200px;
  left: -150px;
}

#app::after {
  bottom: -200px;
  right: -150px;
  animation-delay: 4s;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(20px);
  }
}

nav {
  padding: 20px 40px;
  margin-bottom: 30px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  background: linear-gradient(90deg, #42b983, #3a7c7d);
  border-radius: 10px;
  display: inline-block;
  transition: transform 0.3s ease, background-color 0.3s ease;
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 1px;
}

/* nav {
  width: 100%; /* Ensure the navbar spans the full width /
  padding: 20px 40px;
  margin-bottom: 30px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  background: linear-gradient(90deg, #42b983, #3a7c7d);
  border-radius: 0; /* Remove rounded corners /
  display: block; /* Ensure it takes up the full width /
  transition: transform 0.3s ease, background-color 0.3s ease;
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 1px;
}
*/
/* New class to turn nav background black on About page */
.black-nav {
  background: #000;
}

nav:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.15);
}

nav a {
  color: #ffffff;
  text-decoration: none;
  padding: 8px 15px;
  transition: all 0.3s ease;
  border-radius: 5px;
  position: relative;
  overflow: hidden;
  display: inline-block;
}

nav a::before {
  content: "";
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: rgba(255, 255, 255, 0.2);
  transition: transform 0.3s ease;
  transform: skewX(-30deg) translateX(0);
}

nav a:hover::before {
  transform: skewX(-30deg) translateX(100%);
}

nav a:hover {
  background-color: rgba(255, 255, 255, 0.2);
  color: #ffffff;
}

nav a.router-link-exact-active {
  background-color: rgba(255, 255, 255, 0.2);
  color: #ffffff;
  box-shadow: 0 0 10px rgba(66, 185, 131, 0.3), 0 0 15px rgba(66, 185, 131, 0.2);
}

h4 {
  font-size: 20px;
  color: #333;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.1);
  margin-top: 30px;
}
</style>
