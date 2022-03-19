<div class="header">
  <h1>LIMADA NA7NOU HOUNA !</h1>
  <p>A website created by IDFKN.</p>
</div>

<!-- <div class="navbar">
  <a href="#a">Link</a>
  <a href="#s">Link</a>
  <a href="#d">Link</a>
  <a href="#current-blog-post" class="right">Blog</a>
</div> -->



<script>

import {  List,
	   ListItem,
	   Divider,
	   Card,
	   Subheader,
	   Avatar, MaterialApp } from 'svelte-materialify';
	   import { onMount } from "svelte";
	   import Textarea from 'svelte-materialify';
	export let search = ' ';
	let loading = false;
	// const API_URL = "https://api.giphy.com/v1/gifs/search?api_key=JnxTmEGKXjZeUKBzRjTQoMDg8OX8pS5U&rating=pg&q="
	const API_URL ="https://api.giphy.com/v1/gifs/search?api_key=yAQFKnN1xs5b6lXKQitvudVg5WadxtH0&limit=10&offset=0&rating=g&lang=en&q="
	let gifs = [];


	async function formSubmitted(event){
		event.preventDefault();
		loading = true;
		gifs = [];
		const url = `${API_URL}${search}`;
		const response = await fetch(url);
		const json =  await response.json();
		gifs = json.data.map(gif => gif.images.fixed_height.url);
		console.log(gifs);
		loading = false;
	}

	</script>
   
	
<form on:submit={formSubmitted}>
	<label for="search">Search a gif : </label>
	
	<!-- <input bind:value={search}  placeholder="Gifs ??" id="search" name="search"> -->
	<Textarea bind:value={search} id="search" name="search" autogrow rows={1} placeholder="Gifs ??">Auto Grow</Textarea>
	<button type="submit">OK</button>
</form>
{#if loading}
<img alt="loading" src="https://media3.giphy.com/media/OUH5FTK3tAE3l3T01j/giphy.gif?cid=ecf05e47oba5ws8zo7tqcnp0i1fafwqgk9umgjdhz1djdtik&rid=giphy.gif&ct=g0"/>
{/if}

<div class="results">
	{#each gifs as gif}
		<img alt="gif" src = {gif} />
	{/each}

</div>

   <MaterialApp>
   <Card>
	 <List>
	   <Subheader>Features</Subheader>
	   <ListItem>
		 <div slot="prepend">
		   <Avatar><img src="//picsum.photos/100?random=1" alt="Avatar" /></Avatar>
		 </div>
		 Grosserie
		 <span slot="subtitle"> <b>Einküfen</b> - T9adia </span>
	   </ListItem>
	   <Divider inset />
	   <ListItem>
		 <div slot="prepend">
		   <Avatar><img src="//picsum.photos/100?random=2" alt="Avatar" /></Avatar>
		 </div>
		 Galerie
		 <span slot="subtitle"> <b>Tsawer</b> - Fun </span>
	   </ListItem>
	   <Divider inset />
	   <ListItem>
		 <div slot="prepend">
		   <Avatar><img src="//picsum.photos/100?random=3" alt="Avatar" /></Avatar>
		 </div>
		 ToDo
		 <span slot="subtitle"> <b>Sebastian Currywurst</b> - Darija Matalan </span>
	   </ListItem>
	 </List>
   </Card>
   </MaterialApp>
<div class="footer">
  <h2>Footer</h2>
</div>


<style>
	* {
		box-sizing: border-box;
	}
	
	/* Header/logo Title */
	.header {
		padding: 80px;
		text-align: center;
		background: #1abc9c;
		color: white;
	}

	/* Increase the font size of the heading */
	.header h1 {
		font-size: 40px;
	}

	/* Style the top navigation bar */
	.navbar {
		overflow: hidden;
		background-color: #333;
	}

	/* Style the navigation bar links */
	.navbar a {
		float: left;
		display: block;
		color: white;
		text-align: center;
		padding: 14px 20px;
		text-decoration: none;
	}

	/* Right-aligned link */
	.navbar a.right {
		float: right;
	}

	/* Change color on hover */
	.navbar a:hover {
		background-color: #ddd;
		color: black;
	}

	/* Column container */
	.row {  
		display: -ms-flexbox; /* IE10 */
		display: flex;
		-ms-flex-wrap: wrap; /* IE10 */
		flex-wrap: wrap;

	}

	/* Create two unequal columns that sits next to each other */
	/* Sidebar/left column */
	.side {
		-ms-flex: 30%; /* IE10 */
		flex: 30%;
		background-color: #f1f1f1;
		padding: 20px;
	}

	/* Main column */
	.main {   
		-ms-flex: 70%; /* IE10 */
		flex: 70%;
		background-color: white;
		padding: 20px;
	}

	/* Fake image, just for this example */
	.fakeimg {
		background-color: #aaa;
		width: 100%;
		padding: 20px;
	}
	
	
	/* Footer */
	.footer {
		padding: 20px;
		text-align: center;
		background: #ddd;
	}

	/* Responsive layout - when the screen is less than 700px wide, make the two columns stack on top of each other instead of next to each other */
	@media screen and (max-width: 700px) {
		.row {   
			flex-direction: column;
		}
	}

	/* Responsive layout - when the screen is less than 400px wide, make the navigation links stack on top of each other instead of next to each other */
	@media screen and (max-width: 400px) {
		.navbar a {
			float: none;
			width: 100%;
		}
	}
</style>