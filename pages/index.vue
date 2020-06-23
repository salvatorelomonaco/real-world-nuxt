<template>
  <!-- homepage -->
  <div>
    <h1>Events</h1>
    <EventCard
      v-for="(event, index) in events"
      :key="index"
      :event="event"
      :data-index="index"
    />
  </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue'
export default {
  components: {
    EventCard,
  },
  // con asyncData Nuxt aspettera' che la chiamata API finisca per renderizare la componente
  async asyncData({ $axios, error }) {
    try {
      // await ci permette di far runnare  prima la chiamata API e poi il codice js
      const response = await $axios.get('http://localhost:3000/events')
      return {
        events: response.data,
      }
    } catch (e) {
      error({
        statusCode: 500,
        message: 'Unable to fetch events at thi time. Please try again',
      })
    }
  },
  // proprieta' usata da vue-meta
  head() {
    return {
      // titolo per la pagina
      title: 'Event Listing',
    }
  },
}
</script>
