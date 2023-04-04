<script setup>
const props = defineProps(['app','obj','path'])

const elems = []
props.obj.forEach( elem => elems.push(props.app.value(elem)) )
</script>

<template>

	<span v-if="!obj.size">
		<span class="xrLabel">Set</span><span class="xrArray xrEmpty"></span>
	</span>

	<span v-else>
		<span class="xrLabel">Set</span>
		<table>
			<tr v-for="obj in elems">
				<td><component :is="obj[0]" :app="app" :param="obj[1]" :obj="obj[2]" :path="path"/></td>
			</tr>
		</table>
	</span>

</template>