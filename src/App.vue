<script setup>
import { ref } from 'vue';
import RecipeList from './components/RecipeList.vue';
import RecipeDetails from './components/RecipeDetails.vue';
import AddRecipeForm from './components/AddRecipeForm.vue';

const recipes = ref([]);
const selectedRecipe = ref(null);

const addRecipe = (newRecipe) => {
  recipes.value.push(newRecipe);
};

const selectRecipe = (recipe) => {
  selectedRecipe.value = recipe;
};
</script>

<template>
  <div id="app">
    <h1>Recipe Cost and Calorie Tracker</h1>
    <AddRecipeForm @add-recipe="addRecipe" />
    <RecipeList :recipes="recipes" @select-recipe="selectRecipe" />
    <RecipeDetails :recipe="selectedRecipe" />
  </div>
</template>
