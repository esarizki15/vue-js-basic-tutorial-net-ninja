<template>
  <div class="add-blog">
    <h2>Add New Blog Post</h2>
    <form v-if="!submitted">
      <label for="title">Blog Title:</label>
      <input type="text" name="title" v-model="blog.title" required>
      <label for="title">Blog Content:</label>
      <textarea name="content" v-model="blog.content"></textarea>
      <div id="checkbox">
        <label>Esa</label>
      <input type="checkbox" v-model="blog.categories" value="esa">
        <label>Rizki</label>
      <input type="checkbox" v-model="blog.categories" value="rizki">
        <label>Hari</label>
      <input type="checkbox" v-model="blog.categories" value="hari">
        <label>Utama</label>
      <input type="checkbox" v-model="blog.categories" value="utama">
      <label>Author :</label>
      <select v-model="blog.author">
        <option v-for="(author, index) in authors" :key="index">{{author}}</option>
      </select>
      <button @click.prevent="post">Post</button>
      </div>
    </form>
    <div v-if="submitted">
      <h3>Sukses!!</h3>
    </div>
    <div id="preview">
      <h3>Preview Blog</h3>
      <p>Blog title: {{blog.title}}</p>
      <p>Blog content: {{blog.content}}</p>
      <p>Blog Categories:</p>
      <ul>
        <li v-for="(category, index) in blog.categories" :key="index">{{category}}</li>
      </ul>
    </div>
    <p>Author is : {{blog.author}}</p>
  </div>
</template>

<script>
export default {
  name: 'addBlog',
  data:()=>({
    blog:{
      title:"",
      content:"",
      categories:[],
      author:"",
      info: "",
    },
    submitted: false,
    authors:[
      'Esa Rizki',
      'Abu Jelal'
    ],
    }),
  mounted(){
    this.axios
      .get('http://jsonplaceholder.typicode.com/posts')
      .then((response) => {
        console.log(response.data.slice(0,10))
        this.blog.info = response.data.slice(0,10)
      })
      .catch((error) => {
      // console.log(error)
      })
  },
  methods:{
    post(){
      this.axios
      .post('https://net-ninja-68db3.firebaseio.com/posts.json', this.blog)
      .then((response) => {
        console.log(response)
        this.submitted = true;
      })
      .catch((error) => {
      // console.log(error)
      });
    }
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
