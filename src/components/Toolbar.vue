<template>
  <ion-toolbar>
    <ion-buttons @click="openMenu()" slot="start">
      <ion-menu-button auto-hide="false"></ion-menu-button>
    </ion-buttons>
    <ion-title slot="secondary">{{ title }}</ion-title>
    <ion-searchbar v-if="enableSearch" slot="secondary" v-on:ionInput="updateInput"></ion-searchbar>
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
    title: String,
    enableSearch: {
      type: Boolean,
      default: false
    }
  },
  emits: ['update:modelValue'],
  methods: {
    openMenu() {
      menuController.open("app-menu");
    },
    updateInput(text: any) {
      this.$emit('update:modelValue', text.target.value)
    }
  },
});
</script>