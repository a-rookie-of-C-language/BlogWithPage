<script setup lang="ts">
import { useRoute, useRouter } from 'vue-router'
import { marked } from 'marked'
import { ref, onMounted } from 'vue'
// 路由实例
const route = useRoute()
const router = useRouter()

// 获取文章ID
const articleId = route.params.id

// 文章内容（Markdown格式）
const markdownContent = `# 如何使用Vue 3和TypeScript构建现代Web应用

## 引言

Vue 3是Vue.js的最新主要版本，它带来了许多令人兴奋的新特性，包括Composition API、更好的TypeScript支持、更小的包体积和更好的性能。本文将介绍如何利用Vue 3和TypeScript构建现代Web应用。

## Vue 3的主要特性

### Composition API

Composition API是Vue 3最重要的全新特性之一，它提供了一种更灵活的方式来组织组件逻辑。与Vue 2的Options API相比，Composition API允许我们按照逻辑关注点来组织代码，而不是按照选项类型。

\`
import { onMounted, computed } from 'vue'

export default {
  setup() {
    // 响应式状态
    const count = ref(0)
    
    // 计算属性
    const doubleCount = computed(() => count.value * 2)
    
    // 方法
    function increment() {
      count.value++
    }
    
    // 生命周期钩子
    onMounted(() => {
      console.log('组件已挂载')
    })
    
    // 暴露给模板
    return {
      count,
      doubleCount,
      increment
    }
  }
}
\`
### 更好的TypeScript支持

Vue 3是用TypeScript重写的，因此它提供了更好的TypeScript支持。Vue 3的类型定义更加精确，使得在使用TypeScript开发Vue应用时能够获得更好的类型检查和IDE支持。

\`
import { defineComponent, ref } from 'vue'

export default defineComponent({
  setup() {
    const count = ref<number>(0)
    
    function increment() {
      count.value++
    }
    
    return {
      count,
      increment
    }
  }
})
\`

## 构建Vue 3 + TypeScript项目

### 使用Vite创建项目

Vite是一个由Vue团队开发的新一代前端构建工具，它比传统的webpack开发服务器快得多。使用Vite创建Vue 3 + TypeScript项目非常简单：

\`\`\`bash
npm init vite@latest my-vue-app -- --template vue-ts
cd my-vue-app
npm install
npm run dev
\`\`\`

### 项目结构

一个典型的Vue 3 + TypeScript项目结构如下：

\`\`\`
├── public/
├── src/
│   ├── assets/
│   ├── components/
│   ├── views/
│   ├── router/
│   ├── store/
│   ├── App.vue
│   ├── main.ts
│   └── shims-vue.d.ts
├── .gitignore
├── index.html
├── package.json
├── tsconfig.json
└── vite.config.ts
\`\`\`

## 结论

Vue 3和TypeScript的结合为构建现代Web应用提供了强大的工具和出色的开发体验。通过利用Composition API、更好的TypeScript支持和Vite等工具，我们可以构建出更加可维护、可扩展和高性能的Web应用。
`

// 将Markdown转换为HTML
const htmlContent = marked(markdownContent)

// 文章详情数据
const article = ref({
  id: Number(articleId),
  title: '如何使用Vue 3和TypeScript构建现代Web应用',
  content: htmlContent,
  cover: 'https://picsum.photos/id/1/800/450',
  category: { id: 1, name: '前端开发' },
  tags: [{ id: 1, name: 'Vue' }, { id: 2, name: 'TypeScript' }],
  author: '张三',
  publishDate: '2023-06-15',
  viewCount: 1250,
  commentCount: 28
})

