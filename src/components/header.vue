<template>
  <nav>
    <ul>
      <li><router-link to="/" exact>Blog</router-link></li>
      <li><router-link to="/add" exact>Add a New Blog</router-link></li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'Navbar'
}
</script>

<style scoped>
nav {
  background: #444;
  padding: 14px 0;
  margin-bottom: 40px;
}

ul {
  list-style: none;
  text-align: center;
  margin: 0;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #fff;
  text-decoration: none;
  padding: 8px 16px;
  border-radius: 8px;
  transition: 0.3s;
}

.router-link-active{
    background: #eee;
    color: #444;
}

a:hover {
  background: #666;
}
</style>