<!-- src/components/ListItem.vue -->
<template>
  <div class="list-item">
    <div class="list-item-section">
      <div class="text-title">Rank</div>
      <div class="text-box">{{ crypto.rank }}</div>
    </div>
    <div class="list-item-section">
      <div class="text-title">{{ crypto.name }}</div>
      <div class="text-box">{{ crypto.symbol }}</div>
    </div>
    <div class="list-item-section">
      <div class="text-title">USD</div>
      <div class="text-box">{{ crypto.price_usd }}</div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { Crypto } from "@/data/crypto";
import { defineProps } from "vue";

defineProps({
  crypto: {
    type: Object as () => Crypto,
    required: true,
  },
});
</script>

<style scoped>
.list-item {
  display: flex;
  flex-direction: row;
  align-items: center;
  border: 1px solid rgb(235, 200, 110);
  background-color: rgb(255, 243, 209);
  padding-top: 4px;
  padding-bottom: 4px;
}

.list-item-section {
  display: flex;
  flex: 1;
  flex-direction: column;
  align-items: center;
}

.text-box {
  font-size: 24px;
  flex: 1;
  text-align: center;
}
.text-title {
  font-size: 14px;
  flex: 1;
  text-align: center;
}
</style>
