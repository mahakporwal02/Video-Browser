<template>
    <div>
        <SearchBar v-on:termChange="onTermChange"></SearchBar>
        <VideoList v-bind:videos="videos"></VideoList>
        {{videos.length}}
    </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';
import VideoList from './components/VideoList.vue';
import axios from 'axios'
const API_KEY ='AIzaSyBUhAjDWWXP_02c9G6jj5Oj9F3D3CCgco0'
export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList
    },
    data() {
        return {videos: [],}
    },
    methods :{
        onTermChange(searchTerm ) {
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key:API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
                }).then(
                    response => {
                        this.videos = response.data.items;
                    });
            }
        }
    }
</script>