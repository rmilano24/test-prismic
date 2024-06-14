<script lang="ts">
	import {onMount} from "svelte";
	import gsap from 'gsap';
	import type { Content } from '@prismicio/client';
	import { PrismicRichText } from '@prismicio/svelte';
	import Label from './Label.svelte';

	export let slice: Content.RichTextSlice;

	onMount(()=> {
		const tl = gsap.timeline({ defaults: {
		ease: 'power2.inOut'}});

		tl.fromTo(".fademe", { scale: 0.5 }, { scale: 1, opacity: 1, duration: 1.4});
	});

</script>

<section class="container text-red-600 fademe">
	<PrismicRichText
		field={slice.primary.content}
		components={{
			label: Label
		}}
	/>
</section>

<style>
	.container {
		max-width: 600px;
		margin: 6em auto;
		font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif,
			'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol';
	}
</style>
