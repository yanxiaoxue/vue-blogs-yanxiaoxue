<template>
  <nav>
      <ul>
          <li>
              <!-- <a href="/">首页</a> -->
              <router-link exact="" to="/">首页</router-link>
          </li>
           <li>
              <!-- <a href="/add">添加博客</a> -->
              <router-link exact="" to="/add">添加博客</router-link>

          </li>
      </ul>
  </nav>
</template>

<script>
export default {
  name: 'mr-header',
  props: {
    msg: String
  }
}
</script>


<style scoped>
ul{
  list-style-type: none;
  text-align: center;
  margin: 0;
}
li{
  display: inline-block;
  margin: 0 10px
}
a{
  color: #fff;
  text-decoration: none;
  padding: 6px 8px;
  border-radius: 10px;
}
nav{
  background: #272020;
  padding: 14px 0;
  margin-bottom: 40px;
}
.router-link-active{
  background: #eee;
  color: #444;
}
</style>
