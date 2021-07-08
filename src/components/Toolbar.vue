<template>
  <ion-toolbar>
    <ion-buttons @click="openMenu()" slot="start">
      <ion-menu-button auto-hide="false"></ion-menu-button>
    </ion-buttons>
    <ion-title slot="secondary">{{ title }}</ion-title>
    <ion-searchbar v-if="enableSearch" slot="secondary" v-on:ionInput="updateInput"></ion-searchbar>
    <ion-buttons v-if="enableDetailListIcon" slot="end">
      <ion-button @click="updateDetailListIcon">
        <ion-icon :icon="detailListIcon"></ion-icon>
      </ion-button>
    </ion-buttons>
  </ion-toolbar>
</template>

<script lang="ts">
import { IonButtons, IonIcon, IonMenuButton, IonTitle, IonToolbar, menuController } from '@ionic/vue';
import { gridOutline, listOutline } from 'ionicons/icons';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Toolbar',
  components: {
    IonButtons,
    IonIcon,
    IonMenuButton,
    IonTitle,
    IonToolbar,
  },
  props: {
    title: String,
    enableSearch: {
      type: Boolean,
      default: false
    },
    enableDetailListIcon: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      detailListIcon: gridOutline
    }
  },
  emits: ['update:modelValue', 'update:detailListIcon'],
  setup() {
    return { gridOutline, listOutline }
  },
  methods: {
    openMenu() {
      menuController.open("app-menu");
    },
    updateInput(text: any) {
      this.$emit('update:modelValue', text.target.value)
    },
    updateDetailListIcon() {
      if (this.detailListIcon === listOutline) {
        this.$emit('update:detailListIcon', 'grid')
        this.detailListIcon = gridOutline
      } else if (this.detailListIcon === gridOutline) {
        this.$emit('update:detailListIcon', 'list')
        this.detailListIcon = listOutline
      }
    }
  },
});
</script>