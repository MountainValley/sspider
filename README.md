# sspider (simple spider)

### Precondition

现在公司爬虫平台基于scrapy和scrapyd构建，使用过程中的痛点主要有：

1. 众所周知scrapy不支持分布式，分布主要使用scrapyd, 每个爬虫有一点变化都要重新打包上传，扔给调度平台进行调度, 太麻烦了
2. 公司业务大多是爬取特定的页面，文件等，并没有爬取整个站点的需求，用scrapy感觉偏重了
3. 在这个系统上面进行定制扩展并不简单，比如如果我需要接收信息爬取特定的页面，在这个系统几乎很难实现，实现了也很丑

### 实现

基于以上痛点，想写一个自己想要的爬虫平台。

在项目还没有写一行代码的时候，基于本人幻想，应该有以下特点：

1. 易于定制
2. 分布式
3. 简单

当然，基于本人目前仍是菜鸟中的菜鸟的技术水平，这个项目目前仍是学习折腾性质。

项目将主要参(chao)考(xi)：

1. Scrapy(不可否认scrapy的设计真的太帅了)
2. Django
3. rq(简单易用)

项目主要基于：

1. gevent
2. requests

### Architecture

主从架构，之间利用redis进行通信(参考`rq`)

#### 主节点

1. 任务注册
2. 任务调度
3. 任务统计，监控

#### 从节点

1. 争抢任务
2. 实例化任务

---

### Installation

当前版本`0.0.2`

```
pip install git+https://github.com/fucangyu/sspider.git@0.0.2
```

### Usage

参考`examples`

### TODO

1. spider模板
2. 监控
3. proxy
