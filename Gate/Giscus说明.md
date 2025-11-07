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

## 目前已知 bug

如果你不给上一级目录 md 先添加 Discussion 而是先给下级的页面添加的话，由于模糊匹配机制，在尝试搜索上级页面评论区的时候会搜索到下级页面的评论区。

如果你不幸卡了这个bug，那你得先建一个 Announcement 类别的 Discussion，然后名字是 *url 编码后的页面标题*，这样就能被优先匹配到了。

然鹅刚好你不是仓库所有者，你建不了 Announcement Discussion，那你只能取巧的绕远路：

- 找个没有创建 Discussion 的页面
- 评论让 bot 创建一条 Announcement Discussion
- 跑去仓库 Discussion 区给那条 Discussion 改名

修是能修好，缺点是 Discussion 的内容会比较乱。

所以尽量先给上级创建评论区，再创建下级的评论区

## 通过主题配置是否显示评论区

在 md 源文件前面的 frontmatter 里面写这个：
```
---
BookComments: false
---
```

就能关闭页面评论区的显示