// 评论列表数据
const comments = ref([
  {
    id: 1,
    content: '非常详细的教程，对我帮助很大！',
    author: '用户A',
    avatar: 'https://picsum.photos/id/1001/100/100',
    publishDate: '2023-06-16',
    likes: 15
  },
  {
    id: 2,
    content: '我在尝试使用Composition API时遇到了一些问题，请问如何处理响应式数组的更新？',
    author: '用户B',
    avatar: 'https://picsum.photos/id/1002/100/100',
    publishDate: '2023-06-17',
    likes: 8
  },
  {
    id: 3,
    content: '这篇文章写得很好，期待更多关于Vue 3的内容！',
    author: '用户C',
    avatar: 'https://picsum.photos/id/1003/100/100',
    publishDate: '2023-06-18',
    likes: 20
  }
])

// 相关文章数据
const relatedArticles = ref([
  {
    id: 4,
    title: 'Vue 3性能优化技巧',
    cover: 'https://picsum.photos/id/4/400/225',
    publishDate: '2023-05-10',
    viewCount: 980
  },
  {
    id: 5,
    title: 'TypeScript高级类型使用指南',
    cover: 'https://picsum.photos/id/5/400/225',
    publishDate: '2023-04-22',
    viewCount: 1120
  },
  {
    id: 6,
    title: 'Vite vs Webpack：新一代构建工具对比',
    cover: 'https://picsum.photos/id/6/400/225',
    publishDate: '2023-03-15',
    viewCount: 1560
  }
])

// 跳转到相关文章
const goToRelatedArticle = (id: number) => {
  router.push(`/article/${id}`)
}

// 跳转到分类页
const goToCategory = (id: number) => {
  router.push(`/category/${id}`)
}

// 跳转到标签页
const goToTag = (id: number) => {
  router.push(`/tag/${id}`)
}

// 模拟从API获取数据
onMounted(() => {
  // 这里将来会替换为实际的API调用
  console.log(`获取文章ID: ${articleId} 的详细信息`)
})
</script>

