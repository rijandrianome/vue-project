<template>
    <a v-bind:href="url">{{ text }}</a>
</template>

<script>
export default {
    name: 'NavLink',
    props: ['url', 'text']
}
</script>

<style>
</style>