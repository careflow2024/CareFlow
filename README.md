# CareFlow 静态站点

App 内「关于我们」「隐私政策」「用户协议」对应的公开页面，部署到 **https://careflow.sionstudio.xyz**。

源码同步发布到独立仓库：[careflow2024/CareFlow](https://github.com/careflow2024/CareFlow)

## 目录结构

```
index.html          → /
about/index.html    → /about/
privacy/index.html  → /privacy/
terms/index.html    → /terms/
styles.css
CNAME               → 自定义域名 careflow.sionstudio.xyz
```

## 发布到 GitHub Pages

在 `website/` 目录执行（需有 `careflow2024/CareFlow` 仓库写权限）：

```bash
./deploy.sh
```

或手动：

```bash
git clone git@github.com:careflow2024/CareFlow.git /tmp/careflow-website
rsync -av --delete --exclude deploy.sh --exclude README.md \
  ./ /tmp/careflow-website/
cp README.md /tmp/careflow-website/
cd /tmp/careflow-website
git add -A && git commit -m "Update site" && git push
```

### 首次启用 Pages

1. 打开 [Settings → Pages](https://github.com/careflow2024/CareFlow/settings/pages)
2. **Source**: Deploy from a branch → `main` / `/ (root)`
3. **Custom domain**: `careflow.sionstudio.xyz`
4. DNS 生效后勾选 **Enforce HTTPS**

### Cloudflare DNS

```
careflow  CNAME  careflow2024.github.io
```

### 验证

- https://careflow.sionstudio.xyz/privacy
- https://careflow.sionstudio.xyz/terms
- https://careflow.sionstudio.xyz/about

App Store / Google Play 隐私政策 URL：**https://careflow.sionstudio.xyz/privacy**

## 本地预览

```bash
cd website && python3 -m http.server 8080
```

App 内链接定义在 `shared/.../platform/ExternalUri.kt` 的 `LegalUrls` 对象中。
