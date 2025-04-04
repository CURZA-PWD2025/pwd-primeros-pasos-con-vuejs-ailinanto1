<script setup>
import { ref } from 'vue';

const username = ref('');
const email = ref('');
const password = ref('');
const birthdate = ref('');
const user = ref(null);

const createUser = () => {4
    if (!username.value || !email.value || !password.value || !birthdate.value) {
        alert('Completa todos los campos.');
        return;
    }

    const birthYear = new Date(birthdate.value).getFullYear();
    const currentYear = new Date().getFullYear();
    const age = currentYear - birthYear;

    user.value = { username: username.value, email: email.value, age };

    alert(`Usuario creado:\nNombre: ${user.value.username}\nEmail: ${user.value.email}\nEdad: ${user.value.age}`);

    username.value = '';
    email.value = '';
    password.value = '';
    birthdate.value = '';
};
</script>

<template>
    <form @submit.prevent="createUser">
        <input type="text" v-model="username" placeholder="Nombre de usuario" required />
        <input type="email" v-model="email" placeholder="Email" required />
        <input type="password" v-model="password" placeholder="Contraseña" required />
        <input type="date" v-model="birthdate" required />
        <button type="submit">Crear Usuario</button>
    </form>

    <div v-if="user">
        <p>Nombre: {{ user.username }}</p>
        <p>Email: {{ user.email }}</p>
        <p>Edad: {{ user.age }}</p>
    </div>
</template>

<style scoped>
form {
    display: flex;
    flex-direction: column;
    max-width: 350px;
    margin: auto;
    gap: 12px;
    background: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
}

body {
    background-color: #f4f4f9;
    font-family: Arial, sans-serif;
    color: #333;
}

input {
    padding: 10px;
    border: 2px solid #6C63FF;
    border-radius: 5px;
    font-size: 1rem;
    background-color: #ffffff;
    color: #333;
}

button {
    background-color: #FF6584;
    color: white;
    border: none;
    cursor: pointer;
    font-size: 1rem;
    padding: 10px;
    border-radius: 5px;
    transition: background 0.3s ease;
}

button:hover {
    background-color: #e04e70;
}

div {
    margin-top: 20px;
    padding: 15px;
    background-color: #6C63FF;
    color: white;
    border-radius: 10px;
    text-align: center;
}
</style>