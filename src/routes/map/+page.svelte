<svelte:head>
	<title>Map</title>
	<meta name="description" content="About this Map" />
   
</svelte:head>

<script>
    import { onMount } from 'svelte';
    import Map from 'ol/Map.js';

    let map;
  
    onMount(() => {
      import('ol/Map').then(({ default: Map }) => {
        import('ol/View').then(({ default: View }) => {
          map = new Map({
            target: 'map',
            layers: [
              new ol.layer.Tile({
                source: new ol.source.OSM()
              })
            ],
            view: new View({
              center: [0, 0],
              zoom: 2
            })
          });
        });
      });
    });
  </script>
  
  <style>
    #map {
      width: 100%;
      height: 100%;
    }
  </style>
  
  <div id="map"></div>