<template>
    <li class="list-group-item media" @click="onVideoSelect"><!--@click = click event-->
        <img class="mr-3" v-bind:src="thumbnailUrl" /><!--where we will be passing the property from the api to the parent's component with v-bind-->
        <div class="media-body">{{ myVideo.snippet.title }}</div> <!-- binds the list of video titles from youtube api to the videolist component-->
    </li>
</template>

<script>
export default {
    name: "VideoListItem",
    props:  ['myVideo'],  // tells the child property about the property it should expect from the parent 
    computed: {
        thumbnailUrl() {
            return this.myVideo.snippet.thumbnails.default.url;
        },
    },
    methods:  {
        onVideoSelect() {
            this.$emit('videoSelect', this.myVideo);
        }
    }
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

