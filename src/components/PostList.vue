<template>
  <div class="post-list">
    <div v-for="post in posts" :key="post.id" class="post">
      <single-post :post="post" />
    </div>
  </div>
</template>

<script>
import { onMounted, onUnmounted, onUpdated } from "vue";
import SinglePost from "./SinglePost.vue";
export default {
  components: {
    SinglePost,
  },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
  setup(props) {
    onMounted(() => {
      console.log("PostList mounted");
    });
    onUnmounted(() => {
      console.log("PostList unmounted");
    });
    onUpdated(() => {
      console.log("PostList updated");
    });
  },
};
</script>

<style scoped>
.post-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}
.post {
  border: 1px solid #ccc;
  padding: 20px;
  border-radius: 5px;
}
.post h2 {
  margin-bottom: 10px;
}
.post p {
  margin: 0;
}
</style>
