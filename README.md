# 旭明眼科診所 — Blogger → Jekyll / GitHub Pages

來源：2026-11-17 Google Takeout 中「旭明眼科診所」的 Blogger 公開文章。

## 完整性
- Blogger 的 `feed.atom` 共 93 筆 POST，其中已發布 88 篇，草稿 5 篇。
- **88 篇已發布文章全部轉為 `_posts/`；原始 URL 以 `permalink` 保留。**
- 草稿、Blogger 帳號設定、其他部落格及未確認的照片都**沒有**放到這個公開網站。
- 可唯一核對來源檔名的照片已放入 `assets/blogger-images/`；無法可靠配對者暫時使用原 Blogger 圖片 URL。詳細列表請參閱獨立交付的 `sgeyeclinic-migration-report.zip`。

## GitHub Pages 發布
1. 將**本目錄內所有內容**上傳到 `jacksonlei-eyedoc/sgeyeclinic-website` Repo 根目錄。大量檔案請使用 GitHub Desktop。
2. 到 Repository `Settings > Pages` 設定 `Deploy from a branch`、`main`、`/(root)`。
3. 先使用 `https://jacksonlei-eyedoc.github.io/sgeyeclinic-website/` 檢查文章、圖片、內部連結、手機版。
4. 暫不變更原站 DNS。此專案已設定 `preview_mode: true` 及 `robots.txt` 禁止搜尋引擎索引測試站。

## 改成正式網域（*測試全部通過後*）
1. 修改 `_config.yml`：
   - `url: "https://www.sgeyeclinic.com"`
   - `baseurl: ""`
   - `preview_mode: false`
2. 將 `robots.txt` 改為允許搜尋引擎索引，並保留 sitemap 路徑。
3. GitHub Pages 的 Custom domain 設定 `www.sgeyeclinic.com`，依 GitHub 文件更新 DNS CNAME。視需要處理根網域 `sgeyeclinic.com`。
4. 完成 HTTPS、內部連結、舊文章 URL、行動版、404、Search Console 與圖片檢查，再考慮下架 Blogger。

## 本機 Jekyll 預覽（需 Ruby）
```bash
bundle install
bundle exec jekyll serve
```
預設專案站 `baseurl` 在本機也會保留；若本機要用根目錄預覽，可執行：
```bash
bundle exec jekyll serve --baseurl ""
```
打開 http://127.0.0.1:4000/ 。

## 維護
- 新文章放在 `_posts/YYYY-MM-DD-title.md`；front matter 指定 `layout: post`。
- 文章的 `permalink` 已保留原 Blogger 文章年月網址。
- 頁首、頁尾：`_layouts/default.html`；內頁：`_layouts/post.html`。
- CSS：`assets/css/site.css`；搜尋和手機導覽：`assets/js/site.js`。

## 需人工覆核
- 幾篇 Blogger 已發布文章原標題留白，已從正文中擷取公告標題作為顯示名稱。
- 門診時間及掛號規則取自原文歷史備份，正式上線前務必再由診所確認。
- 部分圖片僅存 Blogger 遠端網址；原站若移除，其圖片可能失效。
- Blogger 的留言、內建搜尋、樣板動態小工具不會以原方式運作；本網站另提供靜態文章搜尋篩選。
- 不公開任何私人資料，包括草稿、Blogger 帳號設定與備份中的其他網誌。
