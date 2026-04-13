
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Aqua Vitalis: Providing Drinking Water in the Southern Arizona Desert</title>
	<style>
		@import url('https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,500;9..144,700&family=Manrope:wght@400;500;700&display=swap');

		:root {
			--bg: #e7decd;
			--surface: #fffaf0;
			--ink: #2d2418;
			--muted: #6a5a45;
			--accent: #7d5a3c;
			--line: #dacdb7;
			--leaflet-ui: #f8f8f6;
			--leaflet-border: #c5c8c0;
			--leaflet-shadow: rgba(30, 38, 20, 0.18);
		}

		* {
			box-sizing: border-box;
			margin: 0;
			padding: 0;
		}

		body {
			font-family: "Manrope", "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
			background:
				radial-gradient(circle at 12% 10%, rgba(252, 232, 181, 0.4), transparent 38%),
				radial-gradient(circle at 88% 22%, rgba(163, 196, 171, 0.32), transparent 42%),
				linear-gradient(180deg, #e8dfcf 0%, #e0d2b7 100%);
			color: var(--ink);
			line-height: 1.5;
			min-height: 100vh;
		}

		header {
			background: color-mix(in srgb, var(--surface) 90%, #f0e4ce 10%);
			border-bottom: 1px solid color-mix(in srgb, var(--line) 84%, #bea780 16%);
			padding: 1rem 1.25rem;
			position: sticky;
			top: 0;
			z-index: 20;
			backdrop-filter: blur(6px);
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
			font-family: "Fraunces", Georgia, "Times New Roman", serif;
			font-size: clamp(1.05rem, 2vw, 1.35rem);
			font-weight: 700;
			letter-spacing: 0.01em;
		}

		main {
			max-width: 1200px;
			margin: 0 auto;
			padding: 1.25rem;
			display: grid;
			gap: 1.25rem;
		}

		main > section,
		main > div {
			width: calc(100% + 2rem);
			margin-left: -3.5rem;
		}

		.about-map-box {
			padding: 1rem 1.25rem;
			background: linear-gradient(120deg, #fff4de 0%, #fdebc8 100%);
			border: 1px solid var(--line);
			border-left: 6px solid #7d5a3c;
			border-radius: 10px;
			box-shadow: 0 8px 20px rgba(75, 49, 21, 0.08);
		}

		.about-map-box h2 {
			margin: 0 0 0.4rem;
		}

		section {
			background: var(--surface);
			border: 1px solid var(--line);
			border-radius: 10px;
			padding: 1rem;
			box-shadow: 0 8px 20px rgba(56, 40, 15, 0.08);
		}

		h1, h2 {
			font-family: "Fraunces", Georgia, "Times New Roman", serif;
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
			border-radius: 14px;
			border: 1px solid color-mix(in srgb, var(--line) 76%, #99866b 24%);
			box-shadow: 0 16px 34px rgba(47, 31, 11, 0.2);
		}

		#map {
			width: 100%;
			height: 700px;
			background: #ddd2bc;
			border: 0;
		}

		.map-embed {
			width: 100%;
			height: 700px;
			border: 0;
			display: block;
			background: #ddd2bc;
		}

		.map-caption {
			display: flex;
			align-items: center;
			justify-content: space-between;
			gap: 0.75rem;
			padding: 0.72rem 0.9rem;
			border-top: 1px solid var(--leaflet-border);
			background: var(--leaflet-ui);
			font-size: 0.88rem;
			color: #374232;
			box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.75);
		}

		.map-badge {
			display: inline-flex;
			align-items: center;
			gap: 0.35rem;
			padding: 0.26rem 0.5rem;
			border-radius: 3px;
			border: 1px solid var(--leaflet-border);
			background: #ffffff;
			box-shadow: 0 1px 4px var(--leaflet-shadow);
			font-weight: 700;
			color: #2b3124;
			text-transform: uppercase;
			font-size: 0.72rem;
			letter-spacing: 0.08em;
		}

		a {
			color: #3d5f43;
			text-decoration-thickness: 0.08em;
			text-underline-offset: 0.18em;
		}

		a:hover {
			color: #23382a;
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

		.analysis-image {
			width: 100%;
			max-width: 200px;
			height: auto;
			margin-top: 0;
			border-radius: 8px;
			border: 1px solid var(--line);
			display: block;
		}

		.analysis-image-row {
			display: flex;
			gap: 0.75rem;
			margin-top: 0.8rem;
			align-items: flex-start;
			flex-wrap: wrap;
		}

		.analysis-image-stack {
			display: flex;
			flex-direction: column;
			gap: 0.55rem;
		}

		.analysis-inline-note {
			max-width: 200px;
			color: var(--muted);
			font-size: 0.92rem;
			line-height: 1.4;
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

		.pie-chart-wrap {
			margin-top: 0.9rem;
			padding: 0.8rem;
			border: 1px solid var(--line);
			border-radius: 8px;
			background: #fff7eb;
		}

		.pie-chart-title {
			font-size: 0.88rem;
			color: #5d4a34;
			margin-bottom: 0.55rem;
		}

		.pie-chart-canvas-wrap {
			position: relative;
			height: 280px;
		}

		.weather-section {
			display: grid;
			gap: 0.9rem;
		}

		.weather-header {
			display: flex;
			justify-content: space-between;
			align-items: flex-start;
			gap: 1rem;
			flex-wrap: wrap;
		}

		.weather-actions {
			display: flex;
			align-items: center;
			gap: 0.75rem;
			flex-wrap: wrap;
		}

		.weather-status {
			font-size: 0.88rem;
			color: #5d4a34;
		}

		.weather-status[data-state="error"] {
			color: #8a3d22;
		}

		.weather-refresh {
			border: 1px solid #8f7658;
			border-radius: 999px;
			padding: 0.45rem 0.9rem;
			background: linear-gradient(180deg, #fff9ed 0%, #f1dfb6 100%);
			color: #2d2418;
			font: inherit;
			font-weight: 700;
			cursor: pointer;
		}

		.weather-refresh:hover {
			background: linear-gradient(180deg, #fff3d9 0%, #ecd59c 100%);
		}

		.weather-refresh:disabled {
			opacity: 0.65;
			cursor: wait;
		}

		.weather-grid {
			display: grid;
			grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
			gap: 0.85rem;
		}

		.weather-card {
			padding: 0.9rem;
			border-radius: 10px;
			border: 1px solid var(--line);
			background:
				radial-gradient(circle at top right, rgba(255, 220, 140, 0.35), transparent 38%),
				linear-gradient(180deg, #fffaf0 0%, #f6ead1 100%);
			box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.8);
		}

		.weather-card h3 {
			font-family: "Fraunces", Georgia, "Times New Roman", serif;
			font-size: 1.08rem;
			margin-bottom: 0.25rem;
		}

		.weather-meta {
			font-size: 0.85rem;
			color: #6a5a45;
			margin-bottom: 0.7rem;
		}

		.weather-temp {
			font-size: 1.85rem;
			font-weight: 700;
			line-height: 1;
			margin-bottom: 0.35rem;
		}

		.weather-summary {
			font-size: 0.95rem;
			font-weight: 700;
			color: #3d5f43;
			margin-bottom: 0.5rem;
		}

		.weather-stats {
			display: grid;
			gap: 0.35rem;
			font-size: 0.9rem;
			color: #4a3b28;
		}

		.weather-empty {
			padding: 1rem;
			border: 1px dashed #bea780;
			border-radius: 8px;
			background: #fff8ea;
			color: #6a5a45;
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

			.weather-header {
				flex-direction: column;
				align-items: flex-start;
			}

			.photo-grid {
				grid-template-columns: repeat(2, minmax(0, 1fr));
			}

			#map {
				height: 620px;
			}

			.map-embed {
				height: 620px;
			}

			.map-caption {
				flex-direction: column;
				align-items: flex-start;
			}
		}

		@media (max-width: 560px) {
			.photo-grid {
				grid-template-columns: 1fr;
			}

			#map {
				height: 520px;
			}

			.map-embed {
				height: 520px;
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

	<main>
		<section class="hero about-map-box" aria-label="About and interactive map section">
			<h2>About this Map</h2>
			<p>
				This map has been designed as a tool to help the organization 
				Humane Borders visualize and optimize the deployment of drinking water stations
				in the counties of Yuma, Pima, and Santa Cruz in southern Arizona.
			</p>
			<p>
				Use the layer feature to toggle on and off locations of water stations and 
				deaths of individuals over the past five years. Use the time slider to see locations
				for deaths at monthly intervals.You can also enable the distance tool to
				see how far each death occurred from a water station.
			</p>
		</section>

		<section class="map-panel" id="map-section">
			<iframe
				class="map-embed"
				src="Project.html"
				title="Southern Arizona water station map"
				allow="fullscreen"
				allowfullscreen
				loading="eager">
			</iframe>
			<div class="map-caption">
				<span class="map-badge">Leaflet-style UI</span>
				<span>Map design and layers created using Leaflet and ArcGIS Online.</span>
			</div>
		</section>

		<section class="weather-section" id="weather-section" aria-label="Real-time weather in southern Arizona">
			<div class="weather-header">
				<div>
					<h2>Real-Time Weather</h2>
					<p>Current conditions for southern Arizona locations near the water station network.</p>
				</div>
				<div class="weather-actions">
					<div class="weather-status" id="weatherStatus">Loading current conditions...</div>
					<button class="weather-refresh" id="refreshWeatherButton" type="button">Refresh Weather</button>
				</div>
			</div>
			<div class="weather-grid" id="weatherGrid">
				<div class="weather-empty">Weather data is loading.</div>
			</div>
		</section>

		<div class="content-grid">
			<section id="about-section">
				<h2>Preliminary Analysis</h2>
				<p>
					The harsh conditions of the Sonoran Desert make travel on foot a life-threatening prospect.
					People cross the international border at many points, and take many routes. However, the data indicate
					some areas as "hot spots" for deaths. Deployment of new or existing water stations to these
					areas may make a positive impact.
				</p>
				<div class="analysis-image-row">
					<img class="analysis-image" src="Hotspot_1.png" alt="Preliminary analysis hotspot map 1">
					<div class="analysis-image-stack">
						<img class="analysis-image" src="Hotspot_2.png" alt="Preliminary analysis hotspot map 2">
						<p class="analysis-inline-note">Clusters of deaths more than 10 miles from a station (indicated in pink) also suggest that a water station in this area could be beneficial.</p>
						<img class="analysis-image" src="Hotspot_3.png" alt="Preliminary analysis hotspot map 3">
					</div>
				</div>
			</section>

			<section>
				<h2>Sobering Facts</h2>
				<p>
					
				</p>
				<div class="quick-facts-grid">
					<div class="fact-card">
						<div class="fact-label">Deaths since 2021</div>
						<div class="fact-value" id="factsDeathsCount">Loading...</div>
					</div>
					<div class="fact-card">
						<div class="fact-label">Average age of the deceased</div>
						<div class="fact-value" id="factsAvgAge">Loading...</div>
					</div>
					<div class="fact-card">
						<div class="fact-label">Average distance from deceased to nearest water station (miles)</div>
						<div class="fact-value" id="factsAvgDistance">Loading...</div>
					</div>
				</div>
				<div class="pie-chart-wrap">
					<div class="pie-chart-title">Deaths by Month of Year</div>
					<div class="pie-chart-canvas-wrap">
						<canvas id="deathsByMonthChart" aria-label="Pie chart of deaths by month of year"></canvas>
					</div>
				</div>
			</section>
		</div>

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
		
	</footer>

	<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.3/dist/chart.umd.min.js"></script>
	<script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-datalabels@2.2.0"></script>
	<script src="https://unpkg.com/@turf/turf@6.5.0/turf.min.js"></script>
	<script>
			const ALLOWED_DEATH_COUNTIES = new Set(['yuma', 'pima', 'santa cruz']);
			const WATER_STATION_SERVICE_URL = 'https://services.arcgis.com/o6oETlrWetREI1A2/arcgis/rest/services/water_3_mile_buffer/FeatureServer';
			const DEATHS_SERVICE_URL = 'https://services.arcgis.com/o6oETlrWetREI1A2/arcgis/rest/services/migrant_deaths_2021_2025/FeatureServer';
			const RESERVATIONS_SERVICE_URL = 'https://services.arcgis.com/o6oETlrWetREI1A2/arcgis/rest/services/American_Indian_Reservations_in_Arizona/FeatureServer';
			const SOUTHERN_AZ_WEATHER_POINTS = [
				{ name: 'Yuma', county: 'Yuma County', lat: 32.6927, lon: -114.6277 },
				{ name: 'Ajo', county: 'Pima County', lat: 32.3717, lon: -112.8607 },
				{ name: 'Sells', county: 'Pima County', lat: 31.911, lon: -111.8812 },
				{ name: 'Tucson', county: 'Pima County', lat: 32.2226, lon: -110.9747 },
				{ name: 'Nogales', county: 'Santa Cruz County', lat: 31.3404, lon: -110.9343 }
			];
			let deathsByMonthChart = null;
			const FALLBACK_WATER_STATIONS = [
				{ name: 'Bates Well Station', lat: 32.183319, lon: -112.943256 },
				{ name: 'Bishop Carcano Station', lat: 31.840364, lon: -111.387703 },
				{ name: 'Dancehall Station', lat: 31.574359, lon: -111.332252 },
				{ name: 'Dripping Springs Station', lat: 32.031417, lon: -112.892194 },
				{ name: 'Green Valley Station', lat: 31.806908, lon: -110.999031 },
				{ name: 'Ruby', lat: 31.569451, lon: -111.332645 }
			];

			function setQuickFacts(count, averageAge, averageDistanceMiles) {
				const countEl = document.getElementById('factsDeathsCount');
				const ageEl = document.getElementById('factsAvgAge');
				const distanceEl = document.getElementById('factsAvgDistance');

				if (countEl) countEl.textContent = String(count);
				if (ageEl) ageEl.textContent = Number.isFinite(averageAge) ? averageAge.toFixed(1) : 'N/A';
				if (distanceEl) distanceEl.textContent = Number.isFinite(averageDistanceMiles) ? averageDistanceMiles.toFixed(2) : 'N/A';
			}

			function setQuickFactsUnavailable() {
				setQuickFacts('N/A', NaN, NaN);
			}

			function getWeatherDescription(code) {
				const descriptions = {
					0: 'Clear sky',
					1: 'Mostly clear',
					2: 'Partly cloudy',
					3: 'Overcast',
					45: 'Fog',
					48: 'Rime fog',
					51: 'Light drizzle',
					53: 'Drizzle',
					55: 'Dense drizzle',
					56: 'Freezing drizzle',
					57: 'Heavy freezing drizzle',
					61: 'Light rain',
					63: 'Rain',
					65: 'Heavy rain',
					66: 'Freezing rain',
					67: 'Heavy freezing rain',
					71: 'Light snow',
					73: 'Snow',
					75: 'Heavy snow',
					77: 'Snow grains',
					80: 'Rain showers',
					81: 'Heavy showers',
					82: 'Violent showers',
					85: 'Snow showers',
					86: 'Heavy snow showers',
					95: 'Thunderstorm',
					96: 'Thunderstorm with hail',
					99: 'Severe thunderstorm'
				};
				return descriptions[code] || 'Current conditions';
			}

			function formatWeatherTimestamp(value) {
				const parsed = new Date(value);
				if (Number.isNaN(parsed.getTime())) return 'Unavailable';
				return parsed.toLocaleString([], {
					month: 'short',
					day: 'numeric',
					hour: 'numeric',
					minute: '2-digit'
				});
			}

			function setWeatherStatus(text, state) {
				const statusEl = document.getElementById('weatherStatus');
				if (!statusEl) return;
				statusEl.textContent = text;
				if (state) {
					statusEl.dataset.state = state;
				} else {
					delete statusEl.dataset.state;
				}
			}

			function renderWeatherCards(entries) {
				const grid = document.getElementById('weatherGrid');
				if (!grid) return;

				if (!Array.isArray(entries) || entries.length === 0) {
					grid.innerHTML = '<div class="weather-empty">Weather data is currently unavailable.</div>';
					return;
				}

				grid.innerHTML = entries.map(entry => `
					<article class="weather-card">
						<h3>${entry.name}</h3>
						<div class="weather-meta">${entry.county}</div>
						<div class="weather-temp">${entry.temperature}&deg;F</div>
						<div class="weather-summary">${entry.summary}</div>
						<div class="weather-stats">
							<div>Wind: ${entry.windSpeed} mph</div>
							<div>Humidity: ${entry.humidity}%</div>
							<div>Observed: ${entry.observedAt}</div>
						</div>
					</article>
				`).join('');
			}

			async function fetchWeatherForPoint(point) {
				const params = new URLSearchParams({
					latitude: String(point.lat),
					longitude: String(point.lon),
					current: 'temperature_2m,relative_humidity_2m,wind_speed_10m,weather_code',
					temperature_unit: 'fahrenheit',
					wind_speed_unit: 'mph',
					timezone: 'auto'
				});
				const response = await fetch('https://api.open-meteo.com/v1/forecast?' + params.toString());
				if (!response.ok) throw new Error('Weather request failed');
				const payload = await response.json();
				const current = payload && payload.current ? payload.current : {};
				return {
					name: point.name,
					county: point.county,
					temperature: Number.isFinite(current.temperature_2m) ? Math.round(current.temperature_2m) : 'N/A',
					humidity: Number.isFinite(current.relative_humidity_2m) ? Math.round(current.relative_humidity_2m) : 'N/A',
					windSpeed: Number.isFinite(current.wind_speed_10m) ? Math.round(current.wind_speed_10m) : 'N/A',
					summary: getWeatherDescription(current.weather_code),
					observedAt: formatWeatherTimestamp(current.time)
				};
			}

			async function loadWeatherDashboard() {
				const refreshButton = document.getElementById('refreshWeatherButton');
				if (refreshButton) refreshButton.disabled = true;
				setWeatherStatus('Loading current conditions...');

				try {
					const weatherEntries = await Promise.all(
						SOUTHERN_AZ_WEATHER_POINTS.map(fetchWeatherForPoint)
					);
					renderWeatherCards(weatherEntries);
					setWeatherStatus('Updated ' + new Date().toLocaleTimeString([], { hour: 'numeric', minute: '2-digit' }));
				} catch (_err) {
					renderWeatherCards([]);
					setWeatherStatus('Weather service unavailable right now.', 'error');
				} finally {
					if (refreshButton) refreshButton.disabled = false;
				}
			}

			function getPointCoordinates(feature) {
				const coords = feature && feature.geometry ? feature.geometry.coordinates : null;
				return Array.isArray(coords) && coords.length >= 2 ? [coords[0], coords[1]] : null;
			}

			function normalizeCountyName(value) {
				return String(value || '')
					.trim()
					.toLowerCase()
					.replace(/_/g, ' ')
					.replace(/\bcounty\b/g, '')
					.replace(/\s+/g, ' ')
					.trim();
			}

			function getFeatureCounty(feature) {
				const props = feature && feature.properties ? feature.properties : {};
				const county = props.COUNTY || props.County || props.county || '';
				return normalizeCountyName(county);
			}

			function isAllowedDeathCounty(feature) {
				return ALLOWED_DEATH_COUNTIES.has(getFeatureCounty(feature));
			}

			function isAllowedTargetCounty(value) {
				const normalized = normalizeCountyName(value);
				return !normalized || ALLOWED_DEATH_COUNTIES.has(normalized);
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

			function getNumericAge(feature) {
				const props = feature && feature.properties ? feature.properties : {};
				const value = props.AGE || props.Age || props.age;
				if (value === null || value === undefined || String(value).trim() === '') return null;
				const parsed = Number(value);
				return Number.isFinite(parsed) && parsed > 0 ? parsed : null;
			}

			function getDeathYear(feature) {
				const props = feature && feature.properties ? feature.properties : {};
				const raw = props.DATE || props.Date || props.date || '';

				if (typeof raw === 'number' && Number.isFinite(raw)) {
					const asDate = raw > 1e11 ? new Date(raw) : (raw > 1e9 ? new Date(raw * 1000) : null);
					if (asDate && !Number.isNaN(asDate.getTime())) return asDate.getUTCFullYear();
				}

				const text = String(raw).trim();
				if (!text) return null;

				const parsed = new Date(text);
				if (!Number.isNaN(parsed.getTime())) return parsed.getUTCFullYear();

				const match = text.match(/\b(19|20)\d{2}\b/);
				return match ? Number(match[0]) : null;
			}

			function getDeathMonth(feature) {
				const props = feature && feature.properties ? feature.properties : {};
				const raw = props.DATE || props.Date || props.date || '';

				if (typeof raw === 'number' && Number.isFinite(raw)) {
					const asDate = raw > 1e11 ? new Date(raw) : (raw > 1e9 ? new Date(raw * 1000) : null);
					if (asDate && !Number.isNaN(asDate.getTime())) return asDate.getUTCMonth() + 1;
				}

				const text = String(raw).trim();
				if (!text) return null;

				const slashMatch = text.match(/^(\d{1,2})\/(\d{1,2})\/(\d{2,4})$/);
				if (slashMatch) {
					const month = Number(slashMatch[1]);
					return Number.isFinite(month) ? month : null;
				}

				const parsed = new Date(text);
				return Number.isNaN(parsed.getTime()) ? null : parsed.getUTCMonth() + 1;
			}

			function renderDeathsByMonthChart(features) {
				const chartCanvas = document.getElementById('deathsByMonthChart');
				if (!chartCanvas || typeof Chart === 'undefined') return;

				const monthLabels = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
				const monthCounts = new Array(12).fill(0);

				features.forEach(feature => {
					const month = getDeathMonth(feature);
					if (month && month >= 1 && month <= 12) {
						monthCounts[month - 1] += 1;
					}
				});

				if (deathsByMonthChart) {
					deathsByMonthChart.destroy();
				}

				deathsByMonthChart = new Chart(chartCanvas, {
					type: 'pie',
					data: {
						labels: monthLabels,
						datasets: [{
							data: monthCounts,
							backgroundColor: [
								'#5a6fb2', '#6b86c8', '#6fa8d6', '#74b87b',
								'#b8c96a', '#f1cf4a', '#ef9b2d', '#d75a2b',
								'#c9822e', '#a76b6f', '#7a63a8', '#5d5aa1'
							],
							borderColor: '#fffaf0',
							borderWidth: 2,
							radius: '76%'
						}]
					},
					options: {
						responsive: true,
						maintainAspectRatio: false,
						layout: {
							padding: {
								top: 18,
								right: 28,
								bottom: 18,
								left: 28
							}
						},
						plugins: {
							legend: {
								display: false
							},
							datalabels: {
								formatter: function (_value, context) {
									return context.chart.data.labels[context.dataIndex];
								},
								color: '#2d2418',
								font: {
									weight: '700',
									size: 11
								},
								anchor: 'end',
								align: 'end',
								offset: 8,
								clip: false
							}
						}
					},
					plugins: [ChartDataLabels]
				});
			}

			function haversineMiles(lat1, lon1, lat2, lon2) {
				const toRadians = value => value * Math.PI / 180;
				const earthRadiusMiles = 3958.7613;
				const dLat = toRadians(lat2 - lat1);
				const dLon = toRadians(lon2 - lon1);
				const a = Math.sin(dLat / 2) ** 2 +
					Math.cos(toRadians(lat1)) * Math.cos(toRadians(lat2)) * Math.sin(dLon / 2) ** 2;
				const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));
				return earthRadiusMiles * c;
			}

			function findNearestWaterDistanceMiles(coords, waterStations) {
				if (!coords || !Array.isArray(waterStations) || waterStations.length === 0) return null;
				let nearestMiles = Infinity;
				waterStations.forEach(station => {
					const miles = haversineMiles(coords[1], coords[0], station.lat, station.lon);
					if (miles < nearestMiles) nearestMiles = miles;
				});
				return Number.isFinite(nearestMiles) ? nearestMiles : null;
			}

			async function resolveFeatureLayerUrl(serviceUrl) {
				if (/\/FeatureServer\/\d+$/.test(serviceUrl)) return serviceUrl;

				try {
					const response = await fetch(serviceUrl + '?f=pjson');
					const info = await response.json();
					if (info && Array.isArray(info.layers) && info.layers.length > 0) {
						return serviceUrl + '/' + info.layers[0].id;
					}
				} catch (_err) {
					return serviceUrl + '/0';
				}

				return serviceUrl + '/0';
			}

			async function fetchFeatureCollection(serviceUrl) {
				const layerUrl = await resolveFeatureLayerUrl(serviceUrl);
				const queryUrl = layerUrl + '/query?where=1%3D1&outFields=*&outSR=4326&f=geojson';
				const response = await fetch(queryUrl);
				if (!response.ok) throw new Error('Feature query failed');
				return response.json();
			}

			async function loadWaterStations() {
				try {
					const response = await fetch('water_stations.csv');
					if (!response.ok) throw new Error('Water station CSV failed to load');
					const csv = await response.text();
					const fromCsv = csv
						.split(/\r?\n/)
						.map(line => line.trim())
						.filter(Boolean)
						.map(line => line.split(','))
						.filter(parts => parts.length >= 4)
						.filter(parts => {
							const type = String(parts[3] || '').trim().toLowerCase();
							if (type !== 'station' && type !== 'seasonal_station') return false;
							return isAllowedTargetCounty(parts[4] || '');
						})
						.map(parts => ({
							name: String(parts[0] || '').replace(/_/g, ' ').trim() || 'Water station',
							lat: Number(parts[1]),
							lon: Number(parts[2])
						}))
						.filter(station => Number.isFinite(station.lat) && Number.isFinite(station.lon));

					if (fromCsv.length > 0) return fromCsv;
				} catch (_err) {
					// Fall back to online service for file:// and other local CSV loading issues.
				}

				try {
					const collection = await fetchFeatureCollection(WATER_STATION_SERVICE_URL);
					const features = Array.isArray(collection.features) ? collection.features : [];
					const fromService = features
						.map(feature => {
							const coords = getPointCoordinates(feature);
							const props = feature && feature.properties ? feature.properties : {};
							if (!coords) return null;
							const county = props.COUNTY || props.County || props.county || props.COUNTY_NAME || props.county_name || '';
							if (!isAllowedTargetCounty(county)) return null;
							return {
								name: String(props.name || props.NAME || 'Water station'),
								lat: Number(coords[1]),
								lon: Number(coords[0])
							};
						})
						.filter(station => station && Number.isFinite(station.lat) && Number.isFinite(station.lon));

					if (fromService.length > 0) return fromService;
				} catch (_err) {
					// Use built-in fallback as last resort.
				}

				return FALLBACK_WATER_STATIONS;
			}

			function isPointInsideAnyReservation(coords, reservationFeatures) {
				if (typeof turf === 'undefined' || !coords || !Array.isArray(reservationFeatures)) return false;
				const pt = turf.point(coords);
				return reservationFeatures.some(feature => {
					try {
						return turf.booleanPointInPolygon(pt, feature);
					} catch (_err) {
						return false;
					}
				});
			}

			async function loadQuickFacts() {
				try {
					const [waterStations, deathsCollection, reservationsCollection] = await Promise.all([
						loadWaterStations(),
						fetchFeatureCollection(DEATHS_SERVICE_URL),
						fetchFeatureCollection(RESERVATIONS_SERVICE_URL)
					]);

					const reservationFeatures = (reservationsCollection.features || []).filter(isTohonoOodhamReservation);
					const filteredDeaths = (deathsCollection.features || []).filter(feature => {
						const coords = getPointCoordinates(feature);
						if (!coords) return false;
						if (!isAllowedDeathCounty(feature)) return false;
						return !isPointInsideAnyReservation(coords, reservationFeatures);
					});

					const since2021 = filteredDeaths.filter(feature => {
						const year = getDeathYear(feature);
						return year !== null && year >= 2021;
					});

					const ages = since2021.map(getNumericAge).filter(age => age !== null);
					const averageAge = ages.length ? ages.reduce((sum, age) => sum + age, 0) / ages.length : NaN;
					const distances = since2021
						.map(feature => findNearestWaterDistanceMiles(getPointCoordinates(feature), waterStations))
						.filter(distance => Number.isFinite(distance));
					const averageDistanceMiles = distances.length
						? distances.reduce((sum, distance) => sum + distance, 0) / distances.length
						: NaN;

					setQuickFacts(since2021.length, averageAge, averageDistanceMiles);
					renderDeathsByMonthChart(since2021);
				} catch (_err) {
					setQuickFactsUnavailable();
					renderDeathsByMonthChart([]);
				}
			}

			const refreshWeatherButton = document.getElementById('refreshWeatherButton');
			if (refreshWeatherButton) {
				refreshWeatherButton.addEventListener('click', loadWeatherDashboard);
			}

			loadWeatherDashboard();
			loadQuickFacts();
	</script>
</body>
</html>
