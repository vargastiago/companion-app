<template>
  <div class="SocialPost" :class="{ SocialPost__selected: selected }" @click="onSelectedClick">
    <div class="header">
      <img class="avatar" :src="avatarSrc" />
      <div class="name">{{ username }}</div>
      <div class="userId">{{ userId }}</div>
      <IconDelete />
    </div>
    <div class="post">{{ post }}</div>
    <SocialPostComments v-if="showComments" :comments="comments" />
    <div class="interactions">
      <IconHeart />
      {{ interactions }}
      <IconCommunity />
      {{ commentsNumber }}
      <button v-show="hasComments" @click="onShowCommentClick">Show comments</button>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref, computed } from 'vue';
import SocialPostComments from './SocialPostComments.vue';
import IconDelete from '../icons/IconDelete.vue';
import IconHeart from '../icons/IconHeart.vue';
import IconCommunity from '../icons/IconCommunity.vue';

const selected = ref(false);
const onSelectedClick = () => {
  selected.value = !selected.value;
};

const showComments = ref(false);
const onShowCommentClick = () => {
  console.log('Showing comments');
  showComments.value = !showComments.value;
};

const commentsNumber = computed(() => {
  return props.comments.length;
});

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
    display: flex;
    font-weight: bold;
    margin-top: 8px;
    gap: 8px;
    svg {
      width: 24px;
      height: 24px;
      fill: var(--color-border);
    }
  }
}
</style>
