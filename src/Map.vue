<script>
import ObjectRow from './ObjectRow.vue'
</script>

<script setup>
const props = defineProps(['app','obj','param','path'])
</script>

<template>

	<span v-if="!obj.size">
		<span class="xrLabel">Map</span><span class="xrObject xrEmpty"></span>
	</span>

	<span v-else>
		<span class="xrLabel">Map</span>
		<table>
			<ObjectRow v-for="elem in [...obj]" :app="app" :Key="elem[0].toString()" :obj="elem[1]" :path="path+'.'+elem[0].toString()" />
		</table>
	</span>

</template>
