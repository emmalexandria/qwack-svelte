<script lang="ts">
	import Icon from '$lib/components/icon/Icon.svelte';
	import '../../styles/variables.css';

	import type { Snippet } from 'svelte';
	interface Props {
		size?: 'small' | 'medium' | 'large';
		primary?: boolean;
		href?: string;
		type?: 'button' | 'submit';
		children: Snippet;
		suffixIcon?: FeatherIconNames;
	}
	let {
		size = 'medium',
		primary = false,
		href,
		type = 'button',
		children,
		suffixIcon
	}: Props = $props();
	import type { FeatherIconNames } from 'feather-icons';
</script>

{#if href}
	<a
		{href}
		class:small={size == 'small'}
		class:medium={size == 'medium'}
		class:large={size == 'large'}
		class:primary
	>
		{@render children?.()}
		{#if suffixIcon}
			<span>
				<Icon icon={suffixIcon} height="full" />
			</span>
		{/if}
	</a>
{:else}
	<button
		{type}
		class:small={size == 'small'}
		class:medium={size == 'medium'}
		class:large={size == 'large'}
		class:primary
	>
		{@render children?.()}
		{#if suffixIcon}
			<span>
				<Icon icon={suffixIcon} height="full" />
			</span>
		{/if}
	</button>
{/if}

<style lang="scss">
	button,
	a {
		display: flex;
		flex-direction: row;
		align-items: center;
		gap: var(--qwack-space-1);
		cursor: pointer;
		outline: none;
		border: none;
		background-color: transparent;
		border-radius: var(--qwack-rounded-sm);
		font-weight: 600;
		border-width: 1px;
		border-style: solid;
		transition: all var(--qwack-t-duration) var(--qwack-t-exit);
	}

	button:not(.primary),
	a:not(.primary) {
		color: var(--qwack-foreground);
		border-color: var(--qwack-foreground);

		&:hover {
			background-color: var(--qwack-foreground);
			color: var(--qwack-background);
			transition: all var(--qwack-t-duration) var(--qwack-t-enter);
		}
	}

	.primary {
		border-color: var(--qwack-accent);
		color: var(--qwack-accent);

		&:hover {
			background-color: var(--qwack-accent);
			color: var(--qwack-background);
			transition: all var(--qwack-t-duration) var(--qwack-t-enter);
		}
	}

	.small {
		font-size: var(--qwack-font-sm);
		letter-spacing: 0.25px;
		padding: var(--qwack-space-1) var(--qwack-space-1_5);

		span {
			height: var(--qwack-font-sm);
		}
	}

	.medium {
		font-size: var(--qwack-font-r);
		letter-spacing: 0.5px;
		padding: var(--qwack-space-2) var(--qwack-space-2_5);

		span {
			height: var(--qwack-font-r);
		}
	}

	.large {
		font-size: var(--qwack-font-lg);
		letter-spacing: 1px;
		padding: var(--qwack-space-2) var(--qwack-space-2_5);

		span {
			height: var(--qwack-font-lg);
		}
	}
</style>
