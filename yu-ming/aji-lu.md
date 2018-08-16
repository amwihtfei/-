### 域名解析

#### 记录值的区别和灵活运用

|  | 功能介绍 | 好处 |
| :--- | :--- | :--- |
| a记录 | 域名对应解析到指定ip |  |
| cname记录 | 可以多个别名cname，解析到一个指定的域名\(非ip\)；比如a.weidinner.com b.weidinner.com可以解析指向到c.weidinner.com，确保走向 | saas系统，或者多个项目的域名，可以解析到一个指定域名；这样可以公用一个ip和项目代码，减少维护的成本 |

#### 代码进行域名解析

方式：通过aliyun的openapi进行域名的自动化解析

composer包：

```
composer require ykaej/aliyun

```

#### saas系统，租户和域名的绑定



