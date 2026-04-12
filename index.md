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
			--bg: #e7decd;
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

		main {
			max-width: 1200px;
			margin: 0 auto;
			padding: 1.25rem;
			display: grid;
			gap: 1.25rem;
		}

		.about-map-box {
			max-width: 1200px;
			margin: 1rem auto 0;
			padding: 1rem 1.25rem;
			background: #fff4de;
			border: 1px solid var(--line);
			border-left: 6px solid #7d5a3c;
			border-radius: 10px;
		}

		.about-map-box h2 {
			margin: 0 0 0.4rem;
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
			width: calc(100vw - 2rem);
			max-width: none;
			margin-left: calc(50% - 50vw + 1rem);
			margin-right: calc(50% - 50vw + 1rem);
		}

		#map {
			width: 100%;
			height: 560px;
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

		.quick-facts-grid {
			display: grid;
			gap: 0.75rem;
			margin-top: 0.75rem;
		}

		.fact-card {
			border: 1px solid var(--line);
			border-radius: 8px;
			padding: 0.7rem;
			background: #fff7eb;
		}

		.fact-label {
			font-size: 0.88rem;
			color: #5d4a34;
		}

		.fact-value {
			font-size: 1.3rem;
			font-weight: 700;
			color: #2d2418;
			margin-top: 0.15rem;
		}

		.chart-wrap {
			height: 120px;
			margin-top: 0.4rem;
		}

		.chart-wrap canvas {
			width: 100% !important;
			height: 100% !important;
		}

		.legend {
			background: rgba(255, 250, 240, 0.96);
			border: 1px solid #bda98b;
			border-radius: 10px;
			padding: 0.65rem 0.75rem;
			box-shadow: 0 4px 14px rgba(33, 24, 11, 0.28);
			color: #2d2418;
			font-size: 0.88rem;
			line-height: 1.25;
			max-width: 260px;
		}

		.legend strong {
			display: block;
			margin-bottom: 0.35rem;
			font-size: 0.93rem;
		}

		.legend-row {
			display: flex;
			align-items: center;
			gap: 0.45rem;
			margin: 0.2rem 0;
		}

		.legend-swatch {
			display: inline-block;
			flex: 0 0 auto;
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
				height: 460px;
			}
		}

		@media (max-width: 560px) {
			.photo-grid {
				grid-template-columns: 1fr;
			}

			#map {
				height: 380px;
			}
		}
	</style>
