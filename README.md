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