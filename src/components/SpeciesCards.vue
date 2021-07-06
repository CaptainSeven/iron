<template>
  <ion-list>
    <ion-item v-for="item in speciesList" :key="item">
      <ion-img :src="require('../assets/' + species[item].image)"></ion-img>
    </ion-item>
  </ion-list>
</template>

<script lang="ts">
import { IonImg, IonItem, IonList } from '@ionic/vue';
import { defineComponent } from 'vue';
import Fuse from 'fuse.js'
import species from '../species.json';

const speciesNames = Object.keys(species);
const fuseSpecies = new Fuse(speciesNames);

export default defineComponent({
  name: 'SpeciesCards',
  components: {
    IonImg,
    IonItem,
    IonList,
  },
  props: {
    speciesFilter: {
      default: ''
    }
  },
  computed: {
    speciesList(): string[] {
      if(this.speciesFilter) {
        const search = fuseSpecies.search(this.speciesFilter)
        return search.map(x => x.item)
      } else {
        return speciesNames;
      }
    }
  },
  data() {
    return {
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