<template>
   <div class="container">
      <SearchBar @termChange="onTermChange"></SearchBar>
      <VideoList :videos="videos"></VideoList>
   </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar/SearchBar.vue';
import VideoList from './components/VideoList/VideoList.vue';

const API_KEY = 'AIzaSyDs6UxY9kmO93l3PxxcSTyHcjT22_xyCKo';

export default {
   name: 'App',
   components: {
      SearchBar,
      VideoList,
   },
   data: function () {
      return { videos: [] };
   },
   methods: {
      onTermChange: function (searchTerm) {
         axios
            .get(
               'https://www.googleapis.com/youtube/v3/search',
               {
                  params: {
                     key: API_KEY,
                     type: 'video',
                     part: 'snippet',
                     q: searchTerm,
                  },
               }
            )
            .then((response) => {
               this.videos = response.data.items;
            })
            .catch((err) => console.log(err.message));
      },
   },
};
</script>
