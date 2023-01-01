<script setup lang="ts">
// FIXME: cannot be compiled under '--isolatedModules' because it is considered a global script file. Add an import, export, or an empty 'export {}' statement to make it a module.
const item1 = 'カレーライス'
const price1 = 400
const url1 = 'https://pkg.navitime.co.jp/matsuyafoods/spot/detail?code=0000001506'

const item2 = 'ハンバーグ'
const price2 = 600
const url2 = 'https://www.nakaita.com/shop/shop-0-97/'

const buy = (itemName: string) => alert(`${itemName}を購入する`)
</script>

<template>
  <div class="container">
    <h1>最近の支出</h1>
    <div class="payment-item">
      <label>{{ item1 }}</label>
      <label>{{ price1 }}</label>
      <a :href="url1" target="_blank" rel="noopener noreferrer">bought here</a>
      <button @click="buy(item1)">buy</button>
    </div>
    <div class="payment-item">
      <label>{{ item2 }}</label>
      <label>{{ price2 }}</label>
      <a :href="url2" target="_blank" rel="noopener noreferrer">bought here</a>
      <button @click="buy(item2)">buy</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  width: 1000px;
}

.payment-item {
  margin: 8px;
  padding: 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 50px;
  width: 100%;
  background-color: gray;
  border-radius: 5px;
}

label {
  font-size: 25px;
}
</style>
