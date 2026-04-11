<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Aqua Vitalis: Providing Drinking Water in the Southern Arizona Desert</title>
	<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
		integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY=" crossorigin="" />
	<style>
		:root {
			--bg: #f4efe5;
			--surface: #fffaf0;
			--ink: #2d2418;
			--muted: #6a5a45;
			--accent: #7d5a3c;
			--line: #dacdb7;
		}

		* {
			box-sizing: border-box;
			margin: 0;
			padding: 0;
		}

		body {
			font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
			background: var(--bg);
			color: var(--ink);
			line-height: 1.5;
		}

		header {
			background: var(--surface);
			border-bottom: 1px solid var(--line);
			padding: 1rem 1.25rem;
			position: sticky;
			top: 0;
			z-index: 20;
		}

		nav {
			display: flex;
			align-items: center;
			justify-content: space-between;
			max-width: 1200px;
			margin: 0 auto;
			gap: 1rem;
		}

		.site-title {
			font-size: 1.2rem;
			font-weight: 700;
			letter-spacing: 0.02em;
		}

		.nav-links {
			display: flex;
			gap: 1rem;
			flex-wrap: wrap;
		}

		.nav-links a {
			color: var(--accent);
			text-decoration: none;
			font-weight: 600;
		}

		main {
			max-width: 1200px;
			margin: 0 auto;
			padding: 1.25rem;
			display: grid;
			gap: 1.25rem;
		}

		section {
			background: var(--surface);
			border: 1px solid var(--line);
			border-radius: 10px;
			padding: 1rem;
		}

		h1, h2 {
			margin-bottom: 0.5rem;
		}

		p {
			color: var(--muted);
		}

		.hero {
			display: grid;
			gap: 0.75rem;
		}

		.map-panel {
			padding: 0;
			overflow: hidden;
		}

		#map {
			width: 100%;
			height: 460px;
			background: #ddd2bc;
			border: 0;
		}

		.map-caption {
			padding: 0.75rem 1rem;
			border-top: 1px solid var(--line);
			background: #f9f2e5;
			font-size: 0.95rem;
		}

		.content-grid {
			display: grid;
			grid-template-columns: 2fr 1fr;
			gap: 1rem;
		}

		.photo-grid {
			display: grid;
			grid-template-columns: repeat(3, minmax(0, 1fr));
			gap: 0.75rem;
			margin-top: 0.5rem;
		}

		.photo-grid img {
			width: 100%;
			height: 180px;
			object-fit: cover;
			border-radius: 8px;
			border: 1px solid var(--line);
			background: #efe3cb;
		}

		.video-wrap {
			margin-top: 0.5rem;
			position: relative;
			width: 100%;
			padding-top: 56.25%;
			border-radius: 8px;
			overflow: hidden;
			border: 1px solid var(--line);
			background: #e9dcc4;
		}

		.video-wrap iframe,
		.video-wrap video {
			position: absolute;
			top: 0;
			left: 0;
			width: 100%;
			height: 100%;
			border: 0;
		}

		.dashboard-wrap {
			margin-top: 0.6rem;
			position: relative;
			width: 100%;
			height: 420px;
			border-radius: 8px;
			overflow: hidden;
			border: 1px solid var(--line);
			background: #efe3cb;
		}

		.dashboard-wrap iframe {
			width: 100%;
			height: 100%;
			border: 0;
		}

		footer {
			max-width: 1200px;
			margin: 0 auto 1.25rem;
			padding: 0 1.25rem;
			color: var(--muted);
			font-size: 0.9rem;
		}

		@media (max-width: 900px) {
			.content-grid {
				grid-template-columns: 1fr;
			}

			.photo-grid {
				grid-template-columns: repeat(2, minmax(0, 1fr));
			}

			#map {
				height: 360px;
			}
		}

		@media (max-width: 560px) {
			.photo-grid {
				grid-template-columns: 1fr;
			}

			#map {
				height: 300px;
			}
		}
	</style>
