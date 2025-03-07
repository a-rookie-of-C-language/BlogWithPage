<script setup lang="ts">
import { RouterView, RouterLink } from 'vue-router'
</script>

<template>
  <div class="app-container">
    <header class="app-header">
      <div class="header-content">
        <div class="logo">
          <RouterLink to="/">个人技术博客</RouterLink>
        </div>
        <nav class="main-nav">
          <RouterLink to="/" class="nav-item">首页</RouterLink>
          <RouterLink to="/category/1" class="nav-item">前端开发</RouterLink>
          <RouterLink to="/category/2" class="nav-item">后端开发</RouterLink>
          <RouterLink to="/category/3" class="nav-item">运维部署</RouterLink>
          <RouterLink to="/about" class="nav-item">关于我</RouterLink>
        </nav>
      </div>
    </header>

    <main class="app-main">
      <RouterView />
    </main>

    <footer class="app-footer">
      <div class="footer-content">
        <div class="footer-info">
          <p>© 2023 个人技术博客 - 基于Vue 3、TypeScript和GitHub Pages构建</p>
          <p>分享编程技术、学习心得和个人成长</p>
        </div>
        <div class="footer-links">
          <a href="https://github.com" target="_blank" class="footer-link">GitHub</a>
          <a href="https://twitter.com" target="_blank" class="footer-link">Twitter</a>
          <a href="https://linkedin.com" target="_blank" class="footer-link">LinkedIn</a>
        </div>
      </div>
    </footer>
  </div>
</template>

<style>
/* 全局样式 */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
  color: #333;
  background-color: #f7f7f7;
  line-height: 1.6;
}

a {
  text-decoration: none;
  color: inherit;
}

/* 应用容器 */
.app-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

/* 头部样式 */
.app-header {
  background-color: #fff;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  position: sticky;
  top: 0;
  z-index: 100;
}

.header-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 15px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo a {
  font-size: 1.5rem;
  font-weight: bold;
  color: #1890ff;
}

.main-nav {
  display: flex;
  gap: 20px;
}

.nav-item {
  padding: 5px 10px;
  border-radius: 4px;
  transition: background-color 0.3s;
  font-weight: 500;
}

.nav-item:hover {
  background-color: #f0f0f0;
}

.router-link-active {
  color: #1890ff;
}

/* 主要内容区域 */
.app-main {
  flex: 1;
  padding: 20px 0;
}

/* 页脚样式 */
.app-footer {
  background-color: #333;
  color: #fff;
  padding: 30px 0;
  margin-top: 40px;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 20px;
}

.footer-info p {
  margin-bottom: 10px;
  color: #ccc;
}

.footer-links {
  display: flex;
  gap: 15px;
}

.footer-link {
  color: #ccc;
  transition: color 0.3s;
}

.footer-link:hover {
  color: #fff;
}

@media (max-width: 768px) {
  .header-content {
    flex-direction: column;
    gap: 15px;
  }
  
  .main-nav {
    width: 100%;
    justify-content: space-between;
  }
  
  .footer-content {
    flex-direction: column;
    text-align: center;
  }
}
</style>
