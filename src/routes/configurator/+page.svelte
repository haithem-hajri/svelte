<script>
  import { onMount } from "svelte";
  let images = $state([]);
  const productId = 1129;
  const url = `https://konystart.com/start/module/toolcanvas/canvas?p=${productId}&iframe=1&nocookie=1`;

  onMount(() => {

    window.addEventListener("message", (event) => {

      if (event.data.type === "canvasExport") {

        console.log("Images reçues:");
        console.log(event.data.images);
        event.data.images.forEach(img => {
          console.log(img.image);
        });
         images = event.data.images; 
      }

      if (event.data.type === "canvasPDF") {

        console.log("PDF reçu:");
        console.log(event.data.pdf);
        images = event.data.images; 
      }
       if (event.data.type === "canvasSaveConfig") {

      console.log("SAVE CONFIG reçu:");
      console.log(event.data.config);

    }

    if (event.data.type === "canvasSaveBDC") {

      console.log("SAVE BDC reçu:");
      console.log(event.data.config);

    }

    });

  });
</script>

<iframe 
  src={url} 
  width="100%" 
  height="1200" 
  style="border:0" 
  sandbox="allow-scripts allow-same-origin allow-forms allow-popups allow-downloads allow-modals"
  title="Configurateur de produit"
></iframe>

<h2>Images exportées</h2>

<div class="images">
  {#each images as img}
    <img src={img.image} alt="canvas export">
  {/each}
</div>

<style>
.images{
  display:flex;
  gap:20px;
  margin-top:20px;
  flex-wrap:wrap;
}

.images img{
  width:300px;
  border:1px solid #ddd;
}
</style>