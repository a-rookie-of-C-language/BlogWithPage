# 个人技术博客

这是一个使用Vue 3、TypeScript和Vite构建的个人技术博客项目，并通过GitHub Pages进行部署。

## 项目结构

- `blog-frontend/`: 前端Vue应用

## 部署到GitHub Pages

本项目已配置GitHub Actions自动部署流程，只需按照以下步骤操作：

1. 在GitHub上创建一个新的仓库，命名为`blogWithPage`

2. 将本地代码推送到GitHub仓库：

```bash
# 初始化Git仓库（如果尚未初始化）
git init

# 添加远程仓库
git remote add origin https://github.com/你的用户名/blogWithPage.git

# 添加所有文件
git add .

# 提交更改
git commit -m "初始提交"

# 推送到GitHub
git push -u origin main
```

3. 在GitHub仓库设置中启用GitHub Pages：
   - 进入仓库的Settings > Pages
   - Source选择"GitHub Actions"

4. 等待GitHub Actions工作流完成构建和部署

5. 部署完成后，您的博客将可以通过以下URL访问：
   `https://你的用户名.github.io/blogWithPage/`

## 本地开发

```bash
# 进入前端目录
cd blog-frontend

# 安装依赖
npm install

# 启动开发服务器
npm run dev

# 构建生产版本
npm run build
```

## 技术栈

- Vue 3
- TypeScript
- Vite
- Vue Router
- Element Plus
- Marked (Markdown解析)