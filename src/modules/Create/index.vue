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
            <v-card v-for="(value, key) in prompt" :style="`border: solid 3px ${color(key)};`" class="mb-3">
                <v-card-text class="pb-0 mb-0">
                    <v-textarea v-model="prompt[key]" variant="outlined" :label="key" />
                </v-card-text>
                <v-card-actions class="mt-0 pt-0">
                    <v-row>
                        <v-col :cols="key == 'task' ? 12 : 6">
                            <v-btn :disable="prompt[key].length > 5" size="small" color="success" variant="outlined" block
                                append-icon="mdi-check">save</v-btn>
                        </v-col>
                        <v-col v-if="key != 'task'" cols="6">
                            <v-btn size="small" @click="delete prompt[key]" color="error" variant="outlined" block
                                append-icon="mdi-delete">delete</v-btn>
                        </v-col>
                    </v-row>
                </v-card-actions>
            </v-card>
        </v-card-text>
        <v-divider />
        <v-card-actions>
            <template v-for="{ name, color } in options">
                <v-btn v-if="name != 'task'" variant="tonal" @click="prompt[name] = ''" :color="color">{{ name
                }}</v-btn>
            </template>
        </v-card-actions>
    </v-card>
</template>

<script setup>
// goal/what you are tryingto accomplish
// format
// main six are task, context, exemplars, persona, format and tone
import { ref, reactive, computed } from 'vue'

let titleEditMode = ref(true)
let title = ref('')
const options = computed(() => {
    const list = [
        { name: 'task', color: 'black' },
        { name: 'persona', color: 'blue' },
        { name: 'tone', color: 'purple' },
        { name: 'rules', color: 'yellow' },
        { name: 'includes', color: 'green' },
        { name: 'negatives', color: 'red' },
        { name: 'examples', color: 'orange' },
        { name: 'format', color: 'grey' },
    ]
    let filtered = list.filter(item => item.name != prompt[item.name]);
    return filtered
})
let prompt = reactive({
    task: '',
})

let color = (key) => options.value.find(item => item.name == key).color

let toggle = () => { titleEditMode.value = !titleEditMode.value }

</script>

<style lang="scss"></style>