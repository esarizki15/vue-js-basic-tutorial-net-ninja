<template>
  <div class="about">
    <h1>This is an about page</h1>
    <input type="text" v-model="search">
    <div v-for="(blo, index) in filterBlogs" :key="index">
    <router-link :to="'/blog/' + blo.id "><h2>{{blo.title}}</h2></router-link>
    <article>
    {{blo.body}}
    </article>
    </div>
  </div>
</template>
<script>
export default {
  name: 'addBlog',
  data:()=>({
    blog:[],
    search:"",
    }),
  mounted(){
    this.axios
      .get('https://net-ninja-68db3.firebaseio.com/posts.json')
      .then((response) => {
        // console.log(response.data)
        return response.data;
        // this.blog = response.data.slice(0,10)
      }).then((data)=>{
      console.log(data)
      // for(let key in data){
      // }
      })
      .catch((error) => {
      // console.log(error)
      })
  },
  computed:{
  filterBlogs:function(){
  return this.blog.filter((blo)=>{
  return blo.title.match(this.search);
  })
  }
  },
  methods:{
    
  }
  
}
</script>