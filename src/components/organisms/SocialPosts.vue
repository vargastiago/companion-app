<template>
  <SocialPost
    v-for="(post, index) in posts"
    :username="post.user.firstName"
    :id="post.id"
    :avatarSrc="post.user.image"
    :post="post.body"
    :likes="post.likes"
    :key="post.id"
    @delete="onDelete(index)"
  ></SocialPost>
</template>

<script setup>
import { reactive } from 'vue';
import SocialPost from '../molecules/SocialPost.vue';

const onDelete = postIndex => {
  posts.splice(postIndex, 1);
};

const posts = reactive([]);
const fetchPosts = () => {
  const baseUrl = 'https://dummyjson.com';
  fetch(`${baseUrl}/posts?limit=5`)
    .then(postsResponse => postsResponse.json())
    .then(postsData => {
      // Get unique user IDs from posts
      const userIds = [...new Set(postsData.posts.map(p => p.userId))];

      // Fetch only the users we need in parallel
      Promise.all(
        userIds.map(userId =>
          fetch(`${baseUrl}/users/${userId}`).then(usersResponse => usersResponse.json()),
        ),
      ).then(users => {
        const userMap = Object.fromEntries(
          users.map(u => [u.id, { firstName: u.firstName, image: u.image }]),
        );
        const mappedPosts = postsData.posts.map(post => {
          const user = userMap[post.userId];
          return {
            id: post.id,
            body: post.body,
            likes: post.reactions.likes,
            user,
          };
        });
        posts.push(...mappedPosts);
      });
    });
};

fetchPosts();
</script>
