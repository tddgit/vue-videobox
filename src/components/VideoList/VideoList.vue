<template>
   <ul class="list-unstyled">
      <VideoListItem
         v-for="video in videos"
         :video="video"
         :key="video.etag"
      >
      </VideoListItem>
   </ul>
</template>

<script>
import VideoListItem from '../VideoListItem/VideoListItem';

export default {
   name: 'VideoList',
   components: { VideoListItem },
   props: ['videos'],
};
</script>
