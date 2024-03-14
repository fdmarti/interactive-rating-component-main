<template>
	<ThankYouComponent v-if="statusForm" :optionSelected="optionSelected"/>
	<div class="raiting-card" v-else>
		<IconStar />
		<h2>How did we do?</h2>
		<p>
			Please let us know how we did with your support request. All feedback is
			appreciated to help us improve our offering!
		</p>
		<div class="options">
			<OptionComponent
				v-for="option in options"
				:text="option.text"
				:selected="option.selected"
				@click="handleSelectedClick"
			/>
		</div>
		<button class="submit-btn" @click="handleSubmit">Submit</button>
	</div>
</template>
<script setup>
	import './RaitingComponent.css';
	import { ref } from 'vue';
	import { IconStar, OptionComponent } from '../shared';
	import { ThankYouComponent } from '../';

	const optionSelected = ref('');
	const statusForm = ref(false);

	const options = ref([
		{
			text: '1',
			selected: false,
		},
		{
			text: '2',
			selected: false,
		},
		{
			text: '3',
			selected: false,
		},
		{
			text: '4',
			selected: false,
		},
		{
			text: '5',
			selected: false,
		},
	]);

	const handleSelectedClick = ({ target }) => {
		const value = target.innerText;
		options.value.forEach((option) => {
			if (option.text === value) {
				option.selected = true;
				optionSelected.value = option.text;
			} else {
				option.selected = false;
			}
		});
	};

	const handleSubmit = () => {
		if (!optionSelected.value) return;
		statusForm.value = !statusForm.value;

		setTimeout(() => {
			statusForm.value = !statusForm.value;
		}, 5000);
	};
</script>
