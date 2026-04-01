<template>
  <aside>
    <h2>Sidebar</h2>
    <TheButton value="Create Post" />
    <div>Current time: {{ currentTime }}</div>
    <TheButton @click.once="onUpdateTimeClick" value="Update Time" />
  </aside>
</template>

<script setup>
import { ref } from 'vue';
import TheButton from '../atoms/TheButton.vue';

const currentTime = ref(new Date().toLocaleTimeString());
const onUpdateTimeClick = () => {
  currentTime.value = new Date().toLocaleTimeString();
};
</script>

<style scoped>
aside {
  display: flex;
  flex-direction: column;
}
</style>
