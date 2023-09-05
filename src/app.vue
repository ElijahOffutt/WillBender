<script setup lang="ts">

/* template specific */
import Splash from './modules/Splash/index.vue';

let logged = true;

</script>

<template>
  <v-app>
    <v-main class="bg-grey-lighten-4">
      <v-container class="mx-auto" style="max-width: 768px;">
          <h1>Will Bender</h1>
          <b><i>a ai tool for powerful prompting</i></b>
          <v-tabs>
            <v-tab>chat gpt</v-tab>
            <v-tab>google bard</v-tab>
            <v-window>
              <v-window-item>
                <v-input></v-input>
              </v-window-item>
            </v-window>
          </v-tabs>
      </v-container>
    </v-main>
  </v-app>
</template>
