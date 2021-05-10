<template>
  <div id="main">
    <textarea name="editor" id="editor" cols="30" rows="10" v-model="markdown"></textarea>

    <MarkdownPreview :markdown="markdown"></MarkdownPreview>
  </div>
</template>

<script>
import MarkdownPreview from "./components/markdown-preview";
import axios from "axios";

export default {
  name: 'App',
  components: {
    MarkdownPreview
  },
  data(){
    return {
      markdown: ''
    }
  },
  mounted(){
    axios.get('https://gist.githubusercontent.com/cuonggt/9b7d08a597b167299f0d/raw/c872b3fb5f851d00fba18dfbd456179319a3e9fe/markdown_guide.md')
      .then(response => {
        this.markdown = response.data;
      })
  }
}
</script>

<style>
#main {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#main {
  display: grid;
  grid-template-columns: 50% 50%;
  max-height: 100%;
  overflow: scroll;
}

#main textarea{
  max-height: 100%;
  overflow: scroll;
}
</style>
