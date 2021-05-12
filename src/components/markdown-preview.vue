<template>
    <div id="preview" v-html="parsedHtml"></div>
</template>

<script>
import marked from "marked";
import EventBus from '../event-bus';

export default {
    data(){
        return {
            parsedHtml: ''
        }
    },
    created(){
        EventBus.$on('parse-markdown', (markdown) => {
            this.parsedHtml = marked(markdown);
        });
    }
}
</script>

<style>
code {
    overflow-x: scroll;
}
</style>