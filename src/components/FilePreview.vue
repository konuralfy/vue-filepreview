<template>
  <div class="container" :style="container_style" ref="container">
    <div class="image-container">
      <img class="image" :src="getBase64"/>
    </div>
    <div class="title-container">
      <span class="title">{{this.title}}</span>
    </div>
  </div>
</template>

<script>
// import * as icons from '!raw-loader!../assets/pdf.txt';

export default {
  name: 'FilePreview',
  css: {
    extract: true
  },
  props: {
    file_type: String,
    height: String,
    title: String,
    background_color: {type: String , default: "white"}
  },
  computed: {
    container_style () {
      return 'width: ' + this.height + 'px;height: '+this.height+'px;' + "background-color:"+this.background_color;
    },
    getBase64 () {
      var images = require.context('../assets/', false, /\.png$/)
      return images('./' + this.file_type + ".png")
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import '../assets/filepreview.css';
</style>
