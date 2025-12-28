<script setup>

defineProps({
    name: String,
    description: String,
    logo: String,
    isDark: Boolean,
    enabled: Boolean    
})

const emit = defineEmits(['toggle','remove'])

function toggle() {
    emit('toggle')
}

function removeItem() {
    emit('remove')
}




</script>
<template>
    <div class="card w-full flex flex-col justify-between items-center p-4 rounded-lg shadow mt-4"
      :class="isDark? 'bg-[#040918] text-white' : 'bg-[#f7f7f8ff] text-black'">
        <div class="image flex flex-row items-start gap-5 w-full">
            <img :src="logo" alt="Extension logo" class="logo w-20 h-18  " />
            <div class="flex flex-col">
                <h3 class="title font-bold">{{ name }}</h3>
                <p class="description">{{ description }}</p>
            </div>
        </div>

        <div class="flex flex-row justify-between gap-8 w-full ">
            <button 
            @click="removeItem"
            class="border font-bold px-4 py-1 mt-2 rounded-2xl"
            >
                Remove
            </button>
            <button
                @click="toggle"
                class="relative inline-flex h-6 w-12 items-center rounded-full transition-all"
                :class="enabled ? 'bg-red-400' : 'bg-gray-300'"
            >
                <span
                    class="inline-block h-5 w-5 transform rounded-full bg-white transition-all"
                    :class="enabled ? 'translate-x-6' : 'translate-x-1'"
                ></span>
            </button>
        </div>
    </div>
</template>

<style scoped>

</style>