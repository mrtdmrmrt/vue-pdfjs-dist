<template>
  <div id="pageContainer">
    <div id="viewer" class="pdfViewer"></div>
  </div>
</template>

<script>
// const pdfjsLib = require("pdfjs-dist/build/pdf");
//import pdfjsLib from "pdfjs-dist/build/pdf";
import { PDFViewer } from "pdfjs-dist/web/pdf_viewer";
// import "pdfjs-dist/web/pdf_viewer.css";

// console.log(pdfjsLib.getDocument("./sample.pdf"))
// console.log(PDFViewer)
// const pdfWorker = require("pdfjs-dist/build/pdf.worker.min.js")
// pdfjsLib.GlobalWorkerOptions.workerSrc = pdfWorker;
const pdfjsLib = require("pdfjs-dist");
pdfjsLib.GlobalWorkerOptions.workerSrc = require("pdfjs-dist/build/pdf.worker.entry.js");
export default {
  name: "PdfViewer",
  mounted() {
    this.getPdf();
  },
  methods: {
    async getPdf() {
      
      let container = document.getElementById("pageContainer");
      let pdfViewer = new PDFViewer({
        container: container
      });
      let loadingTask = pdfjsLib.getDocument("./sample.pdf");
      let pdf = await loadingTask.promise;
      pdfViewer.setDocument(pdf);
    }
  }
};
</script>

<style>
#pageContainer {
  margin: auto;
  width: 80%;
}

div.page {
  display: inline-block;
}
</style>