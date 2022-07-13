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
	];

	$: numberOfFeedbacks = feedbacks.length;
	$: averageRating = feedbacks.reduce(function(prev,current){
		return prev + current.rating;
	},0) / feedbacks.length;

	function handleDeleteEntry(e){
		let id = e.detail;
		feedbacks = feedbacks.filter( i => i.id != id);
	}
</script>

<div class="wrapper">
	<FeedbackForm />
</div>
<div class="stats-box">
	<h2 class="secondary-heading">{numberOfFeedbacks} Reviews</h2>
	<h2 class="secondary-heading">Ratings Average: {averageRating}</h2>
</div>
<FeedbacksList {feedbacks} on:del:entry={handleDeleteEntry} />

<style lang="scss">
	@import "./scss/_variables.scss";

	.wrapper{
		margin-top: 8rem;
		margin-bottom: 4rem;
    }

	.stats-box{
		margin-bottom: 4rem;
		margin-left: auto;
		margin-right: auto;

		display: flex;
		justify-content: space-between;
		
		max-width: 90rem;
	}

	.secondary-heading{
		font-size: 1.8rem;
		font-weight: 800;
		color: $color-light-1;
	}
</style>