<template>
	<div class="thank-you-card">
		<img
			src="/images/illustration-thank-you.svg"
			alt="illustration thank you image"
		/>

		<span class="option-message">You selected {{ optionSelected }} out of 5</span>

		<h3>Thank you!</h3>
		<p>
			We appreciate you taking the time to give a rating. If you ever need more
			support, don’t hesitate to get in touch!
		</p>
	</div>
</template>

<script setup>
	import './ThankYouComponent.css';
	import { toRefs } from 'vue';

	const props = defineProps({
		optionSelected: String,
	});

	const { optionSelected } = toRefs(props);
</script>
