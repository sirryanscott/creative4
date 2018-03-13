<template>
	<div id="app">
		<h1>Food Storage Inventory</h1>
		<router-view/>
		<div id="footer">
			<div id="github">
				<a href="https://github.com/sirryanscott/creative4.git" target="_blank">
					<img src="/static/images/GitHub_Logo.png"></img>
				</a>
			</div>
		</div>
	</div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
h1 {
	text-align: center;
}
#github {
	width: 100px;
}

img {
	margin-top: 200px;
	width: 100%;
}
</style>
