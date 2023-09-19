<script lang="ts">
	import { onDestroy, tick } from 'svelte';
	import { getId, updatedSourceContext } from 'svelte-maplibre';
	// import flush from 'just-flush';

	export let id: string = getId('vector');
	export let url: string;
	import { Protocol } from 'pmtiles';
	import maplibregl from 'maplibre-gl';

	if (!maplibregl.config.REGISTERED_PROTOCOLS.hasOwnProperty('pmtiles')) {
		let protocol = new Protocol();
		maplibregl.addProtocol('pmtiles', protocol.tile);
	}

	/** Generate a unique id for each feature. This will overwrite existing IDs. */

	const { map, self: source } = updatedSourceContext();

	$: if ($map && $source !== id) {
		if ($source) {
			$map.removeSource($source);
		}

		$source = id;
		console.log('adding source ', url, ' with id ', id);
		$map.addSource($source, {
			type: 'vector',
			url: url
		});
		console.log('Map is ', $map);
	}

	onDestroy(() => {
		if ($source) {
			let sourceName = $source;
			$source = null;
			tick().then(() => {
				// Check if the map is still loaded. If the entire map was being torn down
				// then we don't want to call any other functions on it.
				if ($map?.loaded()) {
					$map?.removeSource(sourceName);
				}
			});
		}
	});
</script>

{#if $source}
	{#key $source}
		<slot />
	{/key}
{/if}
