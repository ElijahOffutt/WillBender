<script setup>
import { ref } from 'vue';
import Create from './modules/Create/index.vue'

let tasks = ref([])
let creating = ref(false)

</script>

<template>
  <v-app>
    <v-main>
      <v-container fluid class="mx-auto" style="max-width: 768px;">

        <v-row justify="space-between">
          <v-col cols="10">
            <h1 class="text-h3 font-weight-medium">Will Bender</h1>
          </v-col>
          <v-col cols="2">
            <v-btn @click="creating = !creating" :color="creating ? 'warning' : 'success'"
              :icon="`mdi-${creating ? 'close' : 'plus'}`" />
          </v-col>
        </v-row>
        <p class="my-3" style="text-indent: 5px;">An ai tool for powerful prompting {{ creating }}</p>
        <v-divider class="mb-5" />
        <v-row v-if="!creating">
          <v-col v-for="task in tasks" cols="12">
            <v-btn block>
              <span style="text-transform: none;">task title</span>
            </v-btn>
          </v-col>
        </v-row>

        <Create v-if="creating" />

      </v-container>
    </v-main>
  </v-app>
</template>
