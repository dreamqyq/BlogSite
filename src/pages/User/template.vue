<template>
  <div id="user">
    <section class="user-info">
      <img class="avatar" :src="toUser.avatar" :alt="toUser.username" :title="toUser.username">
      <div class="user-detail">
        <h3>{{ toUser.username }}</h3>
        <p>博客小站 第 {{ toUser.id }} 号会员</p>
      </div>
    </section>
    <section class="blogs-list">
      <ul>
        <li class="item" v-for="blog in blogs" :key="blog.id">
          <router-link :to="`/details/${blog.id}`">
            <div class="date">
              <span class="day">{{ splitDate(blog.createdAt).date }}</span>
              <span class="month">{{ splitDate(blog.createdAt).month }}月</span>
              <span class="year">{{ splitDate(blog.createdAt).year }}年</span>
            </div>
            <div class="blog-info">
              <h3>{{ blog.title }}</h3>
              <p>{{ blog.description }}</p>
            </div>
          </router-link>
        </li>
      </ul>
    </section>
    <section class="pagination">
      <el-pagination
        background
        layout="prev, pager, next"
        @current-change="onPageChange"
        :current-page.sync="page"
        :total="total">
      </el-pagination>
    </section>
  </div>
</template>

<script src="./template.js"></script>
<style lang="less" src="../My/template.less"></style>
