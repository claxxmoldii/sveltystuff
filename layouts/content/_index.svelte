<script>
	export let title, intro, blog, source, content, allContent;
	import Grid from '../components/grid.svelte';
	import Uses from "../components/source.svelte";
	import Pager from "../components/pager.svelte";

	import FAQ from "../components/faqtoid.svelte";	
	import Tweens from "../components/tweens.svelte";
	import Springs from "../components/springs.svelte";	
	import Transition from "../components/transition.svelte";
	import Animate from "../components/animate.svelte";	

	$: currentPage = content.pager ? content.pager : 1;
	let postsPerPage = 3;
	let allPosts = allContent.filter(content => content.type == "blog");
	let totalPosts = allPosts.length;
	let totalPages = Math.ceil(totalPosts / postsPerPage);
	$: postRangeHigh = currentPage * postsPerPage;
	$: postRangeLow = postRangeHigh - postsPerPage;
</script>

<h1>{title}</h1>

<section id="intro">
	{#each intro as paragraph}
		<p>{@html paragraph}</p>
	{/each}
</section>

{#if blog}
	<div>
		<h3>Recent blog posts:</h3>
		<Grid items={allPosts} {postRangeLow} {postRangeHigh} />
		<br />
	</div>
	<Pager {currentPage} {totalPages} />	
{/if}


<!-- <div class="sveltystuff">
	<h4>svelty-stuff not working...</h4>
	<FAQ />
</div> -->

<div class="sveltystuff">
	<h4>svelty-stuff motion/easing... not working</h4>
	<Tweens />
</div>

<div class="sveltystuff">
	<h4>svelty-stuff transition... yey!</h4>
	<Transition />
</div>

<!-- <div class="sveltystuff">
	<h4>svelty-stuff animate... </h4>
	<Animate />
</div> -->



{#if source}
	<Uses {content} {source} />	
{/if}

<style>
	.sveltystuff {
		min-height: 25vh;
		background-color: aliceblue;
		margin-bottom: 5px;
	}
</style>