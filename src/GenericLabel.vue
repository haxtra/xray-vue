<script setup>
const props = defineProps(['obj','param'])
</script>

<template>
	<span :class="param.class"><span class="xrLabel">{{param.label}}</span>{{obj}}</span>
</template>