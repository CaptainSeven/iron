<template>
  <ion-page>
    <ion-header :translucent="true">
      <toolbar title="Star Wars RPG - Species" :enable-search="true" v-model="speciesFilter" ></toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <species-cards :species-filter="speciesFilter"></species-cards>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage } from '@ionic/vue';
import { defineComponent } from 'vue';
import Toolbar from "@/components/Toolbar.vue";
import SpeciesCards from "@/components/SpeciesCards.vue";

import species from '../species.json';

const speciesNames = Object.keys(species);

export default defineComponent({
  name: 'Species',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    Toolbar,
    SpeciesCards
  },
  data() {
    return {
      speciesFilter: null
    }
  }
});
</script>
