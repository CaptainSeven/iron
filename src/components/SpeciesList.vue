<template>
  <ion-grid v-if="mode === 'grid'">
    <ion-row>
      <ion-col v-for="item in speciesList" :key="item" size="3">
        <ion-img :src="require('../assets/' + species[item].image)"></ion-img>
      </ion-col>
    </ion-row>
  </ion-grid>
  <ion-list v-if="mode === 'list'">
    <ion-item v-for="item in speciesList" :key="item">
      {{ item }}
    </ion-item>
  </ion-list>
</template>

<script lang="ts">
import { IonCol, IonGrid, IonImg, IonItem, IonList, IonRow } from '@ionic/vue';
import { defineComponent } from 'vue';
import Fuse from 'fuse.js'
import species from '../species.json';

const speciesNames = Object.keys(species);
const fuseSpecies = new Fuse(speciesNames);

export default defineComponent({
  name: 'SpeciesList',
  components: {
    IonCol,
    IonGrid,
    IonImg,
    IonItem,
    IonList,
    IonRow
  },
  props: {
    mode: {
      default: 'grid'
    },
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
</style>