<script setup lang="ts">
// 无需额外的逻辑
</script>

<template>
  <div class="about-container">
    <div class="about-header">
      <div class="avatar">
        <img src="https://picsum.photos/id/1005/200/200" alt="博主头像">
      </div>
      <h1>关于我</h1>
      <p class="bio">全栈开发工程师 | 技术博主 | 开源爱好者</p>
    </div>
    
    <div class="about-content">
      <section class="about-section">
        <h2>个人简介</h2>
        <p>你好！我是一名热爱技术的全栈开发工程师，拥有5年的Web开发经验。我热衷于学习新技术，并通过这个博客分享我的学习心得和技术经验。</p>
        <p>我相信技术可以改变世界，而分享知识可以让这种改变更加深远。希望我的博客文章能够帮助到更多的开发者。</p>
      </section>
      
      <section class="about-section">
        <h2>技能专长</h2>
        <div class="skills">
          <div class="skill-category">
            <h3>前端开发</h3>
            <ul>
              <li>HTML5 / CSS3 / JavaScript</li>
              <li>Vue.js / React</li>
              <li>TypeScript</li>
              <li>响应式设计</li>
            </ul>
          </div>
          <div class="skill-category">
            <h3>后端开发</h3>
            <ul>
              <li>Java / Spring Boot</li>
              <li>Node.js / Express</li>
              <li>RESTful API设计</li>
              <li>数据库设计</li>
            </ul>
          </div>
          <div class="skill-category">
            <h3>DevOps</h3>
            <ul>
              <li>Git / GitHub</li>
              <li>Docker</li>
              <li>CI/CD</li>
              <li>云服务部署</li>
            </ul>
          </div>
        </div>
      </section>
      
      <section class="about-section">
        <h2>工作经历</h2>
        <div class="experience">
          <div class="experience-item">
            <div class="experience-header">
              <h3>高级全栈开发工程师</h3>
              <span class="experience-date">2021年至今</span>
            </div>
            <p class="experience-company">科技创新有限公司</p>
            <p>负责公司核心产品的前后端开发，优化用户体验和系统性能，参与技术架构设计和团队管理。</p>
          </div>
          <div class="experience-item">
            <div class="experience-header">
              <h3>Web开发工程师</h3>
              <span class="experience-date">2018年 - 2021年</span>
            </div>
            <p class="experience-company">互联网科技有限公司</p>
            <p>参与多个Web应用项目的开发，负责前端界面实现和后端API开发，以及数据库设计和维护。</p>
          </div>
        </div>
      </section>
      
      <section class="about-section">
        <h2>联系方式</h2>
        <div class="contact-info">
          <p><strong>邮箱：</strong> example@email.com</p>
          <p><strong>GitHub：</strong> <a href="https://github.com/yourusername" target="_blank">github.com/yourusername</a></p>
          <p><strong>LinkedIn：</strong> <a href="https://linkedin.com/in/yourprofile" target="_blank">linkedin.com/in/yourprofile</a></p>
        </div>
      </section>
    </div>
  </div>
</template>

<style scoped>
.about-container {
  max-width: 900px;
  margin: 0 auto;
  padding: 20px;
}

.about-header {
  text-align: center;
  margin-bottom: 40px;
}

.avatar {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  overflow: hidden;
  margin: 0 auto 20px;
  border: 3px solid #1890ff;
}

.avatar img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.about-header h1 {
  font-size: 2.2rem;
  color: #333;
  margin-bottom: 10px;
}

.bio {
  font-size: 1.2rem;
  color: #666;
}

.about-section {
  margin-bottom: 40px;
  background-color: #fff;
  padding: 25px;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
}

.about-section h2 {
  font-size: 1.6rem;
  color: #333;
  margin-bottom: 20px;
  padding-bottom: 10px;
  border-bottom: 1px solid #eee;
}

.about-section p {
  font-size: 1.05rem;
  line-height: 1.7;
  color: #444;
  margin-bottom: 15px;
}

.skills {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 20px;
}

.skill-category h3 {
  font-size: 1.2rem;
  color: #1890ff;
  margin-bottom: 10px;
}

.skill-category ul {
  list-style-type: none;
  padding: 0;
}

.skill-category li {
  padding: 5px 0;
  color: #555;
}

.experience-item {
  margin-bottom: 25px;
}

.experience-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 5px;
}

.experience-header h3 {
  font-size: 1.2rem;
  color: #333;
  margin: 0;
}

.experience-date {
  color: #888;
  font-size: 0.9rem;
}

.experience-company {
  color: #1890ff;
  font-weight: 500;
  margin-bottom: 8px;
}

.contact-info p {
  margin-bottom: 10px;
}

.contact-info a {
  color: #1890ff;
  text-decoration: none;
}

.contact-info a:hover {
  text-decoration: underline;
}

@media (max-width: 768px) {
  .skills {
    grid-template-columns: 1fr;
  }
  
  .experience-header {
    flex-direction: column;
    align-items: flex-start;
  }
  
  .experience-date {
    margin-top: 5px;
  }
}
</style>