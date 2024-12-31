<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error">{{ error }}</div>
    <PostList :posts="posts" />
  </div>
</template>

<script>
import PostList from "../components/PostList.vue";
import { ref } from "vue";
export default {
  name: "Home",
  components: {
    PostList,
  },
  setup() {
    const posts = ref([]);
    const error = ref(null);
    const load = async () => {
      try {
        const res = await fetch("http://localhost:3000/posts");
        if (!res.ok) {
          throw Error("Failed to fetch posts");
        }
        posts.value = await res.json();
      } catch (err) {
        error.value = err.message;
      }
    };
    load();
    return { posts, error };
  },
};
</script>

<style scoped>
.home {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  height: 100%;
}
h1 {
  margin-bottom: 20px;
}
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
