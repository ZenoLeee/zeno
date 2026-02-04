# GitHub Pages 部署指南

本指南将帮助你将 Zeno 项目部署到 GitHub Pages。

## 📋 前置要求

1. **GitHub 账户**
   - 访问 [github.com](https://github.com) 注册

2. **Git 安装**
   - 下载: [git-scm.com](https://git-scm.com/downloads)
   - 安装后打开 Git Bash（Windows）或终端（Mac/Linux）

3. **仓库准备**
   - 确保你的 GitHub 仓库名称为 `username.github.io` 或使用自定义路径

## 🚀 部署步骤

### 方法一：直接使用 GitHub Web 界面（推荐，最简单）

1. **上传文件到 GitHub**
   ```bash
   # 在 D:\zeno 目录下打开 Git Bash 或终端
   cd /d/zeno

   # 初始化 Git（如果还没有）
   git init

   # 添加所有文件
   git add .

   # 提交
   git commit -m "Initial commit: Add Zeno GitHub Pages"

   # 添加远程仓库（替换 yourusername）
   git remote add origin https://github.com/yourusername/zeno.git

   # 推送到 GitHub
   git push -u origin main
   ```

2. **启用 GitHub Pages**
   - 访问你的仓库: `https://github.com/yourusername/zeno`
   - 点击 **Settings** 标签
   - 在左侧菜单找到 **Pages**
   - 在 **Source** 下选择：
     - **Branch**: `main`
     - **Folder**: `/ (root)`
   - 点击 **Save**

3. **等待部署**
   - GitHub 会自动开始部署
   - 几分钟后访问: `https://yourusername.github.io/zeno`
   - 如果看到页面，部署成功！🎉

### 方法二：使用 GitHub CLI (gh)

1. **安装 GitHub CLI**
   - 下载: [cli.github.com](https://cli.github.com)
   - 安装后在终端运行: `gh auth login`

2. **创建并推送仓库**
   ```bash
   cd /d/zeno

   # 创建仓库并推送
   gh repo create zeno --public --source=. --remote=origin --push
   ```

3. **启用 GitHub Pages**
   - 按照方法一的步骤 2 操作

## 📁 文件结构

```
zeno/
├── .git/                    # Git 仓库
├── .gitignore              # Git 忽略文件
├── _config.yml             # Jekyll 配置
├── index.html              # 主页
├── README.md               # 项目说明
└── ProxyHub/               # ProxyHub 项目
    ├── index.html          # 项目展示页
    ├── privacy.html        # 中文隐私政策
    └── privacy_en.html     # 英文隐私政策
```

## ⚙️ _config.yml 配置说明

```yaml
title: Zeno                              # 网站标题
description: 开源项目展示                # 网站描述
url: "https://yourusername.github.io"   # 你的 GitHub Pages URL
baseurl: "/zeno"                         # 仓库名称
lang: zh_CN                              # 默认语言
theme: minima                            # Jekyll 主题（可选）
```

**重要**: 部署前需要修改：
- `yourusername` → 你的 GitHub 用户名
- 其他个人信息

## 🔧 自定义域名（可选）

如果你有自己的域名：

1. **在域名提供商处添加 DNS 记录**
   ```
   类型: CNAME
   名称: www（或 zeno）
   值: yourusername.github.io
   ```

2. **在 GitHub 仓库设置中**
   - 进入 Settings → Pages
   - 在 **Custom domain** 输入你的域名
   - 点击 **Save**

3. **等待 DNS 传播**（最多 48 小时）

## 📱 访问你的网站

部署成功后，可以通过以下地址访问：

- **主域名**: `https://yourusername.github.io/zeno`
- **ProxyHub 页面**: `https://yourusername.github.io/zeno/ProxyHub/`
- **隐私政策**: `https://yourusername.github.io/zeno/ProxyHub/privacy_en.html`

## 🔄 更新网站

当需要更新网站时：

```bash
cd /d/zeno

# 修改文件后
git add .
git commit -m "Update: 描述你的更改"
git push
```

GitHub Pages 会自动重新部署！

## ❓ 常见问题

### Q: 部署后显示 404 错误
**A**: 检查以下几点：
1. 确认仓库名称是否正确
2. 确认 Pages 设置中的分支是否为 `main`
3. 等待几分钟再刷新（有时需要时间）

### Q: 样式显示不正常
**A**: 确保 `_config.yml` 中的 `baseurl` 设置正确，应该是 `/zeno`

### Q: 如何撤销部署？
**A**: 在仓库 Settings → Pages 中点击 **Disable**，或删除 `gh-pages` 分支

### Q: 支持自定义主题吗？
**A**: 支持所有 Jekyll 主题，也可以完全自定义 CSS（我们使用了自定义 CSS）

## 📚 相关资源

- [GitHub Pages 官方文档](https://docs.github.com/en/pages)
- [Jekyll 官方文档](https://jekyllrb.com/docs/)
- [GitHub Pages 设置指南](https://pages.github.com/settings/)

## ✅ 部署检查清单

- [ ] 已修改 `_config.yml` 中的 `yourusername`
- [ ] 已修改 `README.md` 中的个人信息
- [ ] 已修改 `index.html` 中的 GitHub 链接
- [ ] 已修改 `ProxyHub/index.html` 中的链接
- [ ] Git 仓库已初始化
- [ ] 文件已推送到 GitHub
- [ ] GitHub Pages 已启用
- [ ] 网站可以正常访问

---

**祝你部署成功！🎉**

如有问题，请查看 [GitHub Pages 文档](https://docs.github.com/en/pages) 或提交 Issue。
