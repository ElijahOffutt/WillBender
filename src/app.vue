<script setup lang="ts">
import { ref } from 'vue';
/* template specific */

let tab = ref<String>("one");
let ChatGPT_API_Key = ref<String>("")

let logged = true;

</script>

<template>
  <v-app>
    <v-main>
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
                <v-btn color="success" block x-large>configure</v-btn>
              </v-col>
            </v-row>
          </v-window-item>
          <v-window-item value="two">
            <h3>Please Input Credentials</h3>
          </v-window-item>
        </v-window>

      </v-container>
    </v-main>
  </v-app>
</template>
