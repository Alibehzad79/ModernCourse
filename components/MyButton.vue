<script setup>

const props = defineProps([
    'lable',
    'icon',
    'color'
])

</script>

<template>
    <div>
        <v-btn rounded="xl" :color="color" variant="tonal">{{ lable }}
            <template v-slot:append>
                <Icon :name="icon" size="20" />
            </template>
        </v-btn>
    </div>
</template>