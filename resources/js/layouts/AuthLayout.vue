<script setup lang="ts">

import VerticalSidebar from "@/components/sidebars/VerticalSidebar.vue";
import useWindowSize from "@/utils/useWindowSize";
import {ref} from "vue";
import Footer from "@/components/shared/Footer.vue";
import {useLayoutStore} from "@/stores/layoutStore";
import NavbarTopVue from "@/components/shared/NavbarTop.vue";
import TopNavHorizontal from "@/components/shared/TopNavHorizontal.vue";
import HoveredSidebar from "@/components/sidebars/HoveredSidebar.vue";
import TwoColumnSidebar from "@/components/sidebars/TwoColumnSidebar.vue";

const { theme } = useLayoutStore()
const { windowSize } = useWindowSize()
const isSidebarOpen = ref(false)

const setSidebar = (value: boolean) => {
    isSidebarOpen.value = value
}

const toggleSidebar = () => {
    isSidebarOpen.value = !isSidebarOpen.value
}
</script>

<template>
    <NavbarTopVue v-show="theme.layout != 'Horizontal' || theme.layout == 'Horizontal' && windowSize < 1400"
                  :is-sidebar-open="isSidebarOpen" :toggle-sidebar="toggleSidebar" />
    <VerticalSidebar :set-sidebar="setSidebar"
                     v-show="theme.layout === 'Vertical' || theme.layout == 'Horizontal' && windowSize < 1400"
                     :is-sidebar-open="isSidebarOpen" :toggleSidebar="toggleSidebar" />



    <main class="pt-[72px] md:pt-20 xl:pt-[98px] transition-all duration-500 " :class="{
            'ltr:xxl:ml-[280px] ltr:xxxl:ml-[336px] rtl:xxl:mr-[280px] rtl:xxxl:mr-[336px]': isSidebarOpen && theme.layout === 'Vertical', 'ltr:xxl:ml-[280px] ltr:xxxl:ml-[360px] rtl:xxl:mr-[280px] rtl:xxxl:mr-[360px]': isSidebarOpen && theme.layout === 'Two Column',
            'ltr:xxl:ml-20 rtl:xxl:mr-20': isSidebarOpen && theme.layout == 'Hovered',
            'xxl:!pt-[172px]': theme.layout == 'Horizontal'
        }">
        <div class="px-3 sm:px-4 xxxl:px-6 py-6 lg:py-8"
             :class="{ 'max-w-[1700px] mx-auto': theme.layout == 'Horizontal' }">
            <slot />
        </div>
        <Footer />
    </main>
</template>

<style scoped>

</style>
