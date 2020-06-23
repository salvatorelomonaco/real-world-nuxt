<template>
  <!-- pagina per creare eventi -->
  <div>
    <h1>Create an event</h1>
  </div>
</template>

<script>
export default {
  // proprieta' usata da vue-meta
  head() {
    return {
      // titolo per la pagina
      title: 'Create an Event',
      meta: [
        {
          // descrizione per la pagina
          hid: 'description',
          name: 'description',
          content: 'You can create a new event in your neighborhood',
        },
      ],
    }
  },
}
</script>
