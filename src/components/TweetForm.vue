<script setup lang="ts">
import { ref} from 'vue'

const inputContent = ref<string>('')
const inputArea = ref() // template refとリアクティブ名を同じにすれば、取得できる


const emit = defineEmits(['submit'])
const submit = () => {
  emit('submit', inputContent.value)
  inputContent.value = ''
  inputArea.value.focus()
}
</script>

<template>
  <div class="form-container">
    <input v-model="inputContent" ref="inputArea"/>
    <button class="submit" @click="submit">post</button>
  </div>
</template>

<style scoped>
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

</style>
