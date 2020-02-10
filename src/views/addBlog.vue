<template>
  <div class="add-blog">
    <h2>Add New Blog Post</h2>
    <form>
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
      </div>
    </form>
    <div id="preview">
      <h3>Preview Blog</h3>
      <p>Blog title: {{blog.title}}</p>
      <p>Blog content: {{blog.content}}</p>
      <p>Blog Categories:</p>
      <ul>
        <li v-for="(category, index) in blog.categories" :key="index">{{category}}</li>
      </ul>
    </div>
    <label>Author :</label>
    <select v-model="blog.author">
      <option v-for="(author, index) in authors" :key="index">{{author}}</option>
    </select>
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
      author:""
    },
    authors:[
      'Esa Rizki',
      'Abu Jelal'
    ],
    })
  
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
