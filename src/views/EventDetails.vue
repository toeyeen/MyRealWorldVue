<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
import EventService from '../EventService'
export default {
  props: {
    id: {
      type: [String, Number],
      required: true
    }
  },
  data() {
    return {
      event: null
    }
  },
  created() {
    // fetch event (by id) and set local event data
    EventService.getEvent(this.id)
      .then(res => {
        this.event = res.data
      })
      .catch(err => console.log(err))
  }
}
</script>
