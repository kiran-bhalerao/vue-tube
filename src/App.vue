<template>
    <div class="container">
        <search-bar @termChange = "onTermChange" />
        <div class="row">
          <video-details v-if="selectedVideo" :video = "selectedVideo"/>
          <video-list :videos="videos" @videoSelect="onVideoSelect" :className="getListClassName"/>
        </div>
    </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetails from "./components/VideoDetails";

const API_KEY = "AIzaSyDO4mzPhSMXAFwkKBb4cTpHoKNKPvGjuaU";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetails
  },
  data: function() {
    return {
      videos: [],
      selectedVideo: null
    };
  },
  computed: {
    getListClassName() {
      return this.selectedVideo ? "col-md-4" : "col-md-8";
    }
  },
  methods: {
    onVideoSelect(video) {
      this.selectedVideo = video;
    },
    onTermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            maxResults : 10,
            part: "snippet",
            q: searchTerm,
            type: "video"
          }
        })
        .then(res => {
          this.videos = res.data.items;
        });
    }
  }
};
</script>

<style>
.row {
  display: flex;
  flex:1;
  justify-content: center;
}
</style>

