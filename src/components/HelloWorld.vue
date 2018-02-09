<template>
 

 <div class="main">
<button v-on:click="show">SHOW DATA
 </button>
 <ol>
  <li v-for="title in titles" >{{title}}</li>
</ol>

 </div>
  
</template>


<script>

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      results: [],
      titles:[],
      urls:[]
    }
  },
  methods:{
    show()
    {
      axios.get("https://newsapi.org/v2/top-headlines?country=us&category=business&apiKey=e3dbee9cd0994fb28d300538611d2106")
    .then(response => {this.results = response.data.articles;
    console.log(this.results);
    for(var x=0;x<this.results.length;x++)
    {
      this.titles.push(this.results[x].title);
      this.urls.push(this.results[x].url);
    }
    //this.titles=this.results.title;
    console.log(this.titles);

    })
    },

    beforeMount()
    {
      this.show();
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {

  
  margin-left: 0px;
  padding-bottom:8px;
  text-align: left;
}
a {
  color: #42b983;
}
button
{
  background-color: gray;
  color: white;
  border:2px solid white;
}
</style>
