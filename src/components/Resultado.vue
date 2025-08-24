<script setup>
const props = defineProps(["resultado"]);
</script>

<template>
    <div class="alert alert-primary mt-4 fs-3 fw-bold rounded-3 shadow-sm d-inline-block px-5 text-end">
        {{ props.resultado }}
    </div>
</template>
