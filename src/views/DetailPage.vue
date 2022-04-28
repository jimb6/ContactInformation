<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Contact Details</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content>

    </ion-content>
  </ion-page>
</template>

<script lang="ts">

import {defineComponent} from "vue";
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent
} from '@ionic/vue'

export default defineComponent({
  name: "DetailPage",
  components: {
    IonPage,
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent
  }
})

</script>

<style scoped>

</style>
