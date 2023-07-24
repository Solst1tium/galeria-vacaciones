<script setup>
import GaleriaComponent from './components/GaleriaComponent.vue'
import { ref } from 'vue';

const images = ref(
    [
    "https://img.freepik.com/fotos-premium/belleza-natural-campo-ambiente-manana-campos-arroz-montanas-al-amanecer-norte-bengkulu-indonesia_80375-348.jpg",
    "https://img.freepik.com/fotos-premium/terrazas-campos-arroz-montana-tailandia_56644-430.jpg",
    "https://img.freepik.com/fotos-premium/belleza-natural-campo-ambiente-manana-campos-arroz-montanas-al-amanecer-norte-bengkulu-indonesia_80375-348.jpg"
    ]);

const eliminarImagen = (index) => {
 images.value.splice(index, 1)
};

const agregarImagen = (src) => {
images.value.push(src)
};
</script>
<template>

    <GaleriaComponent 
    title="Galería de vacaciones"   
    :imagenes ="images"
    @delete="eliminarImagen"
    @add="agregarImagen"
    >
  </GaleriaComponent>

</template>

