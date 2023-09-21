<template>
  <div>
    Nombre de livre dans le rayon : {{ numberOfLikes }}
  </div>
</template>

<script setup>
defineProps({
  numberOfLikes: Number,
});
</script>
