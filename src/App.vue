<template>
  <div>
    <SearchBar @termChanged="TermChange"></SearchBar>
    <VideoList
      @videoSelect="videoSelect"
      v-bind:videos="videos"
    ></VideoList>
  </div>
</template>


<script>
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import axios from "axios";
const API_KEY = "AIzaSyCGxjr9QXhqD9ZoTL6QldrFvSBZ-2ShZ0U";
export default {
  name: "App",
  components: {
    SearchBar: SearchBar,
    VideoList: VideoList,
  },
  data() {
    return { videos: [] };
  },
  methods: {
    videoSelect(video) {
      console.log(video);
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