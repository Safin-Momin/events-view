<script setup>
import { ref, onMounted } from 'vue'
import EventService from '../services/EventService.js'

const props = defineProps({
  id: {
    required: true
  }
})

const event = ref(null)

onMounted(() => {
  EventService.getEvent(props.id)
    .then((response) => {
      event.value = response.data
    })
    .catch((error) => {
      console.log(error)
    })
})
</script>

<template>
  <div class="container details">
    <div v-if="event">
      <div class="list">
        <h1>{{ event.name }} organised by {{ event.organisedBy }}</h1>
        <h4>{{ event.time }} on {{ event.date }} @ {{ event.location }}</h4>
        <h4>{{ event.coveredArea }} in {{ event.population }} Members</h4>
        <h3>{{ event.fee }}</h3>
      </div>
    </div>
    <router-link to="/" class="btn">Back</router-link>
  </div>
</template>

<style>
.details {
  min-height: 95vh;
}

.btn {
  padding: 8px 20px;
  color: #222;
  font-size: 1.3rem;
  border: none;
  transition: all 0.5s;
  box-shadow: 0 0 10px #999;
  margin-top: 5px;
  border-radius: 5px;
}

.btn:hover {
  background-color: rgb(36, 195, 195);
  color: #444;
}
</style>
