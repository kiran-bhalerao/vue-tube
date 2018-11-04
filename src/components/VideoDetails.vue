<template>
<div class="col-md-8 videoDetail">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe :src="videoUrl" frameborder="0" class="embed-responsive-item"></iframe>
    </div>
    <div class="details">
      <h4 class="mt-2">{{video.snippet.title}}</h4>
      <p>{{video.snippet.description}}</p>
    </div>
</div>    
</template>

<script>
export default {
  name: "VideoDetails",
  props: ["video"],
  computed: {
    videoUrl() {
      return `https://www.youtube.com/embed/${this.video.id.videoId}`;
    }
  }
};
</script>

<style>
.details {
  padding: 20px;
  background-color: #f3f3f3;
}
</style>
