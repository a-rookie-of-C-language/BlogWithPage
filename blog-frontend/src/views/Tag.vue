<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { useRoute, useRouter } from 'vue-router'

// 路由实例
const route = useRoute()
const router = useRouter()

// 获取标签ID
const tagId = Number(route.params.id)

// 标签信息
const tag = ref({
  id: tagId,
  name: tagId === 1 ? 'Vue' : tagId === 2 ? 'TypeScript' : tagId === 3 ? 'Spring Boot' : 'Java',
  description: '这里是标签描述，介绍该标签相关的技术和应用场景。'
})

// 该标签下的文章列表
const articles = ref([
  {
    id: 1,
    title: '如何使用Vue 3和TypeScript构建现代Web应用',
    summary: 'Vue 3带来了Composition API、更好的TypeScript支持等新特性，本文将介绍如何利用这些特性构建现代Web应用。',
    cover: 'https://picsum.photos/id/1/800/450',
    publishDate: '2023-06-15',
    viewCount: 1250,
    category: { id: 1, name: '前端开发' }
  },
  {
    id: 4,
    title: 'Vue 3性能优化技巧',
    summary: '本文将分享一些Vue 3应用的性能优化技巧，包括组件懒加载、虚拟列表、计算属性优化等方面的内容。',
    cover: 'https://picsum.photos/id/4/800/450',
    publishDate: '2023-05-10',
    viewCount: 980,
    category: { id: 1, name: '前端开发' }
  },
  {
    id: 7,
    title: 'Vue Router 4新特性详解',
    summary: 'Vue Router 4是Vue 3的官方路由库，本文将详细介绍其新特性和使用方法。',
    cover: 'https://picsum.photos/id/7/800/450',
    publishDate: '2023-03-25',
    viewCount: 865,
    category: { id: 1, name: '前端开发' }
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

// 模拟从API获取数据
onMounted(() => {
  // 这里将来会替换为实际的API调用
  console.log(`获取标签ID: ${tagId} 的文章列表`)
})
</script>

<template>
  <div class="tag-container">
    <div class="tag-header">
      <h1>{{ tag.name }}</h1>
      <p class="tag-description">{{ tag.description }}</p>
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
            <span 
              class="category" 
              @click="goToCategory(article.category.id, $event)"
            >
              {{ article.category.name }}
            </span>
            <div class="article-info">
              <span class="publish-date">{{ article.publishDate }}</span>
              <span class="view-count">阅读 {{ article.viewCount }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.tag-container {
  max-width: 1000px;
  margin: 0 auto;
  padding: 20px;
}

.tag-header {
  text-align: center;
  margin-bottom: 40px;
  padding-bottom: 20px;
  border-bottom: 1px solid #eee;
}

.tag-header h1 {
  font-size: 2.2rem;
  color: #333;
  margin-bottom: 10px;
}

.tag-description {
  font-size: 1.1rem;
  color: #666;
}

.article-list {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.article-card {
  display: flex;
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
  width: 300px;
  height: 200px;
  overflow: hidden;
  flex-shrink: 0;
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
  flex: 1;
  padding: 20px;
  display: flex;
  flex-direction: column;
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
  flex: 1;
}

.article-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.category {
  background-color: #e6f7ff;
  color: #1890ff;
  padding: 2px 8px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 0.85rem;
}

.article-info {
  display: flex;
  gap: 15px;
  font-size: 0.85rem;
  color: #999;
}

@media (max-width: 768px) {
  .article-card {
    flex-direction: column;
  }
  
  .article-cover {
    width: 100%;
    height: 180px;
  }
}
</style>