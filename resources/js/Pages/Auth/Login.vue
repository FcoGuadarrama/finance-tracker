<script setup lang="ts">
    import { IconEyeOff } from '@tabler/icons-vue'
    import { IconArrowLeft } from '@tabler/icons-vue'
    import { IconEye } from '@tabler/icons-vue'
    import { ref } from 'vue'
    import GuestLayout from "@/layouts/GuestLayout.vue";
    import {useForm} from "@inertiajs/vue3";

    const showPass = ref(false)

    const props = defineProps({
        canResetPassword: {
            type: Boolean,
            default: false
        },
        status: {
            type: Object
        }
    })

    const form = useForm({
        email: '',
        password: ''
    });

    const submit = () => {
        form.post(route('login'), {
            onFinish: () => form.reset('password'),
        });
    };

</script>

<template>
    <GuestLayout>
        <div
            class="min-h-screen grid grid-cols-2 gap-5 relative lg:after:absolute lg:after:w-1/2 py-10 lg:py-20 after:h-full lg:after:bg-primary/5 lg:dark:after:bg-bg3 ltr:after:right-0 rtl:after:left-0 after:top-0"
        >
            <div class="col-span-2 lg:col-span-1 flex items-center justify-center px-5 md:px-10 xl:px-20 xxl:px-28">
                <div class="box w-full p-3 md:p-4 xl:p-6 items-center">
                    <form class="box bg-primary/5 dark:bg-bg3 lg:p-6 xl:p-8" @submit.prevent="submit">
                        <!--                    <RouterLink to="/dashboards/personal-1" class="flex items-center gap-2 text-sm"> <IconArrowLeft :size="20" /> Back To Home </RouterLink>-->
                        <h3 class="h3 my-4">Welcome Back!</h3>
                        <p class="md:mb-6 md:pb-6 mb-4 pb-4 bb-dashed text-sm md:text-base">Sign in to your account and join us</p>
                        <label for="email" class="md:text-lg font-medium block mb-4"> Enter Your Email ID </label>
                        <input
                            type="email"
                            v-model="form.email"
                            class="w-full text-sm focus:outline-none bg-n0 dark:bg-bg4 border border-n30 dark:border-n500 rounded-3xl px-3 md:px-6 py-2 md:py-3 mb-5"
                            placeholder="Enter Your Email"
                            id="email"
                            required
                        />
                        <label for="password" class="md:text-lg font-medium block mb-4"> Enter Your Password </label>
                        <div class="bg-n0 dark:bg-bg4 border border-n30 dark:border-n500 rounded-3xl px-3 md:px-6 py-2 md:py-3 mb-4 relative">
                            <input v-model="form.password" :type="showPass ? 'text' : 'password'" class="w-11/12 text-sm focus:outline-none bg-transparent" placeholder="Enter Your Password" id="password" required />
                            <span @click="showPass = !showPass" class="absolute ltr:right-5 rtl:left-5 top-1/2 -translate-y-1/2 cursor-pointer">
              <IconEye v-if="showPass" />
              <IconEyeOff v-else />
            </span>
                        </div>

                        <!--                    <RouterLink to="/forgot-password" class="flex justify-end text-primary text-sm"> Forgot Password </RouterLink>-->
                        <p class="mt-3">
                            Don&apos;t have an account?
                            <!--                        <RouterLink class="text-primary" to="/signup-1"> Signup </RouterLink>-->
                        </p>
                        <div class="mt-6 lg:mt-8 flex gap-6">
                            <button class="btn px-5">Login</button>
                        </div>
                    </form>
                </div>
            </div>
            <div class="col-span-2 lg:col-span-1 flex items-center justify-center">
                <img src="/storage/images/login-1.png" class="relative z-[2] px-4" alt="img" :width="696" :height="547" />
            </div>
        </div>

    </GuestLayout>
</template>
