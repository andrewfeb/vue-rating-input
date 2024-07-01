<script setup>
import { StarIcon as StarIconOutline } from '@heroicons/vue/24/outline';
import { StarIcon as StarIconSolid } from '@heroicons/vue/24/solid';

defineProps({
  count: {
    type: Number,
    default: 5,
  },
  modelValue: {
    type: Number
  }
});

const emit = defineEmits({
  "update:modelValue": (input) => {
    if (input && typeof input === "number") {
      return true
    } else{
      console.log('Input must be number')
      return false
    }
  }
});

const updateRating = (rating) => {
  emit('update:modelValue', rating)
}
</script>

<template>
  <div 
    tabindex="0" 
    autofocus 
    data-test="rating-wrapper" 
    :class="[modelValue === count ? 'perfect-rating' : '']"
  >
    <button tabindex="-1"
      data-test="rating-button"
      v-for="star in count"
      :key="star"
      @click="updateRating(star)"
    >
      <template v-if="modelValue >= star">
        <StarIconSolid data-test="solid-star" class="solid-star" />
      </template>
      
      <template v-else>
        <StarIconOutline data-test="outline-star" class="outline-star" />
      </template>
    </button>
  </div>
</template>
