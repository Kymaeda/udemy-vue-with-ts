<script setup lang="ts">
import { ref, reactive, computed, watch, toRefs, onBeforeMount, onMounted, onUpdated } from 'vue'

const item1 = ref<string>('カレーライス')
const price1 = 400
const url1 = 'https://pkg.navitime.co.jp/matsuyafoods/spot/detail?code=0000001506'

const item2 = reactive({
  name: 'ハンバーグ',
  price: 1000,
  url: 'https://www.nakaita.com/shop/shop-0-97/'
})

const buy = (itemName: string) => alert(`${itemName}を購入する`)
const addItemName = (e: any) => {
  item2.name = e.currentTarget.value
}
const addItemPrice = (e: any) => {
  item2.price = e.currentTarget.value
}
const clear = () => {
  item2.name = ''
  item2.price = 0
}
const itemBudget = 5000
// const priceLabel = computed(() => {
//   return item2.price > itemBudget ? 'Too Expensive!!!' : item2.price
// })

// NOTE: watchの引数(1: 監視対象のリアクティブな値, 2: 関数)
// NOTE: リアクティブなオブジェクトのプロパティ(非リアクティブ)をwatchする場合,toRefsでプロパティをリアクティブにする
const priceLabel = ref<string>(`${item2.price} yen`)
const { price } = toRefs(item2)
watch(price, () => {
  if (price.value > itemBudget) {
    priceLabel.value = 'Too Expensive!!!'
  } else {
    priceLabel.value = `${item2.price} yen`
  }
})

// Lifecycle Hooks
onBeforeMount(() => console.log('before mounted'))
onMounted(() => console.log('on mounted'))
// NOTE: テンプレートの再描画が必要な場合のみ、関数が実行される(リアクティブな値が変更されてもテンプレートの再描画がされないと実行されない)
onUpdated(() => console.log('updated'))
</script>

<template>
  <div class="container">
    <h1>最近の支出</h1>
    <input @input="addItemName" v-model="item2.name"/>
    <input @input="addItemPrice" v-model="item2.price"/>
    <button @click="clear">Clear</button>
    <div class="payment-item">
      <label>{{ item1 }}</label>
      <label>{{ price1 }}</label>
      <a :href="url1" target="_blank" rel="noopener noreferrer">bought here</a>
      <button @click="buy(item1)">buy</button>
    </div>
    <div class="payment-item">
      <label>{{ item2.name }}</label>
      <label>{{ priceLabel }}</label>
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
  align-items: center;
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
  width: 80%;
}

input {
  margin: 5px;
  height: 30px;
  width: 50%;
}

label {
  font-size: 25px;
}
</style>
