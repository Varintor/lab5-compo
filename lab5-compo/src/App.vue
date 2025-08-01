<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { useMessageStore } from '@/stores/message'
import { storeToRefs } from 'pinia';
const store = useMessageStore()
const { message } = storeToRefs(store)
</script>

<template>
  <div class="text-center font-sans text-gray-700 antialias">
    <header>
      <div id="flashMessage" class="animate-fade bg-red-500 p-4 text-black border border-black" v-if="message">
        <h4>{{ message }}</h4>
      </div>
      <div class="wrapper">
        <nav class="py-6">
          <RouterLink class="font-bold text-gray-700"router-link-exact-active-class="text-green-500" :to="{name: 'event-list-view'}">Event</RouterLink> | 
          <RouterLink class="font-bold text-gray-700"router-link-exact-active-class="text-green-500" :to="{name: 'about'}">About</RouterLink> |
          <RouterLink class="font-bold text-gray-700"router-link-exact-active-class="text-green-500" :to="{name: 'students'}">Student</RouterLink>
        </nav>
        <div class="page-size-selector">
          <span>Page Size: </span>
          <RouterLink :to="{ name: 'event-list-view', query: { page: 1, size: 2 }}">2</RouterLink> |
          <RouterLink :to="{ name: 'event-list-view', query: { page: 1, size: 3 }}">3</RouterLink> |
          <RouterLink :to="{ name: 'event-list-view', query: { page: 1, size: 4 }}">4</RouterLink> 
        </div>
      </div>
    </header>

    <RouterView />
  </div>
</template>


<style>

nav{
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active{
  color: #42b983;
}

h2{
  font-size: 20px;
}

.page-size-selector {
  margin-top: 10px;
}

.page-size-selector a {
  margin: 0 4px;
  font-weight: normal;
}
@keyframes yellowfade {
  from { background-color: yellow; }
  to { background-color: transparent; }
}
#flashMessage {
  animation: yellowfade 3s ease-in-out;
}
</style>
