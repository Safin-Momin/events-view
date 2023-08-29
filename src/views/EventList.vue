<script setup>
import { ref, onMounted } from 'vue'
import EventCard from '../components/EventCard.vue'
import EventService from '../services/EventService'

const events = ref(null)
onMounted(() => {
  EventService.getEvents()
    .then((response) => {
      events.value = response.data
    })
    .catch((error) => {
      console.log(error)
    })
})
</script>

<template>
  <div class="container details">
    <h1>Events</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.list {
  background-color: rgb(36, 195, 195);
  color: #444;
  border-radius: 5px;
  box-shadow: 0 0 10px #666;
  padding: 1px 10px 10px;
  text-align: center;
  margin: 20px 0;
  min-width: 300px;
}

h1 {
  color: #444;
}

* {
  text-decoration: none;
}
</style>
