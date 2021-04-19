<template>
  <div>
    <h1>Create an Event</h1>
  </div>
</template>
<script>
export default {
  head() {
    return {
      title: "Event Listing"
    };
  },
  asyncData(context) {
    return context.$axios.get("http://localhost:3001/events").then(response => {
      return {
        events: response.data
      };
    });
  }
};
</script>
