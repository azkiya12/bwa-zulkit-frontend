<script setup>
import LogoVue from './Logo.vue';
import UserInfoVue from './UserInfo.vue';
import NavbarLinkVue from './NavbarLink.vue';
</script>

<template>
    <nav class="bg-white border-gray-200 px-2 sm:px-4 py-2.5 rounded dark:bg-gray-800">
        <div class="container flex flex-wrap items-center justify-between mx-auto my-2">
            <LogoVue />
            <UserInfoVue />
            <NavbarLinkVue />
        </div>
    </nav>
</template>