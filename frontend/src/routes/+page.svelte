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
	<article>
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
</main>
<style>




</style>