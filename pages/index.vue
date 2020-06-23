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
  asyncData({ $axios, error }) {
    return $axios
      .get('http://localhost:3000/events')
      .then((response) => {
        return {
          events: response.data,
        }
      })
      .catch((e) => {
        // eslint-disable-next-line no-undef
        error({
          statusCode: 500,
          message: 'Unable to fetch events at thi time. Please try again',
        })
      })
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
