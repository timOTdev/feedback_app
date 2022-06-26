<script>
	import FeedbackList from "./components/FeedbackList.svelte";

	let feedback = [
		{
			id: 1,
			rating: 10,
			text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
		},
		{
			id: 2,
			rating: 9,
			text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
		},
		{
			id: 3,
			rating: 8,
			text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
		},
	]

	// Receives a ID from Card component and deletes from store.
	const deleteFeedback = (e) => {
		// Fetch the itemID on e.detail.
		const itemID = e.detail

		// Filters out everything but the received ID.
		feedback = feedback.filter(item => item.id !== itemID)
	}
</script>

<main class="container">
	<FeedbackList
		{feedback}
		on:delete-feedback={deleteFeedback}
	/>
</main>
