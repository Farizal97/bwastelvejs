<script>
    export let  currentEmoji = emoji;
    let current = 'button1';
	// setTimeout(function() { currentEmoji = '\u{1F625}'; 
	// }, 1000);
</script>

<style>
    div {
        font-size: 3em;
        margin-bottom: 0.5em;
    }
</style>

<div>{currentEmoji}</div>
<button
class="btn" 
class:btn-primary={current === 'button1'} 
on:click={() => current = 'button1'}>button 1
</button>
<button 
class="btn" 
class:btn-primary={current === 'button2'} 
on:click={() => current = 'button2'}>button 2
</button>
<button 
class="btn" 
class:btn-primary={current === 'button3'} 
on:click={() => current = 'button3'}>button 3
</button>
