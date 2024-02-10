<script setup lang="ts">
import { ref, watch } from 'vue';

const nombre = ref('nombre');
const apellido = ref('apellido');
const mensajeInvalido = ref('');
const mensajeedad = ref('');
const mensajetelefono = ref('');
const edad = ref(0);
const genero = ref('');
const telefono = ref('');


function mensaje() {

    if (nombre.value === apellido.value) {
        mensajeInvalido.value = 'Los nombres no pueden ser iguales.';
    } else {
        mensajeInvalido.value = '';
    }

    if (edad.value >= 0 && edad.value <= 60) {
        mensajeedad.value = ''
    } else {
        mensajeedad.value = 'Edad invalidad 0 a 60 años';
    }

    if (telefono.value.length >= 10) {
        mensajetelefono.value = 'inserte solo 10 numeros';
    } else {
        mensajetelefono.value = '';
    }
    
}

watch([nombre, apellido, edad, telefono], () => {
    mensaje();
    
});

</script>


<template>
    <div class="form">

        <h3>Nombre</h3>
        <input type="text" v-model="nombre">
        <h3>Apellido</h3>
        <input type="text" v-model="apellido">
        <p v-if="mensajeInvalido !== ''" class="error-message">{{ mensajeInvalido }}</p>

        <h3>Género</h3>
        <select v-model="genero">
            <option value="">Selecciona una opción</option>
            <option value="Masculino">Masculino</option>
            <option value="Femenino">Femenino</option>
            <option value="Otro">Otro</option>
        </select>

        <h3>Edad</h3>
        <input type="number" v-model="edad">
        <p v-if="mensajeedad !== ''" class="error-message">{{ mensajeedad }}</p>

        <h3>Número de teléfono</h3>
        <input type="tel" pattern="[0-9]{10}" v-model="telefono">
        <p v-if="mensajetelefono !== ''" class="error-message">{{ mensajetelefono }}</p>

    </div>
    <div>
        <h1> INFORMACION</h1>
        <h5> Nombre : {{ nombre }} </h5>
        <h5> Apellido : {{ apellido }}</h5>
        <h5> Edad : {{ edad }}</h5>
        <h5> Genero : {{ genero }}</h5>
        <h5> Numero de telefono : {{ telefono }}</h5>

    </div>
    
</template>
  
<style scoped>
.form {
    max-width: 400px;
    margin: 0 auto;
}

h3 {
    font-size: 18px;
    margin-bottom: 8px;
}

input,
select {
    width: 100%;
    padding: 10px;
    margin-bottom: 16px;
    border: 1px solid #360055;
    border-radius: 8px;
    font-size: 16px;
    outline: none;
}

.input-error {
    border-color: #FF3333;
}

.error-message {
    color: #FF3333;
    font-size: 16px;
    margin-top: 8px;
    padding: 8px;
    background-color: #FFD6D6;
    border: 1px solid #E57373;
    border-radius: 4px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

/* Add any additional styling based on your preference */
</style>
