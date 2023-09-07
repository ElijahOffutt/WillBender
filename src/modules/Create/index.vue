<template>
    <v-card elevation="3">
        <v-card-title>
            <v-text-field variant="solo" density="compact" @keyup.enter="titleEditMode = false" v-if="titleEditMode"
                v-model="title" label="Task Title" solo />
            <h3 @click="titleEditMode = true" v-if="!titleEditMode && title.length > 0">
                <b>{{ title }}</b>
                <v-tooltip text="Edit Title" location="top" activator="parent" />
            </h3>
        </v-card-title>
        <v-card-text>
            <v-textarea v-model="prompt.task" variant="solo" label="Task Text" />
        </v-card-text>
        <p>{{ prompt.task.value }}</p>
        <v-divider />
        <v-card-actions>
            <v-btn variant="default" color="blue">Persona</v-btn>
        </v-card-actions>
    </v-card>
</template>

<script setup>
// goal/what you are tryingto accomplish
// format
// main six are task, context, exemplars, persona, format and tone
import { ref, reactive } from 'vue'

let titleEditMode = ref(true)
let title = ref('')
let prompt = reactive({
    task: ''
})

let toggle = () => { titleEditMode.value = !titleEditMode.value }

</script>

<style lang="scss"></style>