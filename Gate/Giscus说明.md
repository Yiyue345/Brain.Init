---
title: Giscus说明
toc: true
---

## Giscus 是什么

感兴趣自己搜。

简单讲就是基于 Github Discussion 实现的评论系统。评论都会存在仓库的 Discussion 功能中。

## 管理员需要注意的是

因为配置 Giscus 的时候选择使用 Announcement 来配置，所以新的 Discussion 只能由仓库所有者或者有读写权限的人员创建。而每一个页面都对应一个 Discussion。

**所以你想要给大家开放评论的话，你需要先发一条评论(或者给一个react反应)自动创建一个 Discussion，这样其他人才能评论**

## 通过主题配置是否显示评论区

在 md 源文件前面的 frontmatter 里面写这个：
```
---
BookComments: false
---
```

就能关闭页面评论区的显示