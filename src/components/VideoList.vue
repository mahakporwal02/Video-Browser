<template>
    <div>
       <VideoListItem v-bind:key="video" v-for="video in videos"></VideoListItem>
    </div>
</template>
<script>
import VideoListItem from './VideoListItem.vue';
export default {
  name: 'VideoList', 
  components: {
      VideoListItem,
  },
  props: {
      videos: Array,
  }
}
</script>
<style scoped>

</style>