</head>
<body>
	<header>
		<nav>
			<div class="site-title">Aqua Vitalis: Providing Drinking Water in the Southern Arizona Desert</div>
		</nav>
	</header>

	<section class="about-map-box" aria-label="About this map section">
		<h2>About this Map</h2>
		<p>
			This map has been designed as a tool to help the organization 
			Humane Borders visualize and optimize the deployment of drinking water stations
			in the counties of Yuma, Pima, and Santa Cruz in southern Arizona.
		</p>
	</section>

	<main>
		<section class="hero">
			<h1>Interactive Map</h1>
			<p>
				Use the layer feature to toggle on and off locations of water stations and 
				deaths of individuals over the past five years. You can also enable the distance tool to
				see how far each death occurred from a water station.
			</p>
		</section>

		<section class="map-panel" id="map-section">
			<div id="map" aria-label="Map display area"></div>
			<div class="map-caption">
				Map design and layers created using Leaflet and ArcGIS Online.
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
					Computed from loaded map data (outside reservation territory).
				</p>
				<div class="quick-facts-grid">
					<div class="fact-card">
						<div class="fact-label">Deaths Since 2021</div>
						<div class="fact-value" id="factsDeathsCount">Loading...</div>
					</div>
					<div class="fact-card">
						<div class="fact-label">Average Age Since 2021 (years)</div>
						<div class="fact-value" id="factsAvgAge">Loading...</div>
					</div>
					<div class="fact-card">
						<div class="fact-label">Average distance from deceased to nearest water station (miles)</div>
						<div class="fact-value" id="factsAvgDistance">Loading...</div>
					</div>
				</div>
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
	<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.4/dist/chart.umd.min.js"></script>
	<script>
		var map = L.map('map', {
			zoomSnap: 0.5
		}).setView([31.8800834, -111.2059306], 8.5);
		map.createPane('waterStationsPane');
		map.getPane('waterStationsPane').style.zIndex = 700;

		var streetLayer = L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
			attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
		});

		var terrainLayer = L.tileLayer('https://{s}.tile.opentopomap.org/{z}/{x}/{y}.png', {
			attribution: 'Map data: &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, <a href="https://opentopomap.org">OpenTopoMap</a> (CC-BY-SA)',
			subdomains: 'abc',
			minZoom: 0,
			maxZoom: 17
		});

		var waterStationsLayerGroup = L.layerGroup().addTo(map);
		var migrantLayerGroup = L.layerGroup().addTo(map);
		var deathsOutsideLayerGroup = L.layerGroup().addTo(map);
		var deathsInReservationLayerGroup = L.layerGroup().addTo(map);
		var deaths10MilesFromWaterLayerGroup = L.layerGroup().addTo(map);
		var deathsHeatLayerGroup = L.layerGroup().addTo(map);
		var deathsInReservationHeatLayerGroup = L.layerGroup().addTo(map);
		var distanceMeasureLayerGroup = L.layerGroup().addTo(map);

		var waterStationPoints = [];
		var csvWaterStationPoints = [];
		var outsideReservationDeathFeatures = [];
		var measurementEnabled = false;
		var currentMeasureRequestId = 0;
		var currentQuickFactsDeathFeatures = [];
		var quickFactsCharts = {
			deaths: null,
			age: null,
			distance: null
		};
		const ALLOWED_DEATH_COUNTIES = new Set(['yuma', 'pima', 'santa cruz']);
		const FALLBACK_NON_STATION_NAMES = new Set([
			'Charlie Bell Well',
			'Chilton Well',
			'Jacks Well',
			'Jose Juan Tank',
			'Little Tule Well',
			'Papago Well',
			'Red Tail Tank'
		]);
		const HARD_FALLBACK_WATER_STATIONS = [
			{ name: 'ABS', lat: 31.575015, lon: -111.331171 },
			{ name: 'Bates Well Station', lat: 32.183319, lon: -112.943256 },
			{ name: 'Bishop Carcano Station', lat: 31.840364, lon: -111.387703 },
			{ name: 'Bruce Parks', lat: 32.262789, lon: -111.287204 },
			{ name: 'Cemetery Hill Station', lat: 31.634443, lon: -111.240211 },
			{ name: 'Charlie Bell Well', lat: 32.384769, lon: -113.102867 },
			{ name: 'Chilton Well', lat: 31.385299, lon: -111.238541 },
			{ name: 'Dancehall Station', lat: 31.574359, lon: -111.332252 },
			{ name: 'Dripping Springs Station', lat: 32.031417, lon: -112.892194 },
			{ name: 'Duvall North', lat: 32.055163, lon: -111.349197 },
			{ name: 'Ed McCullough Station', lat: 32.32052, lon: -111.43246 },
			{ name: 'Esperanza', lat: 31.559975, lon: -111.318592 },
			{ name: 'Figuero Station', lat: 31.639519, lon: -111.414569 },
			{ name: 'Gene Buell Station', lat: 32.226005, lon: -111.287222 },
			{ name: 'Green Valley Station', lat: 31.806908, lon: -110.999031 },
			{ name: 'Growler Station', lat: 32.15703, lon: -113.02102 },
			{ name: 'Guadalupe', lat: 32.11501, lon: -111.30873 },
			{ name: 'HummingBird Station', lat: 31.676499, lon: -111.391615 },
			{ name: 'Jackalope Station', lat: 32.030961, lon: -111.360158 },
			{ name: 'Jacks Well', lat: 32.414025, lon: -113.050753 },
			{ name: 'Jose Juan Tank', lat: 32.087607, lon: -113.097671 },
			{ name: 'K9 Station', lat: 31.657406, lon: -111.264305 },
			{ name: 'Kim Johnson Station', lat: 31.836151, lon: -111.3989 },
			{ name: 'Little Tule Well', lat: 32.370275, lon: -112.951664 },
			{ name: 'Luis and Cindy Urrea at Agua Dulces', lat: 32.123688, lon: -113.197329 },
			{ name: 'Organ Pipe East Station', lat: 31.97755, lon: -112.773144 },
			{ name: 'Organ Pipe North', lat: 32.188882, lon: -112.806416 },
			{ name: 'Papago Well', lat: 32.099139, lon: -113.286921 },
			{ name: 'Polaris', lat: 32.32075, lon: -111.355789 },
			{ name: 'Poplar Grove Station', lat: 32.08643, lon: -111.32635 },
			{ name: 'Purple Mountain Station', lat: 31.601478, lon: -111.281225 },
			{ name: 'Red Tail Tank', lat: 32.247779, lon: -113.167223 },
			{ name: 'Reyes Carias', lat: 32.27723, lon: -111.35022 },
			{ name: 'Rocky Road Station', lat: 31.713722, lon: -111.185427 },
			{ name: 'Ross Mine Road Station', lat: 31.61335, lon: -111.404553 },
			{ name: 'Ruby', lat: 31.569451, lon: -111.332645 },
			{ name: 'San Luis', lat: 32.493951, lon: -114.811442 },
			{ name: 'Senita Basin Station', lat: 31.950303, lon: -112.865781 },
			{ name: 'Silverbell', lat: 32.383707, lon: -111.565184 },
			{ name: 'Soberanes Station', lat: 31.657747, lon: -111.292046 },
			{ name: 'Tim Holt', lat: 32.388025, lon: -111.575028 },
			{ name: 'Tres Bellotas Ranch Border', lat: 31.422869, lon: -111.355888 },
			{ name: 'Tres Bellotas Tank', lat: 31.461361, lon: -111.338417 },
			{ name: 'Whispering Coyote', lat: 32.313432, lon: -111.346849 }
		];

		// If your AGOL layers are private, paste a valid token string here.
		// Leave empty for public services.
		const AGOL_TOKEN = '';

		function getPointCoordinates(feature) {
			const geom = feature && feature.geometry ? feature.geometry : {};
			const coords = geom.coordinates || [];
			if (!Array.isArray(coords) || coords.length < 2) return null;
			return [coords[0], coords[1]]; // [lon, lat]
		}

		function isValidWaterStationType(typeValue) {
			const normalized = String(typeValue || '').trim().toLowerCase();
			return normalized === 'station' || normalized === 'seasonal_station';
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

		function getFeatureCounty(feature) {
			const props = feature && (feature.properties || feature.attributes) ? (feature.properties || feature.attributes) : {};
			const county = props.COUNTY || props.County || props.county || '';
			return String(county).trim().toLowerCase();
		}

		function isAllowedDeathCounty(feature) {
			return ALLOWED_DEATH_COUNTIES.has(getFeatureCounty(feature));
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

		function findNearestWaterStation(deathLatLng) {
			const candidates = csvWaterStationPoints.length > 0 ? csvWaterStationPoints : waterStationPoints;
			if (!deathLatLng || candidates.length === 0) return null;

			let nearest = null;
			let nearestMeters = Infinity;
			candidates.forEach(station => {
				const meters = map.distance(deathLatLng, station.latlng);
				if (meters < nearestMeters) {
					nearestMeters = meters;
					nearest = station;
				}
			});

			if (!nearest) return null;
			return { station: nearest, meters: nearestMeters };
		}

		function getNumericAge(feature) {
			const props = feature && (feature.properties || feature.attributes) ? (feature.properties || feature.attributes) : {};
			const value = props.AGE || props.Age || props.age;
			if (value === null || value === undefined || String(value).trim() === '') return null;
			const parsed = Number(value);
			return Number.isFinite(parsed) && parsed > 0 ? parsed : null;
		}

		function getDeathYear(feature) {
			const props = feature && (feature.properties || feature.attributes) ? (feature.properties || feature.attributes) : {};
			const raw = props.DATE || props.Date || props.date || '';

			if (typeof raw === 'number' && Number.isFinite(raw)) {
				const asDate = raw > 1e11 ? new Date(raw) : (raw > 1e9 ? new Date(raw * 1000) : null);
				if (asDate && !Number.isNaN(asDate.getTime())) {
					const year = asDate.getUTCFullYear();
					if (year >= 1900 && year <= 2100) return year;
				}
			}

			const text = String(raw).trim();
			if (text) {
				const parsed = new Date(text);
				if (!Number.isNaN(parsed.getTime())) {
					const year = parsed.getUTCFullYear();
					if (year >= 1900 && year <= 2100) return year;
				}

				const match = text.match(/\b(19|20)\d{2}\b/);
				if (match) return Number(match[0]);
			}

			return null;
		}

		async function loadWaterStationsFromCsv() {
			try {
				const response = await fetch('water_stations.csv');
				if (!response.ok) return loadWaterStationsFromFallback();

				const csv = await response.text();
				const lines = csv.split(/\r?\n/).map(line => line.trim()).filter(Boolean);
				if (lines.length === 0) return loadWaterStationsFromFallback();

				waterStationsLayerGroup.clearLayers();
				csvWaterStationPoints = [];

				lines.forEach(line => {
					const parts = line.split(',');
					if (parts.length < 4) return;

					const stationType = String(parts[3] || '').trim();
					if (!isValidWaterStationType(stationType)) return;

					const name = String(parts[0] || '').replace(/_/g, ' ').trim() || 'Water station';
					const lat = Number(parts[1]);
					const lon = Number(parts[2]);
					if (!Number.isFinite(lat) || !Number.isFinite(lon)) return;

					const latlng = L.latLng(lat, lon);
					const stationMarker = L.circleMarker(latlng, {
						pane: 'waterStationsPane',
						radius: 5,
						color: '#0057d9',
						weight: 1,
						fillColor: '#1e88ff',
						fillOpacity: 0.95
					}).bindPopup(name);

					stationMarker.addTo(waterStationsLayerGroup);
					stationMarker.bringToFront();

					csvWaterStationPoints.push({
						latlng: stationMarker.getLatLng(),
						name: name
					});
				});

				if (csvWaterStationPoints.length === 0) return loadWaterStationsFromFallback();
				return true;
			} catch (_err) {
				return loadWaterStationsFromFallback();
			}
		}

		function loadWaterStationsFromFallback() {
			if (!Array.isArray(HARD_FALLBACK_WATER_STATIONS) || HARD_FALLBACK_WATER_STATIONS.length === 0) {
				return false;
			}

			waterStationsLayerGroup.clearLayers();
			csvWaterStationPoints = [];

			HARD_FALLBACK_WATER_STATIONS.forEach(station => {
				if (!Number.isFinite(station.lat) || !Number.isFinite(station.lon)) return;
				if (FALLBACK_NON_STATION_NAMES.has(station.name)) return;

				const latlng = L.latLng(station.lat, station.lon);
				const stationMarker = L.circleMarker(latlng, {
					pane: 'waterStationsPane',
					radius: 5,
					color: '#0057d9',
					weight: 1,
					fillColor: '#1e88ff',
					fillOpacity: 0.95
				}).bindPopup(station.name);

				stationMarker.addTo(waterStationsLayerGroup);
				stationMarker.bringToFront();

				csvWaterStationPoints.push({
					latlng: stationMarker.getLatLng(),
					name: station.name
				});
			});

			return csvWaterStationPoints.length > 0;
		}

		function getAverageNearestWaterMiles(features) {
			if (!Array.isArray(features) || features.length === 0) return null;

			let totalMiles = 0;
			let counted = 0;
			features.forEach(feature => {
				const coords = getPointCoordinates(feature);
				if (!coords) return;

				const nearest = findNearestWaterStation(L.latLng(coords[1], coords[0]));
				if (!nearest) return;

				totalMiles += (nearest.meters / 1609.344);
				counted += 1;
			});

			if (counted === 0) return null;
			return totalMiles / counted;
		}

		function createOrUpdateFactChart(existingChart, canvasId, label, value, color, maxHint) {
			const canvas = document.getElementById(canvasId);
			if (!canvas || typeof Chart === 'undefined') return existingChart;

			const numericValue = Number.isFinite(value) ? value : 0;
			const axisMax = Math.max(maxHint || 1, numericValue * 1.25, 1);

			if (existingChart) {
				existingChart.data.datasets[0].data = [numericValue];
				existingChart.options.scales.y.max = axisMax;
				existingChart.update();
				return existingChart;
			}

			return new Chart(canvas, {
				type: 'bar',
				data: {
					labels: [label],
					datasets: [{
						data: [numericValue],
						backgroundColor: color,
						borderRadius: 8,
						barThickness: 42
					}]
				},
				options: {
					responsive: true,
					maintainAspectRatio: false,
					plugins: {
						legend: { display: false },
						tooltip: { enabled: true }
					},
					scales: {
						x: {
							grid: { display: false },
							ticks: { color: '#5d4a34' }
						},
						y: {
							beginAtZero: true,
							max: axisMax,
							ticks: { color: '#5d4a34' },
							grid: { color: 'rgba(123, 98, 66, 0.18)' }
						}
					}
				}
			});
		}

		function updateQuickFactsCharts() {
			const features = currentQuickFactsDeathFeatures;
			const featuresSince2021 = features.filter(f => {
				const y = getDeathYear(f);
				return y !== null && y >= 2021;
			});
			const countSince2021 = featuresSince2021.length;

			const ages = featuresSince2021.map(getNumericAge).filter(v => v !== null);
			const averageAge = ages.length ? (ages.reduce((sum, v) => sum + v, 0) / ages.length) : null;

			const averageMiles = getAverageNearestWaterMiles(featuresSince2021);

			const countEl = document.getElementById('factsDeathsCount');
			const ageEl = document.getElementById('factsAvgAge');
			const distanceEl = document.getElementById('factsAvgDistance');

			if (countEl) countEl.textContent = String(countSince2021);
			if (ageEl) ageEl.textContent = Number.isFinite(averageAge) ? averageAge.toFixed(1) : 'N/A';
			if (distanceEl) distanceEl.textContent = Number.isFinite(averageMiles) ? averageMiles.toFixed(2) : 'N/A';
		}

		function refresh10MilesFromWaterLayer() {
			deaths10MilesFromWaterLayerGroup.clearLayers();

			if (!Array.isArray(outsideReservationDeathFeatures) || outsideReservationDeathFeatures.length === 0) return;
			const stationCandidates = csvWaterStationPoints.length > 0 ? csvWaterStationPoints : waterStationPoints;
			if (!Array.isArray(stationCandidates) || stationCandidates.length === 0) return;

			const thresholdMeters = 10 * 1609.344;
			outsideReservationDeathFeatures.forEach(feature => {
				const props = feature.properties || feature.attributes || {};
				const coords = getPointCoordinates(feature);
				if (!coords) return;

				const deathLatLng = L.latLng(coords[1], coords[0]);
				const nearest = findNearestWaterStation(deathLatLng);
				if (!nearest || nearest.meters <= thresholdMeters) return;

				const miles = nearest.meters / 1609.344;
				const marker = L.circleMarker(deathLatLng, {
					radius: 4,
					color: '#cc2f7f',
					weight: 1.5,
					fillColor: '#ff4fa3',
					fillOpacity: 0.95
				});

				marker.bindPopup(
					`Sex: ${props.SEX || props.Sex || props.sex || 'N/A'}<br>` +
					`Age: ${props.AGE || props.Age || props.age || 'N/A'}<br>` +
					`Nearest water distance: ${miles.toFixed(2)} miles`
				);
				marker.on('click', function () {
					if (measurementEnabled) {
						measureToNearestWater(marker.getLatLng());
					}
				});

				marker.addTo(deaths10MilesFromWaterLayerGroup);
			});
		}

		function getRouteProfile() {
			const select = document.getElementById('routeProfileMap') || document.getElementById('routeProfile');
			const value = select ? select.value : 'driving';
			return value === 'walking' ? 'walking' : 'driving';
		}

		function formatRouteMode(profile) {
			return profile === 'walking' ? 'Walking' : 'Driving';
		}

		async function fetchRouteMetrics(startLatLng, endLatLng, profile) {
			const start = `${startLatLng.lng},${startLatLng.lat}`;
			const end = `${endLatLng.lng},${endLatLng.lat}`;
			const url = `https://router.project-osrm.org/route/v1/${profile}/${start};${end}?overview=full&geometries=geojson`;

			const response = await fetch(url);
			if (!response.ok) throw new Error('Routing request failed');

			const data = await response.json();
			const route = data && Array.isArray(data.routes) ? data.routes[0] : null;
			if (!route || !route.geometry || !Array.isArray(route.geometry.coordinates)) {
				throw new Error('No route returned');
			}

			return {
				meters: Number(route.distance),
				coordinates: route.geometry.coordinates
			};
		}

		async function measureToNearestWater(deathLatLng) {
			const requestId = ++currentMeasureRequestId;
			const result = findNearestWaterStation(deathLatLng);
			const output = document.getElementById('measureOutput');
			const outputMap = document.getElementById('measureOutputMap');
			const profile = getRouteProfile();
			const modeLabel = formatRouteMode(profile);

			distanceMeasureLayerGroup.clearLayers();

			if (!result) {
				if (output) output.textContent = 'No water stations available for distance measurement yet.';
				if (outputMap) outputMap.textContent = 'No water stations available for distance measurement yet.';
				return;
			}

			if (output) output.textContent = `Calculating ${modeLabel.toLowerCase()} route...`;
			if (outputMap) outputMap.textContent = `Calculating ${modeLabel.toLowerCase()} route...`;

			let meters = result.meters;
			let usedRoute = false;
			let routeLatLngs = [deathLatLng, result.station.latlng];

			try {
				const routeResult = await fetchRouteMetrics(deathLatLng, result.station.latlng, profile);
				if (requestId !== currentMeasureRequestId) return;

				if (Number.isFinite(routeResult.meters)) {
					meters = routeResult.meters;
				}

				routeLatLngs = routeResult.coordinates.map(coord => L.latLng(coord[1], coord[0]));
				usedRoute = routeLatLngs.length > 1;
			} catch (_err) {
				// Keep straight-line fallback if routing is unavailable.
			}

			if (requestId !== currentMeasureRequestId) return;

			const miles = meters / 1609.344;

			const line = L.polyline(routeLatLngs, {
				color: '#1f5fa8',
				weight: 3,
				opacity: 0.9,
				dashArray: usedRoute ? null : '8, 6'
			}).addTo(distanceMeasureLayerGroup);

			L.circleMarker(deathLatLng, {
				radius: 6,
				color: '#5a0000',
				weight: 2,
				fillColor: '#5a0000',
				fillOpacity: 1
			}).addTo(distanceMeasureLayerGroup);

			L.circleMarker(result.station.latlng, {
				radius: 7,
				color: '#0057d9',
				weight: 2,
				fillColor: '#1e88ff',
				fillOpacity: 1
			}).addTo(distanceMeasureLayerGroup);

			line.bindPopup(
				`Closest station: ${result.station.name}<br>` +
				`Mode: ${modeLabel}${usedRoute ? '' : ' (straight-line fallback)'}<br>` +
				`Distance: ${miles.toFixed(2)} miles (${meters.toFixed(0)} m)`
			).openPopup();

			const resultHtml =
				`<strong>Nearest-water distance</strong><br>` +
				`Closest station: ${result.station.name}<br>` +
				`Mode: ${modeLabel}${usedRoute ? '' : ' (straight-line fallback)'}<br>` +
				`Distance: ${miles.toFixed(2)} miles (${meters.toFixed(0)} m)`;

			if (output) output.innerHTML = resultHtml;
			if (outputMap) outputMap.innerHTML = resultHtml;
		}

		function setMeasurementEnabled(enabled) {
			measurementEnabled = enabled;

			const btn = document.getElementById('toggleMeasure');
			const output = document.getElementById('measureOutput');
			const btnMap = document.getElementById('toggleMeasureMap');
			const outputMap = document.getElementById('measureOutputMap');

			if (enabled) {
				if (btn) btn.textContent = 'Disable nearest-water measure';
				if (btnMap) btnMap.textContent = 'Disable nearest-water measure';
				if (output) output.textContent = `Measurement is on (${formatRouteMode(getRouteProfile())}). Click any death point to measure to the nearest water station.`;
				if (outputMap) outputMap.textContent = `Measurement is on (${formatRouteMode(getRouteProfile())}). Click any death point to measure to the nearest water station.`;
			} else {
				if (btn) btn.textContent = 'Enable nearest-water measure';
				if (btnMap) btnMap.textContent = 'Enable nearest-water measure';
				if (output) output.textContent = 'Nearest-water measure is off.';
				if (outputMap) outputMap.textContent = 'Nearest-water measure is off.';
				distanceMeasureLayerGroup.clearLayers();
			}
		}

		streetLayer.addTo(map);

		L.control.layers({
			'Streets': streetLayer,
			'Terrain': terrainLayer
		}, {
			'Water Stations': waterStationsLayerGroup,
			'Migrant Deaths': migrantLayerGroup,
			'Migrant Deaths Outside Buffer': deathsOutsideLayerGroup,
			'Deaths in Reservation Territory': deathsInReservationLayerGroup,
			'Deaths > 10 Miles from Water': deaths10MilesFromWaterLayerGroup,
			'Heat Map of Deaths': deathsHeatLayerGroup,
			'Heat Map of Reservation Deaths': deathsInReservationHeatLayerGroup
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
			const reservationsLayerUrl = await resolveFeatureLayerUrl('https://services.arcgis.com/o6oETlrWetREI1A2/arcgis/rest/services/American_Indian_Reservations_in_Arizona/FeatureServer');
			const loadedCsvStations = await loadWaterStationsFromCsv();

			// Force uniform death symbols: small dark-red circles.
			const deathPointToLayer = function (_geojson, latlng) {
				return L.circleMarker(latlng, {
					radius: 4,
					color: '#5a0000',
					weight: 1,
					fillColor: '#5a0000',
					fillOpacity: 0.95
				});
			};

			const reservationDeathPointToLayer = function (_geojson, latlng) {
				return L.circleMarker(latlng, {
					radius: 4,
					color: '#5a0000',
					weight: 1,
					fillColor: '#5a0000',
					fillOpacity: 0.95
				});
			};

			// Draw water station points as blue circles using each water feature's station coordinates.
			if (!loadedCsvStations) {
				const waterStationsQueryLayer = L.esri.featureLayer({
					url: waterBufferLayerUrl,
					token: AGOL_TOKEN || undefined
				});

				waterStationsQueryLayer.query().where('1=1').run(function (error, featureCollection) {
					if (error) {
						console.error('Failed to load water station features:', error);
						return;
					}

					const features = (featureCollection && featureCollection.features) ? featureCollection.features : [];
					waterStationPoints = [];
					features.forEach(feature => {
						const props = feature.properties || feature.attributes || {};
						const coords = getPointCoordinates(feature);

						let latlng = null;
						if (coords) {
							latlng = L.latLng(coords[1], coords[0]);
						} else {
							const latitude = Number(props.latitude || props.LATITUDE || props.lat || props.Lat);
							const longitude = Number(props.longitude || props.LONGITUDE || props.lon || props.Lon || props.lng || props.Lng);
							if (Number.isFinite(latitude) && Number.isFinite(longitude)) {
								latlng = L.latLng(latitude, longitude);
							}
						}

						if (!latlng) return;

						const stationName = (props.name === null || props.name === undefined || String(props.name).trim() === '')
							? 'No station name available'
							: String(props.name);

						const stationMarker = L.circleMarker(latlng, {
							pane: 'waterStationsPane',
							radius: 5,
							color: '#0057d9',
							weight: 1,
							fillColor: '#1e88ff',
							fillOpacity: 0.95
						}).bindPopup(`${stationName}`);

						stationMarker.on('click', function (e) {
							if (e && e.originalEvent) {
								L.DomEvent.stopPropagation(e.originalEvent);
							}
							stationMarker.openPopup();
						});

						stationMarker.addTo(waterStationsLayerGroup);
						stationMarker.bringToFront();

						waterStationPoints.push({
							latlng: stationMarker.getLatLng(),
							name: stationName
						});
					});

					refresh10MilesFromWaterLayer();
					updateQuickFactsCharts();
				});
			} else {
				refresh10MilesFromWaterLayer();
				updateQuickFactsCharts();
			}

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

			// Query migrant deaths and render only those outside Tohono O'odham reservation land.
			const migrantDeathsQueryLayer = L.esri.featureLayer({
				url: migrantDeathsLayerUrl,
				token: AGOL_TOKEN || undefined
			});

			migrantDeathsQueryLayer.query().where('1=1').run(function (error, featureCollection) {
				if (error) {
					console.error('Failed to load migrant deaths table from AGOL:', error);
					return;
				}

				const allFeatures = (featureCollection && featureCollection.features) ? featureCollection.features : [];
				const countyFilteredFeatures = allFeatures.filter(isAllowedDeathCounty);
				const filteredFeatures = countyFilteredFeatures.filter(feature => {
					const coords = getPointCoordinates(feature);
					if (!coords) return false;
					return !isPointInsideAnyReservation(coords[0], coords[1], tohonoReservationFeatures);
				});
				const inReservationFeatures = countyFilteredFeatures.filter(feature => {
					const coords = getPointCoordinates(feature);
					if (!coords) return false;
					return isPointInsideAnyReservation(coords[0], coords[1], tohonoReservationFeatures);
				});

				outsideReservationDeathFeatures = filteredFeatures;
				currentQuickFactsDeathFeatures = filteredFeatures;
				refresh10MilesFromWaterLayer();
				updateQuickFactsCharts();

				migrantLayerGroup.clearLayers();
				filteredFeatures.forEach(feature => {
					const props = feature.properties || {};
					const coords = getPointCoordinates(feature);
					if (!coords) return;

					const marker = deathPointToLayer(feature, L.latLng(coords[1], coords[0]));
					marker.bindPopup(
						`Sex: ${props.SEX || props.Sex || props.sex || 'N/A'}<br>` +
						`Age: ${props.AGE || props.Age || props.age || 'N/A'}`
					);
					marker.on('click', function () {
						if (measurementEnabled) {
							measureToNearestWater(marker.getLatLng());
						}
					});
					marker.addTo(migrantLayerGroup);
				});

				deathsInReservationLayerGroup.clearLayers();
				inReservationFeatures.forEach(feature => {
					const props = feature.properties || {};
					const coords = getPointCoordinates(feature);
					if (!coords) return;

					const marker = reservationDeathPointToLayer(feature, L.latLng(coords[1], coords[0]));
					marker.bindPopup(
						`Sex: ${props.SEX || props.Sex || props.sex || 'N/A'}<br>` +
						`Age: ${props.AGE || props.Age || props.age || 'N/A'}`
					);
					marker.on('click', function () {
						if (measurementEnabled) {
							measureToNearestWater(marker.getLatLng());
						}
					});
					marker.addTo(deathsInReservationLayerGroup);
				});

				if (typeof L.heatLayer === 'function') {
					const heatPoints = filteredFeatures
						.map(feature => {
							const coords = getPointCoordinates(feature);
							if (!coords) return null;
							return [coords[1], coords[0], 0.8];
						})
						.filter(Boolean);

					const deathsHeatLayer = L.heatLayer(heatPoints, {
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

					deathsHeatLayerGroup.clearLayers();
					deathsHeatLayerGroup.addLayer(deathsHeatLayer);

					const reservationHeatPoints = inReservationFeatures
						.map(feature => {
							const coords = getPointCoordinates(feature);
							if (!coords) return null;
							return [coords[1], coords[0], 0.8];
						})
						.filter(Boolean);

					const reservationDeathsHeatLayer = L.heatLayer(reservationHeatPoints, {
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

					deathsInReservationHeatLayerGroup.clearLayers();
					deathsInReservationHeatLayerGroup.addLayer(reservationDeathsHeatLayer);
				}

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
					console.error('Failed to load deaths-outside-buffer features:', error);
					return;
				}

				const outsideFeatures = (featureCollection.features || []).filter(feature => {
					if (!isAllowedDeathCounty(feature)) return false;
					const coords = getPointCoordinates(feature);
					if (!coords) return false;
					return !isPointInsideAnyReservation(coords[0], coords[1], tohonoReservationFeatures);
				});

				deathsOutsideLayerGroup.clearLayers();
				outsideFeatures.forEach(feature => {
					const props = feature.properties || {};
					const coords = getPointCoordinates(feature);
					if (!coords) return;

					const marker = deathPointToLayer(feature, L.latLng(coords[1], coords[0]));
					marker.bindPopup(
						`Sex: ${props.SEX || props.Sex || props.sex || 'N/A'}<br>` +
						`Age: ${props.AGE || props.Age || props.age || 'N/A'}`
					);
					marker.on('click', function () {
						if (measurementEnabled) {
							measureToNearestWater(marker.getLatLng());
						}
					});
					marker.addTo(deathsOutsideLayerGroup);
				});
			});
		}

		initAgolLayers();

		// Zoom-to-active-data function
		function zoomToActiveData() {
			const bounds = L.latLngBounds([]);

			if (map.hasLayer(waterStationsLayerGroup)) {
				waterStationsLayerGroup.eachLayer(layer => {
					if (layer.getLatLng) bounds.extend(layer.getLatLng());
				});
			}

			if (map.hasLayer(migrantLayerGroup)) {
				migrantLayerGroup.eachLayer(layer => {
					if (layer.getLatLng) bounds.extend(layer.getLatLng());
				});
			}

			if (map.hasLayer(deathsOutsideLayerGroup)) {
				deathsOutsideLayerGroup.eachLayer(layer => {
					if (layer.getLatLng) bounds.extend(layer.getLatLng());
				});
			}

			if (map.hasLayer(deathsInReservationLayerGroup)) {
				deathsInReservationLayerGroup.eachLayer(layer => {
					if (layer.getLatLng) bounds.extend(layer.getLatLng());
				});
			}

			if (map.hasLayer(deaths10MilesFromWaterLayerGroup)) {
				deaths10MilesFromWaterLayerGroup.eachLayer(layer => {
					if (layer.getLatLng) bounds.extend(layer.getLatLng());
				});
			}

			if (bounds.isValid()) {
				map.fitBounds(bounds, {padding: [20, 20]});
			} else {
				alert('No data visible to zoom to. Enable at least one overlay layer.');
			}
		}

		// Zoom control button
		var zoomControl = L.control({position: 'topleft'});
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

		// In-map measurement control so users can access the tool without scrolling.
		var measureControl = L.control({position: 'topright'});
		measureControl.onAdd = function () {
			var div = L.DomUtil.create('div', 'leaflet-control');
			div.style.background = 'white';
			div.style.padding = '8px';
			div.style.borderRadius = '4px';
			div.style.boxShadow = '0 1px 5px rgba(0,0,0,0.4)';
			div.style.maxWidth = '260px';
			div.innerHTML =
				'<label for="routeProfileMap" style="display: block; font-size: 12px; margin-bottom: 6px; color: #222;">Route mode:</label>' +
				'<select id="routeProfileMap" style="padding: 6px 8px; width: 100%; margin-bottom: 8px;"><option value="driving">Driving</option><option value="walking">Walking</option></select>' +
				'<button id="toggleMeasureMap" class="measure-button" style="padding: 6px 10px; cursor: pointer; width: 100%;">Enable nearest-water measure</button>' +
				'<div id="measureOutputMap" style="margin-top: 8px; font-size: 12px; color: #222; line-height: 1.3;">Nearest-water measure is off.</div>';

			L.DomEvent.disableClickPropagation(div);
			return div;
		};
		measureControl.addTo(map);

		// Legend control
		var legend = L.control({position: 'bottomright'});
		legend.onAdd = function () {
			var div = L.DomUtil.create('div', 'legend');
			div.innerHTML = '<strong>Legend</strong>' +
				'<div class="legend-row"><span class="legend-swatch" style="background: #1e88ff; width: 10px; height: 10px; border-radius: 50%; border: 1px solid #0057d9;"></span><span>Water Station</span></div>' +
				'<div class="legend-row"><span class="legend-swatch" style="background: red; width: 10px; height: 10px; border-radius: 50%; border: 1px solid #8b0000;"></span><span>Deaths</span></div>' +
				'<div class="legend-row"><span class="legend-swatch" style="background: #ff4fa3; width: 10px; height: 10px; border-radius: 50%; border: 1px solid #cc2f7f;"></span><span>Deaths &gt; 10 Miles from Water</span></div>';
			L.DomEvent.disableClickPropagation(div);
			return div;
		};
		legend.addTo(map);

		function computeLayerStats() {
			function layerSummary(layerGroup) {
				const points = [];
				layerGroup.eachLayer(marker => {
					if (marker.getLatLng) {
						points.push(marker.getLatLng());
					} else if (marker.getBounds) {
						points.push(marker.getBounds().getCenter());
					}
				});
				if (points.length === 0) {
					return { count: 0, centroid: null };
				}
				let latSum = 0, lngSum = 0;
				points.forEach(pt => {
					latSum += pt.lat;
					lngSum += pt.lng;
				});
				return {
					count: points.length,
					centroid: [latSum / points.length, lngSum / points.length]
				};
			}

			const waterStats = layerSummary(waterStationsLayerGroup);
			const deathStats = layerSummary(migrantLayerGroup);

			const formatPoint = p => p ? `${p[0].toFixed(5)}, ${p[1].toFixed(5)}` : 'N/A';

			const geoOutput = document.getElementById('geoprocessOutput');
			if (geoOutput) {
				geoOutput.innerHTML =
					`<strong>Geoprocessing results</strong><br>` +
					`Water stations: ${waterStats.count} points; centroid ${formatPoint(waterStats.centroid)}<br>` +
					`Migrant deaths: ${deathStats.count} points; centroid ${formatPoint(deathStats.centroid)}<br>`;
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

		function syncRouteProfile(targetValue) {
			const baseSelect = document.getElementById('routeProfile');
			const mapSelect = document.getElementById('routeProfileMap');
			if (baseSelect && baseSelect.value !== targetValue) baseSelect.value = targetValue;
			if (mapSelect && mapSelect.value !== targetValue) mapSelect.value = targetValue;
			if (measurementEnabled) {
				setMeasurementEnabled(true);
			}
		}

		var runGeoprocessButton = document.getElementById('runGeoprocess');
		if (runGeoprocessButton) {
			runGeoprocessButton.addEventListener('click', computeLayerStats);
		}

		var baseRouteProfile = document.getElementById('routeProfile');
		if (baseRouteProfile) {
			baseRouteProfile.addEventListener('change', function (e) {
				syncRouteProfile(e.target.value);
			});
		}

		document.addEventListener('change', function (e) {
			if (e.target && e.target.id === 'routeProfileMap') {
				syncRouteProfile(e.target.value);
			}
		});

		var baseToggleMeasure = document.getElementById('toggleMeasure');
		if (baseToggleMeasure) {
			baseToggleMeasure.addEventListener('click', function () {
				setMeasurementEnabled(!measurementEnabled);
			});
		}

		document.addEventListener('click', function (e) {
			if (e.target && e.target.id === 'toggleMeasureMap') {
				setMeasurementEnabled(!measurementEnabled);
			}
		});
	</script>
</body>
</html>