</head>
<body>
	<header>
		<nav>
			<div class="site-title">Aqua Vitalis: Providing Drinking Water in the Southern Arizona Desert</div>
			<div class="nav-links">
				<a href="#map-section">Map</a>
				<a href="#about-section">Text</a>
				<a href="#photos-section">Photos</a>
				<a href="#video-section">Video</a>
			</div>
		</nav>
	</header>

	<main>
		<section class="hero">
			<h1>Interactive Map</h1>
			<p>
				Use this template to combine geographic data, explanatory text, imagery,
				and video in one place.
			</p>
		</section>

		<section class="map-panel" id="map-section">
			<div id="map" aria-label="Map display area"></div>
			<div class="map-caption">
				Interactive Southern Arizona map loaded from the project configuration,
				including AGOL layers, legend, and layer controls.
			</div>
		</section>

		<div class="content-grid">
			<section id="about-section">
				<h2>Project Text</h2>
				<p>
					Add your narrative, methods, findings, and context here. This section
					works well for introductions, timeline events, and key insights.
				</p>
			</section>

			<section>
				<h2>Quick Facts</h2>
				<p>
					Live dashboard from ArcGIS Online.
				</p>
				<div class="dashboard-wrap">
					<iframe
						src="https://www.arcgis.com/apps/dashboards/d3de89c3071b40febff4c26452e2f720"
						title="ArcGIS Dashboard Quick Facts"
						loading="lazy"
						referrerpolicy="strict-origin-when-cross-origin"
						allowfullscreen>
					</iframe>
				</div>
				<p style="margin-top: 0.6rem;">
					If the dashboard does not load here, open it on
					<a href="https://www.arcgis.com/apps/dashboards/d3de89c3071b40febff4c26452e2f720" target="_blank" rel="noopener noreferrer">ArcGIS Dashboard</a>.
				</p>
			</section>
		</div>

		<section id="photos-section">
			<h2>Photo Gallery</h2>
			<p>Replace these placeholder images with your project photos.</p>
			<div class="photo-grid">
				<img src="https://placehold.co/600x400?text=Photo+1" alt="Placeholder photo 1">
				<img src="https://placehold.co/600x400?text=Photo+2" alt="Placeholder photo 2">
				<img src="https://placehold.co/600x400?text=Photo+3" alt="Placeholder photo 3">
			</div>
		</section>

		<section id="video-section">
			<h2>About Humane Borders' Mission</h2>
			<p>Featured YouTube video.</p>
			<div class="video-wrap">
				<iframe
					src="https://www.youtube.com/embed/wXiyJBaN0Qk"
					title="YouTube video"
					allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
					allowfullscreen>
				</iframe>
			</div>
			<p style="margin-top: 0.6rem;">
				If the video does not load here, watch it on
				<a href="https://www.youtube.com/watch?v=wXiyJBaN0Qk" target="_blank" rel="noopener noreferrer">YouTube</a>.
			</p>
		</section>
	</main>

	<footer>
		<p>Template ready. Connect your map script and replace placeholder content.</p>
	</footer>

	<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"
		integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo=" crossorigin=""></script>
	<script src="https://unpkg.com/esri-leaflet@3.0.12/dist/esri-leaflet.js"></script>
	<script src="https://unpkg.com/leaflet.heat@0.2.0/dist/leaflet-heat.js"></script>
	<script src="https://unpkg.com/@turf/turf@6.5.0/turf.min.js"></script>
	<script>
		var map = L.map('map').setView([32.4, -112.634], 8);

		var streetLayer = L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
			attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
		});

		var terrainLayer = L.tileLayer('https://{s}.tile.opentopomap.org/{z}/{x}/{y}.png', {
			attribution: 'Map data: &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, <a href="https://opentopomap.org">OpenTopoMap</a> (CC-BY-SA)',
			subdomains: 'abc',
			minZoom: 0,
			maxZoom: 17
		});

		var waterLayerGroup = L.layerGroup().addTo(map);
		var migrantLayerGroup = L.layerGroup().addTo(map);
		var deathsOutsideLayerGroup = L.layerGroup().addTo(map);
		var borderLayerGroup = L.layerGroup().addTo(map);
		var roadsLayerGroup = L.layerGroup().addTo(map);
		var reservationsLayerGroup = L.layerGroup().addTo(map);
		var countyBoundariesLayerGroup = L.layerGroup().addTo(map);

		const AGOL_TOKEN = '';

		function getPointCoordinates(feature) {
			const geom = feature && feature.geometry ? feature.geometry : {};
			const coords = geom.coordinates || [];
			if (!Array.isArray(coords) || coords.length < 2) return null;
			return [coords[0], coords[1]];
		}

		function textContainsTohonoOodham(value) {
			if (typeof value !== 'string') return false;
			const normalized = value.toLowerCase();
			return normalized.includes('tohono') || normalized.includes('oodham') || normalized.includes("o'odham") || normalized.includes('o odham');
		}

		function isTohonoOodhamReservation(feature) {
			if (!feature || !feature.properties) return false;
			return Object.values(feature.properties).some(textContainsTohonoOodham);
		}

		function isPointInsideAnyReservation(lon, lat, reservationFeatures) {
			if (typeof turf === 'undefined' || !Array.isArray(reservationFeatures) || reservationFeatures.length === 0) {
				return false;
			}

			const pt = turf.point([lon, lat]);
			for (const polyFeature of reservationFeatures) {
				try {
					if (turf.booleanPointInPolygon(pt, polyFeature)) return true;
				} catch (_err) {
					// Skip malformed geometries and continue checking others.
				}
			}
			return false;
		}

		streetLayer.addTo(map);

		L.control.layers({
			'Streets': streetLayer,
			'Terrain': terrainLayer
		}, {
			'Water 3-mile Buffers': waterLayerGroup,
			'Migrant Deaths': migrantLayerGroup,
			'Deaths Outside 2-mile Buffers': deathsOutsideLayerGroup,
			'US-Mexico Border': borderLayerGroup,
			'AZ Roads': roadsLayerGroup,
			'AZ Reservations': reservationsLayerGroup,
			'AZ County Boundaries': countyBoundariesLayerGroup
		}).addTo(map);

		async function resolveFeatureLayerUrl(serviceUrl) {
			if (/\/FeatureServer\/\d+$/.test(serviceUrl)) {
				return serviceUrl;
			}

			try {
				const response = await fetch(serviceUrl + '?f=pjson');
				const info = await response.json();
				if (info && Array.isArray(info.layers) && info.layers.length > 0) {
					return serviceUrl + '/' + info.layers[0].id;
				}
			} catch (err) {
				console.warn('Could not resolve layer id for service:', serviceUrl, err);
			}

			return serviceUrl + '/0';
		}

		async function initAgolLayers() {
			const waterBufferLayerUrl = await resolveFeatureLayerUrl('https://services.arcgis.com/o6oETlrWetREI1A2/arcgis/rest/services/water_3_mile_buffer/FeatureServer');
			const migrantDeathsLayerUrl = await resolveFeatureLayerUrl('https://services.arcgis.com/o6oETlrWetREI1A2/arcgis/rest/services/migrant_deaths_2021_2025/FeatureServer');
			const deathsOutsideLayerUrl = await resolveFeatureLayerUrl('https://services.arcgis.com/o6oETlrWetREI1A2/arcgis/rest/services/deaths_outside_buffers/FeatureServer');
			const azRoadsLayerUrl = await resolveFeatureLayerUrl('https://services.arcgis.com/o6oETlrWetREI1A2/arcgis/rest/services/AZ_Roads/FeatureServer');
			const reservationsLayerUrl = await resolveFeatureLayerUrl('https://services.arcgis.com/o6oETlrWetREI1A2/arcgis/rest/services/American_Indian_Reservations_in_Arizona/FeatureServer');
			const countyBoundaryLayerUrl = await resolveFeatureLayerUrl('https://services.arcgis.com/o6oETlrWetREI1A2/arcgis/rest/services/Arizona_County_Boundary/FeatureServer');

			const deathPointToLayer = function (_geojson, latlng) {
				return L.circleMarker(latlng, {
					radius: 4,
					color: '#5a0000',
					weight: 1,
					fillColor: '#5a0000',
					fillOpacity: 0.95
				});
			};

			const agolWaterBufferLayer = L.esri.featureLayer({
				url: waterBufferLayerUrl,
				token: AGOL_TOKEN || undefined,
				style: function () {
					return {
						color: '#1f5fa8',
						weight: 2,
						opacity: 0.85,
						fillColor: '#4b8fd6',
						fillOpacity: 0.12
					};
				}
			});
			agolWaterBufferLayer.addTo(waterLayerGroup);

			const reservationsQueryLayer = L.esri.featureLayer({
				url: reservationsLayerUrl,
				token: AGOL_TOKEN || undefined
			});

			const tohonoReservationFeatures = await new Promise(resolve => {
				reservationsQueryLayer.query().where('1=1').run(function (error, featureCollection) {
					if (error) {
						console.error('Failed to load reservation features for death filtering:', error);
						resolve([]);
						return;
					}
					const features = (featureCollection && featureCollection.features) ? featureCollection.features : [];
					resolve(features.filter(isTohonoOodhamReservation));
				});
			});

			const migrantDeathsQueryLayer = L.esri.featureLayer({
				url: migrantDeathsLayerUrl,
				token: AGOL_TOKEN || undefined
			});

			migrantDeathsQueryLayer.query().where('1=1').run(function (error, featureCollection) {
				if (error) {
					console.error('Failed to load migrant deaths from AGOL:', error);
					return;
				}

				const allFeatures = (featureCollection && featureCollection.features) ? featureCollection.features : [];
				const filteredFeatures = allFeatures.filter(feature => {
					const coords = getPointCoordinates(feature);
					if (!coords) return false;
					return !isPointInsideAnyReservation(coords[0], coords[1], tohonoReservationFeatures);
				});

				migrantLayerGroup.clearLayers();
				filteredFeatures.forEach(feature => {
					const props = feature.properties || {};
					const coords = getPointCoordinates(feature);
					if (!coords) return;

					const marker = deathPointToLayer(feature, L.latLng(coords[1], coords[0]));
					marker.bindPopup(
						'Date: ' + (props.DATE || props.Date || props.date || 'N/A') + '<br>' +
						'Sex: ' + (props.SEX || props.Sex || props.sex || 'N/A') + '<br>' +
						'Age: ' + (props.AGE || props.Age || props.age || 'N/A') + '<br>' +
						'Corridor: ' + (props.CORRIDOR || props.Corridor || props.corridor || 'N/A') + '<br>' +
						'County: ' + (props.COUNTY || props.County || props.county || 'N/A')
					);
					marker.addTo(migrantLayerGroup);
				});

				const tableBody = document.getElementById('migrantTableBody');
				if (tableBody) {
					tableBody.innerHTML = '';
					filteredFeatures.forEach(feature => {
						const props = feature.properties || {};
						const coords = getPointCoordinates(feature) || ['', ''];
						const rowValues = [
							props.ID || props.Id || props.id || '',
							props.LAST_NAME || props.LASTNAME || props.LastName || props.LAST || '',
							props.FIRST_NAME || props.FIRSTNAME || props.FirstName || props.FIRST || '',
							props.SEX || props.Sex || props.sex || '',
							props.AGE || props.Age || props.age || '',
							props.DATE || props.Date || props.date || '',
							props.LAND_STATUS || props.LANDSTATUS || props.LandStatus || '',
							props.CORRIDOR || props.Corridor || props.corridor || '',
							props.COUNTY || props.County || props.county || '',
							coords[1],
							coords[0]
						];
						const row = tableBody.insertRow();
						rowValues.forEach(value => {
							const cell = row.insertCell();
							cell.textContent = value === null || value === undefined ? '' : String(value);
						});
					});
				}
			});

			const agolDeathsOutsideLayer = L.esri.featureLayer({
				url: deathsOutsideLayerUrl,
				token: AGOL_TOKEN || undefined
			});

			agolDeathsOutsideLayer.query().where('1=1').run(function (error, featureCollection) {
				if (error) {
					console.error('Failed to load deaths-outside-buffer features for heatmap:', error);
					return;
				}

				const filteredHeatFeatures = (featureCollection.features || []).filter(feature => {
					const coords = getPointCoordinates(feature);
					if (!coords) return false;
					return !isPointInsideAnyReservation(coords[0], coords[1], tohonoReservationFeatures);
				});

				const heatPoints = filteredHeatFeatures
					.map(feature => {
						const coords = getPointCoordinates(feature);
						if (!coords) return null;
						return [coords[1], coords[0], 0.8];
					})
					.filter(Boolean);

				if (typeof L.heatLayer !== 'function') {
					console.error('Leaflet heat plugin did not load; cannot render deaths heatmap.');
					return;
				}

				const deathsOutsideHeatLayer = L.heatLayer(heatPoints, {
					radius: 20,
					blur: 15,
					maxZoom: 11,
					minOpacity: 0.35,
					gradient: {
						0.2: '#5a0000',
						0.5: '#8b0000',
						0.8: '#b22222',
						1.0: '#ff4d4d'
					}
				});

				deathsOutsideLayerGroup.clearLayers();
				deathsOutsideLayerGroup.addLayer(deathsOutsideHeatLayer);
			});

			const agolAzRoadsLayer = L.esri.featureLayer({
				url: azRoadsLayerUrl,
				token: AGOL_TOKEN || undefined,
				style: function () {
					return {
						color: '#6b4f2a',
						weight: 2,
						opacity: 0.8
					};
				}
			});
			agolAzRoadsLayer.bindPopup(function (layer) {
				const props = layer.feature && layer.feature.properties ? layer.feature.properties : {};
				const roadName = props.NAME || props.ROAD_NAME || props.STREET || props.FULLNAME || 'Road segment';
				return 'Road: ' + roadName;
			});
			agolAzRoadsLayer.addTo(roadsLayerGroup);

			const agolReservationsLayer = L.esri.featureLayer({
				url: reservationsLayerUrl,
				token: AGOL_TOKEN || undefined,
				style: function () {
					return {
						color: '#6e5a2c',
						weight: 1.5,
						opacity: 0.9,
						fillColor: '#b6a36a',
						fillOpacity: 0.18
					};
				}
			});
			agolReservationsLayer.bindPopup(function (layer) {
				const props = layer.feature && layer.feature.properties ? layer.feature.properties : {};
				const name = props.NAME || props.RESERVATIO || props.TRIBE_NAME || props.TRIBENAME || 'Reservation';
				return 'Reservation: ' + name;
			});
			agolReservationsLayer.addTo(reservationsLayerGroup);

			const agolCountyBoundaryLayer = L.esri.featureLayer({
				url: countyBoundaryLayerUrl,
				token: AGOL_TOKEN || undefined,
				style: function () {
					return {
						color: '#8b5a2b',
						weight: 1.5,
						opacity: 0.9,
						fillOpacity: 0.03
					};
				}
			});
			agolCountyBoundaryLayer.bindPopup(function (layer) {
				const props = layer.feature && layer.feature.properties ? layer.feature.properties : {};
				const countyName = props.NAME || props.COUNTY || props.COUNTY_NAM || props.COUNTY_NAME || 'County';
				return 'County: ' + countyName;
			});
			agolCountyBoundaryLayer.addTo(countyBoundariesLayerGroup);
		}

		initAgolLayers();

		fetch('https://raw.githubusercontent.com/nvkelso/natural-earth-vector/master/geojson/ne_10m_admin_0_boundary_lines_land.geojson')
			.then(response => response.json())
			.then(data => {
				function isUsMexicoFeature(feature) {
					const p = feature.properties || {};
					const left = p.ADM0_LEFT;
					const right = p.ADM0_RIGHT;
					return (
						(left === 'United States of America' && right === 'Mexico') ||
						(left === 'Mexico' && right === 'United States of America')
					);
				}

				function isNearUsMexicoBorder(feature) {
					if (!feature.bbox || feature.bbox.length < 4) return true;
					const minLon = feature.bbox[0];
					const minLat = feature.bbox[1];
					const maxLon = feature.bbox[2];
					const maxLat = feature.bbox[3];
					return !(maxLon < -118 || minLon > -94 || maxLat < 24 || minLat > 34);
				}

				const borderFeatures = (data.features || []).filter(
					f => isUsMexicoFeature(f) && isNearUsMexicoBorder(f)
				);

				L.geoJson({ type: 'FeatureCollection', features: borderFeatures }, {
					style: {
						color: '#ffffff',
						weight: 8,
						opacity: 0.9,
						lineCap: 'round'
					}
				}).addTo(borderLayerGroup);

				L.geoJson({ type: 'FeatureCollection', features: borderFeatures }, {
					style: {
						color: '#b30000',
						weight: 4,
						opacity: 1,
						lineCap: 'round'
					}
				}).addTo(borderLayerGroup);
			})
			.catch(error => {
				console.error('Failed to load U.S.-Mexico border data:', error);
			});

		function zoomToActiveData() {
			const bounds = L.latLngBounds([]);

			if (map.hasLayer(waterLayerGroup)) {
				waterLayerGroup.eachLayer(layer => {
					if (layer.getLatLng) bounds.extend(layer.getLatLng());
					else if (layer.getBounds) bounds.extend(layer.getBounds().getCenter());
				});
			}

			if (map.hasLayer(migrantLayerGroup)) {
				migrantLayerGroup.eachLayer(layer => {
					if (layer.getLatLng) bounds.extend(layer.getLatLng());
					else if (layer.getBounds) bounds.extend(layer.getBounds().getCenter());
				});
			}

			if (bounds.isValid()) {
				map.fitBounds(bounds, { padding: [20, 20] });
			} else {
				alert('No data visible to zoom to. Enable at least one overlay layer.');
			}
		}

		var zoomControl = L.control({ position: 'topleft' });
		zoomControl.onAdd = function () {
			var div = L.DomUtil.create('div', 'leaflet-bar leaflet-control');
			var link = L.DomUtil.create('a', '', div);
			link.title = 'Zoom to visible data';
			link.href = '#';
			link.innerHTML = '⤢';

			L.DomEvent.on(link, 'click', L.DomEvent.stopPropagation)
				.on(link, 'click', L.DomEvent.preventDefault)
				.on(link, 'click', zoomToActiveData);

			return div;
		};
		zoomControl.addTo(map);

		var legend = L.control({ position: 'bottomright' });
		legend.onAdd = function () {
			var div = L.DomUtil.create('div', 'legend');
			div.innerHTML = '<strong>Legend</strong><br>' +
				'<i style="background: #b30000; width: 12px; height: 4px; margin-top: 4px;"></i> US-Mexico Border<br>' +
				'<i style="background: #4b8fd6; width: 12px; height: 10px; border: 1px solid #1f5fa8;"></i> Water 3-mile Buffers<br>' +
				'<i style="background: red; width: 10px; height: 10px;"></i> Migrant Deaths<br>';
			return div;
		};
		legend.addTo(map);

		function computeLayerStats() {
			function layerSummary(layerGroup) {
				const points = [];
				layerGroup.eachLayer(marker => {
					if (marker.getLatLng) points.push(marker.getLatLng());
					else if (marker.getBounds) points.push(marker.getBounds().getCenter());
				});
				if (points.length === 0) return { count: 0, centroid: null };
				let latSum = 0;
				let lngSum = 0;
				points.forEach(pt => {
					latSum += pt.lat;
					lngSum += pt.lng;
				});
				return {
					count: points.length,
					centroid: [latSum / points.length, lngSum / points.length]
				};
			}

			const waterStats = layerSummary(waterLayerGroup);
			const deathStats = layerSummary(migrantLayerGroup);

			const output = document.getElementById('geoprocessOutput');
			if (output) {
				const formatPoint = p => p ? p[0].toFixed(5) + ', ' + p[1].toFixed(5) : 'N/A';
				output.innerHTML = '<strong>Geoprocessing results</strong><br>' +
					'Water stations: ' + waterStats.count + ' points; centroid ' + formatPoint(waterStats.centroid) + '<br>' +
					'Migrant deaths: ' + deathStats.count + ' points; centroid ' + formatPoint(deathStats.centroid) + '<br>';
			}

			if (waterStats.centroid) {
				L.circle([waterStats.centroid[0], waterStats.centroid[1]], {
					color: 'blue',
					weight: 2,
					radius: 2000,
					fillOpacity: 0.1
				}).addTo(map);
			}

			if (deathStats.centroid) {
				L.circle([deathStats.centroid[0], deathStats.centroid[1]], {
					color: 'red',
					weight: 2,
					radius: 2000,
					fillOpacity: 0.08
				}).addTo(map);
			}
		}

		var runGeoprocessButton = document.getElementById('runGeoprocess');
		if (runGeoprocessButton) {
			runGeoprocessButton.addEventListener('click', computeLayerStats);
		}
	</script>
</body>
</html>
