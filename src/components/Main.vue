<template>
	<div>
		<app-header></app-header>
		<h1>main content</h1>
		<add-inventory></add-inventory>
	</div>
</template>

<script>
	import AppHeader from './AppHeader.vue'
	import AddInventory from './AddInventory.vue'
	export default {
		name: 'Main',
		components: {  
			AppHeader,
			AddInventory,
		}
	}
</script>
