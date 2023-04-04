<script setup>
const props = defineProps(['obj','param'])
</script>

<template>
	<div :class="'xr'+param"><span class="xrLabel">{{param}}</span>{{obj}}</div>
</template>