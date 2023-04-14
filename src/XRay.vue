<script>
import {ref} from 'vue'
import XRayEngine from './engine.js'
import './xray.css'
</script>

<script setup>

	const props = defineProps({
		obj: null,
		header: {
			type: Boolean,
			default: true,
		},
		title: {
			type: String,
			default: 'XRay',
		},
		minimize: Boolean,
		collapse: [Boolean, String, Array],
		collapseExcept: [String, Array],
	})

	const app = new XRayEngine(props.obj, {collapse:props.collapse, collapseExcept:props.collapseExcept})

	const params = app.value(props.obj, '$')

	const minimized = ref(props.minimize)

	const togglePanel = () => minimized.value = !minimized.value

	function promptPath(e){
		const title = e.target.title
		if(title){
			e.stopPropagation()
			e.preventDefault()
			prompt('Object path:', title)
		}
	}

</script>

<template>

	<div class="XRay" @contextmenu="promptPath">

		<div v-if="header" class="xrHeader" v-bind:class="{xrMinimized:minimized}" @click="togglePanel">
			<div class="xrTitle">{{title}}</div>
		</div>

		<div v-if="!minimized" class="xrContent">
			<component :app="app" :is="params[0]" :param="params[1]" :obj="params[2]" path="$" />
		</div>

	</div>

</template>