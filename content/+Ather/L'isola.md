---
map_height_y: 1536
map_width_x: 2048
scale_pixels: 268
scale_pixels_range: 25
mapCalc1: 0.09328358208955223
---

> [!NOTE]- Quick Calculator  
> Map Height in Pixels: `INPUT[number:map_height_y]`  
> Map Width in Pixels: `INPUT[number:map_width_x]`  
> lat: `VIEW[{map_height_y} / 2][math]`  
> long: `VIEW[{map_width_x} / 2][math]`  
> How Many Pixels In Scale: `INPUT[number:scale_pixels]`  
> How Many Units in Scale: `INPUT[number:scale_pixels_range]`  
> Scale: `VIEW[1/({scale_pixels}/{scale_pixels_range})][math:mapCalc1]`
<!-- Importa la libreria Leaflet CSS e JS -->

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<div id="HimitsuMap" style="width: 95%; height: 800px; border-radius: 8px;"></div>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    // Definizione delle dimensioni dell'immagine
    var h = 1536, w = 2048;
    
    // Inizializzazione della mappa per immagini 2D (Simple CRS)
    var map = L.map('HimitsuMap', {
      crs: L.CRS.Simple,
      minZoom: -1.5,
      maxZoom: 1,
      zoomSnap: 0.5
    });

    var bounds = [[0, 0], [h, w]];
    // Inserisci qui il percorso corretto della tua immagine su Quartz
    var image = L.imageOverlay('./HImitsu.jpg', bounds).addTo(map);

    map.fitBounds(bounds);
  });
</script>

```leaflet  
id: HimitsuMap ### Must be unique with no spaces  
image: [[HImitsu.jpg]] ### Link to the map image file. Do not add a ! in front of the image  
bounds: [[0,0], [1536, 2048]] ### Size of the map in px Height_y, Width_x. Ignore 0,0  
height: 800px ### Size of the leaflet embed in px on your screen  
width: 95% ### Size of the leaflet embed in your note  
lat: 768 ### To center the map, make this half of the map height.  
long: 1024 ### To center the map, make this half of the map width.  
minZoom: -1.5 ### Controls how far away from the map you can zoom out. Hover over the target icon to see the current level.  
maxZoom: 1 ### Controls how far towards the map you can zoom in. Hover over the target icon to see the current level.  
defaultZoom: -1 ### Sets the default zoom level when the map loads. Hover over the target icon to see the current level.  
zoomDelta: 0.5 ### Adjust how much the zoom changes when you zoom in or out.  
unit: mi ### The value displayed when measuring so you know what type of unit is being measure.  
scale: 0.09328358208955223 ### Real units/px (resolution) of your map  
recenter: false  
darkmode: false ### marker
```
