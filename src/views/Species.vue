<template>
  <ion-page>
    <ion-header :translucent="true">
      <toolbar title="Star Wars RPG - Species"></toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <species-cards></species-cards>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage } from '@ionic/vue';
import { defineComponent } from 'vue';
import Toolbar from "@/components/Toolbar.vue";
import SpeciesCards from "@/components/SpeciesCards.vue";

export default defineComponent({
  name: 'Species',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    Toolbar,
    SpeciesCards
  }
});
</script>
