<template>
  <ion-toolbar>
    <ion-buttons @click="openMenu()" slot="start">
      <ion-menu-button auto-hide="false"></ion-menu-button>
    </ion-buttons>
    <ion-title>{{ title }}</ion-title>
  </ion-toolbar>
</template>

<script lang="ts">
import { IonButtons, IonMenuButton, IonTitle, IonToolbar, menuController } from '@ionic/vue';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Toolbar',
  components: {
    IonButtons,
    IonMenuButton,
    IonTitle,
    IonToolbar,
  },
  props: {
    title: String
  },
  methods: {
    openMenu() {
      menuController.open("app-menu");
    },
  },
});
</script>