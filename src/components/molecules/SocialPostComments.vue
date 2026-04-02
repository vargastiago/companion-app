<template>
  <div class="SocialPostComments">
    <template v-if="comments.length === 0">
      <p>There are no comments for this post!</p>
    </template>
    <template v-else>
      <p>Comments:</p>
      <div v-for="comment in comments" :key="comment.id" class="comment">
        <p>
          {{ comment.username }}: <strong>{{ comment.body }}</strong>
        </p>
      </div>
    </template>
  </div>
</template>

<script setup>
import { reactive } from 'vue';

const props = defineProps({
  postId: Number,
});

const comments = reactive([]);
const fetchComments = postId => {
  const baseUrl = 'https://dummyjson.com/';

  fetch(`${baseUrl}comments/post/${postId}`)
    .then(response => response.json())
    .then(result => {
      const commentsWithUser = result.comments.map(comment => ({
        id: comment.id,
        body: comment.body,
        username: comment.user.username,
      }));
      comments.splice(0, comments.length, ...commentsWithUser);
    });
};

fetchComments(props.postId);
</script>

<style lang="scss">
.SocialPostComments {
  padding-left: 24px;
  p {
    font-weight: bold;
  }
  .comment {
    display: flex;
    justify-content: space-between;
    background-color: var(--color-input-mute);
    border-radius: 10px;
    margin-bottom: 8px;
    padding: 8px 16px;
    color: var(--color-background-soft);
    width: 75%;
  }
  svg {
    fill: var(--color-background-mute);
  }
}
</style>
