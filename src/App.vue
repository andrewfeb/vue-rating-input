<script setup>
import { ref } from "vue";
import RatingInput from "./components/RatingInput.vue";

const rating = ref(0);

const onPress = (e) => {
  // if key press is number 0-9
  if (e.keyCode >= 48 && e.keyCode <=57) {
    rating.value = parseInt(e.key)
  // if pressing the ArrowDown or ArrowLeft key should decrement the rating by 1
  }else if (e.keyCode == 37 || e.keyCode == 40) {
    if (rating.value > 0) {
      rating.value -= 1;
    }
  // if pressing the ArrowUp or ArrowrRight key should increment the rating by 1
  }else if (e.keyCode == 38 || e.keyCode == 39) {
    if (rating.value < 10) {
      rating.value += 1;
    }
  }
}
</script>

<template>
  <h1>Rating Input Feature Challenge</h1>
  <RatingInput v-model="rating" :count="10" @keyup="onPress"/>
  <p>You Selected Rating: {{ rating || "NA" }}</p>
</template>
