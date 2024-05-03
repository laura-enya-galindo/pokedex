<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';

    const router = useRouter();

    const goToSearch = () => {
        router.push(`/search`);
    };

</script>

<template>
    <div>
        <button @click="goToSearch()"> Search Pokemon </button>
        <slot/>
    </div>
</template>