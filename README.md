# blog-generator
A blog generator with my own theme customized upon PaperMod.  
基于 hugo 的 PaperMod, 简单做了下修改, 仍在完善中。

## Initialize
- 初始化过程已**截图**
    - hugo new site
    - PaperMod 主题安装
    - hugo.yaml
        - theme: "PaperMod"
- 修改 archetypes/default.md 为 yaml 格式
- 添加 .gitignore
- 添加 .gitkeep 占位

## Theme Customize
- **layouts & assets**
    - theme-vars.css
        - **主题颜色**, 仅注释, 待后续调整
    - anchored_headings.css & anchored_headings.html
        - anchor of [h1-h6] 的图案、颜色
    - archives.html
        - 仅注释, 标记下 ShowAllPagesInArchive 和 mainSections 的位置
    - breadcrumbs.html
        - breadcrumb 格式: 🔖 Yiny
    - footer.html
        - copyright 格式: © 2024 Yiny's Blog
    - 404.html
    - robots.txt
        - 禁止爬虫

## Theme Customize - Search
- **search.html**
    - 修改显示格式
- **Section Search**
    - /index.json(默认) : 只在根目录生成用于 search 的 json, 即只有全局搜索(site.RegularPages)
    - section search: 我希望 section 的搜索结果不受其他 section 影响, 即局部搜索
        - **list.json:** 生成 section 的 json
        - **list.html:** 在 list page 里增加 🔍 按钮

## Theme Configure
- **archetypes/default.md**
- **content/ - 骨架搭建**
    - 几个特殊的 .md 文件
        - about(关于): 不写自己, 写点祝福吧
        - blogroll(友链): 待填
        - archives(文章), 多个 search(搜索). ==注意配置 "layout" 才会生效==
    - 关联配置: menu buttons socialIcons taxonomies(暂时维持默认)
- **static 图标**
    - 头像: avatar/*
    - 封面: about/*
    - favicon/*
- **hugo.yaml**
    - 按 [PaperMod wiki](https://github.com/adityatelange/hugo-PaperMod/wiki/) 与 [Hugo Doc](https://gohugo.io/getting-started/configuration/) 修改配置
        - profile-mode copyright ...
        - 暂未启用: comments, share, ShowPostNavLinks(上一页下一页), hidemeta ...
        - 详情参考配置文件

## Theme Configure - rawhtml
- **配置 [markup.goldmark.renderer.unsafe]: true**
    - goldmark 默认不会渲染 html, 需要在 markdown 里用 `{{ rawhtml}}` `{{ /rawhtml }}`
    - 启用以能在 markdown 里直接使用 html, 顺便把 about.md 改了
    - ps. 在模版里用 safehtml

## Theme Customize - Add Animation Effects
- 新增特效
    - **fish.js** - 底部小鱼跃动特效
    - **canvas-nest** - 蛛网背景
    - **cursor**
    - **firework.js** - 鼠标点击特效
    - **Aplayer** - 音乐播放器, 音乐外链
- 相关文件
    - **assets/**
        - css/extended/
            cursors.css, fish.css
        - js/*
    - **layouts/**
        - partials/**extended_footer.html**
    - **static/**
        - audio/*
        - cursors/*

## bugFix - cursors 获取失败 404
- 问题描述
    - 本地运行正常, 但是 GitHub Page 显示异常, 报错 404 即文件下载异常
- 原因分析
    - css 路径写的有问题, 原以为是需要带域名 wooyiny.github.io
    - 结果是因为 url 最后的  `\` 被一起识别进后缀名 `.png\` 导致文件类型识别异常, 太离谱了

## Refactor - Aplayer 改用外链访问资源
- 问题描述
    - Github 的仓库免费空间和网速都有限制,  将音频文件原封上传属实太大了, 用外链更合适
- 具体实现
    -  **extend_footer.html** - Aplayer 配置里的 URL 改用外链
        - 目前使用的 Github Repo + PicGo + jsdelivr 的方案, 设置了两个仓库, 一个用做图床, 一个用于音乐外链
    - 删除 static/**audio**/*
- 后续
    - 资源还是得慢慢上云才行, 否则本体太大无法接受

## Refactor - 外链访问
- Aplayer 外链重构 (audio cover lrc), 并修改歌词颜色
- copyright 右对齐, 主要是和歌词的位置冲突了
- about 改用外链 avator cursor favicon 暂时保留

## Theme Update
- PaperMod 主题更新. 理由: 当前版本显示 logo 有 bug, 观感很不好
    - separator displayed with Single lang sites
- 注意
    - submodule 的 HEAD 是分离状态, 要 checkout 到 master 才能 pull
    - 更新完记得 detach HEAD, 以防之后自动跟着更新

## Refactor - about 外链地址
- about 外链地址写错了
- content 目录名改了几个

## bugFix - 目录重命名后访问异常
- 问题描述
    - 目录名关联三个功能: menu、archives 搜索、 button 主页图标
    - 重命名后, 配置文件忘记改了, 造成访问异常

## Refactor - TI5 cursor
- 目录名从 *cursors* 改用 *cursor*
- 改用 DOTA2 TI5 金叶子指针

## bugFix - search 功能异常
- 原因
    - 配置文件必须配上 [outputs:], 否则缺少 json 文件会导致搜索功能异常