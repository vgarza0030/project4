<script setup>
import { ref } from 'vue';

const emit = defineEmits(['add-recipe']);

const name = ref('');
const ingredientsInput = ref('');
const costsInput = ref('');
const caloriesInput = ref('');

const submitForm = () => {
  const ingredients = ingredientsInput.value.split(',').map((item) => item.trim());
  const costs = costsInput.value.split(',').map((item) => parseFloat(item.trim()));
  const calories = caloriesInput.value.split(',').map((item) => parseInt(item.trim()));

  const newRecipe = {
    name: name.value,
    ingredients,
    costs,
    calories,
  };

  emit('add-recipe', newRecipe);

  
  name.value = '';
  ingredientsInput.value = '';
  costsInput.value = '';
  caloriesInput.value = '';
};
</script>

<template>
  <div>
    <h2>Add New Recipe</h2>
    <form @submit.prevent="submitForm">
      <label for="name">Recipe Name:</label>
      <input type="text" v-model="name" required />

      <label for="ingredients">Ingredients (comma-separated):</label>
      <input type="text" v-model="ingredientsInput" required />

      <label for="costs">Costs (comma-separated):</label>
      <input type="text" v-model="costsInput" required />

      <label for="calories">Calories (comma-separated):</label>
      <input type="text" v-model="caloriesInput" required />

      <button type="submit">Add Recipe</button>
    </form>
  </div>
</template>
