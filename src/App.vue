<template id="app">
  <div id="app-container">
    <RatingCard
      :ratingTitle="ratingTitle"
      :ratingDescription="ratingDescription"
    />
  </div>
</template>

<script>
import RatingCard from "./components/RatingCard.vue";

export default {
  name: "app",
  components: {
    RatingCard,
  },
  data() {
    return {
      ratingTitle: "How did we do?",
      ratingDescription:
        "Please let us know how we did with your support request. All feedback is appreciated to help us improve our offering!",
    };
  },
};
</script>

<style>
#app-container {
  background-color: hsl(216, 12%, 8%);
  height: 100vh;
  color: white;
  display: flex;
}
</style>
