<script setup></script>

<template>
    <div>
        <div class="container mx-auto p-3 bg-gray-50 rounded-lg">
            <div class="flex flex-col-reverse lg:flex-row gap-5 lg:gap-0">
                <div class="lg:w-2/3 flex flex-col gap-5 lg:gap-10 justify-center items-start">
                    <span class="uppercase text-[#704FE6]">welcom edunity online courses</span>
                    <h1 class="capitalize text-3xl lg:text-6xl font-bold">Achieving Your Dreams
                        Through Education</h1>
                    <p>We are experienced in educationl platform and skilled strategies
                        for the success of our online learning.</p>
                    <v-btn color="purple" size="large" class="w-full lg:w-1/2">
                        Find Courses
                        <template v-slot:append>
                            <Icon name="solar:arrow-right-up-broken" size="30" />
                        </template>
                    </v-btn>
                </div>
                <div class="lg:w-1/2">
                    <v-img src="https://media.skilldeer.com/550x450/173645dfaa1149522832b2b3a899099700d83df8.png"
                        class="lg:h-[400px] rounded-lg" cover></v-img>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped></style>