<script setup>
defineProps({
  event: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <router-link :to="{ name: 'event-details', params: { id: event.id } }">
    <div class="list">
      <h2>{{ event.name }}</h2>
      <span>@{{ event.time }} on {{ event.date }}</span>
    </div>
  </router-link>
</template>
