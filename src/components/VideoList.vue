<template>
    <ul class="list-group">
      <VideoListItem v-for="video in videos" :key="video.etag"
      :video="video"
      @videoSelect="onVideoSelect"
       ></VideoListItem>
    </ul>
</template>

<script>
import VideoListItem from "./VueListItem";
export default {
    name: "VideoList",
    components: {
        VideoListItem,
    },
    props: ["videos"],
    methods: {
        onVideoSelect(video){
            this.$emit("videoSelect", video);
        }
    }
}
</script>

<style scoped>

</style>