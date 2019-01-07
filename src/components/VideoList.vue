<template>
<ul>
      <VideoListItem
       v-for="myVideo in myVideos"
       v-bind:myVideo = "myVideo"> <!--
          // v-for is a vue directive to render a list of items based on an array
          // v-bind binds the child property to the parent component -->




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
    props:  ['myVideos']  // props = property names.
    //'myVideos' from parent property app.vue
};


</script>

<style>

</style>
