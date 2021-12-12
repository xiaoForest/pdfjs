<template>
  <div ref="viewer"></div>
</template>

<script>
/* eslint-disable */
import WebViewer from "@pdftron/pdfjs-express-viewer";

export default {
  name: "WebViewer",
  props: {
    path: String,
  },
  mounted: function () {
    WebViewer(
      {
        path: this.path,
        initialDoc: `https://hpread.xhwxpos.com/uploads/20211022/38676e9236fa6656ac59eb3cf3427862.pdf`,
        licenseKey: 'sqVmw9Ab5HE9jNTYSwPJ',
      },
      this.$refs.viewer
    ).then((instance) => {
      // now you can access APIs through the WebViewer instance
      const { Core, UI } = instance;
      // instance.UI.setLanguage('../../public/lib/ui/i18n/translation-zh_cn.json');
      // adding an event listener for when a document is loaded
      Core.documentViewer.addEventListener("documentLoaded", () => {
        console.log("document loaded");
      });

      // adding an event listener for when the page number has changed
      Core.documentViewer.addEventListener(
        "pageNumberUpdated",
        (pageNumber) => {
          console.log(`Page number is: ${pageNumber}`);
        }
      );

      // adds a button to the header that on click sets the page to the next page
      UI.setHeaderItems((header) => {
        header.push({
          type: "actionButton",
          img: "https://icons.getbootstrap.com/assets/icons/caret-right-fill.svg",
          onClick: () => {
            const currentPage = Core.documentViewer.getCurrentPage();
            const totalPages = Core.documentViewer.getPageCount();
            const atLastPage = currentPage === totalPages;

            if (atLastPage) {
              Core.documentViewer.setCurrentPage(1);
            } else {
              Core.documentViewer.setCurrentPage(currentPage + 1);
            }
          },
        });
      });
    });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div {
  width: 100%;
  height: 100vh;
}
</style>
