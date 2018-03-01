# OpenLayers 4.6+ wrapper for Polymer 2.
This is a Polymer 2-native wrapper for OpenLayers. It allows a simple embedding of an OpenLayers vector map into a Polymer project, adding layers to a self-hosted tile server, and adding markers on the map.

# Install
    bower install --save meledin/ol-map
    
# Usage
The map will embed itself in the target webpage with as little code as

    <ol-map></ol-map>
    
This will default to using the OSM tile servers. These are not intended for production use, so point the map to a custom tile source. The following also illustrates the default properties, which can be used to steer the map. Longitude, latitude and zoom will also notify when changed based on user panning.

    <ol-map longitude=0 latitude=0 zoom=1 animate animate-duration=500>
      <ol-layer url="https://my.tileserver.net/{z}/{x}/{y}.png"></ol-layer>
    </ol-map>
  
The wrapper currently supports the following properties on all layers:
 * zIndex
 * opacity
 
## Adding a line
Lines are added using the <ol-line> and <ol-point> elements. A line accepts 2+ points, and will draw a fill between each of the points in turn. Each segment of the line can have its color changed using the `color` property of <ol-point>, or it can be globally set on the line. Use `width` and `lineDash` to customise the line appearance further.

    <ol-line width=2 line-dash="[5]">
      <ol-point longitude=1 latitude=1></ol-point>
      <ol-point longitude=1 latitude=2 color="#FF0000"></ol-point>
    </ol-line>
    
Any property bindingts to items within the line _should_ cascade back to the line.

## Adding a marker
Two types of markers are implemented: icons and circles.

    <ol-marker-icon src="//dev.openlayers.org/img/marker.png" longitude=1 latitude=1 color="0xFF0000"></ol-marker-icon>
    <ol-marker-circle longitude=1 latitude=1 radius=100 color="0xFF0000" stroke="0x00FF00" stroke-width=2></ol-marker-circle>
