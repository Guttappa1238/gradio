<script context="module">
	let _id = 0;
</script>

<script lang="ts">
	import { createEventDispatcher } from "svelte";
	import { Block, BlockTitle } from "@gradio/atoms";

	export let value: number = 0;
	export let style: string = "";
	export let minimum: number = 0;
	export let maximum: number = 100;
	export let step: number = 1;
	export let disabled: boolean = false;
	export let label: string;
	export let show_label: boolean;

	const id = `range_id_${_id++}`;

	const dispatch = createEventDispatcher<{ change: number }>();

	$: dispatch("change", value);
</script>

<div class="w-full flex flex-col">
	<div class="flex justify-between">
		<label for={id}>
			<BlockTitle {show_label}>{label}</BlockTitle>
		</label>
		<div class="font-medium dark:text-gray-300">{value}</div>
	</div>
</div>

<input
	type="range"
	{id}
	name="cowbell"
	class="w-full disabled:cursor-not-allowed"
	bind:value
	min={minimum}
	max={maximum}
	{step}
	{disabled}
/>
