<template>
  <div class="login">
	  <form>
		  <h1>Login</h1>
		  <label for="username">Username</label><br>
		  <input type="text" placeholder="username"><br>
		  <label for="password">Password</label><br>
		  <input type="password" placeholder="password"><br>
		  <router-link to="/main"><button>Login</button></router-link>
	  </form>
  </div>
</template>

<script>
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
	text-align: center;
	font-weight: normal;
}

form {
	width: 400px;
	margin: auto;
	margin-top: 150px;
	font-size: 20pt;
}

button, input {
	box-sizing: border-box;
	width: 100%;
	padding: 8px;
	font-size: 15pt;
}

input {
	margin-top: 5px;
	margin-bottom: 15px;
	border-radius: 7px;
}

button {
	border-radius: 20px;
	color: #fff;
	background: #D9002E;
	border: solid;
}
	

</style>
