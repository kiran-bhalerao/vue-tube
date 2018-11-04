<template>
   <li class="mt-1 mb-1" @click="onVideoSelect">
    <img :src="thumbnailUrl" alt="thumbnail.img" class="m-2" />
    <div class="m-2">{{video.snippet.title}} 😄</div>
   </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: ["video"],
  methods: {
    onVideoSelect() {
      this.$emit("videoSelect", this.video);
    }
  },
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    }
  }
};
</script>
<style scoped>
li {
  display: flex;
  cursor: pointer;
  background-color: #f3f3f3;
}
li:hover {
  background-color: #e0e0e0;
}
</style>
