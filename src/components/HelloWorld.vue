<template>
  <div class="hello">
   	<ul>
   		<li v-for=" item in list">
   			<p>名字{{item.author_name}}</p>
   			<p>标题{{item.title}}</p>
   			<img :src="item.thumbnail_pic_s"/>
   		</li>
   	</ul>
  </div>
</template>

<script>
	import api from './../axios/api.js'
	
export default {
  name: 'HelloWorld',
  data () {
    return {
			list:[]
    }
  },
  created(){
	api.JH_news('/news/index', 'type=top&key=123456')
	  .then(res => {
	    this.list=res.articles;
			console.log(this.list);
	  });
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
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
