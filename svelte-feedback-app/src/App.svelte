<script lang="ts">
  import FeedbackList from "./components/FeedbackList.svelte";
  import FeedbackStats from "./components/FeedbackStats.svelte";
  import FeedbackForm from "./components/FeedbackForm.svelte";

	let feedback = [
		{
			id:1,
			rating: 10, 
			text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras scelerisque est at leo tempor varius. Vestibulum id dapibus tellus. Ut bibendum ex sem, in vehicula nunc vulputate '
		},
		{
			id:2,
			rating: 9, 
			text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras scelerisque est at leo tempor varius. Vestibulum id dapibus tellus. Ut bibendum ex sem, in vehicula nunc vulputate '
		},
		{
			id:3,
			rating: 8, 
			text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras scelerisque est at leo tempor varius. Vestibulum id dapibus tellus. Ut bibendum ex sem, in vehicula nunc vulputate '
		}
	]
	

	$: count = feedback.length
	$: average = feedback.reduce((a, {rating}) => a + rating, 0) / feedback.length

	const addFeedback = (e) => {

		const newFeedback = e.detail
		feedback = [newFeedback, ...feedback]
	}

	const deleteFeedback = (e) => {
		const itemID = e.detail;
		feedback = feedback.filter((item) => item.id != itemID)
		
	}
</script>

<main class="container">
	<FeedbackForm on:add-feedback={addFeedback}/>
	<FeedbackStats {count} {average}/>
	<FeedbackList {feedback} on:delete-feedback = {deleteFeedback}/>
</main>

<style>
</style>