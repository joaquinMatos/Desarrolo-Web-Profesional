<template>
    <div>
        <menuItems v-for="routes in RouterView" :name="routes.name" :path="routes.path" :conejos="1"></menuItems>
        <h2> </h2>
    </div>
</template>

<script lang="ts" setup>

import ImenuItem from "@/Interface/ImenuItem" 
import router from '@/router';


const RouterView = router.options.routes.filter((route) => {
    return route /* {name: router.name, path: router.path} */
}) as ImenuItem

</script>
