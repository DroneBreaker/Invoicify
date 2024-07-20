<template>
    <button class="bg-orange-500 p-4 px-2 w-32 rounded-md text-sm transition ease-in-out delay-100 hover:-translate-y-1 hover:scale-110 hover:bg-white duration-1000 hover:text-black">
        {{ title }}
    </button>
</template>

<script setup>
    // Define the button text
    defineProps({
        title: {
            type: String,
            required: true,
        },

        location: {
            type: String,
            required: true,
        }
    })
</script>

<style lang="scss" scoped>

</style>