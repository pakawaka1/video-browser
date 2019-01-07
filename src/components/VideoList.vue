<template>
<ul class="list-group col-md-4">
      <VideoListItem
       v-for="myVideo in myVideos"
       v-bind:myVideo="myVideo"
       :key="myVideo.etag"
       @videoSelect="onVideoSelect">
           <!-- // v-for is a vue directive to render a list of items based on an array

          // v-bind (which can be shortened to (: myVideo="myVideo") binds the child property to the parent component

          //:key combined with v-bind for added specificity such as updating our list.  Here, the .etag is a unique id from youtube's api.
          
          //  @videoSelect param from VideoListemItem.vue click event onVideoSelect method-->
      </VideoListItem>
</ul>
</template>

<script>
import VideoListItem from './VideoListItem';

export default {
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props:  
        ['myVideos'],  // props = property names.//'myVideos' from parent property app.vue
    methods: {
        onVideoSelect(myVideo) {
            this.$emit('videoSelect', myVideo);
        }
    }
};


</script>

<style>

</style>
