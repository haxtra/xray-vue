<script>
import ObjectRow from './ObjectRow.vue'
</script>

<script setup>
const props = defineProps(['app','obj','path'])
const keys = Object.keys(props.obj)
</script>

<template>

	<span v-if="!keys.length" class="xrObject xrEmpty"></span>

	<table v-else>
		<ObjectRow v-for="key in keys" :key="key" :app="app" :Key="key" :obj="obj[key]" :path="path + '.' + key" />
	</table>

</template>