<script setup>
 import { ref, reactive, onMounted } from 'vue'
import { db } from './data/guitarras'
import Guitarra from './components/guitarra.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

const guitarras = ref([]) 
const carrito   = ref([])

onMounted(()=>{
  guitarras.value = db;
});

const agregarCarrito = (guitarra)=>{
   guitarra.cantidad = 1;
   carrito.value.push(guitarra); 
 }

</script>

<template>
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GuitarLA</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@400;700;900&display=swap" rel="stylesheet"> 
    <link rel="stylesheet" href="./src/style.css">
</head>
<body>
    <Header></Header>
    <main class="container-xl mt-5">
        <h2 class="text-center">Nuestra Colección</h2>
        <div class="row mt-5"> 
             <Guitarra 
                 v-for="guitarra in guitarras"
                 v-bind:guitarra="guitarra"
                 @agregar-carrito="agregarCarrito"
             />
        </div>
    </main>
    <Footer></Footer>



</body>
</html>
</template>

<style scoped>

</style>
 