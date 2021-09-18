<template>
  <footer>
    <div class="container">
      <div class="left">
        <div class="col-1">
          <router-link class="header" :to="{ name: 'Home' }">FireBlogs</router-link>
          <ul>
            <li>
              <a href="#"><youtube class="svg-icon"></youtube></a>
            </li>
            <li>
              <a href="#"><twitter class="svg-icon"></twitter></a>
            </li>
            <li>
              <a href="#"><instagram class="svg-icon"></instagram></a>
            </li>
            <li>
              <a href="#"><linkedin class="svg-icon"></linkedin></a>
            </li>
          </ul>
        </div>
        <div class="col-2">
          <ul>
            <router-link class="link" :to="{ name: 'Home' }">Home</router-link>
            <router-link class="link" :to="{ name: 'Blogs' }">Blogs</router-link>
            <router-link v-if="user" class="link" to="#">Create Post</router-link>
            <router-link v-if="!user" class="link" :to="{ name: 'Login' }">Login In / Register</router-link>
          </ul>
        </div>
      </div>
      <div class="right">
        <p>Copyright 2021 All Rights Reverved</p>
      </div>
    </div>
  </footer>
</template>

<script>
import youtube from '../assets/Icons/youtube-brands.svg';
import twitter from '../assets/Icons/twitter-brands.svg';
import instagram from '../assets/Icons/instagram-brands.svg';
import linkedin from '../assets/Icons/linkedin-brands.svg';
export default {
  name: 'footer-vue',
  components: {
    youtube,
    twitter,
    instagram,
    linkedin
  },
  data(){
    return {
      user: null
    }
  }
}
</script>

<style scoped>
footer {
  margin-top: auto;
  padding: 100px 25px;
  background-color: #303030;
}
footer .container {
  display: flex;
  flex-direction: column;
  gap: 32px; 
}
@media (min-width: 800px) {
  footer .container {
    flex-direction: row;
    gap: 0;
  }
}
.container > div {
  display: flex;
  flex: 1;
}
.left {
  gap: 32px;
  color: #fff;
  display: flex;
  flex-direction: column;
  align-items: center;
}
@media (min-width: 800px) {
  .left {
    gap: 0;
    flex-direction: row;
    align-items: initial;
  }
}
.header {
  text-align: center;
  font-size: 24px;
  color: #fff;
  text-decoration: none;
  font-weight: 600;
}
@media (min-width: 800px) {
  .header {
    text-align: initial;
  }
}
.left ul {
  gap: 16px;
  list-style: none;
  display: flex;
}
.col-1,
.col-2 {
  gap: 32px;
  display: flex;
  flex: 1;
}
@media (min-width: 800px) {
  .col-1,
  .col-2 {
    gap: 0;
  }
}
.col-1 {
  flex-direction: column;
}
.col-1 h2 {
  text-align: center;
}
@media (min-width: 800px) {
  .col-1 h2 {
    text-align: initial;
  }
}
.col-1 ul {
  margin-top: auto;
}
.col-1 ul li {
  display: flex;
  align-items: center;
}
.svg-icon {
  width: 24px;
  height: auto;
  color: #fff;
}
.col-2 ul {
  height: 100%;
  justify-content: center;
  flex-wrap: wrap;
}
@media (min-width: 800px) {
  .col-2 ul {
    flex-direction: column;
  }
}
.col-2 .link {
  font-size: 16px;
  font-weight: 500;
  color: #fff;
  text-decoration: none;
}
.right {
  gap: 32px;
  color: #fff;
  align-items: center;
  flex-direction: column;
}
@media (min-width: 800px) {
  .right {
    align-items: flex-end;
    gap: 0;
  }
}
p {
  margin-top: auto;
}
</style>