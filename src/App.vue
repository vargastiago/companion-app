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
    comments: ['great post', 'amazing post'],
    likes: 2,
    retweets: 1,
    tags: ['tag 1'],
  },
  {
    username: 'Username two',
    userId: 'usernameID2',
    avatarSrc: 'https://i.pravatar.cc/40',
    post: 'This is my second post',
    comments: [],
    likes: 3,
    retweets: 1,
    tags: ['tag 1', 'tag 2'],
  },
]);
</script>

<template>
  <TheHeader />
  <SocialPost
    v-for="post in posts"
    :username="post.username"
    :user-id="post.userId"
    :avatar-src="post.avatarSrc"
    :post="post.post"
    :comments="post.comments"
    :likes="post.likes"
    :retweets="post.retweets"
    :key="post.userId"
  ></SocialPost>
</template>

<style></style>
