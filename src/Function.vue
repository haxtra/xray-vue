<script>
import ObjectRow from './ObjectRow.vue'
</script>

<script setup>
const props = defineProps(['app','obj','path','param'])

const keys = props.app.functionSniffer(props.obj)
const objType = Object.prototype.toString.call(props.obj)
const fnType = (/\[object (\w+)\]/.exec(objType))[1]
const fnName = props.obj.name ? props.obj.name : '[Anonymous]'
</script>

<template>

	<span class="xrFunction">{{fnType}} {{fnName}}</span>

	<table v-if="keys.length">
		<ObjectRow v-for="key in keys" :key="key" :app="app" :Key="key" :obj="obj[key]" :path="path+'.'+key" />
	</table>

</template>
