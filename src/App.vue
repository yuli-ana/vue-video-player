<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoDetail :video="selectedVideo" />
    <VideoList @videoSelect="onVideoSelect" :videos="videos"/>
  </div>
</template>


<script>
import axios from "axios"
import VideoDetail from "./components/VideoDetail"
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
const API_KEY="AIzaSyBwgo22MP8XnOfAOLD6Xyt4dAjDfV__DuI";

export default {
  name: 'App',
  components: {SearchBar, VideoList, VideoDetail},
  data(){
    return {
      videos: [],
      selectedVideo: null
    }
  },
  methods: {
    onTermChange(searchTerm){
      console.log(searchTerm)
      axios.get("https://www.googleapis.com/youtube/v3/search", {
        params: {
          key: API_KEY,
          type: "video",
          part: "snippet",
          q: searchTerm,
        }
      }).then(response => {
        console.log(response)
        this.videos = response.data.items
      })
    },
    onVideoSelect(video){
      console.log(video);
      this.selectedVideo = video;
    }
  }
}
</script>