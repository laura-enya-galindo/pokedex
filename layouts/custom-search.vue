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

<style>
    button {
        height: 2.5rem;
        padding: 0rem 1.875rem;
        border: none;
        background-color: #484848;
        color: white;
        transition: all 1s ease-in-out;
        cursor: pointer;
        border-radius: 2px;
    }

    button:hover {
        background-color: #343434;
    }
</style>