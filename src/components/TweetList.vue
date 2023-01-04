<script setup lang="ts">
// viteなので、defineProps/defineEmitsは不要
// import { defineProps } from 'vue'

type Tweet = {
  id: number,
  content: string,
}

interface Props {
  tweets: Tweet[]
}

// NOTE: これと同義. defineProps<{ id: number, content: string }[]>()
defineProps<Props>()

const emit = defineEmits(['delete'])
const deleteContent = (index: number) => {
  emit('delete', index)
}
</script>

<template>
  <div class="tweet-container">
    <p v-if="tweets.length == 0">Submit your first tweet!!!!</p>
    <ul v-else>
      <li v-for="(tweet, index) in tweets" :key="tweet.id">
        <span>{{ tweet.content }}</span>
        <button @click="deleteContent(index)">delete</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.tweet-container {
  width: 60%;
}

ul {
  margin: 0;
  padding: 0;
}

li {
  list-style: none;
  width: 100%;
  background-color: gray;
  margin: 10px 0;
  padding: 5px 0;
  border-radius: 5px;
}
</style>
