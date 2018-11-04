<template>
  <div :class="className">
    <div v-if="renderNext" class="ml-2 mt-1 mb-1">Up Next</div>
    <ul v-for="video in videos" :key="video.etag" class="list-group">
      <video-list-item :video="video" @videoSelect="onVideoSelect"/>
    </ul>
  </div>
</template>

<script>
import VideoListItem from "./VideoListItem";
export default {
  name: "VideoList",
  props: ["videos", "className"],
  computed: {
    renderNext() {
      return this.className === "col-md-4" ? true : false;
    }
  },
  methods: {
    onVideoSelect(video) {
      this.$emit("videoSelect", video);
    }
  },
  components: {
    VideoListItem
  }
};
</script>

