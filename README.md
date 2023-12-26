## LaserScan目录扫描

LaserScan是本人在Golang学习中开发的一块高效、简单、实用、体积小的目录扫描工具

### 项目简介

在如今的渗透测试中，基本上所有白帽子都知道信息收集在漏洞挖掘中很重要。但是收集出来的信息如何最大化利用，如何从当前信息中定位出更脆弱的目标。我认为一个白帽子在处理收集来的信息时，应该有一套标准化的流程。例如收集到了目标上百个子域名，就应该给处理子域名指定一套标准化的流程。

1. 对子域名的IP进行整理，标记IP权重
2. 扫描IP、IP段开放的端口
3. 根据扫描端口过滤出一些脆弱性的服务
4. 扫描子域名、IP、IP段WEB服务
5. 目录扫描、POC扫描
6. 指纹筛查

`LaserScan`主要是用来实现第五步的目录扫描

### 功能介绍

#### 实现功能

1. 自定义超时时间
2. 自定义延时请求时间
3. 自定义线程
4. 内置关键字跳过【目前内置了一些waf的关键字，检测到会自动停止程序】
5. 集成佩奇文库POC路径【会直接扫描一些漏洞的API,未实现】
6. 扫描进度条【可能会有一些凌乱】

#### 待实现功能

1. 设置代理功能
2. 批量IP扫描目录功能
3. 随机fuzz请求头
4. Body长度去重

### 使用说明

```
Usage of LaserScan.exe:
  -e int
        -e 指定超时时间,如: -e 3 (default 5)
  -f string
        -f 指定加载字典路径,如: -f xx.txt (default "./dict.txt")
  -s int
        -s 指定请求延迟时间,如: -s 3,默认线程为0
  -t int
        -t 指定线程,如: -t 3,默认线程为5 (default 5)
  -u string
        -u 指定url目标地址,如: -u https://example.com
 若默认请求延迟和超时时间，则可直接使用LaserScan.exe -u https://example.com -f dict.txt即可
```

### 使用截图

![image](https://user-images.githubusercontent.com/87681228/224193701-ffeafae5-ca72-4389-85fb-b2d45f21f6b0.png)

![image](https://user-images.githubusercontent.com/87681228/224193798-2cf08de6-0a1b-47ac-a177-ea071215137b.png)
