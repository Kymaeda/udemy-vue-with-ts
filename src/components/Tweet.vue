<script setup lang="ts">
import { ref } from "vue";
import TweetFormVue from "./TweetForm.vue";
import TweetListVue from "./TweetList.vue";

const tweets = ref([
  { id: 1, content: 'ツイートの中身1' },
  { id: 2, content: 'ツイートの中身2' },
  { id: 3, content: 'ツイートの中身3' },
])

// const inputContent = ref<string>('')
// const inputArea = ref() // template refとリアクティブ名を同じにすれば、取得できる
// const submit = () => {
//   tweets.value.push({ id: Math.random(), content: inputContent.value })
//   inputContent.value = ''
//   inputArea.value.focus()
// }
const deleteContent = (index: number) => {
  tweets.value.splice(index, 1)
}
</script>

<template>
  <div class="container">
    <h1>Tweets</h1>
    <TweetFormVue />

    <div class="tweet-container">
      <p v-if="tweets.length == 0">Submit your first tweet!!!!</p>
      <ul v-else>
        <TweetListVue :tweets="tweets" />
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

.tweet-container {
  width: 60%;
}
</style>
