<script lang="ts">
	import { createEventDispatcher } from "svelte";
	import { Block, BlockLabel } from "@gradio/atoms";

	import { Image } from "@gradio/icons";

	export let value: null | string;
	export let label: string | undefined = undefined;
	export let style: string = "";
	export let show_label: boolean;

	const dispatch = createEventDispatcher<{
		change: string;
	}>();

	$: value && dispatch("change", value);
</script>

<BlockLabel {show_label} Icon={Image} label={label || "Image"} />
{#if value === null}
	<div class="min-h-[16rem] flex justify-center items-center">
		<div class="h-10 dark:text-white opacity-50"><Image /></div>
	</div>
{:else}
	<img class="w-full h-full object-contain" src={value} {style} alt="" />
{/if}
