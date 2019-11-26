![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 使数据库离线和在线
#### Take SQL Database Offline And Online
**发布-日期: 2016年02月26日 (评论)**

![#](images/##############?raw=true "#")

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
这是一些使数据库脱机，然后再次联机的快速SQL逻辑。它对维护参考很有帮助。


## English
Here’s some quick SQL logic that will take the database offline, then online again. It’s helpful for maintenance reference.



---
## Logic (Take SQL Databases Offline)
```SQL
use master;
set nocount on
 
-- check if database is online.  if so proceed to take offline.  if not; do nothing.
--检查数据库是否在线。如果在线，设置为离线。如果离线，什么都不用做。
if exists(select state_desc from sys.databases where name = 'MyDatabase' and state_desc = 'online')
    begin
        alter database [MyDatabase] set offline with rollback immediate;
    end
    else
        print 'The database is already offline. No changes will be made';
 
-- confirm the database is OFFLINE.
--确认数据库处于脱机状态。
select
    'server_name'       = upper(@@servername)
,   'database_name'     = upper(name)
,   'is_offline'        = state_desc
from
    sys.databases
where
    name = 'MyDatabase';
 
-- set database online
--设置数据库联机

alter database [MyDatabase] set online;
 
-- confirm the database is ONLINE.
--确认数据库已联机。
select
    'server_name'       = upper(@@servername)
,   'database_name'     = upper(name)
,   'is_offline'        = state_desc
from
    sys.databases
where
    name = 'MyDatabase';


```

---

---
## Logic (Take SQL Databases Online)
```SQL
use master;
set nocount on
 
-- check if database is online.  if so proceed to take offline.  if not; do nothing.
--检查数据库是否在线。如果在线，设置为离线。如果离线，什么都不用做。
if exists(select state_desc from sys.databases where name = 'MyDatabase' and state_desc = 'online')
    begin
        alter database [MyDatabase] set offline with rollback immediate;
    end
    else
        print 'The database is already offline. No changes will be made';
 
-- confirm the database is OFFLINE.
--确认数据库处于脱机状态。
select
    'server_name'       = upper(@@servername)
,   'database_name'     = upper(name)
,   'is_offline'        = state_desc
from
    sys.databases
where
    name = 'MyDatabase';
 
-- set database online
--设置数据库联机
alter database [MyDatabase] set online;
 
-- confirm the database is ONLINE.
--确认数据库已联机。
select
    'server_name'       = upper(@@servername)
,   'database_name'     = upper(name)
,   'is_offline'        = state_desc
from
    sys.databases
where
    name = 'MyDatabase';


```




[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

