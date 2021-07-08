<template>
  <ion-page>
    <ion-header :translucent="true">
      <toolbar title="Star Wars RPG - Species" v-model="speciesFilter" :enable-search="true" :enable-detail-list-icon="true" @update:detailListIcon="speciesIcon = $event"></toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <species-list :species-filter="speciesFilter" :mode="speciesIcon"></species-list>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage } from '@ionic/vue';
import { defineComponent } from 'vue';
import Toolbar from "@/components/Toolbar.vue";
import SpeciesList from "@/components/SpeciesList.vue";

export default defineComponent({
  name: 'Species',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    Toolbar,
    SpeciesList
  },
  data() {
    return {
      speciesFilter: null,
      speciesIcon: 'grid'
    }
  }
});
</script>
