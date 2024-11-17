<!-- src/components/ListItem.vue -->
<template>
  <div class="list-item">
    <div class="text-box">{{ crypto.name }}</div>
    <div class="text-box">{{ crypto.symbol }}</div>
    <div class="text-box">{{ crypto.price_usd }}</div>
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
}

.text-box {
  flex: 1;
  padding: 10px;
  text-align: center;
}
</style>
