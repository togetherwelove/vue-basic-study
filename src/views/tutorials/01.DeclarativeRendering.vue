<template>
    <h1>Declarative Rendering</h1>
    <h2>{{ title.split('').reverse().join('') }}</h2>
    <p>{{ counter.count }}</p>
</template>

<script setup>
    import {ref, reactive} from 'vue'
    const title = ref("Hello world!")
    const counter = reactive({count:0})

    counter.count++
    console.log(counter.count)
</script>