<template>
  <div class="article-detail-container">
    <div class="article-header">
      <h1 class="article-title">{{ article.title }}</h1>
      <div class="article-meta">
        <span class="author">作者：{{ article.author }}</span>
        <span class="publish-date">发布于：{{ article.publishDate }}</span>
        <span class="view-count">阅读：{{ article.viewCount }}</span>
        <span class="comment-count">评论：{{ article.commentCount }}</span>
      </div>
      <div class="article-tags">
        <span 
          class="category" 
          @click="goToCategory(article.category.id)"
        >
          {{ article.category.name }}
        </span>
        <span 
          v-for="tag in article.tags" 
          :key="tag.id" 
          class="tag"
          @click="goToTag(tag.id)"
        >
          {{ tag.name }}
        </span>
      </div>
    </div>
    
    <div class="article-cover">
      <img :src="article.cover" :alt="article.title">
    </div>
    
    <div class="article-content" v-html="article.content"></div>
    
    <div class="article-comments">
      <h2>评论 ({{ comments.length }})</h2>
      <div class="comment-list">
        <div v-for="comment in comments" :key="comment.id" class="comment-item">
          <div class="comment-avatar">
            <img :src="comment.avatar" :alt="comment.author">
          </div>
          <div class="comment-content">
            <div class="comment-author">{{ comment.author }}</div>
            <div class="comment-text">{{ comment.content }}</div>
            <div class="comment-meta">
              <span class="comment-date">{{ comment.publishDate }}</span>
              <span class="comment-likes">👍 {{ comment.likes }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
    
    <div class="related-articles">
      <h2>相关文章</h2>
      <div class="related-list">
        <div 
          v-for="article in relatedArticles" 
          :key="article.id" 
          class="related-item"
          @click="goToRelatedArticle(article.id)"
        >
          <div class="related-cover">
            <img :src="article.cover" :alt="article.title">
          </div>
          <div class="related-info">
            <h3 class="related-title">{{ article.title }}</h3>
            <div class="related-meta">
              <span class="related-date">{{ article.publishDate }}</span>
              <span class="related-views">阅读 {{ article.viewCount }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* 整体容器样式优化 */
.article-detail-container {
  max-width: 1000px;
  margin: 0 auto;
  padding: 30px 20px;
  background-color: #ffffff;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.05);
  border-radius: 12px;
}

/* 文章头部样式优化 */
.article-header {
  margin-bottom: 30px;
  padding-bottom: 20px;
  border-bottom: 1px solid #f0f0f0;
}

.article-title {
  font-size: 2.4rem;
  margin-bottom: 20px;
  color: #2c3e50;
  line-height: 1.3;
  font-weight: 700;
  letter-spacing: -0.5px;
}

.article-meta {
  display: flex;
  flex-wrap: wrap;
  gap: 18px;
  margin-bottom: 20px;
  font-size: 0.95rem;
  color: #666;
  align-items: center;
}

.article-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-bottom: 20px;
}

.category {
  background-color: #e6f7ff;
  color: #1890ff;
  padding: 5px 12px;
  border-radius: 20px;
  cursor: pointer;
  font-size: 0.9rem;
  font-weight: 500;
  transition: all 0.3s ease;
}

.category:hover {
  background-color: #1890ff;
  color: #ffffff;
}

.tag {
  background-color: #f5f5f5;
  color: #555;
  padding: 5px 12px;
  border-radius: 20px;
  cursor: pointer;
  font-size: 0.9rem;
  transition: all 0.3s ease;
}

.tag:hover {
  background-color: #e0e0e0;
  color: #333;
}

/* 文章封面图优化 */
.article-cover {
  width: 100%;
  height: 450px;
  overflow: hidden;
  border-radius: 12px;
  margin-bottom: 40px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

.article-cover img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.article-cover:hover img {
  transform: scale(1.03);
}

/* 文章内容样式优化 */
.article-content {
  line-height: 1.9;
  color: #333;
  font-size: 1.15rem;
  margin-bottom: 50px;
  max-width: 850px;
  margin-left: auto;
  margin-right: auto;
  letter-spacing: 0.01em;
  padding: 0 15px;
}

/* 代码块样式优化 */
.article-content pre {
  background-color: #1e1e2e;
  border-radius: 10px;
  padding: 25px;
  overflow-x: auto;
  margin: 30px 0;
  border: none;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.15);
  position: relative;
}

.article-content code {
  font-family: 'Fira Code', 'JetBrains Mono', 'SFMono-Regular', Consolas, 'Liberation Mono', Menlo, monospace;
  font-size: 0.95rem;
  background-color: rgba(27, 31, 35, 0.05);
  padding: 3px 6px;
  border-radius: 4px;
  color: #476582;
}

.article-content pre code {
  padding: 0;
  background-color: transparent;
  color: #f8f8f2;
  font-size: 0.95rem;
  line-height: 1.7;
  text-shadow: none;
  font-weight: 400;
}

/* 标题样式优化 */
.article-content h1 {
  font-size: 2.3rem;
  margin-top: 3rem;
  margin-bottom: 1.5rem;
  padding-bottom: 0.7rem;
  border-bottom: 2px solid #eaecef;
  color: #2c3e50;
  font-weight: 700;
}

.article-content h2 {
  font-size: 1.9rem;
  margin-top: 2.5rem;
  margin-bottom: 1.2rem;
  padding-bottom: 0.5rem;
  border-bottom: 1px solid #eaecef;
  color: #2c3e50;
  font-weight: 600;
}

.article-content h3 {
  font-size: 1.5rem;
  margin-top: 2rem;
  margin-bottom: 1.2rem;
  color: #2c3e50;
  font-weight: 600;
}

/* 段落和列表样式优化 */
.article-content p {
  margin: 1.5rem 0;
  line-height: 1.9;
}

.article-content ul, .article-content ol {
  padding-left: 2.2rem;
  margin: 1.5rem 0;
  line-height: 1.8;
}

.article-content li {
  margin-bottom: 0.8rem;
}

/* 引用块样式优化 */
.article-content blockquote {
  padding: 1rem 1.5rem;
  color: #4a5568;
  background-color: #f8f9fa;
  border-left: 0.4rem solid #3182ce;
  margin: 2rem 0;
  border-radius: 0 8px 8px 0;
  font-style: italic;
}

.article-content blockquote p {
  margin: 0.5rem 0;
}

/* 图片样式优化 */
.article-content img {
  max-width: 100%;
  height: auto;
  display: block;
  margin: 2.5rem auto;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.article-content img:hover {
  transform: scale(1.02);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
}

/* 评论区样式优化 */
.article-comments {
  margin-bottom: 50px;
  background-color: #f9f9f9;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.03);
}

.article-comments h2 {
  font-size: 1.8rem;
  margin-bottom: 25px;
  color: #2c3e50;
  border-bottom: 2px solid #eaecef;
  padding-bottom: 12px;
  font-weight: 600;
}

.comment-list {
  display: flex;
  flex-direction: column;
  gap: 25px;
}

.comment-item {
  display: flex;
  gap: 20px;
  background-color: #ffffff;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.comment-item:hover {
  transform: translateY(-3px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
}

.comment-avatar {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  overflow: hidden;
  flex-shrink: 0;
  border: 3px solid #f0f0f0;
}

.comment-avatar img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.comment-avatar:hover img {
  transform: scale(1.1);
}

.comment-content {
  flex: 1;
}

.comment-author {
  font-weight: 600;
  margin-bottom: 8px;
  color: #2c3e50;
  font-size: 1.1rem;
}

.comment-text {
  line-height: 1.7;
  color: #4a5568;
  margin-bottom: 12px;
  font-size: 1rem;
}

.comment-meta {
  display: flex;
  gap: 20px;
  font-size: 0.9rem;
  color: #718096;
  align-items: center;
}

.comment-likes {
  display: flex;
  align-items: center;
  gap: 5px;
  transition: color 0.2s ease;
  cursor: pointer;
}

.comment-likes:hover {
  color: #e53e3e;
}

/* 相关文章样式优化 */
.related-articles {
  margin-top: 40px;
}

.related-articles h2 {
  font-size: 1.8rem;
  margin-bottom: 25px;
  color: #2c3e50;
  border-bottom: 2px solid #eaecef;
  padding-bottom: 12px;
  font-weight: 600;
}

.related-list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 25px;
}

.related-item {
  border-radius: 12px;
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
  background-color: #ffffff;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
}

.related-item:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.12);
}

