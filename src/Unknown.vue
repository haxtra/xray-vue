<script setup>
const props = defineProps(['obj'])

function dump(){
	console.log(props.obj)
}

let text;
try {
	text = props.obj.toString()
} catch {
	text = 'unknown'
}
</script>

<template>
	<span class="xrUnknown" @click="dump"><span class="xrLabel">?</span>{{text}}</span>
</template>