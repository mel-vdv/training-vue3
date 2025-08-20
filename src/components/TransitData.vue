<template>

    <p> {{ msgprop }}</p>

</template>

<script setup>

    const props = defineProps({msgprop: String})
    const emit = defineEmits(['msgEmit'])
    emit('msgEmit', "EMIT : message depuis l'enfant")

</script>