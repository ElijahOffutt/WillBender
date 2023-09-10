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
            <v-btn>save</v-btn>
        </v-card-text>
        <v-btn v-for="(item, name) in prompt">{{name}}</v-btn>
        <p>Payload: {{ prompt }}</p>
        <v-divider />
        <v-card-actions>
            <v-btn v-for="{name, color} in options" variant="default" :color="color">{{name}}</v-btn>
        </v-card-actions>
    </v-card>
</template>

<script setup>
// goal/what you are tryingto accomplish
// format
// main six are task, context, exemplars, persona, format and tone
import { ref, reactive, computed } from 'vue'

let titleEditMode = ref(true)
const options = [
    { name: 'persona', color: 'blue'},
    { name: 'tone', color: 'purple'},
    { name: 'rules', color: 'yellow'},
    { name: 'includes', color: 'green'},
    { name: 'negatives', color: 'red'},
    { name: 'examples', color: 'orange'},
]
let prompt = reactive({
    task: '',
    tone: ''
})

let toggle = () => { titleEditMode.value = !titleEditMode.value }

</script>

<style lang="scss"></style>