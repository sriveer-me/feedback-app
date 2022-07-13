<script>
	import FeedbackForm from './FeedbackForm.svelte';
	import FeedbacksList from './FeedbacksList.svelte';

	let feedbacks = [
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

	function handleDeleteEntry(e){
		let id = e.detail;
		feedbacks = feedbacks.filter( i => i.id != id);
	}
</script>

<FeedbackForm />
<FeedbacksList {feedbacks} on:del:entry={handleDeleteEntry} />