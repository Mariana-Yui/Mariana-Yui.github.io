---
layout: post
title: VScode代码规范
subtitle: 利用editorconfig, prettier, eslint
date: 2020-01-20
author: Mariana
header-img: img/post-bg-1.jpg
catalog: true
tags:
  - 前端
  - vscode
---

## 背景

马上就要大学毕业工作了，实习过程中意识到自己以前一直不在意的团队协作中的代码规范重要性。现在整理一下供以后温习，写的很随意，仅供参考。

## vscode 中的 editorconfig, prettier, eslint

三者是渐进的过程。  
editorconfig 配置编码时的代码风格，prettier 配置编码后的保存时的规范，eslint 和 prettier 类似，但 prettier 不会仅仅是定义规范，不会对不符合规范的代码抛出错误或警告，eslint 则会检查语法，在例如变量未定义时抛出错误。

## editorconfig 配置

1. 安装 editorconfig 包 `npm install -g editorconfig`
2. 安装 vscode 扩展 `ext install EditorConfig`
3. 在项目根目录新建.editorconfig 文件

配置参考：

```sh
# This is the top-most .editorconfig file (do not search in parent directories)
root = true

### All files
[*]
# Force charset utf-8
charset = utf-8
# Indentation
indent_style = tab
indent_size = 4
# line breaks and whitespace
insert_final_newline = true
trim_trailing_whitespace = true
# end_of_line = lf

### Frontend files
[*.{css,scss,less,js,json,ts,sass,php,html,hbs,mustache,phtml,html.twig}]

### Markdown
[*.md]
indent_style = space
indent_size = 4
trim_trailing_whitespace = false

### YAML
[*.yml]
indent_style = space
indent_size = 2

### Specific files
[{package,bower}.json]
indent_style = space
indent_size = 2
```

## prettier 配置

1. 安装 prettier 包 `npm install -g prettier`
2. 安装 prettier for vscode 插件
3. 新建.prettierrc 文件

配置参考：全部参数[here](https://prettier.io/docs/en/configuration.html)

```sh
{
  "semi": true,
  "trailingComma": "all",
  "singleQuote": true,
  "printWidth": 70,
}
```

## eslint 配置

1. 安装 eslint 包 `npm install -g eslint`
2. 初始化 eslint 文件 `eslint --init`, 这里我选择 json 文件 eslint 不生效不知道为什么，换成 js 文件就好了。
3. 配置 .eslintrc.js 文件

配置参考：
```js
module.exports = {
	env: {
		browser: true,
		commonjs: true,
		es6: true,
	},
	extends: ['eslint:recommended'],
	parserOptions: {
		sourceType: 'module',
	},
	rules: {
		indent: ['error', 'tab'],
		'linebreak-style': ['error', 'unix'],
		quotes: ['error', 'single'],
		semi: ['error', 'never'],
	},
}
```

参考资料：  
[editorconfig vs prettier vs eslint](https://stackoverflow.com/questions/48363647/editorconfig-vs-eslint-vs-prettier-is-it-worthwhile-to-use-them-all)  
[editorconfig配置](https://stackoverflow.com/questions/46846128/editorconfig-for-vs-code-not-working)  
[prettier配置](https://www.robinwieruch.de/how-to-use-prettier-vscode)
[eslint配置](https://segmentfault.com/a/1190000009077086)  
[eslint中js规范配置参考](https://juejin.im/post/5cd3f035e51d456e6479b538#heading-4)  
