# 开发教程

> 此项目是基于原作者的 [tw93](https://github.com/tw93/weekly) 项目修改

### 新增功能
1. 评论使用[Waline](https://waline.js.org/),按教程配置即可
2. 文章TOC
3. busuanzi统计
4. 新增站内搜索(从[tw93](https://github.com/tw93/weekly)同步过来)
5. 夜间模式(从[tw93](https://github.com/tw93/weekly)同步过来)
6. 使用 [notion2md](https://github.com/thinkerchan/notion2md) 工作流，只要把项目部署到vercel即可自动更新
7. 新增命令： npm run fetch 20250501  场景：重新拉取该日期前一周的内容


### 项目配置
src/config.ts 中设置站点信息
```js
export const SITE = {
  "title": "测试狗",
  "author": "testdog",
  "description": "测试狗周刊",
  "cardDesc":"🤖 为你播报一周新鲜事",
  "keywords": "测试狗,testdog,testdog.cn",
  "icon": "https://telegram-file.vercel.app/api/file/BQACAgUAAxkDAAIBMGiwJkrWBgue5fa1ipcHmNreG9cGAAJCGQACDCGBVR8ccraBfN8zNgQ.png",
  "favicon": "https://github.githubassets.com/favicons/favicon.svg",
  "pic": "", // 默认头图 也可不填
  "homePage": "https://post.testdog.cn",
  "blogPage": "https://thinkerchan.com",
  "twitterId": "thinkerchan",
  "githubId": "thinkerchan",
  "repo": "thinkerchan/weekly",
  "cmtURL":"https://cmt.testdog.cn",
  "cmtJs":"https://unpkg.com/@waline/client@2.15.8/dist/waline.js",
  "cmtCss":"https://unpkg.com/@waline/client@2.15.8/dist/waline.css",
  "pv":true
}
```

md文档设置toc
```md
---
date: 2019/09/27
toc: true
---

xxxxxxxx
```

### 一、准备工作

1. Fork 本仓库到自己 Github 仓库下
2. 将代码 Clone 到本地，并确定已经安装好 node / npm 环境
3. 执行 `npm i` 安装模块依赖，然后执行 `npm run dev` 看是否可以跑起来

### 二、文档格式说明

1. 假如可以跑起来，可以去 `src/pages/posts` 只留一个 markdown 文件用于格式参考，或者加入自己的文件，文档说明如下
2. 第一行的文档建议是一个图片的展示，这样代码会自动取第一行为你的头图，也可以已通过 front matter 规范用 pic 字段表示，假如都没有填写，会使用默认的图片
3. 中间空一行，第三行是文档的描述，可以用 `small` 标签包裹，用于文字的描述部分，也可用 front matter 规范中 desc 字段表示，假如没有，会使用默认描述
4. 关于文档的时间，也是默认通过 node 取到文档的创建时间，假如不想要这个，也可用 front matter 规范中 date 字段表示
5. 关于文章的标题，可以用 `数字-标题` 的方式，方便很多地方的统一处理

### 部署说明

1. 推荐用 Vercel 部署
2. 首先确保 Fork 的代码已经传到 Github 中了, 然后进入 [Vercel](https://vercel.com/new) 选择 `Continue with GitHub`，将对应的仓库 import 进去
3. 导入后，确定 FRAMEWORK PRESET 是 Astro（[截图](https://gw.alipayobjects.com/zos/k/ic/0BffKE.png)），一般会默认选中，没有的话请选择这个，选择后，点击 Deploy 即可，稍等片刻，等待部署
4. 过了一会儿部署完成了，参考[截图](https://gw.alipayobjects.com/zos/k/e3/QLS7dG.png)位置，就是你的域名地址好了，点击进去就可以访问了，是不是很简单


### github actions
由于本项目使用了[notion2md](https://github.com/thinkerchan/notion2md) 工作流，数据都是从notion数据库定期自动同步过来的。因此要用到github actions。 可以看到[notion2md](https://github.com/thinkerchan/notion2md)的工作流介绍自行设置好`NOTION_TOKEN`和`NOTION_DATABASE_ID`两个变量

### 测试notion连接
如果你按上面步骤部署好了，可以测试notion连接是否正常。
```bash
npm run fetch // 可观察到posts文件夹下有新的md文件生成
```


---
感谢
- [tw93](https://github.com/tw93/weekly)
- [thinkerchan](https://github.com/thinkerchan/weekly)
