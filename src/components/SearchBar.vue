<template>
    <div>
        <input @input="onInput" /> <!--same as v-on:input --input event-->                     
    </div>
</template>

<script>
export default {
    name: 'SearchBar',
    methods:  {
        onInput: function(event) {
            this.$emit('termChange', event.target.value)  // first argumment, 'termChange' can be named anything,  but for best practices, create a name of what is happening); // second argumment, we shoul provide addtional inforration about the event that just occurred'
        }
    }


    
};
</script>

<style>

</style>


