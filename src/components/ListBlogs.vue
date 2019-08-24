<template>
  <div v-theme:column="'narrow'" class="show-blogs">
     <h1>测试Mixin混入</h1>
     <!-- 搜索框 -->
     <input v-model="search" type="text" placeholder="search something...">
     <div v-for ="(blog,index) in filterBlogs" :key="index" class="single-blog">
         <h2 v-rainbow>{{blog.title | to-uppercase}}</h2>
         <article>{{blog.body | slice}}</article>
     </div>
  </div>
</template>
import searchMixins from "../mixins/searchMixins";
<script>
import searchMixins from '../mixins/searchMixins';
export default {
  name: 'ShowBlogs',
  data(){
      return{
        blogs:[],
        search:""
      }
  },
  created(){
    //获取数据
      this.$axios.get("/posts").then(res => {
          console.log(res.data);
          this.blogs = res.data.slice(0,10);
      })
  },
//   computed:{
//      filterBlogs(){
//          return this.blogs.filter(blog => {
//              return blog.title.match(this.search);
//          })
//      }
//   },
  directives:{
      //注册多个指令
      rainbow:{
        bind(el,binding,vnode){
        el.style.color = "#"+ Math.random().toString(16).slice(2,8);
        }
      }
  },
   filters:{
       /*
       第一种形式(不常用)
       "to-uppercase":function(value){
           return value.toUpperCase();
       }
       */
      toUppercase(value){
        return value.toUpperCase();
      }
       
   },
   mixins:[searchMixins]
}
</script>


<style scoped>
.show-blogs{
    max-width: 800px;
    margin: 0 auto;
}
.show-blogs h1{
    color:#fff;
}
.show-blogs input[type = "text"]{
    width: 100%;
    height: 30px;
    box-sizing: border-box;
}
.single-blog{
    padding: 20x;
    margin: 20px 0;
    box-sizing: border-box;
    background: #eee;
}
</style>