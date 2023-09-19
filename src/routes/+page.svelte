<script>
	import '@spectrum-web-components/bundle';
	import { FillLayer, LineLayer, MapLibre } from 'svelte-maplibre';
	import TileSource from '../components/PMTiles/PMTiles.svelte';
</script>

<h1>Welcome to SvelteKit MAPTIME</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
<sp-avatar size="700" label="Demo User" src="https://picsum.photos/500/500" />

<MapLibre
	style="https://basemaps.cartocdn.com/gl/positron-gl-style/style.json"
	center={[-87.622088, 41.878781]}
	zoom={10}
	class="map"
	standardControls
>
	<TileSource
		url={'pmtiles://https://allofthedata.s3.us-west-2.amazonaws.com/creative_communities/tracts.pmtiles'}
	>
		<FillLayer
			id={'v-test-fill'}
			sourceLayer="tracts"
			paint={{
				'fill-color': '#0000FF',
				'fill-opacity': 0.8
			}}
		/>
		<LineLayer
			id={'v-test-line'}
			sourceLayer="tracts"
			paint={{
				'line-width': 2,
				'line-color': '#FFFFFF',
				'line-opacity': 1.0
			}}
		/>
	</TileSource>
</MapLibre>

<style>
	:global(.map) {
		width: 100%;
		height: 1000px;
	}
</style>
