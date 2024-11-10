<script context="module">
	import Icon from './Icon.svelte';
	import { defineMeta } from '@storybook/addon-svelte-csf';

	const { Story } = defineMeta({
		title: 'Atoms/Icon',
		component: Icon,
		args: {
			icon: 'home'
		},
		argTypes: {
			icon: {
				control: 'text'
			},
			height: {
				control: 'text'
			}
		}
	});
</script>

<Story name="Default"></Story>
