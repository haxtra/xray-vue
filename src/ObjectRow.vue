<script>
import { ref } from 'vue'
</script>

<script setup>
const props = defineProps(['app','obj','Key','path'])

const isCollapsed = ref(props.app.isCollapsed(props.path))

const toggleCollapse = () =>
	isCollapsed.value = props.app.toggleCollapse(props.path)

const params = props.app.value(props.obj, props.path)
</script>

<template>

	<tr v-bind:class="{xrCollapsed:isCollapsed}">
		<td class="xrKey" :title="path" @click="toggleCollapse">{{Key}}</td>
		<td class="xrValue">
			<component v-if="!isCollapsed" :app="app" :is="params[0]" :param="params[1]" :obj="params[2]" :path="path" />
		</td>
	</tr>

</template>
