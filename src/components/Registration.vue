<script setup>
import {ref} from 'vue';

const name = ref('');
const email = ref('');
const number = ref('');
const password = ref('');
const confirmPassword = ref('');

const doRegistration = () => {
    console.log('Submitted');
}
</script>

<template>
    <h1 class="text-3xl font-bold text-blue-500 mb-10 text-center">Registration</h1>

    <div class="bg-slate-100 rounded-xl p-10">
        <form action="">
            <div class="form-group">
                <label class="primary-form-label" for="name">Name</label>
                <input class="primary-input-field" type="text" name="" id="name" placeholder="Enter your name" v-model="name">
            </div>

            <div class="form-group">
                <label class="primary-form-label" for="email">Email</label>
                <input class="primary-input-field" type="email" name="" id="email" placeholder="Enter your email" v-model="email">
            </div>

            <div class="form-group">
                <label class="primary-form-label" for="number">Number</label>
                <input class="primary-input-field" type="tel" name="" id="number" placeholder="Enter your number" v-model="number">
            </div>

            <div class="form-group">
                <label class="primary-form-label" for="password">Password</label>
                <input class="primary-input-field" type="password" name="" id="password" placeholder="Enter your password" v-model="password">
            </div>

            <div class="form-group">
                <label class="primary-form-label" for="confirm-password">Confirm Password</label>
                <input class="primary-input-field" type="password" name="" id="confirm-password" placeholder="Confirm your password" v-model="confirmPassword">
            </div>

            <div class="form-group">
                <button @click="doRegistration" class="primary-btn">Submit</button>
            </div>
        </form>
    </div>
</template>