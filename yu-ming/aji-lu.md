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

 $dns = app('aliyun_dns');
 //获取所有子域名
 $dns->aliyunDnsList('domain.com');
 // or 
 $domain->aliyunDnsList('domain.com');

 //添加一个子域名解析
 $dns->aliyunDnsCreate($domainName, $rr, $value, $type='A', $ttl=600, $line='default');
 // or 
 $domain->aliyunDnsCreate($domainName, $rr, $value, $type='A', $ttl=600, $line='default');

 //修改一个子域名解析
 $domain->aliyunDnsUpdate($recordId, $rr, $value, $type='A', $ttl=600, $line='default');

 //修改一个子域名解析状态
 $domain->aliyunDnsEditStatus($record_id, $status); //当前状态 status : 'Disable' or 'Enable'

 //删除一个子域名
 $domain->aliyunDnsDelete($record_id);
```

#### saas系统，租户和域名的绑定

逻辑：通过tenancy的website自动生成唯一的uuid，然后绑定域名，同时通过laraveldiamante使用阿里云自动化生成子域名解析即可。

好处：

1. 数据库等信息，可以进行自动化的隔离：可以将数据库部署在不同的服务器上，方便进行私有化部署。
2. 数据



