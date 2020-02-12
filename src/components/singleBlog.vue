<template>
  <div class="single-blog">
    <h1>This is an single blog page</h1>
  </div>
</template>
<script>
export default {
  name: 'singleBlog',
  data:()=>({
    id:null,
    blog:{},
    }),
  created(){
    this.axios
      .get('http://jsonplaceholder.typicode.com/posts/' + this.$route.params.id)
      .then((response) => {
        console.log(response.data)
        this.id = this.$route.params.id
        this.blog = response.data
      })
      .catch((error) => {
      // console.log(error)
      })
  },
  mounted(){
    
  },
  computed:{
  
  },
  methods:{
    
  }
  
}
</script>