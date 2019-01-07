<template>
    <div v-if="myVideo">
        <div class="details">
            <h4>{{ myVideo.snippet.title }}</h4>    
            <p>{{ myVideo.snippet.description }}</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'VideoDetail',
        props: ['myVideo']
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