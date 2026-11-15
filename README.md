# 六级练习室

这是一个可部署到 GitHub Pages 的静态 CET-6 练习网站。在线答题、计时、标词和练习记录保存在访问者自己的浏览器中，不需要服务器或数据库。

## 文件结构

- `index.html`：网站入口
- `assets/papers/`：6 套真题与答案 PDF
- `site-data/papers/index.json`：题库目录
- `.github/workflows/deploy-pages.yml`：GitHub Pages 自动部署工作流

题库当前包含 2025 年 6 月与 2026 年 6 月各三套试卷。PDF 是否可以公开传播，请先确认相应授权。

## 在线答题说明

- 开始试卷后，可用题目上方的分区按钮切换写作、听力、阅读和翻译；按钮会显示各部分已答数量。选择题可直接点击选项，匹配题输入段落字母，写作与翻译使用文本框，阅读选词填空每空选一个词库字母且词项不可重复。
- 题目和参考答案以可读文本提取结果为基础。由于部分 PDF 文本提取不完整，少数选项残缺的题会要求对照原卷输入 A-D，并标为不参与自动判分；没有可靠答案键的题目会显示待核验，不会猜测判分。
- 写作、翻译等主观题可在线输入并暂存，但网站不会自动评价作文或翻译质量。听力练习需要另行播放原始音频；当前随包提供试卷和答案 PDF，不包含音频。
- 答题进度与生词保存在用户自己的浏览器本地，不会跨设备同步。标词词典未收录的词会显示“释义待补充”。

## 用 GitHub 网页创建新仓库并发布

1. 登录 GitHub，点击右上角 `+`，选择 **New repository**。
2. 输入仓库名称，例如 `cet6-practice`。
3. 选择 **Public**（让所有人可以访问源代码及相关文件）。README、`.gitignore`、License 可先不勾选，点击 **Create repository**。
4. 在新仓库首页点击 **Add file → Upload files**。
5. 在电脑文件管理器中打开本发布目录的内容，将其中所有文件与文件夹拖进上传区域。必须保留 `.github` 隐藏目录以及 `assets`、`site-data` 目录结构。
6. 确认待提交文件列表中包含 `index.html`、`.github/workflows/deploy-pages.yml`、`assets/papers/` 与 `site-data/papers/index.json`。
7. 页面底部填写提交说明，例如 `Publish CET-6 practice website`，选择提交到 `main`，点击 **Commit changes**。
8. 打开仓库 **Settings → Pages**，在 **Build and deployment → Source** 选择 **GitHub Actions**。
9. 打开 **Actions**，进入 `Deploy CET-6 Practice` 工作流，等待最新运行显示绿色成功标记。
10. 部署完成后，在 **Settings → Pages** 页面打开 `Your site is live at ...` 显示的公开地址。

## 验收

- 首页可以正常打开，试卷目录应显示 6 套试卷。
- 分别打开原卷 PDF 和答案 PDF，确认可以查看。
- 开始一套练习，确认所有考试部分都能切换；选择题、段落匹配、选词填空和主观题输入可用，答题进度可以暂存。
- 完成交卷后，核对自动判分范围及本次生词表；答案待核验或选项残缺的题不应被错误判分。

若工作流报错，打开 **Actions → 对应运行 → deploy** 查看第一个红色步骤及日志。此工作流从仓库根目录 `.` 上传，`index.html` 必须位于根目录而非额外的子文件夹内。
