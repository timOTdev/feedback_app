<script>
	// Defined values
	let firstName = 'Tim';
	let lastName = 'Hoang';
	let color = 'blue';
	let showText = false;
	let users = [
		{
			id: '1',
			name: 'John'
		},
		{
			id: '2',
			name: 'Jane'
		},
		{
			id: '3',
			name: 'Bob'
		},
	]

	// Reactive values
	$: name = firstName + ' ' + lastName

	// Functions
	const toggleTitle = () => {
		color = color === 'blue' ? 'red' : 'blue'
	}
	const toggleText = () => {
		showText = !showText
	}
	const addUser = () => {
		users = [...users, { id: '4', name: 'Jen'}]
	}
</script>

<main>
	<!-- Title -->
	<h1 style="color: {color}">Hello {name}!</h1>

	<!-- Loops -->
	<!-- Set the loop key in the parentheses. -->
	{#each users as user (user.id)}
		<h3>{user.id}: {user.name}</h3>
	{/each}

	<hr />

	<!-- Conditional Rendering -->
	{#if showText}
		<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	{:else}
		<p>What would you like to do?</p>
	{/if}

	<!-- Events -->
	<!-- Can also write anonymous functions on the button. IE () => color = 'red' -->
	<p>1. Toggle the title color.</p>
	<button on:click={toggleTitle}>Click Me</button>
	<p>2. Toggle the tutorial link.</p>
	<button on:click={toggleText}>Click Me</button>
	<p>3. Adds a 4th person, Jen.</p>
	<button on:click={addUser}>Click Me</button>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
