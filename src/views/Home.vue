<template>
  <IonPage>
    <IonContent class="ion-text-center">
      <div class="top-wrapper">
        <div>
          <img alt="" src="assets/barcode.gif">
        </div>
        <ion-input class="ion-input" clear-input placeholder="Saisir le code-barres EAN manuellement"
                   value=""></ion-input>
        <div id="or">OU</div>
        <IonButton class="ion-button" expand="block" @click="openScanner">Scanner le code-barres</IonButton>
      </div>
      <div class="bottom-wrapper">
        <h3>Scans récents</h3>
        <ion-card>
          <ion-card-header>
            <ion-card-title>{{ codeBar }}</ion-card-title>
          </ion-card-header>
          <ion-card-content>
            Lorem ipsum
          </ion-card-content>
        </ion-card>

        <ion-card>
          <ion-card-header>
            <ion-card-title>Title</ion-card-title>
          </ion-card-header>
          <ion-card-content>
            Lorem ipsum
          </ion-card-content>
        </ion-card>
      </div>
    </IonContent>
  </IonPage>
</template>

<script lang="js">
  import { IonContent, IonPage, IonButton, IonText } from '@ionic/vue'
  import { defineComponent } from 'vue'
  import { BarcodeScanner } from '@ionic-native/barcode-scanner'
  import { close, scanOutline, pin } from 'ionicons/icons'


  export default defineComponent({
    name: 'Home',
    components: {
      IonContent,
      IonPage,
      IonButton
    },
    data() {
      return {
        codeBar: '',
        pin,
        close,
        scanOutline
      }
    },
    methods: {
      async openScanner() {
        const data = await BarcodeScanner.scan()
        this.codeBar = data.text
      }
    }
  })
</script>

<style lang="scss" scoped>
  .ion-input {
    border: 1px solid #C3C3C3;
    border-radius: 30px;
  }

  .ion-button {
    --border-radius: 30px;
    margin: 0 40px
  }

  .top-wrapper {
    padding: 0 1em;
  }

  .bottom-wrapper {
    background-image: linear-gradient(#DDEDFA, white);
    margin-top: -23px;
    min-height: 60%;
    padding: 60px 1em 1em;
    text-align: left;
  }

  #or {
    display: flex;
    justify-content: center;
    align-items: center;
    color: #C3C3C3;
    margin: 40px auto;

    &::before, &::after {
      content: "";
      display: block;
      background: #C3C3C3;
      width: 30%;
      height: 1px;
      margin: 0 10px;
    }
  }
</style>