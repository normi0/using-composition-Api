<template>
  <div>
    <h2>{{ post.title }}</h2>
    <p v-if="!showFullText">{{ snippet }}</p>
    <p v-else>{{ post.content }}</p>
    <button @click="toggleText">
      {{ showFullText ? "Read Less" : "Read More" }}
    </button>
  </div>
</template>

<script>
import { ref, computed } from "vue";
export default {
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
  setup(props) {
    const showFullText = ref(false);
    const snippet = computed(() => {
      if (showFullText.value) {
        return props.post.content;
      }
      return props.post.content.substring(0, 100) + "...";
    });

    const toggleText = () => {
      showFullText.value = !showFullText.value;
    };

    return {
      post: props.post,
      snippet,
      showFullText,
      toggleText
    };
  },
};
</script>

<style scoped>
button {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  margin-top: 10px;
  border-radius: 5px;
}
</style>
