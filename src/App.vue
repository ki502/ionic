<template>
  <ion-app>
    <ion-header>
      <ion-toolbar>
        <ion-title>회사 이름</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-header>
      <ion-toolbar>
        <ion-title>회사 이름</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content>
      <ion-router-outlet />
    </ion-content>

    <ion-footer>
      <ion-toolbar>
        <ion-title center>서울시 도봉구 방학1동 불라불라불라 3333-333 전화번호: 02-3333-3333</ion-title>
      </ion-toolbar>
  </ion-footer>

  </ion-app>
</template>

<script lang="ts">
import { IonApp, IonRouterOutlet, IonHeader, IonContent, IonTitle } from '@ionic/vue';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'App',
  components: {
    IonApp,
    IonRouterOutlet,
    IonHeader,
    IonContent,
    IonTitle
  }
});
</script>