<script setup>
import { reactive } from 'vue';
import SocialPost from './components/molecules/SocialPost.vue';
import TheHeader from './components/organisms/TheHeader.vue';
const posts = reactive([
  {
    username: 'Username one',
    userId: 'usernameID1',
    avatarSrc: 'https://i.pravatar.cc/40',
    post: 'This is my post',
  },
  {
    username: 'Username two',
    userId: 'usernameID2',
    avatarSrc: 'https://i.pravatar.cc/40',
    post: 'This is my second post',
  },
]);
</script>

<template>
  <TheHeader></TheHeader>
  <SocialPost
    :username="posts[0].username"
    :user-id="posts[0].userId"
    :avatar-src="posts[0].avatarSrc"
    :post="posts[0].post"
  ></SocialPost>
  <SocialPost
    :username="posts[1].username"
    :user-id="posts[1].userId"
    :avatar-src="posts[1].avatarSrc"
    :post="posts[1].post"
  ></SocialPost>
</template>

<style></style>
