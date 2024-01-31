<template id="app">
      <div id="app-container">
        <RatingCard />
  </div>
</template>

<script>
import RatingCard from "./components/RatingCard.vue";

export default {
  name: "app",
  components: {
    RatingCard,
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
