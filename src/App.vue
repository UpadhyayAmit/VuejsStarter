<template>
  <div class="container">
    <SearchBarTag @termChange="onTermChange"></SearchBarTag>
    <div class="row">
      <VideoDetailItem v-bind:video="selectedVideo"></VideoDetailItem>
      <VideoList @finalvideoSelect="onVideoSelectFinal" v-bind:videosList="videos"></VideoList>
    </div>
  </div>
</template>


<script>
import axios from 'axios'
import SearchBar from './components/SearchBar.vue'
import VideoList from './components/VideoList.vue'
import VideoDetail from './components/VideoDetail.vue'
const API_KEY = "AIzaSyDmWO6balwFZCiwS6jEVoSm98jjs9G6tGI"

export default {
  name: "App",
  components: {
    SearchBarTag: SearchBar,
    VideoList: VideoList,
    VideoDetailItem: VideoDetail
  },
  data() {
    return {
      videos: [],
      selectedVideo: null
    }
  },
  methods: {
    onTermChange: function (searchTerm) {
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      }).then(response => {
        this.videos = response.data.items
      })
    },
    onVideoSelectFinal: function (videoData) {
      console.log(videoData)
      this.selectedVideo = videoData
    }
  }
}

</script>

<style>

</style>