<template>
  <div class="livre">
    <h2>{{ title }}</h2>
    <p>{{ author }}</p>
    <p>{{ pages }}</p>
    <p> {{ date }}</p>

    <button v-if="!isLiked" class="button-dislike" @click="$emit('like')">Dislike</button>
    <button v-else class="button-like" @click="$emit('dislike')">Like</button>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  author: String,
  pages: Number,
  date: String,
  isLiked: Boolean,
});

defineEmits(
    [
      'like',
      'dislike',
    ],
);

</script>

<style scoped>
.livre {
  border: 1px solid red;
  padding: 10px;
  margin: 10px;
}

.button-like {
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}

.button-dislike {
  background-color: #f44336;
  border: none;
  color: white;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}

</style>