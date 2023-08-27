<script setup>
import { ref, computed } from 'vue';

// const name = ref('');
// const number = ref('');
const email = ref('');
const password = ref('');
const confirmPassword = ref('');

const startValidation = ref('');

const doRegistration = () => {
    startValidation.value = true;

    if(isValidEmail.value == true && isStrongPassword.value == true && isConfirmPassword.value == true) {
        console.log('Registering...')
    }
}

const isValidEmail = computed(() => {
    return startValidation.value ? /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(email.value) : null;
});

const isStrongPassword = computed(() => {
    return startValidation.value ? /(?=.*[a-z])(?=.*[A-Z])(?=.*[0-9])(?=.*[^A-Za-z0-9])(?=.{8,})/.test(password.value) : null;
});

const isConfirmPassword = computed(() => {
    return startValidation.value ? password.value == confirmPassword.value : null;
});
</script>

<template>
    <h1 class="text-3xl font-bold text-blue-500 mb-10 text-center">Registration</h1>

    <div class="bg-slate-100 rounded-xl p-10">
        <form action="">
            <!-- <div class="form-group">
                <label class="primary-form-label" for="name">Name</label>
                <input class="primary-input-field" type="text" name="" id="name" placeholder="Enter your name" v-model="name">
            </div> -->

            <!-- <div class="form-group">
                <label class="primary-form-label" for="number">Number</label>
                <input class="primary-input-field" type="tel" name="" id="number" placeholder="Enter your number" v-model="number">
            </div> -->

            <div class="form-group">
                <label class="primary-form-label" for="email">Email</label>
                {{ isValidEmail }}
                <input class="primary-input-field" type="email" name="" id="email" placeholder="Enter your email" v-model="email">
                <div v-if="email !='' && !isValidEmail">Email didn't matched!</div>
            </div>

            <div class="form-group">
                <label class="primary-form-label" for="password">Password</label>
                {{ isStrongPassword }} - {{ password }}
                <input class="primary-input-field" type="password" name="" id="password" placeholder="Enter your password" v-model="password">
                <div v-if="password !='' && !isStrongPassword">Weak Password</div>
            </div>

            <div class="form-group">
                <label class="primary-form-label" for="confirm-password">Confirm Password</label>
                {{ isConfirmPassword }} - {{ confirmPassword }}
                <input class="primary-input-field" type="password" name="" id="confirm-password" placeholder="Confirm your password" v-model="confirmPassword">
                <!-- <div v-if="confirmPassword='' && !isConfirmPassword">Password didn't match!</div> -->
            </div>

            <div class="form-group">
                <button @click="doRegistration" class="primary-btn">Submit</button>
            </div>
        </form>
    </div>
</template>