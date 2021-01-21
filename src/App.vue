<template>
  <div>
    <SearchBar @termChanged="TermChange"></SearchBar>
    <VideoList></VideoList>

    {{videos.length}}
  </div>
</template>


<script>
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import axios from "axios";
const API_KEY = "AIzaSyA7NVn_Y89XpOlolGKGuKWTp93qJvSXAUc";
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