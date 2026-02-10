<script setup>

defineProps(["inicio", "fin", "maxLength"]);
const emit = defineEmits(['next', 'prev']);

</script>

<template>
    <div class="btn-grop" role="group" arial-label="Basic example">
        <button 
        @click="emit('prev')" 
        type="button" 
        class="btn btn-outline-primary"
        :disabled="inicio <= 0">Previous</button>

        <button 
        @click="emit('next')" 
        type="button" 
        class="btn btn-outline-primary"
        :disabled="fin >= 100"
        >Next</button>
    </div>
</template>