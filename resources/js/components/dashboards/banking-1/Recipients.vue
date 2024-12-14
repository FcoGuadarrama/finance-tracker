<template>
    <div class="relative flex items-center gap-4 bb-dashed pb-6 mb-6">
        <div class="flex gap-6 w-11/12 overflow-x-auto horiz px-2.5 pb-3" style="scrollbar-width: none"
            ref="scrollContainer">
            <div v-for="{ img, name } in users" :key="name" class="shrink-0 text-center flex flex-col items-center gap-3">
                <img width="48" height="48" class="rounded-full" :src="img" alt="img" />
                <p class="text-sm">{{ name }}</p>
            </div>
        </div>
        <button class="p-3 bg-primary rounded-full text-n0" @click="handleScrollRight">
            <IconArrowNarrowRight :size="22" />
        </button>
    </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';
import { IconArrowNarrowRight } from "@tabler/icons-vue";

const users = [
    {
        name: "Courtney",
        img: "/storage/images/user.png",
    },
    {
        name: "Arthur",
        img: "/storage/images/user-2.png",
    },
    {
        name: "Cody",
        img: "/storage/images/user-3.png",
    },
    {
        name: "Shane",
        img: "/storage/images/user-4.png",
    },
    {
        name: "Esther",
        img: "/storage/images/user-5.png",
    },
    {
        name: "Shaown",
        img: "/storage/images/user-6.png",
    },
    {
        name: "Arlene",
        img: "/storage/images/user-7.png",
    },
    {
        name: "Divan",
        img: "/storage/images/user-4.png",
    },
    {
        name: "Alen",
        img: "/storage/images/user-5.png",
    },
    {
        name: "Poresh",
        img: "/storage/images/user-6.png",
    },
    {
        name: "Javed",
        img: "/storage/images/user-7.png",
    },
    {
        name: "Rana",
        img: "/storage/images/user-6.png",
    },
    {
        name: "Jarul",
        img: "/storage/images/user-7.png",
    },
    {
        name: "Jashim",
        img: "/storage/images/user-4.png",
    },
    {
        name: "Menk",
        img: "/storage/images/user-5.png",
    },
    {
        name: "Najib",
        img: "/storage/images/user-6.png",
    },
    {
        name: "Zod",
        img: "/storage/images/user-7.png",
    },
];

const scrollContainer = ref<HTMLDivElement | null>(null);

const handleScrollRight = () => {
    if (scrollContainer.value) {
        const scrollAmount = 200; // Adjust the scroll amount as needed
        scrollContainer.value.scrollBy({
            top: 0,
            left: scrollAmount,
            behavior: "smooth", // Add smooth scroll behavior
        });
    }
};
</script>
