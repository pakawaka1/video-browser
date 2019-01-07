<template>
    <div class="col-md-8" v-if="myVideo" > <!-- v-if inserts or removes the element based on the truthy-ness of the binding value-->
        <div class="embed-responsive embed-responsive-16by9">
            <iframe class="embed-responsive-item" v-bind:src="videoUrl" /> <!--see videoUrl computed function down below-->
        </div>
        <div class="details">
            <h4>{{ myVideo.snippet.title }}</h4>    
            <p>{{ myVideo.snippet.description }}</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'VideoDetail',
        props: ['myVideo'],
        computed: {
            videoUrl() {
                const videoId = this.myVideo.id.videoId; //...id.videoId from returned object from youtube api under items
                return 'https://www.youtube.com/embed/' + videoId;
            }
        }
    }

</script>

<style scoped>
    .details {
        margin-top: 10px;
        padding: 10px;
        border: 1px solid #ddd;
        border-radius: 4px;
    }

</style>