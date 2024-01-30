<template id="app">
      <div id="app-container">
        <CardComponent />
  </div>
</template>

<script>
import CardComponent from "./components/CardComponent.vue";

export default {
  name: "app",
  components: {
    CardComponent,
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
