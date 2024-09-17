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
{me.name}
hi 
<style>

</style>