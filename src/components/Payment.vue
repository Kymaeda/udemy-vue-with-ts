<script setup lang="ts">
import { ref, reactive } from 'vue'

const item1 = ref<string>('カレーライス')
const price1 = 400
const url1 = 'https://pkg.navitime.co.jp/matsuyafoods/spot/detail?code=0000001506'

const item2 = reactive({
  name: 'ハンバーグ',
  price: 1000,
  url: 'https://www.nakaita.com/shop/shop-0-97/'
})

const buy = (itemName: string) => alert(`${itemName}を購入する`)
const add = (e: any) => {
  item2.name = e.currentTarget.value
}
</script>

<template>
  <div class="container">
    <h1>最近の支出</h1>
    <input @input="add">
    <div class="payment-item">
      <label>{{ item1 }}</label>
      <label>{{ price1 }}</label>
      <a :href="url1" target="_blank" rel="noopener noreferrer">bought here</a>
      <button @click="buy(item1)">buy</button>
    </div>
    <div class="payment-item">
      <label>{{ item2.name }}</label>
      <label>{{ item2.price }}</label>
      <a :href="item2.url" target="_blank" rel="noopener noreferrer">bought here</a>
      <button @click="buy(item2.name)">buy</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  width: 1000px;
  margin: 10px;
}

.payment-item {
  margin: 8px;
  padding: 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 50px;
  background-color: gray;
  border-radius: 5px;
}

label {
  font-size: 25px;
}
</style>
