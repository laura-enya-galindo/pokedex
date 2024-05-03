<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';

    const router = useRouter();

    const goToHome = () => {
        router.push(`/`);
    };

</script>

<template>
    <div>
        <button @click="goToHome()"> Home </button>
        <slot/>
    </div>
</template>