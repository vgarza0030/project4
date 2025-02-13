<script setup>
import { computed } from 'vue';

const props = defineProps(['recipe']);

const totalCost = computed(() => 
  props.recipe ? props.recipe.costs.reduce((sum, cost) => sum + cost, 0) : 0
);

const totalCalories = computed(() => 
  props.recipe ? props.recipe.calories.reduce((sum, cal) => sum + cal, 0) : 0
);
</script>

<template>
  <div v-if="recipe">
    <h2>Details for {{ recipe.name }}</h2>
    <p><strong>Ingredients:</strong> {{ recipe.ingredients.join(', ') }}</p>
    <p><strong>Total Cost:</strong> ${{ totalCost.toFixed(2) }}</p>
    <p><strong>Total Calories:</strong> {{ totalCalories }} kcal</p>
  </div>
</template>
