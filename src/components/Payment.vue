<script setup lang="ts">
</script>

<template>
  <div class="container">
    <h1>最近の支出</h1>
    <div class="payment-item">
      <label>カレーライス</label>
      <label>400円</label>
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
