# 学生作业管理系统

[![GitHub stars](https://img.shields.io/github/stars/itning/Student-Homework-Management-System.svg)](https://github.com/itning/Student-Homework-Management-System/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/itning/Student-Homework-Management-System.svg)](https://github.com/itning/Student-Homework-Management-System/network)
[![GitHub watchers](https://img.shields.io/github/watchers/itning/Student-Homework-Management-System.svg?style=social&label=Watch)]()
[![GitHub followers](https://img.shields.io/github/followers/itning.svg?style=social&label=Follow)]()
[![GitHub issues](https://img.shields.io/github/issues/itning/Student-Homework-Management-System.svg)](https://github.com/itning/Student-Homework-Management-System/issues)

[![GitHub license](https://img.shields.io/github/license/itning/Student-Homework-Management-System.svg)](https://github.com/itning/Student-Homework-Management-System/blob/master/LICENSE)
[![GitHub last commit](https://img.shields.io/github/last-commit/itning/Student-Homework-Management-System.svg)]()
[![GitHub release](https://img.shields.io/github/release/itning/Student-Homework-Management-System.svg)]()
[![GitHub repo size in bytes](https://img.shields.io/github/repo-size/itning/Student-Homework-Management-System.svg)]()
[![language](https://img.shields.io/badge/language-JAVA-orange.svg)]()

**实现功能：**
	
	学生上传文件到系统中，后台统一命名存储文件，管理员登陆后可以批量下载后台打包过后的文件。
	
**项目所用框架：**

前端：
	
	1.JQuery
	2.Bootstrap
	3.Bootstrap-fileinput
后端：
	
	1.SpringMVC
	2.Spring
	3.MyBatis
	4.Shiro
**不足：**

	1.业务代码几乎全写在控制层
	2.全部下载时浏览器获取不到文件大小
	
**更新日志：**
    
    V:1.1.3(Bulid:20170601)
        1.减少了一些无用代码
        
    V:1.1.2(Bulid:20170531)
        1.优化登录页面逻辑
    
    V:1.1.1(Bulid:20170531)
        1.添加了QQ登录接口
        2.优化登录逻辑
        3.修复了一些已知BUG
    
**SQL：**
 -  user表
```
DROP TABLE IF EXISTS `user`;
CREATE TABLE `user` (
  `uid` varchar(255) NOT NULL,
  `username` varchar(255) NOT NULL,
  `password` varchar(255) NOT NULL,
  `headimg` varchar(255) DEFAULT NULL,
  `firstlogin` bit(1) NOT NULL,
  `name` varchar(255) NOT NULL,
  `percode` varchar(255) NOT NULL,
  `userOpenID` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`uid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
 -  orderinfo表
```
DROP TABLE IF EXISTS `orderinfo`;
CREATE TABLE `orderinfo` (
  `oid` int(11) NOT NULL,
  `oname` varchar(255) NOT NULL,
  `osubject` varchar(255) NOT NULL,
  `ostate` bit(1) NOT NULL,
  `otime` datetime NOT NULL ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`oid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
 -  history表
 ```
 DROP TABLE IF EXISTS `history`;
 CREATE TABLE `history` (
   `hid` varchar(255) NOT NULL,
   `huid` varchar(255) NOT NULL,
   `hoid` int(11) NOT NULL,
   `type` varchar(255) NOT NULL,
   `filepath` varchar(255) NOT NULL,
   `uptime` datetime NOT NULL ON UPDATE CURRENT_TIMESTAMP,
   `filesize` double NOT NULL,
   PRIMARY KEY (`hid`),
   KEY `FK_hoid_oid` (`hoid`),
   KEY `FK_huid_uid` (`huid`),
   CONSTRAINT `FK_hoid_oid` FOREIGN KEY (`hoid`) REFERENCES `orderinfo` (`oid`),
   CONSTRAINT `FK_huid_uid` FOREIGN KEY (`huid`) REFERENCES `user` (`uid`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
 ```
 - 添加测试数据和管理员账号
```
INSERT INTO `user` VALUES ('1', '201601010317', '123456789', 'aa.jpg', '\0', '管理员', 'admin', null);
INSERT INTO `user` VALUES ('2', '201601010300', '123456789', 'aa', '\0', '测试', 'user', null);
INSERT INTO `orderinfo` VALUES ('1765435', '类别', '学科', ' ', '2018-04-18 10:23:54');
```
**安装QQ互联SDK**
[官方下载互联SDK](http://qzonestyle.gtimg.cn/qzone/vas/opensns/res/doc/qqConnect_Server_SDK_java_v2.0.zip)
```
mvn install:install-file -Dfile=D:\a.jar -DgroupId=com.qq.connect -DartifactId=qq-connect -Dversion=2.0.0.RELEASE -Dpackaging=jar
```
**预览图片：**

[![Clf7jI.md.png](https://s1.ax1x.com/2018/04/25/Clf7jI.md.png)](https://imgchr.com/i/Clf7jI)
[![Clfv4g.png](https://s1.ax1x.com/2018/04/25/Clfv4g.png)](https://imgchr.com/i/Clfv4g)
[![ClfzCQ.md.png](https://s1.ax1x.com/2018/04/25/ClfzCQ.md.png)](https://imgchr.com/i/ClfzCQ)
[![ClhS3j.md.png](https://s1.ax1x.com/2018/04/25/ClhS3j.md.png)](https://imgchr.com/i/ClhS3j)