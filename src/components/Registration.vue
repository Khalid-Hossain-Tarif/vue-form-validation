<script setup>
import { ref, computed } from 'vue';

const regex = {
    mobile: /(^(\+88|0088)?(01){1}[3456789]{1}(\d){8})$/,
    email: /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/,
    password: /(?=.*[a-z])(?=.*[A-Z])(?=.*[0-9])(?=.*[^A-Za-z0-9])(?=.{8,})/,
};

const name = ref('');
const number = ref('');
const email = ref('');
const password = ref('');
const confirmPassword = ref('');

const doRegistration = () => {
    if (
        isValidNumber.value &&
        isValidEmail.value &&
        isStrongPassword.value &&
        isConfirmPassword.value
    ) {
        alert('Registering...');
    }
};

const isValidNumber = computed(() => {
    return number.value ? regex.mobile.test(number.value) : null;
});

const isValidEmail = computed(() => {
    return email.value ? regex.email.test(email.value) : null;
});

const isStrongPassword = computed(() => {
    return password.value ? regex.password.test(password.value) : null;
});

const isConfirmPassword = computed(() => {
    return confirmPassword.value
        ? password.value === confirmPassword.value
        : null;
});
</script>

<template>
    <h1 class="text-3xl font-bold text-blue-500 mb-10 text-center">
        Registration
    </h1>

    <div class="bg-slate-100 rounded-xl p-10">
        <form action="">
            <div class="form-group">
                <label class="primary-form-label" for="name">Name</label>
                <input class="primary-input-field" type="text" name="" id="name" placeholder="Enter your name"
                    v-model="name" />
            </div>

            <div class="form-group">
                <label class="primary-form-label" for="number">Number</label>
                <input class="primary-input-field" type="tel" name="" id="number" placeholder="Enter your number"
                    v-model="number" />
                <div class="error-message" v-show="number !== '' && !isValidNumber">
                    Input a 11 digits number. Ex: 017******** / +880**********
                </div>
            </div>

            <div class="form-group">
                <label class="primary-form-label" for="email">Email</label>
                <input class="primary-input-field" type="email" name="" id="email" placeholder="Enter your email"
                    v-model="email" required />
                <div class="error-message" v-show="email !== '' && !isValidEmail">
                    Email didn't matched!
                </div>
            </div>

            <div class="form-group">
                <label class="primary-form-label" for="password">Password</label>
                <input class="primary-input-field" type="password" name="" id="password" placeholder="Enter your password"
                    v-model="password" required />
                <div class="error-message" v-show="password !== '' && !isStrongPassword">
                    Weak Password
                </div>
            </div>

            <div class="form-group">
                <label class="primary-form-label" for="confirm-password">Confirm Password</label>
                <input class="primary-input-field" type="password" name="" id="confirm-password"
                    placeholder="Confirm your password" v-model="confirmPassword" required />
                <div class="error-message" v-show="confirmPassword !== '' && !isConfirmPassword">
                    Password didn't match!
                </div>
            </div>

            <div class="form-group">
                <button @click="doRegistration" class="primary-btn">Submit</button>
            </div>
        </form>
    </div>
</template>