<script>
	import {fade,fly} from 'svelte/transition';
	import EmojiDisplay from './EmojiDisplay.svelte';
	import Emojiescription from './EmojiDescription.svelte';
import EmojiDescription from './EmojiDescription.svelte';
	import Button from './Button.svelte';

	let isLoaded = false;
	let currentEmoji = '😊';
	const emojis =  ['😉','🚀'];
	let m = {x:0,y:0};

	function randomizeEmoji(){
		return emojis[Math.floor(Math.random() * emojis.length)];
	}

	function handleRandomButton() {
		currentEmoji = randomizeEmoji();
	}

	setTimeout(function()  {
		isLoaded = true;
	}, 2500);

	function handleMousemove(event){
		m.x = event.clientX;
		m.y = event.clientY;
	}

</script>



<style>
	div {
		margin:2em;
	}
</style>

<svelte:head>
	<link  href='/terminal.min.css' rel='stylesheet' />
</svelte:head>

<div class="container" on:mousemove={handleMousemove}>
	<p>
		The mouse position: {m.x} x {m.y}
	</p>
<h1>Random Emoji</h1>
<ul>
	{#each emojis as emoji}
	<li>{emoji}</li>
	{/each}
</ul>
{#if isLoaded === true}
<div in:fly={{ y:200,duration:2000 }} out:fade>
<EmojiDisplay  {currentEmoji} />
<EmojiDescription />
<Button on:click={handleRandomButton} title={'Randomize'} />
</div>
{:else}
<h2>Loading...</h2>
{/if}

<Button title={'Toggle'} on:click={() => isLoaded = !isLoaded} />
</div>