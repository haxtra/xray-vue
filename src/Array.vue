<script>
import ArrayRow from './ArrayRow.vue'
</script>

<script setup>
const props = defineProps(['app','obj','path'])
</script>

<template>

	<span v-if="!obj.length" class="xrArray xrEmpty"></span>

	<table v-else>
		<ArrayRow v-for="(elem, index) in obj" :app="app" :i="index" :obj="elem" :path="path + '[' + index + ']'"/>
	</table>

</template>
