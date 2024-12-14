<script setup lang="ts">
import { IconMessage } from '@tabler/icons-vue'
import { IconLifebuoy } from '@tabler/icons-vue'
import { IconLogout } from '@tabler/icons-vue'
import { IconSettings } from '@tabler/icons-vue'
import { IconUser } from '@tabler/icons-vue'
import { onClickOutside } from '@vueuse/core'
import { ref } from 'vue'
const isOpen = ref(false)
const profileLinks = [
  {
    icon: IconUser,
    url: '/profile',
    title: 'My Profile'
  },
  {
    icon: IconMessage,
    url: '/dashboards/messaging',
    title: 'Meassages'
  },
  {
    icon: IconLifebuoy,
    url: '#',
    title: 'Help'
  },
  {
    icon: IconSettings,
    url: '/settings',
    title: 'Settings'
  },
  {
    icon: IconLogout,
    url: '/login-1',
    title: 'Logout'
  }
]

const target = ref(null)
onClickOutside(target, () => (isOpen.value = false))
</script>

<template>
  <div class="relative" ref="target">
    <div @click="isOpen = !isOpen" class="cursor-pointer">
      <img src="/storage/images/user.png" class="rounded-full w-10 h-10 md:w-12 md:h-12" :width="48" :height="48" alt="profile img" />
    </div>
    <div
      class="bg-n0 border dark:border-n500 ltr:origin-top-right rtl:origin-top-left dark:bg-n800 rounded-md ltr:right-0 rtl:left-0 shadow-lg absolute top-full duration-300 z-10"
      :class="{ 'opacity-100 scale-100 visible': isOpen, 'opacity-0 scale-0 invisible': !isOpen }"
    >
      <div class="flex flex-col text-center items-center lg:p-4 p-3 border-b dark:border-n500">
        <img src="/storage/images/user.png" :width="60" :height="60" class="rounded-full" alt="profile img" />
        <h6 class="mt-2">William James</h6>
        <span class="text-sm">james@mail.com</span>
      </div>
      <ul class="flex flex-col w-[250px] p-2 md:p-4">
        <li v-for="item in profileLinks" :key="item.title">

        </li>
      </ul>
    </div>
  </div>
</template>
