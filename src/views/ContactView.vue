<script setup lang="ts">
import { ref } from 'vue';
import { useRoute, useRouter } from 'vue-router';
import data_people from '@/data/data_people';
import type People from '@/types/People';

const route = useRoute();
const router = useRouter();

const person = ref<People | null>(null);

const id = parseInt(route.params.id as string);
person.value = data_people.getPeople().find((p) => p.id === id) || null;

const goBack = () => {
    router.back();
};
</script>

<template>
    <div>
        <button @click="goBack" class="btn btn-secondary mb-3">Vissza</button>
        <div v-if="person">
            <img :src="person.avatar" class="mb-3" />
            <h1>{{ person.first_name }} {{ person.last_name }}</h1>
            <p>{{ person.email }}</p>
        </div>
    </div>
</template>

<style scoped>
img {
    width: 200px;
    height: 200px;
}
</style>
