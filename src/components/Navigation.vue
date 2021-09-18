<template>
<header>
  <nav class="container">
    <div class="branding">
      <router-link class="header" :to="{ name: 'Home' }">FireBlogs</router-link>
    </div>
    <div class="nav-links">
      <ul class="nav-links__list" v-show="!mobile">
        <router-link class="link" :to="{ name: 'Home'}">Home</router-link>
        <router-link class="link" :to="{ name: 'Blogs'}">Blog</router-link>
        <router-link class="link" to="#">Create Post</router-link>
        <router-link class="link" :to="{ name: 'Login'}">Login/Register</router-link>
      </ul>
    </div>
  </nav>
  <menuIcon @click="toggleMobileNav" class="menu-icon" v-show="mobile" />
  <transition name="mobile-nav">
    <ul class="mobile-nav" v-show="mobileNav">
        <router-link class="link" :to="{ name: 'Home'}">Home</router-link>
        <router-link class="link" :to="{ name: 'Blogs'}">Blog</router-link>
        <router-link class="link" to="#">Create Post</router-link>
        <router-link class="link" :to="{ name: 'Login'}">Login/Register</router-link>
      </ul>
  </transition>
</header>
</template>

<script>
import menuIcon from '../assets/Icons/bars-regular.svg';
export default {
  name: 'navigation',
  components: {
    menuIcon,
  },
  data() {
    return {
      mobile: null,
      mobileNav: null,
      windownWidth: null,
    }
  },
  created() {
    window.addEventListener('resize', this.checkScreen);
    this.checkScreen();
  },
  methods: {
    checkScreen() {
      this.windownWidth = window.innerWidth;
      if(this.windownWidth <= 750) {
        this.mobile = true;
        return;
      }
      this.mobile = false;
      this.mobileNav = false;
    },
    toggleMobileNav() {
      this.mobileNav = !this.mobileNav;
    }
  }
}
</script>

<style scoped>
header {
  background-color: #fff;
  padding: 0 25px;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
  z-index: 99;
}
.nav-links {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  flex: 1;
}
.nav-links__list,
.nav-links__list .link{
  margin-right: 32px;
}
.nav-links__list .link:last-child {
  margin-right: 0;
}
.link {
  font-weight: 500;
  padding: 0 8px;
  transition: color 0.3s ease;
}
.link:hover {
  color: #1eb8b8;
}
nav {
  display: flex;
  padding: 25px 0;
}
.brading {
  display: flex;
  align-items: center;
}
.header {
  font-weight: 600;
  font-size: 24px;
  text-decoration: none;
  color: #000;
}
.menu-icon {
  cursor: pointer;
  position: absolute;
  top: 32px;
  right: 25px;
  height: 25px;
  width: auto;
}

.mobile-nav {
  padding: 20px;
  width: 70%;
  max-width: 250px;
  display: flex;
  flex-direction: column;
  position: fixed;
  height: 100%;
  background-color: #303030;
  top: 0;
  left: 0;
}
.mobile-nav .link {
  padding: 15px 0;
  color: #fff;
}
.mobile-nav-enter-active,
.mobile-nav-leave-active {
  transition: all 1s ease;
}
.mobile-nav-enter {
  transform: translateX(-250px);
}
.mobile-nav-enter-to {
  transform: translateX(0);
}
.mobile-nav-leave {
  transform: translateX(0);
}
.mobile-nav-leave-to {
  transform: translateX(-250px);
}
</style>