<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Tugas 2 - Crypto List</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="false">
      <div id="container">
        <ion-button class="init-button" @click="fetchCryptos"
          >Get Data</ion-button
        >
        <div id="header">
          <div class="header-text">Nama</div>
          <div class="header-text">Simbol</div>
          <div class="header-text">Harga USD</div>
        </div>
        <ion-list>
          <ListItem
            v-for="crypto in cryptos"
            :key="crypto.id"
            :crypto="crypto"
          />
        </ion-list>
      </div>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import ListItem from "@/components/ListItem.vue";
import { Crypto } from "@/data/crypto";
import {
  IonContent,
  IonHeader,
  IonPage,
  IonTitle,
  IonToolbar,
} from "@ionic/vue";
import { ref } from "vue";

const cryptos = ref<Crypto[]>([]);

const fetchCryptos = async () => {
  try {
    const response = await fetch("https://api.coinlore.net/api/tickers/");
    const json = await response.json();
    cryptos.value = json.data;
    console.log("cryptos", JSON.stringify(json, null, 2));
  } catch (error) {
    console.error("Error fetching posts:", error);
  }
};
</script>

<style scoped>
#container {
  text-align: center;
}
#header {
  display: flex;
  flex-direction: row;
  align-items: center;
  border: 1px solid black;
  padding-top: 8px;
  padding-bottom: 8px;
}
.header-text {
  flex: 1;
  padding: 10px;
  text-align: center;
}
.init-button {
  padding-top: 16px;
  padding-bottom: 16px;
}
</style>
