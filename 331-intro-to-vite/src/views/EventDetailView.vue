<script setup lang="ts">
import { ref, onMounted } from 'vue'
import Event from '@/types/Event'
import EventService from '@/services/EventService'
const event = ref<Event>(null)
const eventId = 5928101
onMounted(() => {
  EventService.getEvent(eventId)
    .then((response) => {
      event.value = response.data
    })
    .catch((error) => {
      console.error('There was an error fetching the event:', error)
    })
})
</script>
 
<template>
  <div v-if="event">
    <hl>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </diy>
</template>
 