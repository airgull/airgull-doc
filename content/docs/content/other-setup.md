---
title: "一些需要重点注意的配置"
linkTitle: "其它设置"
weight: 4
---

有些配置很重要，但有时并不太注意

## 每篇文章显示更新时间的问题

1. 在`config.toml`中设置从 git 提交信息中取时间
  ```toml
  # Will give values to .Lastmod etc.
  enableGitInfo = true
  ```
2. 设置 git 的全局属性`core.quotepath`为`false`，如果不设置，中文文件名将不会记录最后修改日期
  ```shell
  git config --global core.quotepath false
  ```




