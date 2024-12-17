<script setup lang="ts">
import { useRouter } from "vue-router";

const props = defineProps({
    person: Object,
});

const router = useRouter();

const navigateToContact = () => {
    router.push(`/contact/${props.person.id}`);
};
</script>

<template>
    <div class="card m-3">
        <img :src="person.avatar" alt="Avatar" @click="navigateToContact" />
        <p class="text-center" @click="navigateToContact">{{ person.first_name }} {{ person.last_name }}</p>
    </div>
</template>

<style scoped>
.card img  {
    width: 250px;
    height: 250px;
}
</style>
