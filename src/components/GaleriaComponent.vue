<script setup>
import { ref } from 'vue';

defineProps({
    title: {
        type: String,
        default: "Este es un título por defecto"
    },
    imagenes: {
        type: Array,
        required: true
    }
});

const nuevaImagen = ref("");

const emit = defineEmits(['add', 'delete']);

const eliminar = (index) => {
    emit('delete', index)
};

const agregar = () => {
    emit('add', nuevaImagen.value)
    nuevaImagen.value = ""
};
</script>
<template>
    <div class="container">

        <h1>{{ title }}</h1>

        <form class="row g-3 align-items-center">
            <div class="col-auto">
                <label>Ingresa URL de la imagen.</label>
            </div>
            <div class="col-auto">
                <input type="text" class="form-control" v-model="nuevaImagen">
            </div>

            <div class="col-auto">
                <button type="button" class="btn btn-success" @click.prevent="agregar">Agregar</button>
            </div>
        </form>

        <div class="row row-cols-1 row-cols-md-3 g-4">
            <div class="col" v-for="(imagen, index) in imagenes" :key="imagen">
                <div class="card">
                    <img :src="imagen" class="card-img-top" alt="...">
                    <div class="card-body">
                        <button type="button" class="btn btn-danger" @click="eliminar(index)">Eliminar</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.container {
    background-color: rgb(2, 6, 66);
    color: white;
    text-align: center;
    padding: 20px;
    margin: 40px 40px;
}
.card {
    background-color: rgb(2, 6, 66);
}




img {
    max-width: 400px;
    padding: 1rem;
}

form {
    padding: 20px;
    justify-content: center;
}
</style>

