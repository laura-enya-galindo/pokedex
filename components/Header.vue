<template>
    <h1><slot name="header"/></h1>
    <p><slot name="description"/></p>
</template>

<style>
    h1 {
        color: red;
        font-size: x-large;
        text-decoration: underline;
    }
</style>