#custom Leaflet.print

A fork of the [Leaflet.print](https://github.com/aratcliffe/Leaflet.print) project with extensions needed for a work project.
Note: We use a custom mapfish template which includes a title and a comment the user can set - so the comment function only makes sense if there is such a field in your printing template.

Currently the following extension where made:

* Option to add layers which should be ignored while printing
* Use of the [Leaflet.Areaselect](https://github.com/heyman/leaflet-areaselect) plugin to print a specific bounding box
* The possibility to add a comment to the printed document

*Requires Leaflet 0.6.0 or newer, jQuery and the  [Leaflet.Areaselect](https://github.com/heyman/leaflet-areaselect) plugin.*

## Print Provider
| Option | Type | Default | Description
| --- | --- | --- | ---
| ignoreLayers | [L.TileLayer](http://leafletjs.com/reference.html#tilelayer) | `[]` | A list of layers to ignore for printing
| comment | boolean | `false` | Will show an default javascript input prompt to add a user comment to the printed document
| maxCommentLength | int | `false` | Maximum length for the comment text


## Print Control
| Option | Type | Default | Description
| --- | --- | --- | ---
| showArea | boolean | `false` |  Will show a resizable centered box on top of the map to select an area for printing
| layoutAreas |  | `{}` | A json object containing the printing layouts and the default area width and height


## Examples

[Mapfish Example](https://raw.githubusercontent.com/schmidtpa/Leaflet.print/master/examples/mapfish-example.txt)

```javascript
var printProvider = L.print.provider({
   method: 'POST',
   url: 'http://myserver.local/print-servlet/pdf',
   autoLoad: true,
   outputFormat: 'pdf',
   dpi: 254,
   outputFilename: 'pdfExport',
   ignoreLayers: [osm],
   comment:true,
   maxCommentLength: 100,
   customParams: {
		mapTitle: 'My custom map title'
		}
});

var printControl = L.control.print({
   provider: printProvider,
   showArea: true,
   layoutAreas: {
	   'A3 landscape': {
		   height:670,
		   width:1100
	   },
	   'A4 portrait': {
		   height:710,
		   width:545
	   }
   }
}); 

printControl.addTo(map);
```

##License
This software is released under the MIT licence.
