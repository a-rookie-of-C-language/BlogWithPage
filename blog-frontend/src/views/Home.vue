<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'

// 路由实例
const router = useRouter()

// 文章列表数据
const articles = ref([
  {
    id: 1,
    title: '如何使用Vue 3和TypeScript构建现代Web应用',
    summary: 'Vue 3带来了Composition API、更好的TypeScript支持等新特性，本文将介绍如何利用这些特性构建现代Web应用。',
    cover: 'https://picsum.photos/id/1/800/450',
    category: { id: 1, name: '前端开发' },
    tags: [{ id: 1, name: 'Vue' }, { id: 2, name: 'TypeScript' }],
    author: '张三',
    publishDate: '2023-06-15',
    viewCount: 1250
  },
  {
    id: 2,
    title: 'Spring Boot实战：构建RESTful API',
    summary: '本文将介绍如何使用Spring Boot快速构建RESTful API，包括项目搭建、数据库集成、安全认证等方面的内容。',
    cover: 'https://picsum.photos/id/2/800/450',
    category: { id: 2, name: '后端开发' },
    tags: [{ id: 3, name: 'Spring Boot' }, { id: 4, name: 'Java' }],
    author: '李四',
    publishDate: '2023-05-20',
    viewCount: 980
  },
  {
    id: 3,
    title: 'GitHub Pages部署静态网站的最佳实践',
    summary: 'GitHub Pages是一个免费的静态网站托管服务，本文将分享使用GitHub Pages部署静态网站的最佳实践和技巧。',
    cover: 'https://picsum.photos/id/3/800/450',
    category: { id: 3, name: '运维部署' },
    tags: [{ id: 5, name: 'GitHub' }, { id: 6, name: 'CI/CD' }],
    author: '王五',
    publishDate: '2023-04-10',
    viewCount: 756
  }
])

// 跳转到文章详情页
const goToArticle = (id: number) => {
  router.push(`/article/${id}`)
}

// 跳转到分类页
const goToCategory = (id: number, event: Event) => {
  event.stopPropagation()
  router.push(`/category/${id}`)
}

// 跳转到标签页
const goToTag = (id: number, event: Event) => {
  event.stopPropagation()
  router.push(`/tag/${id}`)
}

// 模拟从API获取数据
onMounted(() => {
  // 这里将来会替换为实际的API调用
  console.log('组件已挂载，可以调用API获取数据')
})
</script>

<template>
  <div class="home-container">
    <div class="banner">
      <h1>个人技术博客</h1>
      <p>分享编程技术、学习心得和个人成长</p>
    </div>
    
    <div class="article-list">
      <div 
        v-for="article in articles" 
        :key="article.id" 
        class="article-card"
        @click="goToArticle(article.id)"
      >
        <div class="article-cover">
          <img :src="article.cover" :alt="article.title">
        </div>
        <div class="article-content">
          <h2 class="article-title">{{ article.title }}</h2>
          <p class="article-summary">{{ article.summary }}</p>
          <div class="article-meta">
            <span class="category" @click="goToCategory(article.category.id, $event)">
              {{ article.category.name }}
            </span>
            <span 
              v-for="tag in article.tags" 
              :key="tag.id" 
              class="tag"
              @click="goToTag(tag.id, $event)"
            >
              {{ tag.name }}
            </span>
            <span class="publish-date">{{ article.publishDate }}</span>
            <span class="view-count">阅读 {{ article.viewCount }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.home-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

.banner {
  text-align: center;
  padding: 60px 0;
  background-color: #f5f5f5;
  border-radius: 8px;
  margin-bottom: 30px;
}

.banner h1 {
  font-size: 2.5rem;
  margin-bottom: 10px;
  color: #333;
}

.banner p {
  font-size: 1.2rem;
  color: #666;
}

.article-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
  gap: 30px;
}

.article-card {
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
  background-color: #fff;
}

.article-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.15);
}

.article-cover {
  height: 200px;
  overflow: hidden;
}

.article-cover img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.article-card:hover .article-cover img {
  transform: scale(1.05);
}

.article-content {
  padding: 20px;
}

.article-title {
  font-size: 1.4rem;
  margin-bottom: 10px;
  color: #333;
  line-height: 1.4;
}

.article-summary {
  font-size: 0.95rem;
  color: #666;
  margin-bottom: 15px;
  line-height: 1.6;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.article-meta {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  font-size: 0.85rem;
}

.category {
  background-color: #e6f7ff;
  color: #1890ff;
  padding: 2px 8px;
  border-radius: 4px;
  cursor: pointer;
}

.tag {
  background-color: #f5f5f5;
  color: #666;
  padding: 2px 8px;
  border-radius: 4px;
  cursor: pointer;
}

.publish-date, .view-count {
  color: #999;
}

@media (max-width: 768px) {
  .article-list {
    grid-template-columns: 1fr;
  }
  
  .banner {
    padding: 40px 0;
  }
  
  .banner h1 {
    font-size: 2rem;
  }
}
</style>