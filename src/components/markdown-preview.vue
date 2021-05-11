<template>
    <div id="preview" v-html="parsedHtml"></div>
</template>

<script>
import marked from "marked";

export default {
    props:{
        markdown:{
            type: String,
            require:true,
            default: ''
        }
    },
    computed:{
        parsedHtml(){
            return marked(this.markdown);
        }
  }
}
</script>

<style>
code {
    overflow-x: scroll;
}
</style>