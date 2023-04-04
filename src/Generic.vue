<script setup>
const props = defineProps(['obj','param'])
</script>

<template>
	<span :class="param">{{obj}}</span>
</template>