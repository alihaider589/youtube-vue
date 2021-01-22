<template>
  <div>
    <SearchBar @termChanged="TermChange"></SearchBar>
    <div class="row">
      <VideoDetail :video="selectedVideo" />
      <VideoList @videoSelect="videoSelect" v-bind:videos="videos"></VideoList>
    </div>
  </div>
</template>


<script>
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetails";
import axios from "axios";
const API_KEY = "AIzaSyCccqOc_jqyb8pq26sKEbpQpk5tEPYhKd8";
export default {
  name: "App",
  components: {
    SearchBar: SearchBar,
    VideoList: VideoList,
    VideoDetail: VideoDetail,
  },
  data() {
    return { videos: [], selectedVideo: null };
  },
  methods: {
    videoSelect(video) {
      this.selectedVideo = video;
    },
    TermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm,
          },
        })
        .then((res) => {
          this.videos = res.data.items;
        });
    },
  },
};
</script>