<script setup>
import CardComponent from '@/components/CardComponent.vue';
import { ref } from 'vue';

const users = ref([
    {
        name:"Juana de arco",
        correo: "juana@mail.com"
    },
    {
        name:"Pepe",
        correo: "pepe@mail.com"
    }
])

const borrarTarjeta =(index) =>{
    console.log("Kill to", index)
    users.value.splice(index, 1)
    console.log(users)
}

let name,correo;

const adduser= ()=>{
    const newUser = {
        name: name,
        correo: correo
    }

    users.value.unshift(newUser)
}
</script>

<template>
    <h1 class="text-2xl">
        Hola Mundo
    </h1>
    <input type="text" v-model="name" placeholder="Esciba su nombre" class="border rounded">
    <br><br>
    <input type="text" v-model="correo" placeholder="Escriba su correo" class="border rounded">
    <br>
    <br>
    <button class="bg-green-200 px-2 py-1 rounded" @click="adduser">Añadir</button>
    <br>
    <br>
    <div class="space-y-2">
        <CardComponent v-for="(user, index) in users" :key="index" :name="user.name" :correo="user.correo" :index="index" @borrarTarjeta="borrarTarjeta"/>
    </div>
</template>

<style scoped>

</style>
