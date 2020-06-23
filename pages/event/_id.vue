<template>
  <!-- usare _ comunica a Nuxt di creare un segmento dinamico -->
  <div>
    <h1>{{ event.title }}</h1>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, error, params }) {
    try {
      const response = await $axios.get(
        'http://localhost:3000/events/' + params.id
      )
      return {
        event: response.data,
      }
    } catch (e) {
      error({
        statusCode: 500,
        message: 'Unable to fetch events #' + params.id,
      })
    }
  },
  // proprieta' usata da vue-meta
  head() {
    return {
      // titolo per la pagina
      title: this.event.title,
      meta: [
        {
          // descrizione per la pagina
          hid: 'description',
          name: 'description',
          content: 'What you need to know about ' + this.event.title,
        },
      ],
    }
  },
}
</script>
