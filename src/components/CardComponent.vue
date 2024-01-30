<template>
  <main class="wrapper">
    <section class="cardContainer">
      <img src="../assets/icon-star.svg" alt="icon star" />
      <h1 class="rating-title">How did we do?</h1>
      <p class="rating-description">Please let us know how we did with your support request. All feedback is appreciated
        to help us improve our
        offering!</p>
      <nav class="rating-navbar">
            <button class="rating-link" v-for="item in items" :key="item.id" @click="handleClick(item.value)">{{ item.title }}</button>
          </nav>
          <h5 v-show="!selectedValue && isSubmitted" >Please select a rating</h5>
          <button class="rating-btn" @click="handleSubmit">
            Submit
          </button>
    </section>
  </main>
  
</template>

<script>
export default {
  name: "CardComponent",
  data() {
    return {
      name: "Card",
      isSubmitted: false,
      selectedValue: null,
      items: [{
        title: '1',
        value: '1',
      },
      {
        title: '2',
        value: '2',
      },
      {
        title: '3',
        value: '3',
      },
      {
        title: '4',
        value: '4',
      },
      {
        title: '5',
        value: '5',
      }
      ]
    }
  },
  methods:{
      handleClick (value){
        this.selectedValue = value
      },
      handleSubmit(){
        this.isSubmitted = true
        console.log("Selected value", this.selectedValue)
      }
    }
};
</script>

<style lng="scss" scoped>
@import "./style.scss";
</style>