.related-cover {
  height: 180px;
  overflow: hidden;
}

.related-cover img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.related-item:hover .related-cover img {
  transform: scale(1.08);
}

.related-info {
  padding: 18px;
}

.related-title {
  font-size: 1.1rem;
  margin-bottom: 12px;
  color: #2c3e50;
  font-weight: 600;
  line-height: 1.4;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
  height: 3em;
}

.related-meta {
  display: flex;
  justify-content: space-between;
  color: #718096;
  font-size: 0.9rem;
}

/* 响应式调整 */
@media (max-width: 768px) {
  .article-title {
    font-size: 2rem;
  }
  
  .article-cover {
    height: 300px;
  }
  
  .related-list {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 576px) {
  .article-detail-container {
    padding: 20px 15px;
  }
  
  .article-title {
    font-size: 1.8rem;
  }
  
  .article-cover {
    height: 250px;
  }
  
  .article-content {
    font-size: 1.05rem;
  }
  
  .related-list {
    grid-template-columns: 1fr;
  }
  
  .comment-avatar {
    width: 50px;
    height: 50px;
  }
}
  transform: scale(1.05);
}

.related-info {
  padding: 15px;
}

.related-title {
  font-size: 1.1rem;
  margin: 0 0 10px 0;
  color: #333;
  line-height: 1.4;
}

.related-meta {
  display: flex;
  justify-content: space-between;
  font-size: 0.85rem;
  color: #999;
}
  }
</style>