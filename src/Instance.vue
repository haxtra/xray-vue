<script>
import ObjectRow from './ObjectRow.vue'
</script>

<script setup>
const props = defineProps(['app','obj','param','path'])

const keys = props.app.instanceSniffer(props.obj)
const title = (props.obj.constructor.name || 'anonymous') + ' instance'
</script>


<template>

	<span class="xrLabel xrInstance">{{title}}</span>

	<table v-if="keys.length">
		<ObjectRow v-for="key in keys" :key="key" :app="app" :Key="key" :obj="obj[key]" :path="path+'.'+key" />
	</table>

</template>