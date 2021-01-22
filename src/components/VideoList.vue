<template>
  <div>
    <ul class="list-group">
      <VideoListItem
        v-for="video in videos"
        :key="video.etag"
        v-bind:video="video"
        @videoSelect="videoSelect2"
      ></VideoListItem>
    </ul>
  </div>
</template>


<script>
import VideoListItem from "./VideoListItem";
export default {
  name: "VideoList",
  props: {
    videos: Array,
  },
  components: {
    VideoListItem: VideoListItem,
  },
  methods: {
    videoSelect2(video) {
      this.$emit("videoSelect", video);
    // alert('this is caleld'+video)
    },
  },
};
</script>


<style>
input {
  width: 75%;
}
div {
  text-align: center;
  margin: 20px;
}
</style>