<template>
<ul>
      <VideoListItem v-for="myVideo in myVideos"></VideoListItem>

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
