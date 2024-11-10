<script lang="ts">
	import * as feather from 'feather-icons';
	interface Props {
		icon: feather.FeatherIconNames;
		height?: number | 'full';
		strokeWidth?: number;
	}

	let { icon, height = 24, strokeWidth = 2 }: Props = $props();

	let svgHeight: number | string = $state(height);
	let svgWidth: number | string = $state(height);
	$effect(() => {
		svgWidth = height == 'full' ? 'auto' : height;
		svgHeight = height == 'full' ? '100%' : height;
	});
</script>

{#if feather.icons[icon]}
	<!-- eslint-disable-next-line  -->
	{@html feather.icons[icon].toSvg({
		'stroke-width': strokeWidth,
		height: svgHeight,
		width: svgWidth,
		color: 'currentColor'
	})}
{/if}
