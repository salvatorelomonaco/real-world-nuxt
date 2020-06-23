<template>
  <!-- usare _ comunica a Nuxt di creare un segmento dinamico -->
  <div>
    <h1>Event #{{ id }}</h1>
  </div>
</template>

<script>
export default {
  computed: {
    id() {
      return this.$route.params.id
    },
  },
  // proprieta' usata da vue-meta
  head() {
    return {
      // titolo per la pagina
      title: 'Event #' + this.id,
      meta: [
        {
          // descrizione per la pagina
          hid: 'description',
          name: 'description',
          content: 'What you need to know about event #' + this.id,
        },
      ],
    }
  },
}
</script>
