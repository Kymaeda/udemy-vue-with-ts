<script setup lang="ts">
import { ref } from "vue";

const tweets = ref([
  { id: 1, content: 'ツイートの中身1' },
  { id: 2, content: 'ツイートの中身2' },
  { id: 3, content: 'ツイートの中身3' },
])

const inputContent = ref<string>('')
const submit = () => {
  tweets.value.push({ id: Math.random(), content: inputContent.value })
  inputContent.value = ''
}
</script>

<template>
  <div class="container">
    <h1>Tweets</h1>
    <div class="form-container">
      <input v-model="inputContent" />
      <button class="submit" @click="submit">post</button>
    </div>

    <div class="tweet-container">
      <ul class="tweet-list">
        <li v-for="tweet in tweets" :key="tweet.id">
          <span>{{ tweet.content }}</span>
          <button>delete</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
ul {
  margin: 0;
  padding: 0;
}
.container {
  width: 1280px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form-container {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  background-color: aliceblue;
  padding: 24px 0;
  width: 60%;
  height: 100px;
  margin-bottom: 12px;
  border-radius: 4px;
}

input {
  width: 50%;
  height: 25px;
  border-radius: 5px;
}

.tweet-container {
  width: 60%;
}

.tweet-list {
  list-style: none;
}

.tweet-list li {
  width: 100%;
  background-color: gray;
  margin: 10px 0;
  padding: 5px 0;
  border-radius: 5px;
}
</style>
