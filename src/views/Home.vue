<template>
  <div class="dashboard">
    <nav class="navbar navbar-dark bg-dark">
      <a class="navbar-brand" href="#">
        <img src="https://a.storyblok.com/f/39898/1024x1024/dea4e1b62d/vue-js_logo-svg.png" width="40" height="40">
      </a>
      <div>
        <img :src="$auth.user.picture" width="30" height="30">
        <span class="text-muted font-weight-light px-2">{{$auth.user.name}}</span>
        <button type="button" class="btn btn-outline-secondary btn-sm" @click="$auth.logout()">Logout</button>
      </div>
    </nav>
  
    <div class="jumbotron">
    	<div class="container">
    		<h1 class="H1D">Dashboard</h1>
    		<div id="searchBox">
		    	Market name: <input type="text" v-model="search"/> Websites from: <input type="text" v-model="search"/>
				<div class="resBox" v-for="customer in filteredCustomers">
				 <span>{{customer.name}}</span>
				 <p>{{customer.desc}}</p>
				</div>
			</div>
    	</div>
    </div>

  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
  	return{
  		search: '',
  		customers: [
          { id: '1', name: 'Market resoults from:', desc: 'https://developer.export.gov/market-research- library.html'},
          { id: '2', name: 'websites resoults from:', desc: 'https://developer.similarweb.com/similar_websites_api'}
        ]};
},
computed:
{
    filteredCustomers:function()
    {
    	 var self=this;
       return this.customers.filter(function(cust){return cust.name.toLowerCase().indexOf(self.search.toLowerCase())>=0;});
       //return this.customers;
    }
}
}

</script>

<style scoped>
@import url('https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css');

.H1D {
	text-align: center;
	margin-bottom: 2rem;
}

#searchBox input {
	margin-right: 25px;
}

#searchBox {
	text-align: center;
}

.resBox {
	border: 2px solid #000;
	margin: 15px;
}
</style>