<template>
  <div id="main">
    <Ventana :title="'Editor'">
      <template v-slot:titleButton><button @click="setMarkdown">Convert</button></template>
      <textarea name="editor" id="editor" v-model="editorMarkdown"></textarea>
    </Ventana>

    <Ventana :title="'Preview'">
      <MarkdownPreview ></MarkdownPreview>
    </Ventana>
  </div>
</template>

<script>
import MarkdownPreview from "./components/markdown-preview";
import Ventana from "./components/ventana";
import axios from "axios";
import EventBus from './event-bus';

export default {
  name: 'App',
  components: {
    MarkdownPreview,
    Ventana
  },
  data(){
    return {
      markdown: '',
      editorMarkdown: ''
    }
  },
  mounted(){
    axios.get('https://gist.githubusercontent.com/cuonggt/9b7d08a597b167299f0d/raw/c872b3fb5f851d00fba18dfbd456179319a3e9fe/markdown_guide.md')
      .then(response => {
        this.editorMarkdown = response.data;
      })
  },
  methods:{
    setMarkdown(){
      EventBus.$emit('parse-markdown', this.editorMarkdown);
    }
  }
}
</script>

<style>
body{
  max-height: 100%;
  margin: 0;
}

#main {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

#main {
  width: 100%;
  display: grid;
  grid-template-columns: 50% 50%;
  max-height: 100%;
}

textarea{
  width: 97%;
  height: 100%;
}
</style>
