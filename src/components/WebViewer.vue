<template>
  <div id="pageContainer">
    <canvas id="the-canvas"></canvas>
  </div>
</template>

<script>
import 'pdfjs-dist/web/pdf_viewer.css';
const pdfjsLib = require('pdfjs-dist');
pdfjsLib.GlobalWorkerOptions.workerSrc = require('pdfjs-dist/build/pdf.worker.entry.js');
export default {
  name: 'WebViewer',
  methods: {
    async getPdf() {
      let loadingTask = pdfjsLib.getDocument(
        './sample.pdf'
      );
      loadingTask.promise.then((pdf) => {
        pdf.getPage(1).then((page) => {
          var scale = 1.5;
          var viewport = page.getViewport({ scale: scale });

          var canvas = document.getElementById('the-canvas');
          var context = canvas.getContext('2d');
          canvas.height = viewport.height;
          canvas.width = viewport.width;

          var renderContext = {
            canvasContext: context,
            viewport: viewport,
          };
          page.render(renderContext);
        });
      });
    },
  },
  created(){
    this.getPdf();
  }
};
</script>
