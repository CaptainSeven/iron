<template>
  <ion-list>
    <ion-item v-for="item in speciesNames" :key="item">
      <ion-img :src="require('../assets/' + species[item].image)"></ion-img>
    </ion-item>
  </ion-list>
</template>

<script lang="ts">
import { IonImg, IonItem, IonList } from '@ionic/vue';
import { defineComponent } from 'vue';
import species from '../species.json';

const speciesNames = Object.keys(species);

export default defineComponent({
  name: 'SpeciesCards',
  components: {
    IonImg,
    IonItem,
    IonList,
  },
  data() {
    return{
      species: species,
      speciesNames: speciesNames
    }
  }
});
</script>

<style scoped>
ion-item {
  padding: 32px !important;
}
</style>