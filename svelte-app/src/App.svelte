<script>

	import Modal from './Modal.svelte';
    import AddPersonForm from './AddPersonForm.svelte';

    let people = [
        { name: "yoshi", beltColor: "black", age: 25, id: 1},
        { name: "mario", beltColor: "orange", age: 45, id: 2},
        { name: "luigi", beltColor: "brown", age: 35, id: 3}
    ];

	const handleClick = (id) => {
		// delete the person from people
		people = people.filter((person) => person.id != id);
	}

    const toggleModal = () => {
      showModal = !showModal;
    }

	let num = 25;
    let showModal = false 
    let isPromo = false
</script>

<!-- The message is a <prop-->
<!-- In case, the prop name that is being passed is the same as the value-->
<!-- You can skip the key-value pair system and just declare it as below  -->
<!-- in the showModel prop -->
<Modal {showModal} on:click={toggleModal}>
  <AddPersonForm />
</Modal>

<main>
  <!-- Now, we wanted to trigger the event only once. So, if the button is clicked  -->
  <button on:click|once={toggleModal}>Open Modal</button>
   {#each people as person (person.id)} 
        <div>
            <h4>{person.name}</h4>
			{#if person.beltColor === 'black'}
				<p><strong>MASTER NINJAS</strong></p>
			{/if}	
            <p>{person.age} years old, {person.beltColor} belt.</p>
			<button on:click={() => handleClick(person.id)}>delete</button>
        </div>
   {:else}
		<p>There are no people to show...</p>
   {/each}
</main>

<style>
    main {
        text-align: center;
        padding: 1em;
        max-width: 240px;
        margin: 0 auto;
    }

    @media (min-width: 640px){
      main {
        max-width: none;
      }
    }
</style>
