<template>
  <li class="list-group-item media" @click="onVideoSelect">
    <img class="mr-3" v-bind:src="thumbnailsUrl" />
    <div class="media-body"> {{ video.snippet.title }}</div>

  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: ['video'],
  computed: {
    thumbnailsUrl() {
      return this.video.snippet.thumbnails.default.url
    }
  },
  methods: {
    onVideoSelect() {
      console.log(this.video)
      this.$emit('videoSelect', this.video)
    }
  }
}

</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
}

li:hover {
  background-color: #eee;
}
</style>