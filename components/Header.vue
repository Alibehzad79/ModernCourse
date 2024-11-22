<script setup>

import { useField, useForm } from "vee-validate"

const { handleSubmit, handleReset } = useForm({
    validationSchema: {
        username(value) {
            if (value?.length >= 3) return true
            return "Username neede to b at least 3 characters."
        },
        email(value) {
            if (/^[a-z.-]+@[a-z.-]+\.[a-z]+$/i.test(value)) return true
            return 'Must be a valid e-mail'
        },
        password1(value) {
            if (value?.length >= 6) return true
            return "Password neede to b at least 6 characters."
        },
        password2(value) {
            if (value?.length >= 6) return true
            return "Password neede to b at least 6 characters."
        },
    }
})

const username = useField('username')
const email = useField('email')
const password1 = useField('password1')
const password2 = useField('password2')
const passwordsMatch = ref(false)

const login = handleSubmit(values => {
    alert(JSON.stringify(values, null, 2))
})

const register = handleSubmit(values => {
    if (password1.value.value === password2.value.value) {
        passwordsMatch.value = false
        alert(JSON.stringify(values, null, 2))
    } else {
        passwordsMatch.value = true
    }
})


const sheet = ref(false)
const tab = ref(null)

</script>

<template>
    <div class="p-3 bg-[#17254E] hidden lg:flex">
        <div class="container mx-auto relative">
            <div class="flex items-center justify-between">
                <div class="flex items-center gap-2 text-white">
                    <div class="flex items-center gap-1">
                        <Icon name="solar:phone-calling-broken" size="20" class="text-yellow-300" />
                        <span>(98) 45 111 11 11</span>
                    </div>
                    |
                    <div class="flex items-center gap-1 text-white">
                        <Icon name="solar:mailbox-broken" size="20" class="text-yellow-300" />
                        <span>test@mail.com</span>
                    </div>
                    |
                    <div class="flex items-center gap-1 text-white">
                        <Icon name="solar:map-point-wave-broken" size="20" class="text-yellow-300" />
                        <span>Azerbaijan - Ardabil</span>
                    </div>
                </div>
                <div class="flex items-center gap-5 px-3 bg-yellow-300 h-12 absolute right-0">
                    <NuxtLink to="/instagram">
                        <Icon name="ri:facebook-fill" size="20" />
                    </NuxtLink>
                    <NuxtLink to="/instagram">
                        <Icon name="ri:instagram-line" size="20" />
                    </NuxtLink>
                    <NuxtLink to="/instagram">
                        <Icon name="ri:telegram-line" size="20" />
                    </NuxtLink>
                    <NuxtLink to="/instagram">
                        <Icon name="ri:whatsapp-line" size="20" />
                    </NuxtLink>
                </div>
            </div>
        </div>
    </div>
    <div class="z-50 sticky top-0 p-1 w-full bg-white shadow">
        <div class="container mx-auto">
            <div class="items-center justify-between hidden lg:flex">
                <div>
                    <a href="/"><img class="w-[220px] h-[54px] rounded" src="/img/logo.jpg" />
                    </a>
                </div>
                <div class="flex items-center justify-around gap-5">
                    <NuxtLink to="/">Home</NuxtLink>
                    <NuxtLink to="/about">About Us</NuxtLink>
                    <NuxtLink to="/courses">Courses</NuxtLink>
                    <NuxtLink to="/blog">Blog</NuxtLink>
                    <NuxtLink to="/contact">Contact</NuxtLink>
                </div>
                <div>
                    <v-dialog max-width="500">
                        <template v-slot:activator="{ props: activatorProps }">
                            <MyButton lable="Create Account" color="deep-purple"
                                icon="solar:square-alt-arrow-right-linear" v-bind="activatorProps" variant="flat" />
                        </template>

                        <template v-slot:default="{ isActive }">
                            <v-card>
                                <v-tabs v-model="tab" bg-color="purple" fixed-tabs>
                                    <v-tab value="login">Login</v-tab>
                                    <v-tab value="register">Register</v-tab>
                                </v-tabs>

                                <v-card-text>
                                    <v-tabs-window v-model="tab">
                                        <v-tabs-window-item value="login">
                                            <v-form @submit.prevent="login">
                                                <v-text-field label="Email" v-model="email.value.value"
                                                    :error-messages="email.errorMessage.value"
                                                    color="purple"></v-text-field>
                                                <v-text-field label="Password" color="purple"
                                                    v-model="password1.value.value"
                                                    :error-messages="password1.errorMessage.value"></v-text-field>
                                                <NuxtLink to="/accounts/forgot-password" class="text-blue-500">Forgot
                                                    Password?</NuxtLink>
                                                <v-checkbox label="Remember me"></v-checkbox>
                                                <v-btn type="submit" class="w-full" color="purple"
                                                    variant="tonal">Login</v-btn>
                                            </v-form>
                                        </v-tabs-window-item>

                                        <v-tabs-window-item value="register">
                                            <v-form @submit.prevent="register">
                                                <v-text-field label="Username" color="purple"
                                                    v-model="username.value.value"
                                                    :error-messages="username.errorMessage.value"></v-text-field>
                                                <v-text-field label="Email" color="purple" v-model="email.value.value"
                                                    :error-messages="email.errorMessage.value"></v-text-field>
                                                <v-text-field label="Password" color="purple"
                                                    v-model="password1.value.value"
                                                    :error-messages="password1.errorMessage.value"></v-text-field>
                                                <v-text-field label="Confirm Password" color="purple"
                                                    v-model="password2.value.value"
                                                    :error-messages="password2.errorMessage.value"></v-text-field>
                                                <v-btn type="submit" class="w-full" color="purple"
                                                    variant="tonal">Register</v-btn>
                                            </v-form>
                                            <v-alert v-show="passwordsMatch" text="Please Confirm Passwrod."
                                                title="Passwords is not match" type="error" variant="tonal"
                                                class="mt-5"></v-alert>
                                        </v-tabs-window-item>
                                    </v-tabs-window>
                                </v-card-text>
                                <v-divider></v-divider>
                                <v-card-actions>
                                    <v-btn text="Close" @click="isActive.value = false" color="red" variant="text"
                                        class="w-full" rounded="0"></v-btn>
                                </v-card-actions>
                            </v-card>

                        </template>
                    </v-dialog>
                </div>
            </div>
            <div class="flex items-center justify-between lg:hidden p-2">
                <v-btn variant="text" color="purple" @click="sheet = !sheet">
                    <Icon name="solar:hamburger-menu-outline" size="20" />
                </v-btn>
                <v-dialog max-width="500">
                    <template v-slot:activator="{ props: activatorProps }">
                        <MyButton lable="Create Account" color="deep-purple" icon="solar:square-alt-arrow-right-linear"
                            v-bind="activatorProps" variant="flat" />
                    </template>

                    <template v-slot:default="{ isActive }">
                        <v-card>
                            <v-tabs v-model="tab" bg-color="purple" fixed-tabs>
                                <v-tab value="login">Login</v-tab>
                                <v-tab value="register">Register</v-tab>
                            </v-tabs>

                            <v-card-text>
                                <v-tabs-window v-model="tab">
                                    <v-tabs-window-item value="login">
                                        <v-form @submit.prevent="login">
                                            <v-text-field label="Email" v-model="email.value.value"
                                                :error-messages="email.errorMessage.value"
                                                color="purple"></v-text-field>
                                            <v-text-field label="Password" color="purple"
                                                v-model="password1.value.value"
                                                :error-messages="password1.errorMessage.value"></v-text-field>
                                            <NuxtLink to="/accounts/forgot-password" class="text-blue-500">Forgot
                                                Password?</NuxtLink>
                                            <v-checkbox label="Remember me"></v-checkbox>
                                            <v-btn type="submit" class="w-full" color="purple"
                                                variant="tonal">Login</v-btn>
                                        </v-form>
                                    </v-tabs-window-item>

                                    <v-tabs-window-item value="register">
                                        <v-form @submit.prevent="register">
                                            <v-text-field label="Username" color="purple" v-model="username.value.value"
                                                :error-messages="username.errorMessage.value"></v-text-field>
                                            <v-text-field label="Email" color="purple" v-model="email.value.value"
                                                :error-messages="email.errorMessage.value"></v-text-field>
                                            <v-text-field label="Password" color="purple"
                                                v-model="password1.value.value"
                                                :error-messages="password1.errorMessage.value"></v-text-field>
                                            <v-text-field label="Confirm Password" color="purple"
                                                v-model="password2.value.value"
                                                :error-messages="password2.errorMessage.value"></v-text-field>
                                            <v-btn type="submit" class="w-full" color="purple"
                                                variant="tonal">Register</v-btn>
                                        </v-form>
                                        <v-alert v-show="passwordsMatch" text="Please Confirm Passwrod."
                                            title="Passwords is not match" type="error" variant="tonal"
                                            class="mt-5"></v-alert>
                                    </v-tabs-window-item>
                                </v-tabs-window>
                            </v-card-text>
                            <v-divider></v-divider>
                            <v-card-actions>
                                <v-btn text="Close" @click="isActive.value = false" color="red" variant="text"
                                    class="w-full" rounded="0"></v-btn>
                            </v-card-actions>
                        </v-card>

                    </template>
                </v-dialog>
                <v-bottom-sheet v-model="sheet">
                    <v-card class="text-center gap-5 justify-between py-2 px-2" height="200">
                        <v-card-title>
                            <span class="font-bold text-xl">Menu</span>
                        </v-card-title>
                        <v-divider></v-divider>
                        <v-card-text>
                            <div class="flex flex-col items-center justify-around gap-5">
                                <NuxtLink to="/">Home</NuxtLink>
                                <NuxtLink to="/about">About Us</NuxtLink>
                                <NuxtLink to="/courses">Courses</NuxtLink>
                                <NuxtLink to="/blog">Blog</NuxtLink>
                                <NuxtLink to="/contact">Contact</NuxtLink>
                            </div>
                        </v-card-text>
                        <v-divider></v-divider>
                        <v-card-actions>
                            <v-btn variant="outlined" class="w-full" color="red" @click="sheet = !sheet">
                                close
                            </v-btn>
                        </v-card-actions>
                    </v-card>
                </v-bottom-sheet>
            </div>
        </div>
    </div>
</template>

<style scoped></style>