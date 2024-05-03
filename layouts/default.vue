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
        <button @click="goToSearch()"> Search Pokemon Page </button>
        <slot/>
    </div>
</template>


<style>
    body {
        margin: 1.25rem;
    }

    button {
        height: 2.5rem;
        padding: 0rem 1.875rem;
        border: none;
        background-color: #484848;
        color: white;
        transition: all 1s ease-in-out;
        cursor: pointer;
    }

    button:hover {
        background-color: #343434;
    }
</style>