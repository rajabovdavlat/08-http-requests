<template>
  <div v-theme:column="'narrow'" id="show-blogs">
    <h1>All Blog Articles</h1>
    <input type="text" v-model="search" placeholder="search blog" />
    <div v-for="blog in filteredBlogs" class="single-blog">
      <router-link :to="'/blog/' + blog.id"
        ><h2>{{ blog.title | (to - uppercase) }}</h2></router-link
      >
      <article>{{ blog.content | snippet }}</article>
    </div>
  </div>
</template>

<script>
import searchMixin from "../mixins/searchMixin";

export default {
  data() {
    return {
      blogs: [],
      search: "",
    };
  },
  created() {
    this.$http
      .get(
        "https://vue-project-blog-d102c-default-rtdb.firebaseio.com/posts.json"
      )
      .then(function (data) {
        return data.json();
      }).then(function (data) {
        var blogsArray = [];
        for (let key in data) {
          data[key].id = key
          blogsArray.push(data[key])
        }
        this.blogs = blogsArray
      })
  },
  computed: {},
  filters: {
    "to-uppercase": function (value) {
      return value.toUpperCase();
    },
  },
  mixins: [searchMixin],
};
</script>

<style scoped>
#show-blogs {
  max-width: 800px;
  margin: 0 auto;
}
.single-blog {
  padding: 20px;
  margin: 20px 0;
  box-sizing: border-box;
  background: #eee;
}
</style>
