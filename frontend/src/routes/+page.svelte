<script>
    /** @type {import('./$types').PageData} */
    
    // Check if the data has been received and is an array
    // console.log("Received data in +page.svelte:", data);
	export let data;
	let people = data.people
	let me 
	
	if(people) {   
		let foundPerson = people.find(person => person.id == 41);    
		if(foundPerson) {     
			me = foundPerson;   
		} else {     
			me = 'hier is niets te zien';    
		}  
	} else {   
		me = 'hier is niets te zien'; 
	} 

	console.log(me);
</script>

<main>
	<section>
		<div class="keychain-hanger"></div>
		<img src="/images/keychain.svg" alt="">
	</section>
	<div class="card">
		<article class="front-card">
			<div>
				<header>
					<h2>FDND</h2>
				</header>
				<section>
					<img src="{me.avatar}" width="150" height="150" alt="{me.name} foto">
				</section>
				<footer>
					<h3>{me.name}</h3>
				</footer>
			</div>
		</article>
		<article class="back-card">
			<p>{me.name}  {me.prefix} {me.surname}</p>
			<p>{me.nickname}</p>
			<p>{me.bio}</p>
		</article>
	</div>
	
</main>
<style>

	main {
		/* background-color: goldenrod; */
		font-family: "Krona One", sans-serif;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		transform-style: preserve-3d;
		/* transform: rotateY(180deg); */
		transition: .5s ease;

	}

	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		border: none;

	}

	section .keychain-hanger {
		height: 10em;
		width: 3.5em;
		margin: -.3em;
		z-index: 1;
		background-color: #96CB7E;
	}

	.card {
		max-height: 26em;
		max-width: 17em;
		position: relative;
		transform-style: preserve-3d;
		&::after {
			content: '';
			position: absolute;
			width: 100%;
			height: 100%;
			background-image: url(./plastic-wrap-texture-png.png);
			background-size: cover;
			mix-blend-mode: screen;
			opacity: 70%;
			top: 0;
			left: 0;
			backface-visibility: hidden;
		}
	}

	article {
		padding: 1em;
		background-color: #F3E2CC;
		border-radius: .5em;
		border: 4px solid #679750;

		color: #6ca751;
		margin-top: -3px;
		text-align: center;
		
		
	}

	/* .front-card, .back-card {
		backface-visibility: hidden;
	} */



	

	article div {
		background-color: #443619;
		padding: .5em;
		position: relative;

		
		
		
	}

	article div header, footer {
		border: 1.5px solid #679750;
		padding: .5em;
	}

	article div section {
		border: 1.5px solid #679750;
		border-top: none;
		border-bottom: none;
		padding: 1em;
		height: 15em;

		& img {
			border-radius: 100%;
			height: 100%;
			object-fit: cover;
			outline: 1.5px solid #679750;
			outline-offset: .4em;
			filter: sepia(50%);
			z-index: 1;
		}
	}

	.back-card, .front-card {
		backface-visibility: hidden;
		box-shadow: -11px 10px 35.2px #2f6c0950;
	}

	.back-card {
		position: absolute;
		top: 0;
		width: 100%;
		height: 100%;
		background-color: #679750;
		transform: rotateY(180deg);

		display: flex;
		flex-direction: column;
		gap: .5em;

		& p {
			background-color: #F3E2CC;
			transform: rotate(2deg);
			width: fit-content;
			height: fit-content;

			&:nth-of-type(even) {
				transform: rotate(-2deg);
				margin-left: .5em;
			}
			
		}
		
	}

	.front-card {
		z-index: 1;
		/* position: relative; */

		&::before {
			content: '';
			background-color: #679750;
			width: .7em;
			height: 2.2em;
			position: absolute;
			left: 0;
			top: 50%;
			bottom: 50%;
		}
		&::after {
			content: '';
			background-color: #679750;
			width: .7em;
			height: 2.2em;
			position: absolute;
			right: 0;
			top: 50%;
			bottom: 50%;
		}
	}

</style>