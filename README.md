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