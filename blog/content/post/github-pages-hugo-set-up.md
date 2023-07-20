---
title: "利用Github Pages和Hugo搭建个人博客"
date: 2023-07-20T16:09:01+08:00
draft: false
---

# Hugo 是由 Go 语言实现的静态网站生成器。简单、易用、高效、易扩展、快速部署。  
![1](/img/hugo-logo-wide.png)  
# 安装 hugo  
你可以在此处下载  
```
https://github.com/gohugoio/hugo/releases
```  
将hugo目录添加到系统环境变量  
确认 hugo 安装是否成功  
```
hugo version
hugo v0.110.0-e32a493b7826d02763c3b79623952e625402b168+extended windows/amd64 BuildDate=2023-01-17T12:16:09Z VendorInfo=gohugoio
```  
# 初始化网站目录  
安装好之后，便可以初始化一个 hugo 项目  
```
hugo new site blog
```  
# 下载一个 hugo 主题  
hugo 主题可以理解为是一种网站样式，你可以在该页面
```
https://themes.gohugo.io/
```
选择自己心仪的 hugo 主题。本站目前使用的是even  
```
https://github.com/olOwOlo/hugo-theme-even
```  
进入网站根目录，下载 hugo 主题  
```
git clone https://github.com/olOwOlo/hugo-theme-even themes/even
```  
编辑站点目录下配置文件config.toml  
```
baseURL = "https://alphaokxyz.github.io/"
languageCode = "zh-cn"
defaultContentLanguage = "zh-cn"                             # en / zh-cn / ... (This field determines which i18n file to use)
title = "Alphaokxyz's Blog"
preserveTaxonomyNames = true
enableRobotsTXT = true
enableEmoji = true
theme = "even"
enableGitInfo = false # use git commit log to generate lastmod record # 可根据 Git 中的提交生成最近更新记录。

# Syntax highlighting by Chroma. NOTE: Don't enable `highlightInClient` and `chroma` at the same time!
pygmentsOptions = "linenos=table"
pygmentsCodefences = true
pygmentsUseClasses = true
pygmentsCodefencesGuessSyntax = true

hasCJKLanguage = true     # has chinese/japanese/korean ? # 自动检测是否包含 中文\日文\韩文
paginate = 5                                              # 首页每页显示的文章数
disqusShortname = ""      # disqus_shortname
googleAnalytics = ""      # UA-XXXXXXXX-X
copyright = ""            # default: author.name ↓        # 默认为下面配置的author.name ↓

[author]                  # essential                     # 必需
  name = "Alphaokxyz"

[sitemap]                 # essential                     # 必需
  changefreq = "weekly"
  priority = 0.5
  filename = "sitemap.xml"

[[menu.main]]             # config your menu              # 配置目录
  name = "主页"
  weight = 10
  identifier = "home"
  url = "/"
[[menu.main]]
  name = "归档"
  weight = 20
  identifier = "archives"
  url = "/post/"

[params]
  version = "4.x"           # Used to give a friendly message when you have an incompatible update
  debug = false             # If true, load `eruda.min.js`. See https://github.com/liriliri/eruda

  since = "2023"            # Site creation time          # 站点建立时间
  # use public git repo url to link lastmod git commit, enableGitInfo should be true.
  # 指定 git 仓库地址，可以生成指向最近更新的 git commit 的链接，需要将 enableGitInfo 设置成 true.
  gitRepo = ""

  # site info (optional)                                  # 站点信息（可选，不需要的可以直接注释掉）
  #logoTitle = "Even"        # default: the title value    # 默认值: 上面设置的title值
  keywords = ["Hugo", "theme","even"]
  description = "Alphaokxyz's Blog."

  # paginate of archives, tags and categories             # 归档、标签、分类每页显示的文章数目，建议修改为一个较大的值
  archivePaginate = 50

  # show 'xx Posts In Total' in archive page ?            # 是否在归档页显示文章的总数
  showArchiveCount = true

  # The date format to use; for a list of valid formats, see https://gohugo.io/functions/format/
  dateFormatToUse = "2006-01-02"

  # show word count and read time ?                       # 是否显示字数统计与阅读时间
  moreMeta = false

  # Syntax highlighting by highlight.js
  highlightInClient = false

  # 一些全局开关，你也可以在每一篇内容的 front matter 中针对单篇内容关闭或开启某些功能，在 archetypes/default.md 查看更多信息。
  # Some global options, you can also close or open something in front matter for a single post, see more information from `archetypes/default.md`.
  toc = false                                                                            # 是否开启目录
  autoCollapseToc = false   # Auto expand and collapse toc                              # 目录自动展开/折叠
  fancybox = true           # see https://github.com/fancyapps/fancybox                 # 是否启用fancybox（图片可点击）

  # mathjax
  mathjax = false           # see https://www.mathjax.org/                              # 是否使用mathjax（数学公式）
  mathjaxEnableSingleDollar = false                                                     # 是否使用 $...$ 即可進行inline latex渲染
  mathjaxEnableAutoNumber = false                                                       # 是否使用公式自动编号
  mathjaxUseLocalFiles = false  # You should install mathjax in `your-site/static/lib/mathjax`

  postMetaInFooter = false   # contain author, lastMod, markdown link, license           # 包含作者，上次修改时间，markdown链接，许可信息
  linkToMarkDown = false    # Only effective when hugo will output .md files.           # 链接到markdown原始文件（仅当允许hugo生成markdown文件时有效）
  contentCopyright = ''     # e.g. '<a rel="license noopener" href="https://creativecommons.org/licenses/by-nc-nd/4.0/" target="_blank">CC BY-NC-ND 4.0</a>'

  changyanAppid = ""        # Changyan app id             # 畅言
  changyanAppkey = ""       # Changyan app key

  livereUID = ""            # LiveRe UID                  # 来必力

  baiduPush = false        # baidu push                  # 百度
  baiduAnalytics = ""      # Baidu Analytics
  baiduVerification = ""   # Baidu Verification
  googleVerification = ""  # Google Verification         # 谷歌

  # Link custom CSS and JS assets
  #   (relative to /static/css and /static/js respectively)
  customCSS = []
  customJS = []

  uglyURLs = false          # please keep same with uglyurls setting

  # Show language selector for multilingual site.
  showLanguageSelector = false

  [params.publicCDN]        # load these files from public cdn                          # 启用公共CDN，需自行定义
    enable = false
    jquery = '<script src="https://cdn.jsdelivr.net/npm/jquery@3.2.1/dist/jquery.min.js" integrity="sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4=" crossorigin="anonymous"></script>'
    slideout = '<script src="https://cdn.jsdelivr.net/npm/slideout@1.0.1/dist/slideout.min.js" integrity="sha256-t+zJ/g8/KXIJMjSVQdnibt4dlaDxc9zXr/9oNPeWqdg=" crossorigin="anonymous"></script>'
    fancyboxJS = '<script src="https://cdn.jsdelivr.net/npm/@fancyapps/fancybox@3.1.20/dist/jquery.fancybox.min.js" integrity="sha256-XVLffZaxoWfGUEbdzuLi7pwaUJv1cecsQJQqGLe7axY=" crossorigin="anonymous"></script>'
    fancyboxCSS = '<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fancyapps/fancybox@3.1.20/dist/jquery.fancybox.min.css" integrity="sha256-7TyXnr2YU040zfSP+rEcz29ggW4j56/ujTPwjMzyqFY=" crossorigin="anonymous">'
    timeagoJS = '<script src="https://cdn.jsdelivr.net/npm/timeago.js@3.0.2/dist/timeago.min.js" integrity="sha256-jwCP0NAdCBloaIWTWHmW4i3snUNMHUNO+jr9rYd2iOI=" crossorigin="anonymous"></script>'
    timeagoLocalesJS = '<script src="https://cdn.jsdelivr.net/npm/timeago.js@3.0.2/dist/timeago.locales.min.js" integrity="sha256-ZwofwC1Lf/faQCzN7nZtfijVV6hSwxjQMwXL4gn9qU8=" crossorigin="anonymous"></script>'
    flowchartDiagramsJS = '<script src="https://cdn.jsdelivr.net/npm/raphael@2.2.7/raphael.min.js" integrity="sha256-67By+NpOtm9ka1R6xpUefeGOY8kWWHHRAKlvaTJ7ONI=" crossorigin="anonymous"></script> <script src="https://cdn.jsdelivr.net/npm/flowchart.js@1.8.0/release/flowchart.min.js" integrity="sha256-zNGWjubXoY6rb5MnmpBNefO0RgoVYfle9p0tvOQM+6k=" crossorigin="anonymous"></script>'
    sequenceDiagramsCSS = '<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/bramp/js-sequence-diagrams@2.0.1/dist/sequence-diagram-min.css" integrity="sha384-6QbLKJMz5dS3adWSeINZe74uSydBGFbnzaAYmp+tKyq60S7H2p6V7g1TysM5lAaF" crossorigin="anonymous">'
    sequenceDiagramsJS = '<script src="https://cdn.jsdelivr.net/npm/webfontloader@1.6.28/webfontloader.js" integrity="sha256-4O4pS1SH31ZqrSO2A/2QJTVjTPqVe+jnYgOWUVr7EEc=" crossorigin="anonymous"></script> <script src="https://cdn.jsdelivr.net/npm/snapsvg@0.5.1/dist/snap.svg-min.js" integrity="sha256-oI+elz+sIm+jpn8F/qEspKoKveTc5uKeFHNNVexe6d8=" crossorigin="anonymous"></script> <script src="https://cdn.jsdelivr.net/npm/underscore@1.8.3/underscore-min.js" integrity="sha256-obZACiHd7gkOk9iIL/pimWMTJ4W/pBsKu+oZnSeBIek=" crossorigin="anonymous"></script> <script src="https://cdn.jsdelivr.net/gh/bramp/js-sequence-diagrams@2.0.1/dist/sequence-diagram-min.js" integrity="sha384-8748Vn52gHJYJI0XEuPB2QlPVNUkJlJn9tHqKec6J3q2r9l8fvRxrgn/E5ZHV0sP" crossorigin="anonymous"></script>'

  # Display a message at the beginning of an article to warn the readers that it's content may be outdated.
  # 在文章开头显示提示信息，提醒读者文章内容可能过时。
  [params.outdatedInfoWarning]
    enable = false
    hint = 30               # Display hint if the last modified time is more than these days ago.    # 如果文章最后更新于这天数之前，显示提醒
    warn = 180              # Display warning if the last modified time is more than these days ago.    # 如果文章最后更新于这天数之前，显示警告

  [params.gitment]          # Gitment is a comment system based on GitHub issues. see https://github.com/imsun/gitment
    owner = ""              # Your GitHub ID
    repo = ""               # The repo to store comments
    clientId = ""           # Your client ID
    clientSecret = ""       # Your client secret

  [params.utterances]       # https://utteranc.es/
    owner = ""              # Your GitHub ID
    repo = ""               # The repo to store comments

  [params.gitalk]           # Gitalk is a comment system based on GitHub issues. see https://github.com/gitalk/gitalk
    owner = ""              # Your GitHub ID
    repo = ""               # The repo to store comments
    clientId = ""           # Your client ID
    clientSecret = ""       # Your client secret

  # Valine.
  # You can get your appid and appkey from https://leancloud.cn
  # more info please open https://valine.js.org
  [params.valine]
    enable = false
    appId = '你的appId'
    appKey = '你的appKey'
    notify = false  # mail notifier , https://github.com/xCss/Valine/wiki
    verify = false # Verification code
    avatar = 'mm'
    placeholder = '说点什么吧...'
    visitor = false

  [params.flowchartDiagrams]# see https://blog.olowolo.com/example-site/post/js-flowchart-diagrams/
    enable = false
    options = ""

  [params.sequenceDiagrams] # see https://blog.olowolo.com/example-site/post/js-sequence-diagrams/
    enable = false
    options = ""            # default: "{theme: 'simple'}"

  [params.busuanzi]         # count web traffic by busuanzi                             # 是否使用不蒜子统计站点访问量
    enable = true
    siteUV = false
    sitePV = true
    pagePV = true

  [params.reward]                                         # 文章打赏
    enable = false
    wechat = "/path/to/your/wechat-qr-code.png"           # 微信二维码
    alipay = "/path/to/your/alipay-qr-code.png"           # 支付宝二维码

  [params.social]                                         # 社交链接
    
    g-github = "https://alphaokxyz.github.io/"
    

# See https://gohugo.io/about/hugo-and-gdpr/
[privacy]
  [privacy.googleAnalytics]
    anonymizeIP = true      # 12.214.31.144 -> 12.214.31.0
  [privacy.youtube]
    privacyEnhanced = true

# see https://gohugo.io/getting-started/configuration-markup
[markup]
  [markup.tableOfContents]
    startLevel = 1
  [markup.goldmark.renderer]
    unsafe = true

# 将下面这段配置取消注释可以使 hugo 生成 .md 文件
# Uncomment these options to make hugo output .md files.
#[mediaTypes]
#  [mediaTypes."text/plain"]
#    suffixes = ["md"]
#
#[outputFormats.MarkDown]
#  mediaType = "text/plain"
#  isPlainText = true
#  isHTML = false
#
#[outputs]
#  home = ["HTML", "RSS"]
#  page = ["HTML", "MarkDown"]
#  section = ["HTML", "RSS"]
#  taxonomy = ["HTML", "RSS"]
#  taxonomyTerm = ["HTML"]
```  
# 添加about页面  
在/content目录下新建about.md文件  
```
---
title: "关于"
date: 2023-07-20T15:52:29+08:00
menu: "main"
weight: 50

---

荣誉

刊登于《Linux Magazine》

网路名人堂

2012年4月23日，进入网际网路协会的网路名人堂。

千禧技术奖

2012年4月20日，获得当年的千禧技术奖。该奖被普遍形容为相当于在技术领域的诺贝尔奖。

学术

在1997年，在芬兰赫尔辛基大学计算机科学系，接受了硕士学位（Laudatur级）。两年后，在斯德哥尔摩大学接受名誉博士学位，并在2000年在母校获得了同样的荣誉。

在2005年8月，获得里德学院的霍华德·卫林奖。

工业界  
  

1998年，接受了电子前哨基金会先锋奖。
2000年，被英国电脑学会授予洛夫莱斯勋章。
2001年，与理查德·斯托曼和坂村健分享为了社会／经济福祉的武田奖。
2008年，入选到加州山景城的计算机历史博物馆的资深会员堂（Hall of Fellows）。
```  
# 为网站添加Google Analytics统计  
编辑/themes/even/layouts/partials/head.html  
需将XXXXXXXXXX进行替换  
添加  
```
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-GKCHZ5FEPG"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-XXXXXXXXXX');
</script>
```  
# 为网站添加计时功能  
编辑/themes/even/layouts/partials/footer.html  
添加  
```
<center>
<script>
  function siteTime() {
      var seconds = 1000;
      var minutes = seconds * 60;
      var hours = minutes * 60;
      var days = hours * 24;
      var years = days * 365;
      var today = new Date();
      var startYear = 2001;
      var startMonth = 1;
      var startDate = 1;
      var startHour = 0;
      var startMinute = 0;
      var startSecond = 0;
      var todayYear = today.getFullYear();
      var todayMonth = today.getMonth() + 1;
      var todayDate = today.getDate();
      var todayHour = today.getHours();
      var todayMinute = today.getMinutes();
      var todaySecond = today.getSeconds();
      var t1 = Date.UTC(startYear, startMonth, startDate, startHour, startMinute, startSecond);
      var t2 = Date.UTC(todayYear, todayMonth, todayDate, todayHour, todayMinute, todaySecond);
      var diff = t2 - t1;
      var diffYears = Math.floor(diff / years);
      var diffDays = Math.floor((diff / days) - diffYears * 365);
      var diffHours = Math.floor((diff - (diffYears * 365 + diffDays) * days) / hours);
      var diffMinutes = Math.floor((diff - (diffYears * 365 + diffDays) * days - diffHours * hours) /
          minutes);
      var diffSeconds = Math.floor((diff - (diffYears * 365 + diffDays) * days - diffHours * hours -
          diffMinutes * minutes) / seconds);
      if (startYear == todayYear) {
          //document.getElementById("year").innerHTML = todayYear;
          document.getElementById("sitetime").innerHTML = "本站已运行 " + diffDays + " 天 " + diffHours +
              " 小时 " + diffMinutes + " 分钟 " + diffSeconds + " 秒";
      } else {
          //document.getElementById("year").innerHTML = startYear + " - " + todayYear;
          document.getElementById("sitetime").innerHTML = "本站已运行 " + diffYears + " 年 " + diffDays +
              " 天 " + diffHours + " 小时 " + diffMinutes + " 分钟 " + diffSeconds + " 秒";
      }
  }
  setInterval(siteTime, 1000);
</script>
<span id="sitetime">载入运行时间...</span>
</center>
```  
# 创建文章  
创建一篇空文章  
```
hugo new post/helloworld.md
```  
需要将生成文章头部的draft=true修改为draft=false  
# 启动 hugo 服务器  
```
hugo server -D
```  
启动 hugo 服务器，进入 http://127.0.0.1:1313/ 预览页面  
# 构建静态页面  
若要将博客托管在 github 上，需要上传静态页面。所以，需要使用 hugo 构建静态页面，构建命令如下  
```
hugo
```  
本次该命令将在建立git仓库后执行  
# 使用 Github Pages 搭建个人博客  
GitHub Pages 是一项静态站点托管服务，它直接从 GitHub 上的仓库获取 index.html、HTML、CSS 和 JavaScript 文件，也可以通过构建过程运行文件，然后发布网站  
创建一个新的 github 项目，项目名称需要是username.github.io格式，如下图样例  
![2](/img/screenshot.png)  
# 上传 github pages 项目  
静态页面生成完成后，便可以将整个静态页面以及本项目其他文件上传到 github 项目中。先使用git remote命令添加远端仓库，将文件提交（git add+git commit），最后推送到 Github Pages 项目中  
进入/public目录  
```
git init
git remote add origin git@github.com:alphaokxyz/alphaokxyz.github.io.git
git pull origin main
git checkout main
```  
现在进入网站根目录执行命令，构建hugo  
```
hugo
```  
返回到/public目录，继续推送到github  
```
git add .
git commit -m "1 commit"
git push -u origin main
```  
最后，打开https://alphaokxyz.github.io/  
完成  