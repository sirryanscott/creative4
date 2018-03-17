<template>
	<div>
		<hr>
		<div id="add-inventory-wrapper">
			<form v-on:submit.prevent="addItem">
				<h3 id="form-title">Add to Inventory</h3>
				<input class="input-box" type="text" v-model="text" placeholder="item">
				<select class="input-box" v-model="category">
					<option disabled value="">Category</option>
					<option>Fruits</option>
					<option>Vegetables</option>
					<option>Dairy</option>
					<option>Grains</option>
					<option>Protein</option>
					<option>Oils</option>
					<option>Other</option>
				</select>
				<input id="quantity" type="number" v-model="quantity" placeholder="quantity">
				<div id="checkbox-wrapper">
					<input id="add-to-shopping-list" type="checkbox">
					<label for="add-to-shopping-list">Add to Shopping List</label>
				</div>
				<br><button id="add-button">Add</button><br>
			</form>
		</div>
		<hr>
		<div class="inventory-row">	
			<div class="inventory-col">
				<h1>Fruits</h1>
				<ul>
					<li v-for="item in fruits">{{ item.text }}:   {{ item.quantity }}<button v-on:click="deleteItem(item)" class="delete">X</button></li>
				</ul>
			</div>
			<div class="inventory-col">
				<h1>Vegetables</h1>
				<ul>
					<li v-for="item in vegetables">{{ item.text }}:   {{ item.quantity }}<button v-on:click="deleteItem(item)" class="delete">X</button></li>
				</ul>
			</div>
		</div>
		<div class="inventory-row">	
			<div class="inventory-col">
				<h1>Dairy</h1>
				<ul>
					<li v-for="item in dairy">{{ item.text }}:   {{ item.quantity }}<button v-on:click="deleteItem(item)" class="delete">X</button></li>
				</ul>
			</div>
			<div class="inventory-col">
				<h1>Grains</h1>
				<ul>
					<li v-for="item in grains">{{ item.text }}:   {{ item.quantity }}<button v-on:click="deleteItem(item)" class="delete">X</button></li>
				</ul>
			</div>
		</div>
		<div class="inventory-row">	
			<div class="inventory-col">
				<h1>Protein</h1>
				<ul>
					<li v-for="item in protein">{{ item.text }}:   {{ item.quantity }}<button v-on:click="deleteItem(item)" class="delete">X</button></li>
				</ul>
			</div>
			<div class="inventory-col">
				<h1>Oils</h1>
				<ul>
					<li v-for="item in oils">{{ item.text }}:   {{ item.quantity }}<button v-on:click="deleteItem(item)" class="delete">X</button></li>
				</ul>
			</div>
		</div>
		<div class="inventory-row">	
			<div class="inventory-col">
				<h1>Other</h1>
				<ul>
					<li v-for="item in other">{{ item.text }}:   {{ item.quantity }}<button v-on:click="deleteItem(item)" class="delete">X</button></li>
				</ul>
			</div>
		</div>
	</div>
</template>
<script>
	import axios from 'axios';
	import AppHeader from './AppHeader.vue'
	export default {
		name: 'Main',
		components: {  
			AppHeader,
		},
		data () {
			return {
				items: [],
				text: '',
				quantity: '',
				category: '',
			}
		},
		computed: {
			fruits: function() {
				return this.items.filter(function(item){
					return item.category === 'Fruits';
				});
			},
			vegetables: function() {
				return this.items.filter(function(item){
					return item.category === 'Vegetables';
				});
			},
			dairy: function() {
				return this.items.filter(function(item){
					return item.category === 'Dairy';
				});
			},
			grains: function() {
				return this.items.filter(function(item){
					return item.category === 'Grains';
				});
			},
			protein: function() {
				return this.items.filter(function(item){
					return item.category === 'Protein';
				});
			},
			oils: function() {
				return this.items.filter(function(item){
					return item.category === 'Oils';
				});
			},
			other: function() {
				return this.items.filter(function(item){
					return item.category === 'Other';
				});
			},
			allItems: function() {
				return this.items;
			}
		},
	        created: function() {
	          this.getItems();
	        },
		methods: {
			getItems: function() {
				axios.get("/api/items").then(response => {
					this.items = response.data;
					return true;
				}).catch(err => {
				});
			},
			addItem: function() {
				axios.post("/api/items/", {
				text: this.text,
				quantity: this.quantity,
				category: this.category
				}).then(response => {
					this.text="";
					this.quantity="";
					this.category="";
					this.getItems();
					return true;
				}).catch(err => {
				});
			},
			deleteItem: function(item) {
				axios.delete("/api/items/" + item.id).then(response => {
					this.getItems();
					return true;
				}).catch(err => {
				});
			},
		},
	}
</script>

<style scoped>
hr {
	margin-top: 20px;
	margin-bottom: 20px;
	width: 80%;  
	border:0;
	height: 1px;
	background-image: linear-gradient(to right, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.75), rgba(0, 0, 0, 0));
}
#add-inventory-wrapper {
	width: 400px;
	margin: auto;
}
#form-title {
	text-align: center;
}
#quantity {
	width: 73px;
}
#checkbox-wrapper {
	display:none;
	float: right;
	margin-right: 27px;
}
#add-button {
	width: 100%;
	height: 30px;
	font-weight: bold;
	border-radius: 20px;
	color: #fff;
	background: #D9002E;
	border: solid;
}

input, button {
	font-size: 12pt;
}

input {
	border-radius: 7px;
	padding-left: 3px;
}
.input-box {
	width: 197px;
	box-sizing: border-box;
}
.inventory-col {
	flex: 50%;
	max-width: 13%;
	margin: 0 50px;
}
.inventory-row {
	display: flex;
	flex-wrap: wrap;
	margin: auto;
	justify-content: center;
}
ul {
	font-size: 20pt;
	padding: 0;
	list-style-type: none;
}

li {
	padding-bottom: 4px;
	width: 100%;
}

.delete {
	display: none;
}
li:hover .delete {
	display: inline-block;
	float: right;
}
</style>
