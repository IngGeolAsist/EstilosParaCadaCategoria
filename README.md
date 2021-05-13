# Estilos Para Cada Categoría
Ya que sabes como vamos a trabajar, el resto solamente es localizar los colores que quieres utilizar o que ya están determinados, para esto utilizaremos nuevamente qgis o cualquier herramienta que nos permita tomar muestra de color y nos muestre código de color hexadecimal.
### Empezamos por categorizar las capas por CLAVE en Qgis, para poder trabajar con cada clave por separado y poder consultar el color en cualquier momento.
![screenshot](https://raw.githubusercontent.com/sampach95/EstilosParaCadaCategoria/master/img/Imagen1.png )
### Damos doble click en el primer color, en nuestro caso es “JtKvLu-Cz”. A continuación se despliega la siguiente ventana. 
![screenshot](https://raw.githubusercontent.com/sampach95/EstilosParaCadaCategoria/master/img/Imagen2.png )
### Damos click en la barra de color y se despliega el siguiente menú. Seleccionamos la opción de captura de color, si a continuación das click en cualquier lugar de la pantalla el color quedará guardado y podremos proceder a copial el código HTML. Si activas la opción de pantalla en tu computadora te será más fácil hace este procedimiento
![screenshot](https://raw.githubusercontent.com/sampach95/EstilosParaCadaCategoria/master/img/Imagen3.png )
### Al capturar el color volverás al menu anterior, da click nuevamente en la barra de color y veras un nuevo menú. En la parte derecha debajo de todas las barras de colores verás un recuadro con la notación html del color que capturaste copialo y conservalo.
- En nuestro caso quedó así: JtKvLu-Cz : #76cdd6
![screenshot](https://raw.githubusercontent.com/sampach95/EstilosParaCadaCategoria/master/img/Imagen4.png )
### Te recomiendo que hagas una lista con las claves y el color que vas a utilizar, te resultará mas sencillo solamente copiar y pegar  los colores en el código. Esta es nuestra lista.
- Qhoal:  #fff5dd
- Qhoco:  #f7ece1
- TplQptB:  #bf9487
- TplQptCgp-Ar:  #eedfb3
- TeGd-D:  #ed1c24
- TeoCgp:  #d8e9b9
- TmplA-B:  #fbc9bc
- TplA-Da:  #e4c19b
- TplR-TR:  #f9b6ac
- TplTR-TDa:  #f7b9d4
- ToR-TR:  #e1a49c
- KapceCz-Bro:  #00ac4e
- KiCz-Lu:  #5f7641
- KsLu-Cz:  #698c42
- JtKvLu-Cz:  #76cdd6

### Finalmente, agregas la información al código siguiendo la sintaxis que ya conoces. Así nos quedó a nosotros 

``` html
<script>
  <!-- ----- CAPAS VECTORIALES------	 -->
	var geology = L.geoJson(geology, {
	style:function(feature){
			switch (feature.properties.CLAVE){
				case 'Qhoal': return {color:'#fff5dd',fillOpacity: .5};
				case 'Qhoco': return {color:'#f7ece1',fillOpacity: .5};			
				case 'TplQptB': return {color:'#bf9487',fillOpacity: .5};
				case 'TplQptCgp-Ar': return {color:'#eedfb3',fillOpacity: .5};
				case 'TeGd-D': return {color:'#ed1c24',fillOpacity: .5};
				case 'TeoCgp': return {color:'#d8e9b9',fillOpacity: .5}; 
				case 'TmplA-B': return {color:'#fbc9bc',fillOpacity: .5};
				case 'TplA-Da': return {color:'#e4c19b',fillOpacity: .5};
				case 'TplR-TR': return {color:'#f9b6ac',fillOpacity: .5};
				case 'TplTR-TDa': return {color:'#f7b9d4',fillOpacity: .5};
				case 'ToR-TR': return {color:'#e1a49c',fillOpacity: .5};
				case 'KapceCz-Bro': return {color:'#00ac4e',fillOpacity: .5};	
				case 'KiCz-Lu': return {color:'#5f7641',fillOpacity: .5};
				case 'KsLu-Cz': return {color:'#698c42',fillOpacity: .5};
				case 'JtKvLu-Cz': return {color:'#76cdd6',fillOpacity: .5};	
			}}
			}).addTo(map);
</script>
```

Puedes probar si el mapa funciona cada vez que agregues un nuevo color para detectar si hay errores sobre la marcha. 

### Así es como nos quedó.
![screenshot](https://raw.githubusercontent.com/sampach95/EstilosParaCadaCategoria/master/img/Imagen5.png )

### Podrías agregar un pop up que al dar click te brinde la información de una litología, añadiendo las siguientes líneas de código. 

``` html
<script>
  <!-- ----- CAPAS VECTORIALES------	 -->
	var geology = L.geoJson(geology, {
	style:function(feature){
			switch (feature.properties.CLAVE){
				case 'Qhoal': return {color:'#fff5dd',fillOpacity: .5};
				case 'Qhoco': return {color:'#f7ece1',fillOpacity: .5};			
				case 'TplQptB': return {color:'#bf9487',fillOpacity: .5};
				case 'TplQptCgp-Ar': return {color:'#eedfb3',fillOpacity: .5};
				case 'TeGd-D': return {color:'#ed1c24',fillOpacity: .5};
				case 'TeoCgp': return {color:'#d8e9b9',fillOpacity: .5}; 
				case 'TmplA-B': return {color:'#fbc9bc',fillOpacity: .5};
				case 'TplA-Da': return {color:'#e4c19b',fillOpacity: .5};
				case 'TplR-TR': return {color:'#f9b6ac',fillOpacity: .5};
				case 'TplTR-TDa': return {color:'#f7b9d4',fillOpacity: .5};
				case 'ToR-TR': return {color:'#e1a49c',fillOpacity: .5};
				case 'KapceCz-Bro': return {color:'#00ac4e',fillOpacity: .5};	
				case 'KiCz-Lu': return {color:'#5f7641',fillOpacity: .5};
				case 'KsLu-Cz': return {color:'#698c42',fillOpacity: .5};
				case 'JtKvLu-Cz': return {color:'#76cdd6',fillOpacity: .5};	
			}},
			onEachFeature: function( feature, layer ){
      		layer.bindPopup( "<strong>" + "LITOLOGÍA:" + "</strong><br/>"+ feature.properties.LITOLOGIA)
		}
		}).addTo(map);
</script>
```
### El código completo debería ser como eldiguiente

```html
<html>
<head>
	<meta charset="utf-8">
	<title>Mapa E14C17_2</title>
	
	<!-- -----LIBRERIAS-------- -->
	<link rel="stylesheet" href="https://unpkg.com/leaflet@1.6.0/dist/leaflet.css"
	integrity="sha512-xwE/Az9zrjBIphAcBb3F6JVqxf46+CDLwfLMHloNu6KEQCAWi6HcDUbeOfBIptF7tcCzusKFjFw2yuvEpDL9wQ=="
	crossorigin=""/>
	<script src="https://unpkg.com/leaflet@1.6.0/dist/leaflet.js"
	integrity="sha512-gZwIG9x3wUXg2hdXF6+rVkLF/0Vi9U8D2Ntg4Ga5I5BZpVkVxlJWbSQtXPSiUTtC0TjtGOmxa1AJPuV0CPthew=="
	crossorigin=""></script>
	
	
	<!-- -----CAPAS JSON------ -->
	
	
	<script type="text/javascript" src="DATA/json/Geología_PeñaDe Bernal_GCS.js"></script>
	<script type="text/javascript" src="DATA/json/contact.js"></script>
	
	
	
	
	<!-- -----ESTILOS DEL MAPA------ -->
	<style>
	#mapDIV {
	height: 100%;
	width: 100%;
	border: solid 2px black;
	}
	</style>
</head>

<body>
<div id="mapDIV"></div>

 <script>	
 <!-- ------ CARACTERISTICAS DEL MAPA------ -->
 var map = L.map('mapDIV', {
		center:[20.83748 , -99.71396],
		zoom:11
	});
	
	var scale = L.control.scale({
		'imperial':false
	});
	scale.addTo(map);
	
<!-- ------ ESTILOS PARA CAPAS VECTORIALES ------ -->
	
	var contact_style = {
		color: "#000000",
		weight: 2,
		opacity: 1,
	};
	
<!-- ------CAPAS BASE------ -->
	
	var osm = L.tileLayer('http://a.tile.openstreetmap.org/{z}/{x}/{y}.png',
	{attribution: 'Map Data &copy; OpenStreetMap contributors'
	});
	osm.addTo(map);
	
	var topo = L.tileLayer('https://{s}.tile.opentopomap.org/{z}/{x}/{y}.png', {
	maxZoom: 17,
	attribution: 'Map data: &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, <a href="http://viewfinderpanoramas.org">SRTM</a> | Map style: &copy; <a href="https://opentopomap.org">OpenTopoMap</a> (<a href="https://creativecommons.org/licenses/by-sa/3.0/">CC-BY-SA</a>)'
	}); 
	topo.addTo(map);
	
	var sat = L.tileLayer('https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}', {
	attribution: 'Tiles &copy; Esri &mdash; Source: Esri, i-cubed, USDA, USGS, AEX, GeoEye, Getmapping, Aerogrid, IGN, IGP, UPR-EGP, and the GIS User Community'
	});

<!-- ----- CONTROLADOR DEL MAPA------	 -->
	var basemaps = {
		"OSM": osm,
		"Topografía": topo,										
		"Satélite": sat
		};
	L.control.layers(basemaps).addTo(map);
	
<!-- ----- CAPAS VECTORIALES------	 -->
	var geology = L.geoJson(geology, {
	style:function(feature){
			switch (feature.properties.CLAVE){
				case 'Qhoal': return {color:'#fff5dd',fillOpacity: .5};
				case 'Qhoco': return {color:'#f7ece1',fillOpacity: .5};			
				case 'TplQptB': return {color:'#bf9487',fillOpacity: .5};
				case 'TplQptCgp-Ar': return {color:'#eedfb3',fillOpacity: .5};
				case 'TeGd-D': return {color:'#ed1c24',fillOpacity: .5};
				case 'TeoCgp': return {color:'#d8e9b9',fillOpacity: .5}; 
				case 'TmplA-B': return {color:'#fbc9bc',fillOpacity: .5};
				case 'TplA-Da': return {color:'#e4c19b',fillOpacity: .5};
				case 'TplR-TR': return {color:'#f9b6ac',fillOpacity: .5};
				case 'TplTR-TDa': return {color:'#f7b9d4',fillOpacity: .5};
				case 'ToR-TR': return {color:'#e1a49c',fillOpacity: .5};
				case 'KapceCz-Bro': return {color:'#00ac4e',fillOpacity: .5};	
				case 'KiCz-Lu': return {color:'#5f7641',fillOpacity: .5};
				case 'KsLu-Cz': return {color:'#698c42',fillOpacity: .5};
				case 'JtKvLu-Cz': return {color:'#76cdd6',fillOpacity: .5};	
			}}
			}).addTo(map);
	
	var contact = L.geoJson(contact,{
		style: contact_style
		}).addTo (map);
	 
 </script>
</body>
</html>
```
Siguiente Tutorial 

Haz click en el siguiente enlace para volver a la pagina inicial
https://github.com/sampach95/ComoCrearMapasEnLaWebConLeaflet


