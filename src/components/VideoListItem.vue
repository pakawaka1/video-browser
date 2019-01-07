<template>
    <li>
        {{ myVideo.snippet.title }} <!-- binds the list of video titles from youtube api to the videolist component-->
    </li>
</template>


<script>
export default {
    name: "VideoListItem",
    props:  ['myVideo'] // tells the child property about the property it should expect from the parent 

 
}
</script>

