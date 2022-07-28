<script setup>
import { ref } from "@vue/reactivity";

const anime = ref("fade");
</script>

<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </nav>
    <div class="check">
      <label>
        <input type="radio" v-model="anime" name="anime" value="fade" /> Fade
        <input type="radio" v-model="anime" name="anime" value="slide" /> slide
        <input type="radio" v-model="anime" name="anime" value="slide-down" />
        slide-down
        <input type="radio" v-model="anime" name="anime" value="grow-in" />
        grow-in
        <input type="radio" v-model="anime" name="anime" value="grow-out" />
        grow-out
        <span class="checkmark"></span>
      </label>
    </div>
    <router-view v-slot="{ Component }">
      <transition :name="anime" mode="out-in">
        <!-- <transition name="fade" mode="out-in"> -->
        <Component :is="Component" />
      </transition>
    </router-view>
  </div>
</template>

<style>
/* #app {
  text-align: center;
  font-size: 1rem;
  font-weight: bold;
  color: #333;
  background-color: darkgrey;
  padding: 1rem;
  
}
#app nav {
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 1rem;
} */

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Roboto", sans-serif;
}
nav {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1rem;
}

nav a {
  margin: 0 1rem;
  color: #333;
  text-decoration: none;
  padding: 0.5rem;
  border: 1px solid #333;
  border-radius: 0.25rem;
  font-size: 1rem;
}

nav a:hover,
nav a.router-link-exact-active {
  color: crimson;
  text-decoration: underline;
}

.check {
  display: flex;
  align-items: center;
  justify-content: center;
}

.check label {
  margin: 0 0.5rem;
}
main {
  padding: 1rem;
  max-width: 768px;
  margin: 0 auto;

  will-change: transform, opacity;
}

h1 {
  margin-bottom: 1.5rem;
}
p {
  margin-bottom: 1rem;
}

img {
  width: 100%;
  max-width: 100%;
  margin-bottom: 1.5rem;
  border-radius: 0.25rem;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  /* transform: translateY(1rem); */
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease-out;
}

.slide-enter-from,
.slide-leave-to {
  opacity: 0;
  transform: translateX(-100%);
}

.slide-enter-active,
.slide-leave-active {
  transition:  0.3s ease-out;
}

.slide-down-enter-from,
.slide-down-leave-to {
  opacity: 0;
  transform: translateY(300%);
}

.slide-down-enter-active,
.slide-down-leave-active {
  transition:  0.3s ease-out;
}

.grow-in-enter-from,
.grow-in-leave-to {
  opacity: 0;
  transform: scale(0.3);
}

.grow-in-enter-active,
.grow-in-leave-active {
  transition:  0.3s ease-out;
}

.grow-out-enter-from,
.grow-out-leave-to {
  opacity: 0;
  transform: scale(1.9);
}

.grow-out-enter-active,
.grow-out-leave-active {
  transition:  0.3s ease-out;
}
</style>
