<template>
  <div class="SocialPost" :class="{ SocialPost__selected: selected }" @click="onSelectedClick">
    <div class="header">
      <img class="avatar" :src="avatarSrc" />
      <div class="name">{{ username }}</div>
      <div class="userId">{{ userId }}</div>
    </div>
    <div class="post">{{ post }}</div>
    <button v-show="hasComments" @click="onShowCommentClick">Show comments</button>
    <SocialPostComments v-if="showComments" :comments="comments" />
    <div class="interactions">Interactions: {{ interactions }}</div>
  </div>
</template>

<script setup>
import { onMounted, ref, computed } from 'vue';
import SocialPostComments from './SocialPostComments.vue';

const selected = ref(false);
const onSelectedClick = () => {
  selected.value = !selected.value;
};

const showComments = ref(false);
const onShowCommentClick = () => {
  console.log('Showing comments');
  showComments.value = !showComments.value;
};

const props = defineProps({
  username: String,
  userId: String,
  avatarSrc: String,
  post: String,
  likes: Number,
  retweets: Number,
  comments: Array,
});

const hasComments = computed(() => {
  return props.comments.length > 0;
});

const interactions = computed(() => {
  return props.comments.length + props.likes + props.retweets;
});

onMounted(() => {
  console.log(props.username);
});
</script>

<style lang="scss">
.SocialPost {
  &__selected {
    border: black solid 1px;
  }
  .header {
    display: flex;
    align-items: center;
    margin-bottom: 8px;
  }
  .avatar {
    border-radius: 50%;
    margin-right: 12px;
  }
  .name {
    font-weight: bold;
    margin-right: 8px;
  }
  .interactions {
    font-weight: bold;
    margin-top: 8px;
  }
}
</style>
