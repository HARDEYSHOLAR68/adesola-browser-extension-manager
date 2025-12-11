<script setup>

defineProps({
    name: String,
    description: String,
    logo: String,
    enabled: Boolean
})



</script>
<template>
    <div class="card w-full flex flex-col justify-between items-center p-4 bg-white rounded-lg shadow mt-4">
        <div class="image flex flex-row items-start gap-5 w-full  ">
            <img :src="logo" alt="Extension logo" class="logo w-20 h-18  " />
            <div class="flex flex-col">
                <h3 class="title font-bold">{{ name }}</h3>
                <p class="description">{{ description }}</p>
            </div>
        </div>

        <div class="flex flex-row justify-between gap-8 w-full">
            <button 
            @click="removeItem"
            class=""
            >
                Remove
            </button>
            <button
                @click="isActive = !isActive"
                class="relative inline-flex h-6 w-12 items-center rounded-full transition-all"
                :class="isActive ? 'bg-green-500' : 'bg-gray-300'"
            >
                <span
                    class="inline-block h-5 w-5 transform rounded-full bg-white transition-all"
                    :class="isActive ? 'translate-x-6' : 'translate-x-1'"
                ></span>
            </button>
        </div>
    </div>
</template>

<style scoped>

</style>