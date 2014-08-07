Nutch Htmlunit Plugin
==============

### 项目简介

基于Apache Nutch 1.8和Htmlunit组件，实现对于AJAX加载类型页面的完整页面内容抓取解析。

### 主要特性

* **常规的HTML页面抓取**: 对于常规的例如新闻类没有AJAX特性的页面可以直接用Nutch自带的protocol-http插件抓取。

* **常规的AJAX页面抓取**: 对于绝大部分诸如jQuery ajax加载的页面，可以直接用protocol-htmlunit插件抓取。

* **特殊的AJAX请求页面抓取**: 诸如淘宝/天猫的页面采用了独特的Kissy Javascript组件，
导致htmlunit无法直接感知到需要等待Kissy发起的请求完成;通过等待页面加载解析内容判断处理实现此类页面数据抓取。

* **基于页面滚动的AJAX请求页面抓取**: 诸如淘宝/天猫的商品详情页面会基于页面滚动发起商品描述信息的加载，
通过protocol-htmlunit可以实现此类页面数据抓取。

### 运行体验

由于Nutch运行是基于Unix/Linux环境的，请自行准备Unix/Linux系统或Cygwin运行环境。

git clone整个工程代码后，进行本地git下载目录：

cd nutch-htmlunit/runtime/local
bin/crawl urls crawl false 1  //urls参数为爬虫入库url文件目录; crawl为爬虫输出目录; false本应为solr索引url参数，此处设置为false不做solr索引处理; 1为爬虫执行回数

### 扩展插件说明

* **protocol-htmlunit**: 基于Htmlunit实现的AJAX页面Fetcher插件

* **parse-s2jh**: 基于XPath解析页面元素内容; 基于数据库模式输出解析到结构化数据; 对于个别复杂类型AJAX页面定制判断页面加载完成的回调判断逻辑

* **index-s2jh**: 追加设置需要额外传递给solr索引的属性数据; 设定不需要索引的页面规则;

### 源码工程说明

整个工程基于Apache Nutch 1.8源码工程扩展插件实现，插件的定义和配置与官方插件处理模式一致，具体可参考Apache Nutch 1.8官方文档资料。
具体实现原理和代码，请自行导入Eclipse工程查看即可。