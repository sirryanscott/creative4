<template>
	<div>
		<login></login>
		<h3>** logged out successfully **</h3>
	</div>
</template>

<script>
	import Login from './Login.vue'
	export default {
		name: 'Logout',
		components: { Login }
	}
</script>

<style scoped>
h3 {
	text-align: center;
	margin-top: 70px;
	color: #D9002E;
}
</style>
