<template>
  <div class="ventana">
      <h1>{{title}}</h1>
      <slot>Default footer</slot>
  </div>
</template>

<script>
export default {
    props:{
        title: {
            type: String,
            require: true
        }
    }
}
</script>

<style>
.ventana{
    max-height: 100%;
    word-wrap: break-word;
}

.ventana img {
    width: 100%;
}
</style>