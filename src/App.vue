<template>
  <Livre v-for="livre in livres"
         :title="livre.title"
         :author="livre.author"
         :pages="livre.pages"
         :date="livre.date"
         :is-liked="likes.includes(livre.title)"

         @like="() => likes.push(livre.title)"
         @dislike="() => (likes = likes.filter(b =>  b !== livre.title))"
  />
  <Rayon :number-of-likes="likes.length"/>

  <pre>{{ JSON.stringify(likes, null, 2) }}</pre>
</template>

<script setup>
import {ref} from 'vue';
import Livre from './components/Livre.vue';
import Rayon from '@/components/Rayon.vue';

const likes = ref([]);

const livres = ref(null);

(async () => {livres.value = await fetch('src/assets/livres.json').then(res => res.json());})();
</script>

<style scoped>

</style>
