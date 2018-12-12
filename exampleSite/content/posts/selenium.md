---
author: "zhangyunlong"
date: 2018-11-27
linktitle: selenium
title: 浏览器自动化测试框架
categories: [ "Development", "python" ]
tags: ["python", "browser"]
weight: 10
---


## Introduction

Selenium是一套不同的软件工具，每种工具都有不同的方法来支持测试自动化。大多数Selenium QA工程师专注于最能满足其项目需求的一个或两个工具，但学习所有工具将为您提供许多不同的选项来处理不同的测试自动化问题。整套工具产生了丰富的测试功能，专门针对所有类型的Web应用程序的测试需求。这些操作非常灵活，允许使用许多选项来定位UI元素，并将预期的测试结果与实际的应用程序行为进行比较。Selenium的一个主要功能是支持在多个浏览器平台上执行一个测试。

[官方文档](https://docs.seleniumhq.org/docs/03_webdriver.jsp#chapter03-reference)
## 安装 selenium

```
pip install selenium
```
## 下载浏览器驱动

[在这里下载](https://docs.seleniumhq.org/download/)
[这里也可以](https://blog.csdn.net/tymatlab/article/details/78649727)
## 起步

- 创建一个测试浏览器窗口（这里我把chrome浏览器驱动放在了同目录的bin文件夹下）

```
from selenium import webdriver
browserName = webdriver.Chrome('./bin/chromedriver');
```
- 打开页面

```
browserName.get('http://www.baidu.com');
```
## 获取页面元素

- 按ID

```
element = driver.find_element_by_id("coolestWidgetEvah")

or

from selenium.webdriver.common.by import By
element = driver.find_element(by=By.ID, value="coolestWidgetEvah")
```
- 按类名

```
cheeses = driver.find_elements_by_class_name("cheese")

or

from selenium.webdriver.common.by import By
cheeses = driver.find_elements(By.CLASS_NAME, "cheese")

```

- 按标签名

```
frame = driver.find_element_by_tag_name("iframe")

or

from selenium.webdriver.common.by import By
frame = driver.find_element(By.TAG_NAME, "iframe")
```

- 按名称

```
<input name="cheese" type="text"/>

cheese = driver.find_element_by_name("cheese")

or

from selenium.webdriver.common.by import By
cheese = driver.find_element(By.NAME, "cheese")

```

- a链接文字

```
<a href="http://www.google.com/search?q=cheese">cheeseLink</a>

cheese = driver.find_element_by_link_text("cheeseLink")

or

from selenium.webdriver.common.by import By
cheese = driver.find_element(By.LINK_TEXT, "cheeseLink")
```

- 部分a链接文字(模糊查找)

```
<a href="http://www.google.com/search?q=cheese">search for cheese</a>

cheese = driver.find_element_by_partial_link_text("cheese")

or

from selenium.webdriver.common.by import By
cheese = driver.find_element(By.PARTIAL_LINK_TEXT, "cheese")
```
- 按CSS

```
<div id="food"><span class="dairy">milk</span><span class="dairy aged">cheese</span></div>

cheese = driver.find_element_by_css_selector("#food span.dairy.aged")

or

from selenium.webdriver.common.by import By
cheese = driver.find_element(By.CSS_SELECTOR, "#food span.dairy.aged")
```

- 按xpath

```
如选择 id为uploadifive-file_upload下面的input
browserName.find_elements_by_xpath (".//*[@id='uploadifive-file_upload']/input")
```
## 获取文本值

```
element = driver.find_element_by_id("element_id")
element.text
```

## 填写表单

```
username = wait.until(EC.presence_of_element_located((By.ID, 'userLoginName')))
username.send_keys(user);
```

## 模拟单击

```
browserName.find_elements_by_xpath (".//*[@class='btn btn-success upload-btn']")[0].click();
```

## 同时驱动两个浏览器窗口

```
使用进程 调用 task函数

from multiprocessing import Pool

def main():
    process = Pool(2);
    process.apply_async(task, args=(1,"renjie"));
    process.apply_async(task, args=(2,"renjie"));
    process.close();
    process.join();
```
