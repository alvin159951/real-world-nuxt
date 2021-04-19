<template>
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
import EventCard from "@/components/EventCard.vue";
import { mapState } from "vuex";
export default {
  head() {
    return {
      title: "Event Listing"
    };
  },
  async fetch(context) {
    try {
      await context.store.dispatch("events/fetchEvents");
    } catch (e) {
      context.error({ statusCode: 503, message: "Unable to fetch events" });
    }
  },
  components: {
    EventCard
  },
  computed: mapState({
    events: state => state.events.events
  })
};
</script>
