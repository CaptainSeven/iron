<template>
  <ion-menu menu-id="app-menu" content-id="main-content">
    <ion-header>
      <ion-toolbar>
        <ion-title>Menu</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content>
      <ion-list>
        <ion-item button @click="menuNavigation('/home')">
          <ion-label>Home</ion-label>
        </ion-item>
        <ion-item button @click="menuNavigation('/species')">
          <ion-label>Species</ion-label>
        </ion-item>
      </ion-list>
    </ion-content>
  </ion-menu>
</template>
<script>
import { IonMenu, IonHeader, IonContent, IonToolbar, IonTitle, IonItem, IonList, IonLabel, menuController } from "@ionic/vue";
import { defineComponent } from 'vue';

export default defineComponent( {
  name: 'Menu',
  components: {
    IonMenu,
    IonHeader,
    IonContent,
    IonToolbar,
    IonTitle,
    IonItem,
    IonList,
    IonLabel
  },
  methods:{
    menuNavigation(url){
      menuController.close("app-menu");
      this.$router.push(url);
    }
  }
});
</script>