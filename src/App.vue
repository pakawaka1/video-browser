<template>
    <div class='container'>
        <SearchBar @termChange="onTermChange"></SearchBar> <!--same as v-on: termChange="onTermChange" -->
        <div class="row">
            <VideoDetail v-bind:myVideo="selectedVideo" /> <!--selectedVideo property is passed down to VideoDetail-->
            <VideoList @videoSelect="onVideoSelect" :myVideos="videos"></VideoList> 
            <!-- // @videoSelect="onVideoSelect" from videolist componennt
                // myVideos refers to the data property that we want to show up inside the child 
                // "videos", however is the data property as it appears in the app (or parent) component 
                // v-bind: videos="videos" binds the parents and child components together, but we can use shorthand syntax of :videos="videos"/
                -->
        
        </div>
    </div>
</template>

<script>
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail'

import axios from 'axios'

const API_KEY = 'AIzaSyAOieYlzHXyQw5IJyjDs4G639-NGI7xD9g';
export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList,
        VideoDetail
    },
    // data property that return an object, which will return the video object from YouTube
    data() {
        return { videos: [], selectedVideo: null };
    },
    methods: {
        onVideoSelect(myVideo) {
            this.selectedVideo = myVideo;            
        },
        // onTermChange: function() {
        onTermChange(searchTerm) {
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet', //part - tells the youtube api what type of information we want back
                    q: searchTerm // q=query, which executes the actual request to the api
                }
            }).then(response => { // .then accepts the function that gets from the response that we get back from Youtube
            this.videos = response.data.items;   
                                // .data property is not related to our component instance, but rather, the response object that comes back from Youtube
        });
        }


        },
};
</script>
