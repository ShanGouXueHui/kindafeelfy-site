# kindafeelfy 官网交接记录

## 当前定位
`kindafeelfy-site` 是 `kindafeelfy.cn` 的官网静态站仓库。
当前用于：
- 官网品牌展示
- ICP 备案承接页
- 关于 / 服务 / 隐私页面

`kindafeelfy-nolly` 仍是后台业务系统仓库，不与本仓库合并。

## 当前线上信息
- 域名：`kindafeelfy.cn` / `www.kindafeelfy.cn`
- 服务器：`47.97.245.200`
- Nginx 配置：`/etc/nginx/sites-available/kindafeelfy`
- Nginx 生效链接：`/etc/nginx/sites-enabled/kindafeelfy`
- 线上站点目录：`/var/www/kindafeelfy`
- 当前源码目录：`/home/deploy/projects/kindafeelfy-site`

## ICP 备案信息
- 主体备案号：`琼ICP备2026004428号`
- 网站备案号：`琼ICP备2026004428号-1`

前台页脚当前应展示：
- `琼ICP备2026004428号-1`
并链接到：
- `https://beian.miit.gov.cn/`

## 本次已完成修正
1. 删除旧文案 `ICP备案号：备案中`
2. 新增正式备案号 `琼ICP备2026004428号-1`
3. about / service / privacy 三个页面移除顶部过大的 logo
4. 清理了 nginx 历史备份站点配置，避免重复 `server_name`
5. 官网部署时改为排除 `.git`

## 当前部署命令
```bash
rsync -av --delete --exclude '.git' /home/deploy/projects/kindafeelfy-site/ /var/www/kindafeelfy/
nginx -t && systemctl reload nginx

后续合并建议
当前不合并kindafeelfy-site和kindafeelfy-nolly。
等kindafeelfy-nolly的前台、登录、支付、HTTPS、管理认证都成熟后，
再考虑把官网品牌页、会员页、登录页、支付页统一到新的前端工程中。
关键提交
78333b5fix(site): remove oversized subpage header logo
cb9557efix(site): replace pending filing text with official ICP number
742a35echore(site): add ICP filing footer
