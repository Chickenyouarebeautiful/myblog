---
title: "第一次搭建hugo程序到发布第一篇文章"
description: 
date: 2025-09-08T12:09:33+08:00
tags: ["健忘症"]
categories: ["搭建"]
image: 
math: 
license: 
hidden: false
comments: true
draft: false
---

# 从第一次搭建hugo程序到发布第一篇文章


托管到 **Github** 仓库和部署到 **cloudflare Pages** 

## 1. 准备工作

- [Hugo 官方 GitHub 仓库](https://github.com/gohugoio/hugo)
- [Git 官方下载页面](https://git-scm.com/downloads)

## 2. 创建 Hugo 项目
1. **下载 Hugo**
   - 选择 **Windows x64 版本** 下载，会得到一个压缩包  
   - 解压后，将 `Hugo.exe` 的文件路径添加到系统环境变量，方便后续操作  

2. **选择项目地址**
   - 本例使用桌面路径：
     ```
     C:\Users\yourname\Desktop\
     ```

3. **创建 Hugo 项目**
   - 打开 CMD，进入桌面目录：
     ```cmd
     cd C:\Users\yourname\Desktop\
     hugo new site mysite
     cd mysite
     ```


## 3. 安装 Stack 主题
1. **下载主题**
    - [hugo-theme-stack](https://github.com/CaiJimmy/hugo-theme-stack)
   - 可以选择在 GitHub 作者的项目地址下载并解压到：
     ```
     mysite/themes/
     ```
   - 如果安装了 Git，可以直接使用命令：
     ```bash
     git clone https://github.com/CaiJimmy/hugo-theme-stack.git themes/hugo-theme-stack
     ```

2. **使用演示站点**
   - 作者提供了 `exampleSite` 作为演示，路径在：
     ```
     themes/hugo-theme-stack/exampleSite
     ```
   - 将依赖文件覆盖到 `mysite`，包括：
     ```
     assets/ | images/ | config.yaml | hugo.yaml | ... 等等
     ```

3. **配置启动文件 `hugo.yaml`**
   ```yaml
   baseurl: https://yourwebsitedomain   # 网站地址
   languageCode: zh-cn                  # 语言
   theme: hugo-theme-stack              # 主题
   title: Example Site                  # 网站标题
   copyright: 林的小别野               # 版权信息
    ```
## 4. 添加第一篇文章
1. **发布第一篇文章**
    - 启动本地预览
    ```cmd
    hugo server -D
    ```
    - 如果能看到网站正常运行,我们就来发布第一篇文章
    - 关闭server服务
    ```cmd
    ctrl+c
    ```
    - 他会自动创建一篇文章
    - 接下来可以找到'content/post/'我的第一篇文章'/index.md'进行编辑
    ```cmd
    hugo new content/post/我的第一篇文章/index.md
    ```


## 5. 上传到 GitHub
1. *初始化仓库*
    ```
    git init
    git add .
    git commit -m "Initial commit"
    ```
2. *添加远程仓库*
    ```
    git remote add origin https://github.com/username/my_blog.git
    ```

3. *如果已经存在 origin，使用*
    ```
    git remote set-url origin https://github.com/username/my_blog.git
    ```
3. *如果远程仓库非空，先强制推送覆盖*
    ```
    git push -u origin main --force
    ```
4. *后续托管仓库*
    ```
    git add .
    git commit -m "Add new post"
    git push origin main
    ```



## 5. 部署到 Cloudflare Pages
1. **登录 Cloudflare Pages**  
   - 点击 **Create a project** → 选择你的 **GitHub 仓库**

2. **配置项目**  

| 设置项                | 配置值                                   |
|----------------------|----------------------------------------|
| Production branch     | main                                   |
| Framework preset      | Hugo                                   |
| Hugo version          | Extended 版本（和本地一致）           |
| Build command         | `hugo --gc --minify`                   |
| Build output directory| `public`                                |

> ⚠️ 确保主分支包含 `themes/hugo-theme-stack` 或使用 **Hugo Modules**。

3. **部署项目**
   - 点击 **Save and Deploy**  
   - 部署完成后，会得到一个 `*.pages.dev` 域名

4. **可选步骤：添加自定义域名**
   - 在 Cloudflare Pages 设置自定义域名  
   - 配置对应的 DNS 解析


## 6. 后续更新

1. **切换到项目文件**
    ```
    cd \yourproject\
    ````
2. **发布一篇文章**
    ```
    hugo new content/post/articletitle/index.md

    git add.        # 把整个工作目录（当前目录及子目录）所有 已修改或新增的文件 都加入 Git 暂存区
    git add content/posts/my-new-post/   # 把整个文章路径加入 Git 暂存区
    git add content/posts/my-new-post/articletitle\index.md # 把整个文章加入 Git 暂存区
    ```
    - 注意 单独把文章加入暂存区需要把文章依赖的图片等资源也加进去
    ```
    git add content/posts/my-new-post/index.md
    git commit -m "发布新文章：我的新文章"
    git push origin main
    ```
