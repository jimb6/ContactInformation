<template>
  <ion-page>

    <ion-header>
      <ion-toolbar>
        <ion-title>My Contacts</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content>
      <ion-segment value="all" @ionChange="filterContacts($event)">
        <ion-segment-button value="all">
          All
        </ion-segment-button>
        <ion-segment-button value="family">
          Family
        </ion-segment-button>
        <ion-segment-button value="friends">
          Friends
        </ion-segment-button>
      </ion-segment>

      <ion-list>
        <ion-item v-for="contact in filteredContacts" :key="contact.id" @click="router.push('/detail-page')">
          {{ contact.firstName + ' ' + contact.lastName}}
          <ion-note slot="end">{{ contact.phone }}</ion-note>
        </ion-item>
      </ion-list>

    </ion-content>
  </ion-page>
</template>

<script lang="ts">

import {defineComponent, reactive, ref} from 'vue';
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonSegment,
  IonSegmentButton,
  IonList,
  IonItem,
    IonNote
} from '@ionic/vue';

import {useRouter} from "vue-router";

export default defineComponent({
  name: 'HomePage',
  components: {
    IonPage,
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonSegment,
    IonSegmentButton,
    IonList,
    IonItem,
    IonNote
  },
  setup() {
    const router = useRouter();
    const contacts = [
      { id: 1, firstName: 'Daniel', lastName: 'Baldoz', email: 'daniel.baldoz@candortci.edu.ph', phone: '+63 9087898678', category: 'family' },
      { id: 2, firstName: 'Apple Joyce', lastName: 'Comar', email: 'apple.comar@candortci.edu.ph', phone: '+63 9087898678', category: 'family' },
      { id: 3, firstName: 'Haivy Grace', lastName: 'Balili', email: 'haivy.balili@candortci.edu.ph', phone: '+63 9087898678', category: 'family' },
      { id: 4, firstName: 'Edeson John', lastName: 'Cabanes', email: 'edeson.cabanes@candortci.edu.ph', phone: '+63 9087898678', category: 'friends' },
      { id: 5, firstName: 'Feblyn', lastName: 'Dahab', email: 'feblyn.dahab@candortci.edu.ph', phone: '+63 9087898678', category: 'friends' },
      { id: 6, firstName: 'Francis', lastName: 'Alicando', email: 'francis.alicando@candortci.edu.ph', phone: '+63 9087898678', category: 'friends' }
    ];

    var filteredContacts = ref(contacts);

    var filterContacts = function (event: any) {
      var category = event.detail.value;

      switch (category) {
        case 'family':
          filteredContacts.value = contacts.filter(contact => contact.category === 'family');
          break;
        case 'friends':
          filteredContacts.value = contacts.filter(contact => contact.category === 'friends');
          break;
        default:
          filteredContacts.value = contacts;
      }
    }

    return {
      router,
      filteredContacts,
      filterContacts
    }
  }
});

</script>

<style scoped>

</style>
