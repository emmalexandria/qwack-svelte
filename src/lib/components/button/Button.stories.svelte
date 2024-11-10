<script context="module">
	import Button from './Button.svelte';
	import { defineMeta, setTemplate } from '@storybook/addon-svelte-csf';

	const { Story } = defineMeta({
		title: 'Atoms/Buttons',
		component: Button,
		args: {
			content: 'Button'
		},
		argTypes: {
			suffixIcon: {
				control: 'text'
			}
		}
	});
</script>

<script>
	setTemplate(sharedTemplate);
</script>

{#snippet sharedTemplate(args)}
	{@const { content, ...rest } = args}
	<Button {...rest}>
		{#snippet children()}
			{content}
		{/snippet}
	</Button>
{/snippet}

<Story name="Default"></Story>

<Story name="Icon Suffix" args={{ suffixIcon: 'arrow-right' }}></Story>
