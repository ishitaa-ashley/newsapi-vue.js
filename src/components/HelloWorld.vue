<template>
 

 <div class="main">

 <ol>
  <li v-for="item in results" @click="callurl(`${item.url}`)" > {{item.title}} - {{item.author}}</li>
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
  mounted(){
      axios.get("https://newsapi.org/v2/top-headlines?country=us&category=business&apiKey=e3dbee9cd0994fb28d300538611d2106")
    .then(response => {this.results = response.data.articles;
    console.log(this.results);
   

    })
    },
    methods:{
      callurl(urlnow){
        alert("MOVING TO NEWSPAGE");
        
        window.open(urlnow);
        console.log(urlnow);
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

  border:2px solid gray;
  border-bottom: none;
  margin-left: 0px;
  padding-bottom:8px;
  text-align: left;
  background-color: #FDF9EA;
}
li:last-child
{
  border-bottom:2px solid gray;
}
li:hover
{
  cursor:pointer;
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
