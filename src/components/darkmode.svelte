<script>
    let darkMode = false;
	function toggle() {
        darkMode = !darkMode;
        window.document.body.classList.toggle('dark');
    }
</script>
<button on:click={toggle}>
	{#if darkMode }
		Go light mode
	{:else}
		Go dark mode
	{/if}
</button>
<style>
    button{
        font-family: 'Josefin Sans', sans-serif;
        padding:10px;
        margin:10px;
        border:none;
        color: white;
        background:rgb(21, 69, 230);
    }
    button:hover{
        background:rgb(118, 147, 240);
    }
     button:active{
        background:rgb(195, 209, 255);
        color:black;
   }
   
   
</style>