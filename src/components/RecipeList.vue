<script setup>

defineProps(['recipes']);
defineEmits(['select-recipe']);
</script>

<template>
  <div>
    <h2>Recipes</h2>
    <ul>
      <li v-for="recipe in recipes" :key="recipe.name">
        <button @click="$emit('select-recipe', recipe)">
          {{ recipe.name }}
        </button>
      </li>
    </ul>
  </div>
</template>
