<template>
  <div class="col-md-8" v-if="video">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe class="embed-responsive-item" :src="videoUrl" />
    </div>

    <div class="details">
      <h4>
        {{ video.snippet.title }}
      </h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>


<script>
export default {
  name: "VideoDetails",
  props: ["video"],
  computed: {
    videoUrl() {
      const { videoId } = this.video.id;
      return `https://www.youtube.com/embed/${videoId}`;
    },
  },
};
</script>

<style scoped>
.details {
  margin-top: 20px;
  padding: 20px;
  border: 1px solid black;
  border-radius: 4px;
}
</style>