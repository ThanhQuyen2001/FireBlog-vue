<template>
  <div class="app-wrapper">
    <div class="app">
      <Navigation v-if="!navigation" />
      <router-view />
      <Footer v-if="!navigation" />
    </div>
  </div>
</template>

<script>
import Navigation from './components/Navigation.vue'
import Footer from './components/Footer.vue'
export default {
  name: "app",
  components: {Navigation, Footer},
  data() {
    return {
      navigation: null,
    };
  },
  created() {
    this.checkRoute();
  },
  mounted() {},
  methods: {
    checkRoute() {
      if(this.$route.name === "Login" || this.$route.name === "Register" ||this.$route.name === "ForgotPassword"){
        this.navigation = true;
        return;
      } 
      this.navigation = false;
    }
  },
  watch: {
    $route() {
      this.checkRoute();
    }
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500;600;700&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Quicksand", sans-serif;
}

.app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.container {
  max-width: 1440px;
  margin: 0 auto;
}

.link {
  cursor: pointer;
  text-decoration: none;
  text-transform: uppercase;
  color: black;
}

.link-light {
  color: #fff;
}
.arrow {
  margin-left: 8px;
  width: 12px;
}
.arrow path {
  fill: #000;
}
.arrow-light path {
  fill: #fff;
}
button,
.router-button {
  transition: all 0.5s ease;
  cursor: pointer;
  margin-top: 24px;
  padding: 12px 24px;
  background-color: #303030;
  color: #fff;
  border-radius: 20px;
  border: none;
  text-transform: uppercase;
}
button:hover,
.router-button:hover {
  background-color: rgba(48, 48, 48, 0.7);
}
button:focus,
.router-button:focus {
  outline: none;
}
.blog-card-wrap {
  position: relative;
  padding: 80px 16px;
  background-color: #f1f1f1;
}
@media (min-width: 500px) {
  .blog-card-wrap {
    padding: 100px 16px;
  }
}
.blog-cards {
  display: grid;
  gap: 32px;
  grid-template-columns: 1fr;
}
@media (min-width: 500px) {
  .blog-cards {
    grid-template-columns: repeat(2, 1fr);
  }
}
@media (min-width: 900px) {
  .blog-cards {
    grid-template-columns: repeat(3, 1fr);
  }
}
@media (min-width: 1200px) {
  .blog-cards {
    grid-template-columns: repeat(4, 1fr);
  }
}
</style>
