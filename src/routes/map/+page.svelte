<svelte:head>
	<title>Map</title>
	<meta name="description" content="About this Map" />
   
</svelte:head>

<script>
  import { onMount } from 'svelte';
  import Map from 'ol/Map';
  import View from 'ol/View';
  import TileLayer from 'ol/layer/Tile';
  import OSM from 'ol/source/OSM';

  onMount(async () => {
    const map = await createMap();
  });

  async function createMap() {
    const map = new Map({
      target: 'map',
      layers: [new TileLayer({ source: new OSM() })],
      view: new View({
        center: [0, 0],
        zoom: 2,
      }),
    });
    return map;
  }

</script>

<style>
  #map {
    width: 100%;
    height: 100vh; 
  }
</style>

<div id="map"></div>