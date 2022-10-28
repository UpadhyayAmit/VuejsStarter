<template>
  <ul class="list-group col-md-4">
    <VideoListItem v-for="videoItem in videosList" v-bind:video="videoItem" v-bind:key="videoItem.etag"
      @videoSelect="onVideoSelect">
    </VideoListItem>
  </ul>
</template> 


<script>

import VideoListItem from './VideoListItem.vue';

export default {
  name: "VideoList",
  props: ['videosList'],
  components: {
    VideoListItem: VideoListItem
  },
  methods: {
    onVideoSelect(videoData) {
      // console.log(videoData)
      this.$emit('finalvideoSelect', videoData)
    }
  }
  // props:{   // to check/validate props type
  //   videosList:Array
  // }
}

</script>


<style>

</style>