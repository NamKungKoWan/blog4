---
author: 星の物語
title: 在ubuntu22.04上安裝mediawiki 記錄
description: 
date: 2022-07-05
slug: 
image: 
categories:
    - 
    - 测试
---

## 我想说些什么？

先安裝net-tool,vim。

#### 安裝php7.4.3 （以下命令可安裝所有需要的軟件） （官網上說不兼容php8）

{{< highlight html >}}
apt install imagemagick php7.4-fpm php7.4-intl php7.4-xml php7.4-curl php7.4-gd php7.4-mbstring php7.4-mysql php7.4-mysql php7.4-apcu php7.4-zip
{{< /highlight >}}



## 安裝apache

## 安裝mariadb


{{< highlight html >}}
apt install mariadb-server
{{< /highlight >}}

設置數據庫密碼：
{{< highlight html >}}
mysql -u root p
{{< /highlight >}}

## 在mariadb上創建用戶
{{< highlight html >}}
CREATE DATABASE wikidb;

CREATE USER 'wikiuser'@'localhost' IDENTIFIED BY 'password';

GRANT ALL PRIVILEGES ON wikidb.* TO 'wikiuser'@'localhost' WITH GRANT OPTION;
{{< /highlight >}}

## 給wikidb用戶設置密碼
{{< highlight html >}}
set password for 'wikiuser'@'localhost'=password('设置mysql密码');         //不然在設置localsetting.php時會出問題

flush privileges;

quit

service mysql stop

service mysql restart 
{{< /highlight >}}