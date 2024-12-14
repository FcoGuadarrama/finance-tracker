<script setup lang="ts">
import {useLayoutStore} from "@/stores/layoutStore";

const { theme } = useLayoutStore()

</script>

<template>
    <main>
        <div>
            <slot />
        </div>
    </main>
</template>

<style scoped>

</style>
