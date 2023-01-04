<script setup lang="ts">
import { ref } from "vue";
import TweetFormVue from "./TweetForm.vue";
import TweetListVue from "./TweetList.vue";

const tweets = ref([
  { id: 1, content: 'ツイートの中身1' },
  { id: 2, content: 'ツイートの中身2' },
  { id: 3, content: 'ツイートの中身3' },
])

const submit = (content: string) => {
  tweets.value.push({ id: Math.random(), content })
}
const deleteContent = (index: number) => {
  tweets.value.splice(index, 1)
}
</script>

<template>
  <div class="container">
    <h1>Tweets</h1>
    <TweetFormVue @submit="submit"/>
    <TweetListVue :tweets="tweets" @delete="deleteContent" />
  </div>
</template>

<style scoped>
.container {
  width: 1280px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
