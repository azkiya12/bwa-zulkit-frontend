<script setup>
import { computed, onMounted } from 'vue';
import { useUserStore } from '@/stores/user';

import LogoVue from './Logo.vue';
import UserInfo from './Userinfo.vue';
import NavbarLinkVue from './NavbarLink.vue';
import AuthButton from './AuthButton.vue';

const userStore = useUserStore()
const user = computed(() => userStore.getUser)
const isLoggedIn = computed(() => userStore.isLoggedIn)

onMounted(() => {   
    userStore.fetchUser()
})

</script>

<template>
    <nav class="bg-white border-gray-200 px-2 sm:px-4 py-2.5 rounded dark:bg-gray-800">
        <div class="container flex flex-wrap items-center justify-between mx-auto my-2">
            <LogoVue />
            <UserInfo v-if="isLoggedIn" :user="user.data"/>
            <AuthButton v-else />
            <NavbarLinkVue />
        </div>
    </nav>
</template>