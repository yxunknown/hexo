---
title: dict的update
date: 2019-03-20 22:30:27
tags: 
- Python
- dict
categories: Pythonic
---

Python字典的update方法，真的是一个很神奇而又好用的方法。简单来说，update的行为就是对于原字典不存在的键，则把键值对添加到原字典；若原字典存在该键，则被该键的值更新到原字典中去。

最近经历的项目中，一些配置以json格式的文件进行持久化。然后通过json.loads函数将文件内容加载为字典。对配置文件进行更新或者修改的时候，update方法就太帅气了。

```python
# 比如旧配置是这样
cgf = {
    "enabled": "true",
    "max_value": 90,
    "last_time": 5,
    "alert": "true",
    "item": "delay"
}
# 新配置是这样
new_cfg = {
    "enabled": "true",
    "max_value": 80,
    "last_time": 3,
    "alert": "true"
}
# 然后这样就可以快速的把新配置和就配置合并了
cfg.update(new_cfg)
"""
{
    "enabled": "true",
    "max_value": 80,
    "last_time": 3,
    "alert": "true",
    "item": "delay"
}
"""
```

现在，很沙雕的事情出现了。在配置的内容中，要先增加一项东西，比如说推送邮箱。新上报的配置信息如下：

```python
new_cfg = {
    "enabled": "true",
    "max_value": 80,
    "last_time": 3,
    "alert": "true",
    "email": "someone@ab.com"
}
cfg.update(new_cfg)
# 合并后配置如下
"""
{
    "enabled": "true",
    "max_value": 80,
    "last_time": 3,
    "alert": "true",
    "item": "delay",
    "email": "someone@ab.com"
}
"""
```

