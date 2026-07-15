# cnki-browser-three-layer-search
替代垃圾CNKIAI的增强版skill，调用本地谷歌浏览器进行cnki检索，学术发现式搜索策略。

特色：

复刻学术训练基础能力——关键词发散式深层搜索；

① 在对话中指定一个或一组关注领域后，LLM生成一组概念簇，作为1层检索词；

② 调用本地有头谷歌浏览器进入CNKI（自行解决论文账号和IP权限），执行1层搜索；

③ 对单个关键词的搜索结果进行扫描（重点内容可通过指令深入到正文），分别与概念簇内或其他概念簇关键词进行匹配；

④ 形成认知，获得新关键词，进行2层单独关键词搜索（用于增强命中）

⑤ 继续进行匹配和验证

⑥ 每轮对话沉淀md文档，写入Nowledge Mem MCP。

使用要求

### 1.有头浏览器MCP配置

有些工具会强制调用默认无头浏览器来做桌面浏览器操作，所以需要额外配置一个指向本地谷歌浏览器的MCP

可以考虑打开仓库中的Google Chrome MCP Config.md替换掉自己的路径配置MCP的Json，也可以用GUI配置：

服务器名称

```
cnki-browser
```

服务器类型

```
stdio
```

命令

```
npx（或者本地npx路径）
```

参数

```
-y
chrome-devtools-mcp@latest
--executablePath=C:\Program Files\Google\Chrome\Application\chrome.exe（指向你的本地谷歌浏览器根目录）
--headless=false
--userDataDir=C:\Users\B.H.Liu\AppData\Local\chrome-devtools-mcp\cnki-profile（自己定义，用来存放自动化浏览器的缓存）
```

环境变量留空

## 2.加载skill（复制或者导入）

略

## 3.如果需要，可以配置nowledgememMCP，需要配合本地Nowledge Mem使用，见[Nowledge Mem]([Nowledge Mem | Nowledge Mem](https://mem.nowledge.co/zh/docs))。
