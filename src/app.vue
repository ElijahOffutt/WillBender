<script setup>
import { ref } from 'vue';
import Create from './modules/Create/index.vue'

<<<<<<< HEAD
let tasks = ref([])
let creating = ref(false)
=======
let tab = ref<String>("one");
let ChatGPT_API_Key = ref<String>("")

function myFunc() { alert("het there") }
let logged = true;
>>>>>>> 32ee06208849591a40d08a0de08fecfda418fbf4

</script>

<template>
  <v-app>
    <v-main>
<<<<<<< HEAD
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

        <!-- <v-row>
          <v-col cols="8">
            <v-text-field density="compact" label="ChatGPT API Key" v-model="ChatGPT_API_Key" solo />
          </v-col>
          <v-col cols="4">
            <v-btn @click="fire" size="large" prepend-icon="mdi-check" block :disabled="ChatGPT_API_Key.length == 0"
              color="success">configure</v-btn>
          </v-col>
          <v-col cols="12">
            <p>{{ text }}</p>
          </v-col>
        </v-row> -->

        <v-row v-if="!creating">
          <v-col v-for="task in tasks" cols="12">
            <v-btn block>
              <span style="text-transform: none;">task title</span>
            </v-btn>
          </v-col>
        </v-row>

        <Create v-if="creating" />
=======
      <v-container class="mx-auto" style="max-width: 768px;">

        <h1 class="text-h3 font-weight-medium">Will Bender</h1>
        <p style="text-indent: 5px;">An ai tool for powerful prompting</p>

        <v-tabs fixed-tabs v-model="tab">
          <v-tab value="one">chat gpt</v-tab>
          <v-tab value="two">google bard</v-tab>
        </v-tabs>

        <v-window v-model="tab">
          <v-window-item value="one">
            <h3 class="mt-3">Please Input Credentials</h3>
            <v-row>
              <v-col class="grow">
                <v-text-field solo label="Chat GPT API Key" v-model="ChatGPT_API_Key" />
              </v-col>
              <v-col class="shrink">
                <v-btn @click="myFunc" color="success" block x-large>configure</v-btn>
              </v-col>
            </v-row>
          </v-window-item>
          <v-window-item value="two">
            <h3>Please Input Credentials</h3>
          </v-window-item>
        </v-window>
>>>>>>> 32ee06208849591a40d08a0de08fecfda418fbf4

      </v-container>
    </v-main>
  </v-app>
</template>
