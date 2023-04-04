<script setup>
const props = defineProps(['obj','param'])

function dump(){
	console.log(props.obj)
}
</script>

<template>
	<span :class="'xrLabel '+param.class" @click="dump">{{param.label}}</span>
</template>