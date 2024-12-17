<script setup lang="ts">
import PeopleCard from '@/components/PeopleCard.vue';
import data_people from '@/data/data_people';
import type People from '@/types/People';
import { ref } from 'vue';


const people = ref<People[]>();
people.value = data_people.getPeople();

let isAZ = ref(false);
let isZA = ref(false);

const sortAZ = () => {
    people.value.sort((a, b) => a.first_name.localeCompare(b.first_name));
    isAZ.value = true;
    isZA.value = false;
};

const sortZA = () => {
    people.value.sort((a, b) => b.first_name.localeCompare(a.first_name));
    isZA.value = true;
    isAZ.value = false;
};
</script>

<template>
    <h1 class="display-5">Emberek</h1>
    <div class="mb-3">
        <button @click="sortAZ" class="btn" :class="{ 'btn-primary': isAZ }">Rendezés A-Z</button>
        <button @click="sortZA" class="btn" :class="{ 'btn-primary': isZA }">Rendezés Z-A</button>
    </div>
    <div class="d-flex flex-wrap">
        <PeopleCard v-for="person in people" :key="person.id" :person="person" />
    </div>
</template>

<style scoped></style>
