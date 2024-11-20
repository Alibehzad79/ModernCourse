<script setup>

const sheet = ref(false)

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
                    <a href="/"><v-img :width="80" :height="80" cover=""
                            src="https://gratisography.com/wp-content/uploads/2024/03/gratisography-funflower-800x525.jpg"></v-img>
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
                    <NuxtLink to="/auth">
                        <MyButton lable="Create Account" color="deep-purple"
                            icon="solar:square-alt-arrow-right-linear" />
                    </NuxtLink>
                </div>
            </div>
            <div class="flex items-center justify-between lg:hidden p-2">
                <v-btn variant="flat" color="purple" @click="sheet = !sheet">
                    <Icon name="solar:hamburger-menu-outline" size="20" />
                </v-btn>
                <v-btn rounded="xl" color="deep-purple" variant="tonal">Create Account
                    <template v-slot:append>
                        <Icon name="solar:square-alt-arrow-right-linear" size="20" />
                    </template>
                </v-btn>
                <v-bottom-sheet v-model="sheet">
                    <v-card class="text-center gap-5 justify-between py-2 px-2" height="200">
                        <v-card-header>
                            <span class="font-bold text-xl">Menu</span>
                        </v-card-header>
                        <v-divider></v-divider>
                        <v-card-body>
                            <div class="flex flex-col items-center justify-around gap-5">
                                <NuxtLink to="/">Home</NuxtLink>
                                <NuxtLink to="/about">About Us</NuxtLink>
                                <NuxtLink to="/courses">Courses</NuxtLink>
                                <NuxtLink to="/blog">Blog</NuxtLink>
                                <NuxtLink to="/contact">Contact</NuxtLink>
                            </div>
                        </v-card-body>
                        <v-divider></v-divider>
                        <v-card-body></v-card-body>
                        <v-card-footer>
                            <v-btn variant="outlined" class="w-full" color="red" @click="sheet = !sheet">
                                close
                            </v-btn>
                        </v-card-footer>
                    </v-card>
                </v-bottom-sheet>
            </div>
        </div>
    </div>
</template>

<style scoped></style>