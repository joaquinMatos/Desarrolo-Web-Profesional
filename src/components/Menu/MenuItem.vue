<template>
    <div>
        <RouterLink :to="data.path">{{ data.name }}</RouterLink>
    </div>
</template>
<script lang="ts" setup>

    import ImenuItem from "@/Interface/ImenuItem"

    const data = defineProps<ImenuItem>();

</script>

<!-- 
Nombre 
apellido sean diferente nombre y apellido
edad 0 a 60 
contraseña :nose 
genero = 3 
telefono = 10 caracter
 -->