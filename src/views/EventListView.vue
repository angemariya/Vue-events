<script setup>
import EventCard from '@/components/EventCard.vue'
import EventService from '@/services/EventService.js'
import { onMounted, ref } from 'vue'

const events = ref(null)

onMounted(async() => {
  const data = await EventService.getEvents()
  const eventsData = data.data;
  events.value = eventsData
})
</script>

<template>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}

</style>
