<script setup>
import CreatePost from '../components/molecules/CreatePost.vue';
import SideBar from '../components/organisms/SideBar.vue';
import TheHeader from '../components/organisms/TheHeader.vue';
</script>

<template>
  <TheHeader />
  <SideBar />
  <main>
    <CreatePost />
  </main>
</template>

<style>
@import '../assets/base.css';
aside {
  border-right: 1px solid var(--color-border);
  padding: 16px 32px;
}
main {
  padding: 16px 32px;
}
</style>
