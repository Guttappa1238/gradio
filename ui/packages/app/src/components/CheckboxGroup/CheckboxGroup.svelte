<script lang="ts">
	import { CheckboxGroup } from "@gradio/form";
	import { Block } from "@gradio/atoms";
	import StatusTracker from "../StatusTracker/StatusTracker.svelte";
	import type { LoadingStatus } from "../StatusTracker/types";

	export let value: Array<string> = [];
	export let default_value: Array<string> = [];
	export let choices: Array<string>;

	export let mode: "static" | "dynamic";
	export let style: string = "";
	export let label: string = "Checkbox Group";
	export let form_position: "first" | "last" | "mid" | "single" = "single";
	export let show_label: boolean;

	export let loading_status: LoadingStatus;

	if (default_value) value = default_value;
</script>

<Block {form_position} type="fieldset">
	<StatusTracker {...loading_status} />

	<CheckboxGroup
		bind:value
		{choices}
		{style}
		{label}
		{show_label}
		on:change
		disabled={mode === "static"}
	/>
</Block>
