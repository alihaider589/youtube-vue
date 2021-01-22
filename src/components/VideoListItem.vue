<template>
  <div class="media">
    <li class="mr-3" @click="videoSelect">
      <img :src="thumbnailUrl" />
      <div class="media-body">
        <h5 class="mt-0">
          {{ video.snippet.title }}
        </h5>
      </div>
    </li>
  </div>
</template>


<script>
export default {
  name: "VideoListItem",
  props: {
      video:Object
  },

  
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
  },
  methods: {
    videoSelect() {
      this.$emit('videoSelect',this.video)  
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  border-width: 1;
}
li:hover {
  background-color: #eee;
  cursor: pointer;
}
</style>