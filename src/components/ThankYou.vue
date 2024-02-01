<template>
  <section class="thankYouContainer">
    <img
      src="../assets/illustration-thank-you.svg"
      alt="Illustration thank you"
    />
    <h4 class="thankYouSteps">You selected {{ selectedRating }} out of 5</h4>
    <h1 class="thankYou-title">Thank you!</h1>
    <p class="thankYou-description">
      We appreciate you taking the time to give a rating. If you ever need more
      support, don’t hesitate to get in touch!
    </p>
  </section>
</template>

<script>
export default {
  name: "ThankYou",
  props: {
    selectedRating: String,
  },
  data() {
    return {
      name: "ThankYou",
    };
  },
};
</script>

<style lng="scss" scoped>
@import "./style.scss";
</style>
