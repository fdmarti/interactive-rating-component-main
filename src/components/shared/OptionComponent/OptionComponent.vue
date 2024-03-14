<template>
	<span class="option" :class="{ selected }">{{ text }}</span>
</template>

<script setup>
	import './OptionComponent.css';
	import { toRefs } from 'vue';

	const props = defineProps({
		text: String,
		selected: Boolean,
	});

	const { text, selected } = toRefs(props);
</script>
