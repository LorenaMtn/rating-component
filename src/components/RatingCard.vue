<template>
  <main>
    <main
      class="wrapper"
      @mouseleave="onMouseLeave"
      @mouseover="onMouseMove"
      @mouseenter="onMouseEnter"
      :class="{ hovered: isHovered }"
    >
      <section class="card-container" v-if="!isSubmitted">
        <img src="../assets/icon-star.svg" alt="icon star" />
        <h1 class="rating-title">{{ ratingTitle }}</h1>
        <p class="rating-description">{{ ratingDescription }}</p>
        <nav class="rating-navbar">
          <button
            class="rating-link"
            :class="{ 'rating-link-active': selectedValue === item.value }"
            v-for="item in items"
            :key="item.id"
            @click="handleClick(item.value)"
          >
            {{ item.title }}
          </button>
        </nav>
        <span v-show="selectedValue === null && isClicked"
          >Please select a rating</span
        >
        <button ref="submit" class="rating-btn" @click="handleSubmit">
          Submit
        </button>
      </section>
      <ThankYou v-if="isSubmitted" :selectedRating="selectedValue" />
      <div class="glade" />
    </main>
  </main>
</template>

<script>
import { ref } from "vue";
import ThankYou from "./ThankYou.vue";

const boundingRef = ref(null);

export default {
  name: "CardComponent",
  components: {
    ThankYou,
  },
  data() {
    return {
      name: "Card",
      isHovered: false,
      isClicked: false,
      isSubmitted: false,
      selectedValue: null,
      rotationX: 0,
      rotationY: 0,
      items: [
        {
          title: "1",
          value: "1",
        },
        {
          title: "2",
          value: "2",
        },
        {
          title: "3",
          value: "3",
        },
        {
          title: "4",
          value: "4",
        },
        {
          title: "5",
          value: "5",
        },
      ],
    };
  },
  methods: {
    handleClick(value) {
      this.selectedValue = value;
    },
    handleSubmit() {
      this.isClicked = true;
      if (this.selectedValue) {
        this.isSubmitted = true;
      }
    },
    onMouseLeave() {
      this.isHovered = false;
      boundingRef.current = null;
    },
    onMouseEnter(ev) {
      boundingRef.current = ev.currentTarget.getBoundingClientRect();
    },
    onMouseMove(ev) {
      this.isHovered = true;
      if (!boundingRef.current) return;
      const x = ev.clientX - boundingRef.current.left;
      const y = ev.clientY - boundingRef.current.top;
      const xPercentage = x / boundingRef.current.width;
      const yPercentage = y / boundingRef.current.height;
      const xRotation = (xPercentage - 0.5) * 5;
      const yRotation = (0.5 - yPercentage) * 5;

      this.rotationX = xRotation;
      this.rotationY = yRotation;

      ev.currentTarget.style.setProperty("--x-rotation", `${yRotation}deg`);
      ev.currentTarget.style.setProperty("--y-rotation", `${xRotation}deg`);
      ev.currentTarget.style.setProperty("--x", `${yRotation * 100}%`);
      ev.currentTarget.style.setProperty("--y", `${xRotation * 100}%`);
    },
  },
  props: {
    ratingTitle: String,
    ratingDescription: String,
  },
};
</script>

<style lng="scss" scoped>
@import "./style.scss";
</style>
