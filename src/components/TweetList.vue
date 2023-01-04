<script setup lang="ts">
import { defineProps } from 'vue'

type Tweet = {
  id: number,
  content: string,
}

interface Props {
  tweets: Tweet[]
}

// NOTE: これと同義. defineProps<{ id: number, content: string }>()
defineProps<Props>()

const deleteContent = (id: number) => {
  console.log(id)
}
</script>

<template>
  <li v-for="(tweet, index) in tweets" :key="tweet.id">
    <span>{{ tweet.content }}</span>
    <button @click="deleteContent(index)">delete</button>
  </li>
</template>

<style scoped>
li {
  list-style: none;
  width: 100%;
  background-color: gray;
  margin: 10px 0;
  padding: 5px 0;
  border-radius: 5px;
}
</style>
