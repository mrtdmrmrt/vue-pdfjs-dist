<template>
  <div id="app">
    <PdfViewer/>
    <!-- <WebViewer :path="`${publicPath}lib`" url="https://pdftron.s3.amazonaws.com/downloads/pl/webviewer-demo.pdf"/> -->
  </div>
</template>

<script>
import PdfViewer from "./components/PdfViewer";
//import WebViewer from './components/WebViewer.vue'
export default {
  name: "App",
  components: {
    PdfViewer,
    //WebViewer
  },
  data(){
    return {
      publicPath: process.env.BASE_UR
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: black;
  padding: 50px;
}
</style>
