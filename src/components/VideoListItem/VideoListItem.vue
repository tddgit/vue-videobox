<template>
   <li class="media">
      <img class="mr-3" v-bind:src="thumbnailUrl" />
      <div class="media-body">
         {{ video.snippet.title }}
      </div>
   </li>
</template>

<script>
export default {
   name: 'VideoListItem',
   props: ['video'],
   computed: {
      thumbnailUrl() {
         return this.video.snippet.thumbnails.default.url;
      },
   },
};
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
