# 第10回 Webエンジニアリング演習 レポート
## 学籍番号（名前は書かなくてよい）
4723112
## 実装したコード
<script setup lang="ts">
  import { ref } from 'vue'
  const name = ref('John Doe')
  setInterval(() => {
    if (name.value === 'Hinata') {
      name.value = 'John Doe'
      return
    }
    name.value = 'Hinata'
  }, 2000)

</script>
<template>
  <div>
    <p>Hello, {{ name }}!</p> <!-- Hello, John Doe! と表示される -->
  </div>
</template>