<script setup lang="ts">

/* template specific */

import Counter from './modules/counter/mod.vue';
import Fetcher from './modules/fetcher/mod.vue';
import Splash from './modules/Splash/index.vue';
import Left from './modules/Navigation/Left/index.vue';
import Right from './modules/Navigation/Right/index.vue'

let logged = true;

</script>

<template>
  <v-app>
    <Splash v-if="!logged" />
    <Left />
    <v-main class="bg-grey-lighten-4">
      <v-container class="mx-auto" style="max-width: 768px;">

      </v-container>
    </v-main>
  </v-app>
</template>
