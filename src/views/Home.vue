<template>
  <ion-page>
    <ion-header :translucent="true">
      <toolbar title="Star Wars RPG - Home"></toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <div id="container">
        <ion-img class="ion-justify-content-center" :src="require('../assets/imperial-logo.png')"></ion-img>
        <strong>Welcome</strong>
        <p>Check out the links in the menu.</p>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonImg, IonHeader, IonPage} from '@ionic/vue';
import { defineComponent } from 'vue';
import Toolbar from '../components/Toolbar.vue';

export default defineComponent({
  name: 'Home',
  components: {
    IonContent,
    IonHeader,
    IonImg,
    IonPage,
    Toolbar
  }
});
</script>

<style scoped>
#container {
  text-align: center;

  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container ion-img{
  max-width: 256px;
  display: block;
  margin-left: auto;
  margin-right: auto;
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;

  color: #8c8c8c;

  margin: 0;
}
</style>
